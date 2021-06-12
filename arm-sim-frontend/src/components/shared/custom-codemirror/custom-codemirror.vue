<template>
    <div class="sofy-codemirror">
        <div class="editorOptions " v-if="sqlEditorEnabled">
            <a 
                id="codeButton" 
                style="text-decoration: none; padding: .2em .2em .2em .2em;" 
                :class="['pull-right', { fullButton: fullScreen }]" 
                @click="toggleScreen()" 
                title="Toggle fullscreen">
                <i style="color: black;" class="fa fa-expand" aria-hidden="true" />
            </a>
            <uiv-popover trigger="hover-focus" placement="left">
                <a  style="text-decoration: none; padding: .2em .2em .2em .2em;" 
                    class="pull-right"
                    >
                    <i class="fa fa-info-circle" style="margin-right: 15px;color: black;" aria-hidden="true"></i>
                </a>
            </uiv-popover>

        </div>
        <div style="border:1px solid #DDD;position: relative;">
            <button 
                id="codeButton" 
                v-if="!sqlEditorEnabled" 
                :class="['pull-right', fullScreen ? 'fullButton':'smallButton']" 
                @click="toggleScreen()" 
                title="Toggle fullscreen">
                <i class="fa fa-arrows-alt" aria-hidden="true"></i>
            </button>
            <codemirror 
                ref="cm" 
                class="higher" 
                v-model="text"
                :options="cmOptions" 
                @input="$emit('input', text)"
                />
        </div>  
    </div>
</template>

<script>
import Vue from 'vue'

import VueCodeMirror from 'codemirror'
import 'codemirror/theme/solarized.css'
import 'codemirror/addon/display/fullscreen.js'
import 'codemirror/addon/display/autorefresh.js'
import 'codemirror/mode/armasm/armasm.js'
import 'codemirror/addon/dialog/dialog.js'
import 'codemirror/addon/search/searchcursor.js'
import 'codemirror/addon/search/search.js'
import 'codemirror/addon/scroll/annotatescrollbar.js'
import 'codemirror/addon/search/matchesonscrollbar.js'
import 'codemirror/addon/search/jump-to-line.js'
import 'codemirror/addon/hint/show-hint.js'
import 'codemirror/addon/hint/css-hint.js'

import 'codemirror/lib/codemirror.css'
import 'codemirror/addon/dialog/dialog.css'
import 'codemirror/addon/display/fullscreen.css'
import 'codemirror/addon/search/matchesonscrollbar.css'
import 'codemirror/addon/hint/show-hint.css'

import VueCodemirror from 'vue-codemirror'
import { Notification } from 'uiv'

Vue.use(VueCodemirror)

export default {
    props: {
        value: String,
        sqlEditorEnabled: Boolean,
        options: Object,
    },

    components: { VueCodeMirror },

    data() {
        return {
            text: this.value,
            fullScreen: false,
            cm: null,
            cmOptions: {},
        }
    },

    watch: {
        value(nv) {
            this.text = nv
        },
        options(nv) {
            this.cmOptions = nv
        },
    },

    created() {
        const self = this

        this.cmOptions = this.options || {
            autoRefresh: true,
            tabSize: 4,
            styleActiveLine: true,
            lineNumbers: true,
            line: true,
            mode: 'text/x-armasm',
            theme: 'solarized light',
            height: '400px',
            extraKeys: {
                F11(cm) {
                    self.toggleScreen()
                },
                Esc(cm) {
                    if (cm.getOption('fullScreen')) {
                        setTimeout(() => {
                            cm.setOption('fullScreen', false)
                            self.fullScreen = false
                        })
                    }
                },
                'Ctrl-Space': 'autocomplete',
                'Alt-F': 'findPersistent',
                'Ctrl-Enter'(cm) {
                    if (self.sqlEditorEnabled !== true) return
                    self.execute()
                },
                F5(cm) {
                    if (self.sqlEditorEnabled !== true) return
                    self.execute()
                },
                F2(cm) {
                    if (self.sqlEditorEnabled !== true) return
                    setTimeout(() => {
                        var positionOfCursor = cm.getCursor()
                        cm.replaceSelection('SELECT TOP 100 * FROM ')
                        cm.setCursor(
                            positionOfCursor.line,
                            positionOfCursor.ch + 23,
                        )
                        cm.focus()
                        cm.refresh()
                    })
                },
            },
        }
    },

    mounted() {
        this.cm = this.$refs.cm.codemirror
    },

    methods: {
        addField(fieldName) {
            this.cm.replaceSelection(fieldName)
        },

        execute() {
            let query = ''
            if (this.sqlEditorEnabled === true) {
                query = this.cm.getSelection()
            }
            if (query === '') {
                query = this.text
            }
            query = query.trim()
            if (query === '' || query.length < 5) {
                console.log('>>>>>>', Object.keys(this))
                Notification.notify({
                    type: 'warning',
                    content: 'Please write atleast one query',
                })
            } else {
                this.$emit('execute', query)
            }
        },

        comment() {
            if (this.sqlEditorEnabled !== true) return

            if (
                this.cm.getSelection() !== undefined &&
                this.cm.getSelection() !== null &&
                this.cm.getSelection() !== ''
            ) {
                const range = this.cm.listSelections()
                range[0].anchor.ch = 0

                let textToBeCommented = this.cm.getRange(
                    range[0].anchor,
                    range[0].head,
                )
                textToBeCommented = '--' + textToBeCommented
                textToBeCommented = textToBeCommented.replace(
                    new RegExp('\n', 'g'),
                    '\n--',
                )

                setTimeout(() =>
                    this.cm.replaceRange(
                        textToBeCommented,
                        range[0].anchor,
                        range[0].head,
                    ),
                )
            }
        },

        unComment() {
            if (this.sqlEditorEnabled !== true) return

            if (
                this.cm.getSelection() !== undefined &&
                this.cm.getSelection() !== null &&
                this.cm.getSelection() !== ''
            ) {
                const patternToCheckExistenceOfCommentedCode = new RegExp(
                    /^(--)([0-9|a-z|A-Z]*)/,
                )
                const range = this.cm.listSelections()
                range[0].anchor.ch = 0

                let textToBeUnCommented = this.cm.getRange(
                    range[0].anchor,
                    range[0].head,
                )

                if (textToBeUnCommented !== null) {
                    if (
                        patternToCheckExistenceOfCommentedCode.test(
                            textToBeUnCommented,
                        )
                    ) {
                        textToBeUnCommented = textToBeUnCommented.replace(
                            /--/,
                            '',
                        )
                    }
                }
                if (textToBeUnCommented) {
                    textToBeUnCommented = textToBeUnCommented.replace(
                        new RegExp('\n--', 'g'),
                        '\n',
                    )
                }
                setTimeout(() =>
                    this.cm.replaceRange(
                        textToBeUnCommented,
                        range[0].anchor,
                        range[0].head,
                    ),
                )
            }
        },

        toggleScreen() {
            setTimeout(() => {
                this.cm.setOption(
                    'fullScreen',
                    !this.cm.getOption('fullScreen'),
                )

                this.fullScreen = !this.fullScreen

                // Elevate z-index of CodeMirror while it is in full screen mode,
                // because our app has an element with an even higher z-index.
                var modalElement = document.getElementsByClassName('modal')
                if (modalElement && modalElement.length > 0) {
                    if (this.fullScreen === true) {
                        modalElement[0].style.zIndex = '1200'
                    } else {
                        modalElement[0].style.zIndex = '1050'
                    }
                }
            }, 100)
        },
    },
}
</script>

<style lang="scss" scoped>
.higher {
    height: 400px;
    z-index: 900;
}
.fullButton {
    z-index: 1101;
    position: fixed;
    top: 10px;
    right: 15px;
    background: transparent;
    border: none;
}
.smallButton {
    z-index: 9;
    position: absolute;
    right: 0px;
    top: 0;
    background: transparent;
    opacity: 0.5;
    border: none;
}
.overlay {
    height: auto !important;
}
.editorOptions {
    background-color: #f5f5f5;
    padding: 0.5em 0.5em 0.5em 0.5em;
    border: 1px solid #ddd;
    border-bottom: 0px solid transparent !important;
}

.sofy-codemirror /deep/ {
    .CodeMirror-hints {
        z-index: 1100;
    }
    .CodeMirror-fullscreen {
        z-index: 1100;
    }
    .CodeMirror-sizer {
        margin-left: 30px !important;
        margin-bottom: -12px !important;
        border-right-width: 18px !important;
        min-height: 26px !important;
        padding-right: 0px !important;
        padding-bottom: 0px !important;
    }
    .CodeMirror-linenumbers {
        width: 29px !important;
        border-color: rgba(136, 133, 133, 0.18) !important;
    }
    .CodeMirror-gutters {
        width: auto !important;
    }
}
</style>


<style lang="scss">
.popover {
    max-width: 400px;
    min-width: 260px;
}
</style>

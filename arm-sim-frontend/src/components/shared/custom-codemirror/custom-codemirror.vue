<template>
    <div class="sofy-codemirror">
        <div style="border:1px solid #DDD;position: relative;">
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
    //import 'codemirror/mode/armasm/armasm.js'
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
                    'Ctrl-Space': 'autocomplete',
                    'Alt-F': 'findPersistent',
                },
            }
        },

        mounted() {
            this.cm = this.$refs.cm.codemirror
        },

        methods: {
        },
    }
</script>

<style>
</style>

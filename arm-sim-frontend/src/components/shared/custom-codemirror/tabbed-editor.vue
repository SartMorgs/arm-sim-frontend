<template>
    <div class="tabbed-editor">
        <uiv-tabs
            v-model="editorIndex" 
            @click.native="/fa fa-close/.test($event.target.className) && removeEditor($event.target.dataset.editorid)"
            @before-change="beforeChange">
            <uiv-tab
                v-for="item in sqlEditorList" 
                :title="`${item.title || 'Editor'} ${item.id+1} <i class='fa fa-close ${item.classToAdd}'  data-editorid='${item.id}'></i>`" 
                html-title
                :key="item.id"
                >
                <custom-codemirror 
                    @execute="log"
                    v-model="item.sql"
                    :sqlEditorEnabled="true"
                    :key="item.id"
                    />
            </uiv-tab>
        </uiv-tabs>
    </div>
</template>

<script>
// 1. Enter nothing in the editor and press Execute
// 2. Enter something in the editor and press Execute
// 3. Select some text in the editor and click execute
// 4. Click on an intem in the tree, which sets the editor text, and then click execute

import CustomCodemirror from './custom-codemirror'

export default {
    components: {
        CustomCodemirror,
    },
    methods: {
        addEditor(editor, title) {
            if (!editor || typeof (editor.sql + '') !== 'string') return
            editor.id = ++this.sqlEditorCount
            this.sqlEditorList.push(editor)
        },

        removeEditor(editorId) {
            let id = parseInt(editorId, 10)
            if (this.previousEditorIndex == null) return
            if (this.sqlEditorList.length === 1) {
                this.previousEditorIndex = null
                return
            }
            // if (this.sqlEditorList.length === 2) this.previousEditorIndex = 0

            this.sqlEditorList = this.sqlEditorList.filter(
                item => item.id !== id,
            )
            // if (this.previousEditorIndex > this.sqlEditorList.length - 1)
            // this.previousEditorIndex = 0
            this.editorIndex = this.sqlEditorList.findIndex(
                item => item.id === this.previousEditorIndex,
            )
        },

        beforeChange(from, to, done) {
            this.previousEditorIndex = this.sqlEditorList[from].id
            done()
        },
    },
    data() {
        return {
            previousEditorIndex: null,
            editorIndex: 0,
            sqlEditorCount: 0,
            showClose: false,
            sqlEditorList: [
                {
                    id: 0,
                    sql: '',
                    // classToAdd: 'hide_close_button',
                },
            ],
        }
    },

    created() {
        this.sqlEditorCount = this.sqlEditorList.length - 1
    },
}
</script>

<style>
.hide_close_button {
    display: none !important;
}
</style>

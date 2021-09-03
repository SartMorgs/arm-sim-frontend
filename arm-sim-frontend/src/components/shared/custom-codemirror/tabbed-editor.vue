<template>
    <div class="tabbed-editor">
        <custom-codemirror/>
    </div>
</template>

<script>

import CustomCodemirror from './custom-codemirror'

export default {
    components: {
        CustomCodemirror,
    },
    methods: {
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
}
</script>

<style scoped>
</style>
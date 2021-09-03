<template>
    <div>
        <div class="editor-area">
            <sim-menu/>
            <editor ref="tabbedEditor"/>
        </div>
        <div class="simulation-area">
            <rom-table></rom-table>

            <on-off-table title="Register Bank">
            </on-off-table>

            <on-off-table title="Data Memmory">
            </on-off-table>

            <on-off-table title="Device Memmory">
            </on-off-table>
        </div>
    </div>
</template>

<script>

    import TabbedEditor from './components/shared/custom-codemirror/tabbed-editor.vue'
    import ButtonsMenu from './components/shared/buttons-menu/buttons-menu.vue'
    import OnOffTable from './components/shared/on-off-table/on-off-table.vue'
    import RomTable from './components/shared/rom-table/rom-table.vue'

    export default {

        name: 'App',
        components: {
            "editor": TabbedEditor,
            "sim-menu": ButtonsMenu,
            "on-off-table": OnOffTable,
            "rom-table": RomTable
        },

        data() {
            return {
                data_memmory_fields: [
                    {
                        name: "teste",
                        value: "BBxBB"
                    },
                    {
                        name: "teste",
                        value: "BBxBB"
                    },
                    {
                        name: "teste",
                        value: "BBxBB"
                    },
                    {
                        name: "teste",
                        value: "BBxBB"
                    }
                ]
            }
        },

        methods: {

        }
    }

</script>
</style>

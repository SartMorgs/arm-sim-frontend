<template>
    <div class="arm-rom">
        <h2 class="rom-h2">ROM</h2>

        <table class="rom-table" cellspacing="0" cellpadding="0">
            <tr class="rom-table-column">
                <th class="rom-table-item">NAME</th>
                <th class="rom-table-item">ADDRESS</th>
                <th class="rom-table-item">BINARY INSTRUCTION</th>
                <th class="rom-table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="rom-table-column">
                <td class="rom-table-item">Alfreds Futterkiste</td>
                <td class="rom-table-item">Maria Anders</td>
                <td class="rom-table-item">Germany</td>
                <td class="rom-table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="rom-table-column">
                <td class="rom-table-item">Centro comercial Moctezuma</td>
                <td class="rom-table-item">Francisco Chang</td>
                <td class="rom-table-item">Mexico</td>
                <td class="rom-table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="rom-table-column">
                <td class="rom-table-item">Ernst Handel</td>
                <td class="rom-table-item">Roland Mendel</td>
                <td class="rom-table-item">Austria</td>
                <td class="rom-table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="rom-table-column">
                <td class="rom-table-item">Island Trading</td>
                <td class="rom-table-item">Helen Bennett</td>
                <td class="rom-table-item">UK</td>
                <td class="rom-table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="rom-table-column">
                <td class="rom-table-item">Laughing Bacchus Winecellars</td>
                <td class="rom-table-item">Yoshi Tannamuri</td>
                <td class="rom-table-item">Canada</td>
                <td class="rom-table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="rom-table-column">
                <td class="rom-table-item">Magazzini Alimentari Riuniti</td>
                <td class="rom-table-item">Giovanni Rovelli</td>
                <td class="rom-table-item">Italy</td>
                <td class="rom-table-item">Alfreds Futterkiste</td>
            </tr>
        </table>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                rom_memmory_fields: [
                    {
                        head: "teste",
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
        }
    }
</script>

<style scoped>
    .rom-h2 {
        margin-left: 37.5%;
        margin-top: 2%;
        border: 0.8px solid;
        padding: 5px;
        border-top: none;
        border-left: none;
        border-right: none;
        width: 25%;
        text-align: center;
    }

    .rom-table {
        font-family: arial, sans-serif;
        width: 100%;
        border: 1px solid;
    }
    
    .rom-table-item {
        padding: 8px;
        
    }

    tr, td, th {
        margin: 0;
    }

    th {
        text-align: left;
        font-weight: bold;
        border-bottom: 1px solid;
    }

    td {
        border-bottom: 1px solid gray;
    }
</style>
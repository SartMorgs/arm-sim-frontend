<template>
    <div class="arm-rom">
        <h2 class="rom-h2">ROM</h2>

        <table class="rom-table">
            <tr class="table-column">
                <th class="table-item">NAME</th>
                <th class="table-item">ADDRESS</th>
                <th class="table-item">BINARY INSTRUCTION</th>
                <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
                <td class="table-item">Alfreds Futterkiste</td>
                <td class="table-item">Maria Anders</td>
                <td class="table-item">Germany</td>
                <td class="table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="table-column">
                <td class="table-item">Centro comercial Moctezuma</td>
                <td class="table-item">Francisco Chang</td>
                <td class="table-item">Mexico</td>
                <td class="table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="table-column">
                <td class="table-item">Ernst Handel</td>
                <td class="table-item">Roland Mendel</td>
                <td class="table-item">Austria</td>
                <td class="table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="table-column">
                <td class="table-item">Island Trading</td>
                <td class="table-item">Helen Bennett</td>
                <td class="table-item">UK</td>
                <td class="table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="table-column">
                <td class="table-item">Laughing Bacchus Winecellars</td>
                <td class="table-item">Yoshi Tannamuri</td>
                <td class="table-item">Canada</td>
                <td class="table-item">Alfreds Futterkiste</td>
            </tr>
            <tr class="table-column">
                <td class="table-item">Magazzini Alimentari Riuniti</td>
                <td class="table-item">Giovanni Rovelli</td>
                <td class="table-item">Italy</td>
                <td class="table-item">Alfreds Futterkiste</td>
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
        border-collapse: collapse;
        width: 100%;
    }

    .table-column {

    }

    .table-item {
        border: 1px solid #756E44;
        padding: 8px;
        font-weight: bold;
    }
</style>
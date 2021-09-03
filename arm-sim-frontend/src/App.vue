<template>
  <div>
    <div class="editor-area">
      <sim-menu />
      <editor ref="tabbedEditor" />
    </div>
    <div class="simulation-area">
      <rom-table></rom-table>
    </div>

    <div>
      <div>
        <div class="int-table">
          <h2 class="int-h2">Menu de Interrupções</h2>
          <div class="int-buttons">
            <div class="first-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="second-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="third-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
          </div>
          <div class="int-buttons">
            <div class="first-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="second-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="third-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
          </div>
          <div class="int-buttons">
            <div class="first-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="second-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="third-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
          </div>
          <div class="int-buttons">
            <div class="first-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="second-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="third-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
          </div>
          <div class="int-buttons">
            <div class="first-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="second-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
            <div class="third-btn">
              <button class="int-table-btn">INT 1</button>
              <button class="int-table-input"></button>
            </div>
          </div>
        </div>
        <div class="arm-on-off-table">
          <button
            class="arm-table-btn"
            v-on:click="
              (hideRegister = !hideRegister), (ajustRegister = !ajustRegister)
            "
            v-bind:style="ajustRegister ? 'width: 100%' : 'width: 20%'"
          >
            Banco de Registradores
          </button>
          <table class="arm-table" v-if="!hideRegister">
            <tr class="table-column">
              <th class="table-item">AAXAA</th>
              <th class="table-item">BBXBB</th>
              <th class="table-item">CCXCC</th>
              <th class="table-item">DDXDD</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
          </table>
        </div>

        <div class="arm-on-off-table">
          <button
            class="arm-table-btn"
            v-on:click="(hideRam = !hideRam), (ajustRam = !ajustRam)"
            v-bind:style="ajustRam ? 'width: 100%' : 'width: 20%'"
          >
            Memória RAM
          </button>
          <table class="arm-table" v-if="!hideRam">
            <tr class="table-column">
              <th class="table-item">AAXAA</th>
              <th class="table-item">BBXBB</th>
              <th class="table-item">CCXCC</th>
              <th class="table-item">DDXDD</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
          </table>
        </div>

        <div class="arm-on-off-table">
          <button
            class="arm-table-btn"
            v-on:click="(hideDisp = !hideDisp), (ajustDisp = !ajustDisp)"
            v-bind:style="ajustDisp ? 'width: 100%' : 'width: 20%'"
          >
            Memória de Dispositivos
          </button>
          <table class="arm-table" v-if="!hideDisp">
            <tr class="table-column">
              <th class="table-item">AAXAA</th>
              <th class="table-item">BBXBB</th>
              <th class="table-item">CCXCC</th>
              <th class="table-item">DDXDD</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
            <tr class="table-column">
              <th class="table-item">NAME</th>
              <th class="table-item">ADDRESS</th>
              <th class="table-item">BINARY INSTRUCTION</th>
              <th class="table-item">ASSEMBLY INSTRUCTION</th>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TabbedEditor from "./components/shared/custom-codemirror/tabbed-editor.vue";
import ButtonsMenu from "./components/shared/buttons-menu/buttons-menu.vue";
import RomTable from "./components/shared/rom-table/rom-table.vue";

export default {
  name: "App",
  components: {
    editor: TabbedEditor,
    "sim-menu": ButtonsMenu,
    "rom-table": RomTable,
  },

  data() {
    return {
      hideDisp: false,
      ajustRegister: true,
      ajustRam: true,
      ajustDisp: true,
      hideRam: false,
      hideRegister: false,
      perPage: 3,
      currentPage: 1,
      items: [
        { id: 1, first_name: "Fred", last_name: "Flintstone" },
        { id: 2, first_name: "Wilma", last_name: "Flintstone" },
        { id: 3, first_name: "Barney", last_name: "Rubble" },
        { id: 4, first_name: "Betty", last_name: "Rubble" },
        { id: 5, first_name: "Pebbles", last_name: "Flintstone" },
        { id: 6, first_name: "Bamm Bamm", last_name: "Rubble" },
        { id: 7, first_name: "The Great", last_name: "Gazzoo" },
        { id: 8, first_name: "Rockhead", last_name: "Slate" },
        { id: 9, first_name: "Pearl", last_name: "Slaghoople" },
      ],
    };
  },
  computed: {
    rows() {
      return this.items.length;
    },
  },

  methods: {},
};
</script>
<style >
.arm-table-btn {
  background-color: #f5e68f;
  border: none;
  color: #756e44;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  width: 100%;
}

.arm-on-off-table {
  padding: 2% 2% 2% 2%;
  display: flex;
  flex-direction: column;
}

.table-column {
  display: flex;
  flex-direction: row;
}

.table-item {
  justify-content: space-around;
  margin: 1px;
  width: 70%;
  color: #756e44;
  border: 1px solid #f5e68f;
  box-shadow: 1px 2px #888888;
}

.arm-table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

.int-table {
  margin-top: 2%;
  width: 50%;
  margin-left: 25%;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  border: 1px solid;
}

.int-buttons {
  display: flex;
  justify-content: space-around;
  margin: 2px;
}

.int-table-btn {
  background-color: #f5e68f; /* Green */
  border: none;
  margin-bottom: 2px;
  color: #888888;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.int-table-input {
  background-color: white; /* Green */
  border: 1px solid #aa9106;
  margin-bottom: 2px;
  color: #888888;
  padding: 20px 50px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

.first-btn,
.second-btn,
.third-btn {
  padding: 4px;
}

.int-h2 {
  margin-top: 2%;
  border: 0.8px solid;
  padding: 5px;
  border-top: none;
  border-left: none;
  border-right: none;
  width: 98.7%;
  text-align: center;
}
</style>

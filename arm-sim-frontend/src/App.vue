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
      </div>
      <div id="pagTable" class="col-sm-12">
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
            <tbody>
              <tr class="table-column" v-for="p in displayedPosts">
                <th class="table-item">{{ p.um }}</th>
                <th class="table-item">{{ p.dois }}</th>
                <th class="table-item">{{ p.tres }}</th>
                <th class="table-item">{{ p.quatro }}</th>
                <th class="table-item">{{ p.cinco }}</th>
                <th class="table-item">{{ p.seis }}</th>
                <th class="table-item">{{ p.sete }}</th>
                <th class="table-item">{{ p.oito }}</th>
                <th class="table-item">{{ p.nove }}</th>
                <th class="table-item">{{ p.dez }}</th>
                <th class="table-item">{{ p.onze }}</th>
                <th class="table-item">{{ p.doze }}</th>
                <th class="table-item">{{ p.treze }}</th>
                <th class="table-item">{{ p.catorze }}</th>
                <th class="table-item">{{ p.quinze }}</th>
                <th class="table-item">{{ p.deze }}</th>
              </tr>
            </tbody>
          </table>
          <div class="pagination" v-if="!hideRegister">
            <button type="button" class="page-link">Previous</button>

            <button type="button" class="page-link">1</button>
            <button type="button" class="page-link">2</button>
            <button type="button" class="page-link">3</button>
            <button type="button" class="page-link">4</button>
            <button type="button" class="page-link">5</button>
            <button type="button" class="page-link">6</button>
            <button type="button" class="page-link">7</button>
            <button type="button" class="page-link">8</button>
            <button type="button" class="page-link">9</button>
            <button type="button" class="page-link">10</button>
            <button type="button" class="page-link">11</button>
            <button type="button" class="page-link">12</button>
            <button type="button" class="page-link">13</button>
            <button type="button" class="page-link">14</button>
            <button type="button" class="page-link">15</button>
            <button type="button" class="page-link">16</button>

            <button type="button" class="page-link">Next</button>
          </div>
        </div>
      </div>
      <div id="pagTable" class="col-sm-12">
        <div class="arm-on-off-table">
          <button
            class="arm-table-btn"
            v-on:click="(hideRam = !hideRam), (ajustRam = !ajustRam)"
            v-bind:style="ajustRam ? 'width: 100%' : 'width: 20%'"
          >
            Memória de RAM
          </button>
          <table class="arm-table" v-if="!hideRam">
            <tbody>
              <tr class="table-column" v-for="p in displayedPosts">
                <th class="table-item">{{ p.um }}</th>
                <th class="table-item">{{ p.dois }}</th>
                <th class="table-item">{{ p.tres }}</th>
                <th class="table-item">{{ p.quatro }}</th>
                <th class="table-item">{{ p.cinco }}</th>
                <th class="table-item">{{ p.seis }}</th>
                <th class="table-item">{{ p.sete }}</th>
                <th class="table-item">{{ p.oito }}</th>
                <th class="table-item">{{ p.nove }}</th>
                <th class="table-item">{{ p.dez }}</th>
                <th class="table-item">{{ p.onze }}</th>
                <th class="table-item">{{ p.doze }}</th>
                <th class="table-item">{{ p.treze }}</th>
                <th class="table-item">{{ p.catorze }}</th>
                <th class="table-item">{{ p.quinze }}</th>
                <th class="table-item">{{ p.deze }}</th>
              </tr>
            </tbody>
          </table>
          <div class="pagination" v-if="!hideRam">
            <button type="button" class="page-link">Previous</button>

            <button type="button" class="page-link">1</button>
            <button type="button" class="page-link">2</button>
            <button type="button" class="page-link">3</button>
            <button type="button" class="page-link">4</button>
            <button type="button" class="page-link">5</button>
            <button type="button" class="page-link">6</button>
            <button type="button" class="page-link">7</button>
            <button type="button" class="page-link">8</button>
            <button type="button" class="page-link">9</button>
            <button type="button" class="page-link">10</button>
            <button type="button" class="page-link">11</button>
            <button type="button" class="page-link">12</button>
            <button type="button" class="page-link">13</button>
            <button type="button" class="page-link">14</button>
            <button type="button" class="page-link">15</button>
            <button type="button" class="page-link">16</button>

            <button type="button" class="page-link">Next</button>
          </div>
        </div>
      </div>
      <div id="pagTable" class="col-sm-12">
        <div class="arm-on-off-table">
          <button
            class="arm-table-btn"
            v-on:click="(hideDisp = !hideDisp), (ajustDisp = !ajustDisp)"
            v-bind:style="ajustDisp ? 'width: 100%' : 'width: 20%'"
          >
            Memória de Dispositivos
          </button>
          <table class="arm-table" v-if="!hideDisp">
            <tbody>
              <tr class="table-column" v-for="p in displayedPosts">
                <th class="table-item">{{ p.um }}</th>
                <th class="table-item">{{ p.dois }}</th>
                <th class="table-item">{{ p.tres }}</th>
                <th class="table-item">{{ p.quatro }}</th>
                <th class="table-item">{{ p.cinco }}</th>
                <th class="table-item">{{ p.seis }}</th>
                <th class="table-item">{{ p.sete }}</th>
                <th class="table-item">{{ p.oito }}</th>
                <th class="table-item">{{ p.nove }}</th>
                <th class="table-item">{{ p.dez }}</th>
                <th class="table-item">{{ p.onze }}</th>
                <th class="table-item">{{ p.doze }}</th>
                <th class="table-item">{{ p.treze }}</th>
                <th class="table-item">{{ p.catorze }}</th>
                <th class="table-item">{{ p.quinze }}</th>
                <th class="table-item">{{ p.deze }}</th>
              </tr>
            </tbody>
          </table>
          <div class="pagination" v-if="!hideDisp">
            <button type="button" class="page-link">Previous</button>

            <button type="button" class="page-link">1</button>
            <button type="button" class="page-link">2</button>
            <button type="button" class="page-link">3</button>
            <button type="button" class="page-link">4</button>
            <button type="button" class="page-link">5</button>
            <button type="button" class="page-link">6</button>
            <button type="button" class="page-link">7</button>
            <button type="button" class="page-link">8</button>
            <button type="button" class="page-link">9</button>
            <button type="button" class="page-link">10</button>
            <button type="button" class="page-link">11</button>
            <button type="button" class="page-link">12</button>
            <button type="button" class="page-link">13</button>
            <button type="button" class="page-link">14</button>
            <button type="button" class="page-link">15</button>
            <button type="button" class="page-link">16</button>

            <button type="button" class="page-link">Next</button>
          </div>
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
  el: "#pagTable",
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
      posts: [""],
      page: 1,
      perPage: 17,
      pages: [],
    };
  },
  computed: {
    rows() {
      return this.items.length;
    },
  },

  methods: {
    getPosts() {
      let data = [];
      for (let i = 0; i < 256; i++) {
        let zero = 0;
        this.posts.push({
          um: zero.toString(16),
          dois: zero.toString(16),
          tres: zero.toString(16),
          quatro: zero.toString(16),
          cinco: zero.toString(16),
          seis: zero.toString(16),
          sete: zero.toString(16),
          oito: zero.toString(16),
          nove: zero.toString(16),
          dez: zero.toString(16),
          onze: zero.toString(16),
          doze: zero.toString(16),
          treze: zero.toString(16),
          catorze: zero.toString(16),
          quinze: zero.toString(16),
          deze: zero.toString(16),
        });
      }
    },
    setPages() {
      let numberOfPages = Math.ceil(this.posts.length / this.perPage);
      for (let index = 1; index <= numberOfPages; index++) {
        this.pages.push(index);
      }
    },
    paginate(posts) {
      let page = this.page;
      let perPage = this.perPage;
      let from = page * perPage - perPage;
      let to = page * perPage;
      return posts.slice(from, to);
    },
  },
  computed: {
    displayedPosts() {
      return this.paginate(this.posts);
    },
  },
  created() {
    this.getPosts();
  },
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
button.page-link {
  display: inline-block;
}
button.page-link {
  font-size: 20px;
  background-color: #f5e68f;
  color: #aa9106;
  font-weight: 500;
}
.pagination {
  margin-left: 30%;
  margin-top: 1%;
}
</style>

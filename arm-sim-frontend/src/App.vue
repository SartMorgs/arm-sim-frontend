<template>
  <div>
    <div class="menu">
      <ul class="menu-botoes" id="teste">
        <li v-for="icone of icones" class="menu-botoes-item">
          <input
            type="image"
            :alt="icone.titulo"
            :src="icone.url"
            class="botao"
          />
        </li>
      </ul>
    </div>
    <div>
      <tabbed-editor ref="tabbedEditor" />
    </div>
    <div id="data-memory">
      <button
        id="data-memory-btn"
        v-on:click="hideDataMemory = !hideDataMemory"
      >
        Data Memory
      </button>

      <table width="100%" v-if="!hideDataMemory">
        <tr>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
        </tr>
        <tr>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
        </tr>
        <tr>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
        </tr>
      </table>
    </div>

    <div id="peripheral">
      <button id="peripheral-btn" v-on:click="hidePeripheral = !hidePeripheral">
        Peripheral
      </button>

      <table width="100%" v-if="!hidePeripheral">
        <tr>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
        </tr>
        <tr>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
        </tr>
        <tr>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
          <td>BBxBB</td>
          <td>AAxAA</td>
          <td>FFxFF</td>
        </tr>
      </table>
    </div>

    <div id="rom">
      <h2 id="rom-h2">ROM</h2>
      <table>
        <tr>
          <th style='width: 10%; text-align: left;'>NAME</th>
          <th style='width: 10%; text-align: left;'>ADDRESS</th>
          <th style='width: 40%;'>BINARY INSTRUCTION</th>
          <th style='width: 40%;'>ASSEMBLY INSTRUCTION</th>
        </tr>
        <tr>
          <td>Alfreds Futterkiste</td>
          <td>Maria Anders</td>
          <td>Germany</td>
          <td>Alfreds Futterkiste</td>
        </tr>
        <tr>
          <td>Centro comercial Moctezuma</td>
          <td>Francisco Chang</td>
          <td>Mexico</td>
          <td>Alfreds Futterkiste</td>
        </tr>
        <tr>
          <td>Ernst Handel</td>
          <td>Roland Mendel</td>
          <td>Austria</td>
          <td>Alfreds Futterkiste</td>
        </tr>
        <tr>
          <td>Island Trading</td>
          <td>Helen Bennett</td>
          <td>UK</td>
          <td>Alfreds Futterkiste</td>
        </tr>
        <tr>
          <td>Laughing Bacchus Winecellars</td>
          <td>Yoshi Tannamuri</td>
          <td>Canada</td>
          <td>Alfreds Futterkiste</td>
        </tr>
        <tr>
          <td>Magazzini Alimentari Riuniti</td>
          <td>Giovanni Rovelli</td>
          <td>Italy</td>
          <td>Alfreds Futterkiste</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
import TabbedEditor from "./components/shared/custom-codemirror/tabbed-editor.vue";

export default {
  name: "App",
  components: {
    TabbedEditor,
  },

  data() {
    return {
      icones: [
        {
          url: "src/assets/icons/save-button.svg",
          titulo: "save",
        },
        {
          url: "src/assets/icons/open-button.svg",
          titulo: "open",
        },
        {
          url: "src/assets/icons/compile-button.svg",
          titulo: "compile",
        },
        {
          url: "src/assets/icons/play-button.svg",
          titulo: "play",
        },
        {
          url: "src/assets/icons/pause-button.svg",
          titulo: "pause",
        },
        {
          url: "src/assets/icons/next-button.svg",
          titulo: "next",
        },
        {
          url: "src/assets/icons/stop-button.svg",
          titulo: "stop",
        },
      ],
      hideDataMemory: false,
      hidePeripheral: false,
    };
  },
};
</script>

<style lang="scss">
.menu {
  width: 96%;
  margin: 0 auto;
  padding: 0 auto;
}

.menu-botoes {
  list-style: none;
}

.menu-botoes .menu-botoes-item {
  display: inline-block;
  margin-left: 5%;
}

.menu-botoes .menu-botoes-item .botao {
  width: 100%;
  max-height: 50px;
  max-width: 50px;
  border: 2px solid black;
  padding: 5px;
  background-color: #f5e68f;
}

#data-memory-btn,
#peripheral-btn {
  margin-top: 1%;
  margin-bottom: 1%;
  padding: 1%;
  font-weight: bold;
}

#data-memory tr, #peripheral tr {
  display: flex;
  flex-direction: row;

}

#data-memory th, 
#data-memory td, #peripheral th, #peripheral td {
  justify-content: space-around;
  margin: 1px;
  width: 70%;
  border: 1px solid #070606;
 
}

#rom table, #data-memory table, #peripheral table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

#rom td, #rom th {
  border: 1px solid #070606;
  padding: 8px;
  font-weight: bold;
}

#rom tr:nth-child(even) {
  background-color: #6b6a6a;
  
}

#rom h2 {
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

</style>

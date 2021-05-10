<template>
  <div>
    <div class="menu">
      <ul class="menu-botoes">
        <li v-for="icone of icones" class="menu-botoes-item">
          <input type="image" :alt="icone.titulo" :src="icone.url" class="botao"/>
        </li>
      </ul>
    </div>
    <tabbed-editor ref="tabbedEditor" />
  </div>
</template>

<script>

  import TabbedEditor from './components/shared/custom-codemirror/tabbed-editor.vue'

  export default {

    name: 'App',
    components: {
      TabbedEditor
    },

    data() {
      return {
        icones: [
          {
            url: "src/assets/icons/botao-play.svg",
            titulo: "play"
          },
          {
            url: "src/assets/icons/botao-pause.svg",
            titulo: "pause"
          },
          {
            url: "src/assets/icons/botao-next.svg",
            titulo: "next"
          },
          {
            url: "src/assets/icons/botao-stop.svg",
            titulo: "stop"
          }
        ],
      }
    }
  }

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
    background-color: #F5E68F;
  }
</style>

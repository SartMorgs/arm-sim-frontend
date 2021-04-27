<template>
  <div id"app">
    <v-button :onClick="consoleClick">Custom</v-button>
  </div>
</template>

<script>
  import Button from 'Components'
  
  export default {
    name: 'app',
    components: {
      'v-button': Button
    },
    methods: {
      consoleClick() {
        console.log('Button clicked')
      },
      alertClick() {
        alert('Button clicked')
      }
    }
  }
</script>
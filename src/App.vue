<template>
  <div id="app">
    <header_component :message="msg"></header_component>

    <form v-on:submit.prevent="newCage">
      <input v-model="height">
      <input v-model="width">
      <button>Add</button>
    </form>

    <div v-for="cage in cages">
      <img :src="cage">
    </div>
  </div>
</template>

<script>
import Header from './components/header.vue'

export default {
  name: 'app',
  components: {
    header_component: Header
  },
  data () {
    return {
      cages: [],
      height: 200,
      width: 200,
      msg: 'Hello World'
    }
  },
  methods: {
    newCage: function() {
      this.cages.push(this.getCage(this.height, this.width));
      
      this.height = 200;
      this.width = 200;
    },
    getCage: function(height, width) {
      return "http://www.placecage.com/c/" + String(width) + '/' + String(height)
    }
  }
}
</script>

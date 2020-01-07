<template>
  <div id="app">
    <p>{{number}}</p>
    <button @click="add">add ONE</button>
    <button @click="reduce">reduce ONE</button>
    <hr>
    <button @click="push">PUSH</button>
    <ul v-for="(item, index) in list" :key="index">
      <li>{{item.time}}</li>
    </ul>
    <HelloWorld :arr="list" :num="number" msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    HelloWorld
  },
  data() {
    return {
      number: 0,
      list: [],
    }
  },
  created() {
    this.push()
  },
  methods: {
    add() {
      this.number++
    },
    reduce() {
      this.number--
    },
    push() {
      const time = Date.now()
      const times = new Date()
      const options = {
        time,
        times
      }
      this.list.push(options)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

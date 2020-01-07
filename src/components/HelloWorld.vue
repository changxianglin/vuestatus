<template>
  <div class="hello">
    <h1>{{num}}</h1>
    <h3>{{ msg }}</h3>
    <hr>
    <span>{{app}}</span>
    <hr>
    <span>{{setnum}}</span>
    <ul v-for="(item, index) in getList" :key="index">
      <li>{{item.time + 'go'}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
    num: Number,
    arr: Array,
  },
  computed: {
    getList() {
      const result = []
      this.arr.map(item => result.push(item))
      return result.reverse()
    },
    setnum() { // auto update data
      const index = this.arr.length
      const end = index - 1
      return this.arr[end]
    }
  },
  data() {
    return {
      app: ''
    }
  },
  created() {
    this.setApp()
  },
  methods: {
    setApp() { // manul update data, need envent tigger
      this.app = this.arr[0]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<template>
  <div id="app">
    <!--<h1 v-text="title"></h1>-->
    <input v-model="newItem" @keyup.enter="addNew">
    <ul>
      <li v-for="item in items" :class="{showLove: item.isLove}" @click="changeLove(item)">
          {{item.lable}}
      </li>
    </ul>
    <p>childs tell me: {{ childwords }}</p>
    <component-a msgfromfather="wo shi zb" v-on:chlid-tell-somethings="listento"></component-a>
  </div>
</template>

<script>
import Store from './store.js'
import ComponentA from './components/ComponentA'
export default {
  data: function () {
    return {
      title: 'jie',
      items: Store.fetch(),
      newItem: '',
      childwords: ''
    }
  },
  components: {
    ComponentA
  },
  watch: {
    items: {
      handler: function (items) {
        Store.save(items)
      },
      deep: true
    }
  },
  methods: {
    changeLove: function (item) {
      item.isLove = !item.isLove
    },
    addNew: function () {
      this.items.push({
        lable: this.newItem,
        isLove: false
      })
      this.newItem = ''
    },
    listento: function (msg) {
      this.childwords=msg
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
.showLove{
  text-decoration: underline;
}
</style>

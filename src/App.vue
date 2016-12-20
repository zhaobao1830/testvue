<template>
  <div id="app">
    <h1 v-text="title"></h1>
    <input v-model="newItem" @keyup.enter="addNew">
    <ul>
      <li v-for="item in items" :class="{showLove: item.isLove}" @click="changeLove(item)">
          {{item.lable}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function () {
    return {
      title: 'jie',
      items: [
        {
          lable: 'woshi',
          isLove: true
        },
        {
          lable: 'shiwo',
          isLove: false
        }
      ],
      newItem: ''
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
      console.log(this.newItem)
      this.newItem = ''
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

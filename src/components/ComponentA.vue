<template>
    <div>
       <h1>{{msg}}</h1>
       <h2>{{msgfromfather}}</h2>
       <button @click="onClickMe">Click!</button>
    </div>
</template>
<style>
</style>
<script>
    export default{
      data () {
        return {
          msg: 'hello YJ'
        }
      },
      props: ['msgfromfather'],
      methods: {
        onClickMe: function () {
          console.log(this.msgfromfather)
        }
      }
    }

</script>

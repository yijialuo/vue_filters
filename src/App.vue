<template>
  <div id="app">
    {{date | formatDate}}
  </div>
</template>

<script>

  export default {
    name: 'App',
    data() {
      return {
        date: new Date()
      }
    },
    mounted() {
      this.timer = setInterval(() => {
        this.date = new Date()
      }, 1000)
    },
    beforeDestroy() {
      if (this.timer) {
        clearInterval(this.timer)
      }
    },
    methods: {
      padDate(value) {
        return value < 10 ? '0' + value : value;
      }
    },
    filters: {
      formatDate(value) {
        //拿不到methods中的方法
        console.log(value)
        let date = new Date(value);
        let year = date.getFullYear();
        // let month = this.padDate(date.getMonth() + 1)
        // let day = this.padDate(date.getDate())
        // let hours = this.padDate(date.getHours())
        // let minutes = this.padDate(date.getHours())
        // let seconds = this.padDate(date.getSeconds())
        let month = date.getMonth() + 1
        let day = date.getDate()
        let hours = date.getHours()
        let minutes = date.getMinutes()
        let seconds = date.getSeconds()

        month = month < 10 ? '0' + month : month;
        day = day < 10 ? '0' + day : day;
        hours = hours < 10 ? '0' + hours : hours;
        minutes = minutes < 10 ? '0' + minutes : minutes;
        seconds = seconds < 10 ? '0' + seconds : seconds;
        return year + '-' + month + '-' + day + ' ' + hours + ':' + minutes + ':' + seconds;
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

<template>
  <DemoPage/>
</template>

<script>
import DemoPage from './components/DemoPage.vue'

export default {
  name: 'App',
  components: {
    DemoPage
  },
  setup() {
    let name = "张三";
    let age = 18;
    function sayHello() {
        alert(`我叫${name},我${age}岁了`);
    }
    return {
      name,
      age,
      sayHello
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

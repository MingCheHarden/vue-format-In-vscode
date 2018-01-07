<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
  </div>
</template>


<script>
import HelloWorld from './components/HelloWorld'

export default {
    name: 'app',
    components: {
        HelloWorld
    }
}
</script>

<style>
#app{
    font-family: "Avenir", Helvetica, Arial, sans-serif;

    margin-top: 60px;

    text-align: center;

    color: #2c3e50;

    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

</style>

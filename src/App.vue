<template>
  <div id="app">
    <div class="row">
      <div class="col-md-4">
        <Box nome="G1" url="https://g1.globo.om/" timerequest="5000"/>
      </div>
      <div class="col-md-4">
        <Box nome="Google" url="https://google.com/" timerequest="5000"/>
      </div>
      <div class="col-md-4">
        <Box nome="W3S" url="https://www.w3schools.com" timerequest="5000"/>
      </div>
    </div>
  </div>
</template>

<script>
import Box from "./components/Box.vue";
import axios from "axios";

export default {
  name: "app",
  components: {
    Box
  },
  methods: {}
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 10px;
}
</style>

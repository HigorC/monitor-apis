<template>
  <div id="app">
    <div class="grid">
      <div class="row">
        <div v-for="api in apis" :key="api.id" class="col-md-4">
          {{api.id}}
          <Box :nome="api.nome" :url="api.url" :timeToReload="api.timeToReload"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Box from "./components/Box.vue";
import axios from "axios";

export default {
  name: "app",
  data: function() {
    return {
      apis: [
        {
          nome: "G1",
          url: "https://g1.globo.om/",
          timeToReload: "10000"
        },
        {
          nome: "Google",
          url: "https://google.com/",
          timeToReload: "10000"
        },
        {
          nome: "W3S",
          url: "https://www.w3schools.com",
          timeToReload: "10000"
        }
      ]
    };
  },
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
}

.grid {
  margin: 10px;
}
</style>

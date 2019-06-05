<template>
  <div id="app">
    <div class="grid">
      <div class="row">
        <div
          v-for="api in apis"
          :key="api.id"
          class="cols-boxes"
          :class="{
            'col-12' : apis.length == 1,
            'col-6' : apis.length == 2,
            'col-4' : apis.length >= 3 & apis.length <= 6,
            'col-3' : apis.length > 6
           }"
        >
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
        },
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

<style lang="less">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.cols-boxes {
  margin-bottom: 10px;
}

.grid {
  margin: 10px;
  .row {
    margin-right: 0;
    margin-left: 0;
  }
}
</style>

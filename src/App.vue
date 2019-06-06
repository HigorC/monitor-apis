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
import apisJson from "./assets/sites.json";

export default {
  name: "app",
  data: function() {
    return {
      apis: apisJson
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

body {
  background: #ececece0;
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

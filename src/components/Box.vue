<template>
  <div>
    <div class="box" :class="{'alert-success': req.works,'alert-danger': !req.works }">
      <!-- <div class="header">
          {{url}}
      </div>-->
      <b-spinner v-if="req.active" variant="success" label="Spinning"></b-spinner>
      <div class="content">
        <h2>{{nome}}</h2>
        <h3>{{req.status}}</h3>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  name: "Box",
  props: {
    nome: String,
    url: String,
    timerequest: String
  },
  data: function() {
    return {
      req: {
        active: false,
        status: 400,
        works: false
      }
    };
  },
  mounted: function() {
    setInterval(() => {
      console.log("Chamando...");
      this.req.active = true;
      this.getUrl();
    }, this.timerequest);
  },
  methods: {
    getUrl: function() {
      const proxyurl = "https://cors-anywhere.herokuapp.com/";

      const instance = axios.create({
        baseURL: proxyurl + this.url,
        timeout: 10000,
        headers: {
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Methods":
            "HEAD, OPTIONS, GET, POST, PUT, DELETE",
          "Access-Control-Allow-Headers":
            "Origin, X-Requested-With, Content-Type, Accept, Authorization"
        }
      });

      instance.get().then(
        response => {
          this.req.status = response.status;
          this.req.works = true;
          this.req.active = false;
        },
        err => {
          this.req.active = false;
        }
      );
    }
  }
};
</script>
<style>
.box {
  border: 1px solid black;
  width: 100%;
  height: 300px;
  border-radius: 5px;
  display: flex;
  align-items: center;
}

.content {
  margin: 0 auto;
}

/* .success {
  background-color: green;
}

.danger {
  background-color: red;
} */
</style>



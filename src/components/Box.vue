<template>
  <div class="box" :class="{'box-success': req.works,'box-error': !req.works }">
    <b-container class="box-container">
      <b-row class="box-header" align-v="start">
        <b-col cols="3">
          <b-spinner v-if="req.active" variant="primary" type="grow" label="Spinning"></b-spinner>
        </b-col>
        <b-col class="url" cols="6">{{url}}</b-col>
      </b-row>
      <hr class="separador-header-body">
      <b-row class="box-body" align-v="center">
        <b-col cols="8" offset-md="2">
          <div class="content">
            <h1 class="nome">{{nome}}</h1>
            <h3 class="status">{{req.status}}</h3>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Box",
  props: {
    nome: String,
    url: String,
    timeToReload: String
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
    }, this.timeToReload);
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
<style lang="less">
.box {
  border: 1px solid #ccc;
  border-radius: 5px;

  &-success {
    background-color: #17d060;
  }

  &-error {
    background-color: #e84c4c;
  }

  &-header {
    margin-top: 25px;
    height: 40px;

    .url {
      font-style: italic;
    }
  }

  &-body {
    margin-bottom: 20px;

    .nome {
      color: #fff;
      font-weight: bold;
      font-size: 55px;
      letter-spacing: -3px;
      text-shadow: 1px 1px 5px #2d2d2d;
    }
  }

  hr.separador-header-body {
    margin: 0 0 10px 0;
  }
}

</style>



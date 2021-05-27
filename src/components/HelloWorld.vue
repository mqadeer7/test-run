<template>
  <div class="hello">
    <button @click="sendRequest()">Hallo</button>
    {{message}}
  </div>
</template>

<script>
const axios = require("axios");

export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      message:""
    }},
  methods: {
    sendRequest() {
      axios
        .create({
          baseURL: "https://education-pkr.vatomatic.com/api/method/",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
        })
        .post("login", {
          usr: "dummy@test.com",
          pwd: "vpk!eWfHx%XF",
        })
        .then(() => {
          this.message = "Success";
        })
        .catch(() => {
          this.message = "Failer";
        });
      // fetch("https://education-pkr.vatomatic.com/api/method/login", {
      //   method: "POST",
      //   headers: {
      //     Accept: "application/json",
      //     "Content-Type": "application/json",
      //   },
      //   body: JSON.stringify({
      //     usr: "dummy@test.com",
      //     pwd: "vpk!eWfHx%XF",
      //   }),
      // })
      //   .then((r) => {})
      //   .then((r) => {
      //     console.log(r);
      //   });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<template>
  <div id="example-1">
    <input id="username" type="text" placeholder="用户名" v-model="usr"></input>
    <input id="password" type="password" placeholder="密码" v-model="psw"></input>
    <button v-on:click="post">SIGN IN</button>
  </div>
</template>

<script>
export default {
  name: 'Signin',
  data: function() {
    return {
      usr: "",
      psw: ""
    };
  },
  methods: {
    get: function() {
      this.$http.post("", {"username":this.usr, "password":this.psw}).then(function(res) {
          console.log(res.data);
        }, function() {
          alert("error");
        });
    }
  }
}
</script>

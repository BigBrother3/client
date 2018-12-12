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
    post: function() {
      this.$http.post("https://localhost:8080/", {username:this.usr, password:this.psw},{withCredentials:true}).then(
        function(res) {
          console.log(res.data);
          $cookies.set("LogInUser", res.data);
          this.$router.push({path:'/Search'})
        }, function() {
          alert("error");
        });
    }
  }
}
</script>

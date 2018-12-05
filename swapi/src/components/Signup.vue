<template>
  <div id="signup">
    <input id="username" type="text" placeholder="用户名" v-model="usr"></input>
    <input id="password" type="text" placeholder="密码" v-model="psw"></input>
    <button v-on:click="post">SIGN UP</button>
  </div>
</template>

<script>
export default {
  name: 'Signup',
  data: function(){
    return {
      usr: "",
      psw: ""
    };
  },
  methods: {
    post: function() {
      this.$http.post("", {"username":this.usr, "password":this.psw}).then(function(res) {
          console.log(res.data);
        }, function() {
          alert("error");
        });
    }
  }
}
</script>

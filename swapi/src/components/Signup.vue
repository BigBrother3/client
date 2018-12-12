<template>
  <div id="signup">
    <p>
      <input id="username" type="text" placeholder="用户名" v-model="usr"></input>
    </p>
    <p>
      <input id="password" type="text" placeholder="密码" v-model="psw"></input>
    </p>
    <p>
      <button v-on:click="post">SIGN UP</button>
    </p>
    <p>
      <router-link to="/">Back</router-link>
    </p>
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
      this.$http.post("https://localhost:8080/", 
        {
          username:this.usr, 
          password:this.psw
        },
        {
          withCredentials:true
        }
        ).then(
        function(res) {
          console.log(res.data);
          this.$router.push({path:'/Signin'})
        },
        function() {
          alert("error");
        });
    }
  }
}
</script>

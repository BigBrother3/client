<template>
  <div id="example-1">
    <input id="search" placeholder="搜索" v-model="content"></input>
    <button v-on:click="get()">Search</button>
    <p width="100px" height="100px">{{msg}}</p>
  </div>
</template>

<script>
export default {
  name: 'Signin',
  data: function() {
    return {
      msg: "",
      content: ""
    };
  },
  methods: {
    get: function() {
      this.$http.get("https://swapi.co/api/"+this.content).then(
        function(res) {
          this.msg = res.data;
        }, function() {
          alert("error");
        });
    }
  }
}
</script>

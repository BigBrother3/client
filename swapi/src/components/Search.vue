<template>
  <div id="example-1">
    <div>
      <input id="search" placeholder="搜索" v-model="content"></input>
      <button v-on:click="get()">Search</button>
    </div>
    <div>
      <textarea v-model="msg" rows="30" cols="100"></textarea>
    </div>
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
          this.msg = JSON.stringify(res.data, null, 4);
        }, function() {
          alert("error");
        });
    }
  }
}
</script>

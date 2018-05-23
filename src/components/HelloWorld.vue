<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ obj.age }}</h1>
    <button @click="obj.age += 1">增加年龄</button>
    
    
    <hr>
    <son1-box :father-name="name" :father-obj="obj"></son1-box><hr>
    <son2-box :father-name="name" :father-obj="obj"></son2-box>
  </div>
</template>

<script>
import son1 from "./son1"
import son2 from "./son2"

export default {
  components:{
    "son1Box": son1,
    "son2Box": son2
  },
  data () {
    return {
      msg: 'i am father',
      name: 'HelloWorld.vue',
      obj: {
        name:"HelloWorld.vue",
        age: 50,
        job: "singer"
      }
    }
  },
  computed: {
    // growAge: function () {
    //   this.obj.age += 1
    // }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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

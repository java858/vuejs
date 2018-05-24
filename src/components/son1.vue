<template>
  <div class="hello">
    <h1>{{ msg }}, my father is {{fatherName}}</h1>
    <h1>{{fname}}</h1>
    <h1>{{fobj}}</h1>
    <h1>{{fEvt}}</h1>
    <button @click="test">test</button>
  </div>
</template>

<script>
export default {
  props:[
    "fatherName",
    "fatherObj",
    "fatherEvt"
  ],
  data () {
    return {
      msg: 'i am son1',
      fname: this.fatherName,
      fobj: this.fatherObj,
      fEvt: null
    }
  },
  methods: {
    test: function(){
      console.log("this.fatherEvt:",this.fatherEvt);
      console.log(this.fEvt);
    }
  },
  watch: {
    fatherEvt: function (val) {   //不知道为什么，只能监视fatherEvt，监听fEvt没用，看不到变化
      this.fEvt = val
      console.log("this is son1:",this.fEvt)
    }
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

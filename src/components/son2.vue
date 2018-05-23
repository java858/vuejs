<template>
  <div class="hello">
    <h1>{{ msg }}, my father is {{fatherName}}</h1>
    <h1>{{fname}}</h1>
    <h1>{{fobj}}</h1>
  </div>
</template>

<script>
export default {
  props:[
    "fatherName",
    "fatherObj"
  ],
  data () {
    return {
      msg: 'i am son2',
      fname: this.fatherName,
      fobj: this.fatherObj,
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

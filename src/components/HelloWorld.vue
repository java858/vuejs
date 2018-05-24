<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ name }}</h1>
    <h1>{{ obj.age }}</h1>
    <button @click="obj.age += 1">增加年龄</button>
    <button @click="initWs">初始化websocket</button>
    <button @click="showEvt">showEvt</button>
    <button @click="test">test定时器</button>
    
    
    <hr>
    <son1-box :father-name="name" :father-obj="obj" :father-evt="messageEvt"></son1-box><hr>
    <son2-box :father-name="name" :father-obj="obj"></son2-box>
  </div>
</template>

<script>
import son1 from "./son1"
import son2 from "./son2"
import func from './vue-temp/vue-editor-bridge';
var mytype = {"type":10090};
var typeString = JSON.stringify(mytype);

export default {
  name: 'HelloWorld',
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
      },
      websocket: null,
      messageEvt: null
    }
  },
  computed: {

  },
  methods: {
    initWs: function () {
      var _this = this
      var websocket = new WebSocket("ws://114.80.110.63:34567")
      websocket.onopen = function (evt) {
        websocket.send(typeString)
      }
      websocket.onmessage = function (evt) {
        _this.messageEvt = evt
        console.log('websocket.onmessage has been triggered!')
        // console.log(_this.messageEvt)
      } 
      this.websocket = websocket
    },

    showEvt: function () {
      console.log(this.messageEvt);
      console.log(this.websocket);
    },

    test: function () {
      var _this = this
      setInterval(() => {
        _this.websocket.send(typeString)
      },2000)
    }
  }
  // created: function () {
  //   // var _this = this
  //   //   var websocket = new WebSocket("ws://114.80.110.63:34567")
  //   //   websocket.onopen = function (evt) {
  //   //     websocket.send(typeString)
  //   //   }
  //   //   websocket.onmessage = function (evt) {
  //   //     _this.messageEvt = evt
  //   //     console.log('websocket.onmessage has been triggered!')
  //   //     // console.log(_this.messageEvt)
  //   //   } 
  //   //   this.websocket = websocket
  // },
  // mounted: function () {
  //   // console.log(this.messageEvt);
  //   // console.log(this.websocket);
  // }
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

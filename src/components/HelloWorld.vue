<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ inputText }}</h1>
    <p v-bind:style="style">v-bind テスト</p>
    <p v-bind:class="{testRed:isRed, testBlue:isBlue}">v-bind class テスト</p>
    <p v-bind:class="classes">classes テスト</p>
    <p v-if="isIf">v-if test</p>
    <p v-else>v-else test</p>
    <ul>
      <li v-for="item in items" :key="item.id">{{item.name}}</li>
    </ul>
    <input type="text" v-model="model">
    <p>{{model}}</p>
    <!-- v-on:イベント処理 -->
    <p v-on:click="counter++">{{counter}}</p>
    <Test msg="props test"/>
    <!-- propsで値を渡したいときには":"をつけるかv-bind:をつける-->
    <Test v-for="item in items" :key="item.id" :msg="item.name"/>
    <input type="text" @input="doInput">
    <button @click="doAction">onclick change</button>
    <button @click="doChangeStyle">change style</button>
    <button @click="doChangeStyleClass">change Class</button>
    <button @click="doChangeClasses">change Classes</button>
    <button @click="doChangeIf">change v-if</button>
    <input type="text" v-model="num">
    <p>{{calc}}</p>
    <Test v-bind:msg="newTitle" />
    <button @click="doChangeTitle">changetitle</button>
    <Test msg="emit test" @result-event="appAction"/>
    <p>{{result}}</p>
    <Calc />
  </div>
</template>

<script>
import Calc from "./Calc"
import Test from "./Test"
export default {
  name: 'HelloWorld',
  components: {
    Test,
    Calc,
  },
  data: () => ({
    msg: 'kitanoshohei',
    inputText: 'null',
    style:'color:black',
    isRed:true,
    isBlue:false,
    classes:{
      testRed:true,
      testBlue:false,
    },
    isIf:true,
    items:[
      {id:1, name:'orange'},
      {id:2, name:'apple'},
    ],
    model:'v-model',
    counter:0,
    num:0,
    newTitle:'',
    result:'',
  }),
  methods: {
    doAction () {
      this.msg = 'abekanae';
    },
    doInput (event) {
      this.inputText = event.target.value;
    },
    doChangeStyle () {
      this.style = 'color:red'
    },
    doChangeStyleClass () {
      this.isRed = false;
      this.isBlue = true;
    },
    doChangeClasses () {
      this.classes.testRed = !this.classes.testRed;
      this.classes.testBlue = !this.classes.testBlue;
    },
    doChangeIf () {
      this.isIf = !this.isIf;
    },
    doChangeTitle () {
      var input = prompt("new title");
      this.newTitle = input;
    },
    appAction (message) {
      this.result = 'emit ' + message;
    }
  },
  /* computedはnumが変更された場合に動的に起動する */
  computed: {
    calc () {
      return this.num * this.num;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .testRed {
    color:red;
  }
  .testBlue {
    color:blue;
  }
</style>

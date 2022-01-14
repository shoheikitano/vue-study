<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <!-- input項目で動的に値を変化した場合にdataの変数の値を変えるときにはv-modelを使用する -->
    <input type="text" v-model="title">
    <button @click="doAction">emit</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props:['msg'],
  data: () => ({
    title:'',
  }),
  methods: {
    doAction () {
      this.$emit('result-event', this.title);
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

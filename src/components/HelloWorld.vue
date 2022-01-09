<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ inputText }}</h1>
    <input type="text" @input="doInput">
    <button @click="doAction()">change</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    msg: 'kitanoshohei',
    inputText: 'null',
  }),
  methods: {
    doAction () {
      this.msg = 'abekanae';
    },
    doInput (event) {
      this.inputText = event.target.value;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

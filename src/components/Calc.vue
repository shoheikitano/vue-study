<template>
  <div class="hello">
    <!-- input項目で動的に値を変化した場合にdataの変数の値を変えるときにはv-modelを使用する -->
    {{val}}
    <input type="text" v-model="a">
    <input type="text" v-model="b">
    <input type="text" v-model="val">
    <p>{{add}}</p>
  </div>
</template>

<script>
export default {
  name: 'Calc',
  data: () => ({
    title:'',
    val:'',
    add:'',
  }),
  /* computedはnumが変更された場合に動的に起動する */
  computed: {
    a: {
      get () {
        return this.val *2;
      },
      set (value) {
        this.val = Math.floor(value/2);
      }
    },
    b: {
      get () {
        return this.val * this.val;
      },
      set (value) {
        this.val = Math.floor(Math.sqrt(value));
      }
    }
  },
  created () {
    this.val = 10;
  },
  watch: {
    val (e) {
      this.val = e;
      var val = parseInt(e);
      this.add = Math.floor(val + 2);
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

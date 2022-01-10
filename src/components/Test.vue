<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props:['msg'],
  data: () => ({

  }),
  methods: {
    
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

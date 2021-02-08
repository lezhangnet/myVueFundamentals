<template>
  <div class="mini">
    <h1>This is {{ msg }}</h1>
    <p>
      This is a minimal component.
      Copy me as base of new components.
    </p>
  </div>
</template>

<script>
export default {
  name: 'MiniComponent',
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1 {
  margin: 50px 0 0;
  color: red;
}
p {
  color: #42b983;
}
</style>

<template>
  <div>
    <div class="header">
      <span v-if="open" @click="open = !open">&#x25B2;Collapse</span>
      <span v-if="!open" @click="open = !open">&#x25BC;Expand</span>
    </div>
    <slot v-if="open">
      This is a default content of slot.
    </slot>
  </div>
</template>

<script>
export default {
  name: 'CollapsibleSection',
  data() {
    return {
      open: true,
    };
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

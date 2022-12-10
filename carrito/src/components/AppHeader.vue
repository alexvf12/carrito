<template>
  <header>
    <img src="../assets/logo.svg" width="32" />
    <div>My carrito superpower</div>
    <div>{{ count }}</div>
    <button @click="addOne">Add one !</button>
  </header>
</template>

<script>
export default {
  props: ["count"],
  methods: {
    addOne() {
      // hago muchas cosas

      this.$emit("addOne", 5);
      //  alert(this.count);
    },
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
}
</style>
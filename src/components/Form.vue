<template>
  <form>
    <slot></slot>
  </form>
</template>

<script>
export default {
  name: "KForm",
  props: ["form", "rules"],
  provide() {
    return {
      form: this
    };
  }
};
</script>

<style>
</style>

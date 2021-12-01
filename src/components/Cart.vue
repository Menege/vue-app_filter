<template>
  <div class="block">
    <div class="block__title">
      {{ title }}
    </div>
    <div class="block__disc">
      {{ disc }}
    </div>
    <div class="block__name">
      {{ name }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: {
    name: String,
    title: String,
    disc: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

<template>
  <h2>{{ listLength }} recipes for you:</h2>
</template>

<script>
export default {
  props: ['listLength']
};
</script>

<style scoped>
h2 {
  margin: 0;
  color: #282b30;
}
</style>

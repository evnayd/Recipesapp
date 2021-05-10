<template>
  <div class="recipes">
    <recipe-item
      v-for="meal in meals"
      :key="meal.idMeal"
      v-bind:meal="meal"
    ></recipe-item>
  </div>
</template>
<script>
import RecipeItem from './RecipeItem.vue';
export default {
  components: {
    RecipeItem
  },
  props: ['meals']
};
</script>

<style scoped>
.recipes {
  padding-top: 15px;
  padding-bottom: 5px;
}

@media (min-width: 768px) {
  .recipes {
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
}
</style>

<template>
  <div class="recipe-item">
    <div class="recipe-img">
      <img :src="meal.strMealThumb" alt="food" />
    </div>
    <h3 class="recipe-name">{{ meal.strMeal }}</h3>
    <a :href="link" class="recipe-btn" v-on:click="getDetails"
      >See the recipe</a
    >
  </div>
  <recipe-details
    :mealInfo="mealInfo"
    v-show="detailsAreVisible"
    @close="closeModal"
  ></recipe-details>
</template>

<script>
import RecipeDetails from './RecipeDetails.vue';
export default {
  props: { meal: Object, link: String, src: String },
  components: {
    RecipeDetails
  },
  data() {
    return {
      mealInfo: {},
      detailsAreVisible: false
    };
  },

  methods: {
    getDetails() {
      fetch(`https://www.themealdb.com/api/json/v1/1/lookup.php?i=${this.meal.idMeal}
      `)
        .then(response => {
          return response.json();
        })
        .then(data => {
          if (data) {
            this.mealInfo = data.meals[0];
            this.detailsAreVisible = true;
          }
        })
        .catch(error => {
          console.log(error);
        });
    },
    closeModal() {
      this.detailsAreVisible = false;
    }
  }
};
</script>

<style scoped>
.recipe-item {
  padding-bottom: 30px;
  background-color: #a1d73f;
  width: 100%;
  border-radius: 10px;
  text-align: center;
  margin-bottom: 25px;
  padding: 7px;
}

.recipe-img img {
  width: 100%;
  height: auto;
  border-radius: 10px;
  margin-left: 0;
}

.recipe-name {
  color: #fff;
}

.recipe-btn {
  text-decoration: none;
  background-color: #fff;
  padding: 7px;
  border-radius: 8px;
  color: #e34f46;
  margin-bottom: 10px;
  display: inline-block;
  cursor: pointer;
}

.recipe-btn:hover {
  background-color: #e34f46;
  color: #fff;
}

@media (min-width: 768px) {
  .recipe-item {
    width: 310px;
    margin: 20px;
  }
}
</style>

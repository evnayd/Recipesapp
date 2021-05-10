<template>
  <div class="container" :class="{ 'has-photo': !recipesAreVisible }">
    <search v-on:seeInput="getRecipes"></search>
    <welcome v-show="!recipesAreVisible && !noRecipesFound"></welcome>
    <recipes-for-you
      v-if="recipesAreVisible"
      :listLength="listLength"
    ></recipes-for-you>
    <no-recipe v-else-if="noRecipesFound"></no-recipe>
    <recipes :meals="meals" v-show="recipesAreVisible"> </recipes>
  </div>
</template>

<script>
import Search from './components/Search.vue';
import Recipes from './components/Recipes.vue';
import RecipesForYou from './components/RecipesForYou.vue';
import NoRecipe from './components/NoRecipe.vue';
import Welcome from './components/Welcome.vue';

export default {
  components: {
    Search,
    Recipes,
    RecipesForYou,
    NoRecipe,
    Welcome
  },
  data() {
    return {
      recipesAreVisible: false,
      noRecipesFound: false,
      meals: '',
      listLength: ''
    };
  },
  methods: {
    getRecipes(value) {
      if (!value) {
        this.noRecipesFound = true;
        this.recipesAreVisible = false;
      } else {
        fetch(
          `https://www.themealdb.com/api/json/v1/1/filter.php?i=${value}
      `
        )
          .then(response => {
            return response.json();
          })
          .then(data => {
            if (data.meals) {
              this.meals = data.meals;
              this.recipesAreVisible = true;
              this.listLength = data.meals.length;
            } else {
              console.log('no data');
              this.noRecipesFound = true;
              this.recipesAreVisible = false;
            }
          });
      }
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
  font-family: 'Kiwi Maru', serif;
}

body {
  margin: 0;
  padding: 0;
  background-color: #f1f7f7;
}

ul {
  padding: 0;
}

li {
  list-style: none;
}

.container {
  margin: 0 auto;
  max-width: 1400px;
  padding-right: 20px;
  padding-left: 20px;
  text-align: center;
  padding-top: 40px;
  height: 100vh;
}

.has-photo {
  background-image: url('./img/welcome.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: 20%;
}
</style>

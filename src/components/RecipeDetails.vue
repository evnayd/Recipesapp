<template>
  <div class="backdrop" v-on:click="closeTheDetails">
    <div class="recipe__details details">
      <button
        class="details__btn"
        v-on:click="closeTheDetails"
        aria-label="Close modal"
      >
        Close
      </button>
      <div class="details__content">
        <h2 class="details__title">{{ mealInfo.strMeal }}</h2>
        <p class="details__category">Category: {{ mealInfo.strCategory }}</p>
        <div class="details__instruction">
          <h3>Instructions:</h3>
          <p>
            {{ mealInfo.strInstructions }}
          </p>
        </div>
        <div class="details__img">
          <img alt="food" :src="mealInfo.strMealThumb" />
        </div>
        <div class="details__link">
          <a :href="mealInfo.strYoutube" target="_blank">Video recipe</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    mealInfo: Object
  },
  data() {
    return {
      isActive: true,
      detailsAreVisible: true
    };
  },
  methods: {
    closeTheDetails() {
      this.$emit('close');
    }
  }
};
</script>

<style scoped>
.backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.details {
  width: 100%;
  max-width: 1000px;
  height: 90%;
  overflow-y: scroll;
  border-radius: 10px;
  color: #fff;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #e8a344;
  padding-top: 15px;
  padding-bottom: 15px;
  padding-left: 10px;
  padding-right: 10px;
  display: block;
}

.details__instruction p {
  text-align: left;
}

.details__img img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  border: 3px solid #fff;
  margin-bottom: 15px;
}

.details__link a {
  color: #fff;
  border-bottom: 2px solid #fff;
  text-decoration: none;
  display: inline-block;
  margin-bottom: 10px;
}

.details__link:hover a {
  color: #a1d73f;
  border-bottom: 2px solid #a1d73f;
  text-decoration: none;
}

.details__btn {
  font-family: inherit;
  width: 110px;
  padding: 10px;
  outline: none;
  border: none;
  color: #e34f46;
  background-color: #fff;
  border-radius: 6px;
  cursor: pointer;
}

.details__btn:hover {
  background-color: #e34f46;
  color: #fff;
}

@media (min-width: 768px) {
  .details {
    padding: 20px;
    width: 80%;
  }

  .details__img img {
    margin-top: 20px;
    width: 150px;
    height: 150px;
  }
}
</style>

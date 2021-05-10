<template>
  <form class="search" v-on:submit.prevent="getInputValue">
    <input
      class="search__input"
      type="text"
      placeholder="Enter an ingredient"
      v-model="enteredIngredient"
      v-on:focus="clearTheInput"
    />
    <button class="search__btn" type="submit">
      Find
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      enteredIngredient: ''
    };
  },
  methods: {
    getInputValue() {
      this.$emit('seeInput', this.enteredIngredient);
    },

    clearTheInput() {
      this.enteredIngredient = '';
    }
  }
};
</script>

<style scoped>
.search {
  display: flex;
  margin-bottom: 20px;
}

.search__input {
  width: 400px;
  padding: 10px;
  border: 2px solid #a1d73f;
  border-top-left-radius: 10px;
  margin-right: 10px;
  outline: none;
  font-family: inherit;
}

.search__btn {
  font-family: inherit;
  width: 90px;
  padding: 10px;
  outline: none;
  border: none;
  background-color: #e34f46;
  color: #fff;
  border-radius: 6px;
  cursor: pointer;
}

.search__btn:hover {
  background-color: #a1d73f;
}
</style>

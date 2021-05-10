<template>
  <div class="no-recipe">
    <h2>
      Sorry we can't find recipes with this ingredient. May be you can try with
      another one?
    </h2>
  </div>
</template>

<style scoped>
.no-recipe {
  width: 100%;
  background-color: #fff;
  color: #e34f46;
  margin: 0 auto;
  text-align: left;
  font-size: 14px;
  padding: 30px;
  border-radius: 6px;
}

@media (min-width: 768px) {
  .no-recipe {
    text-align: center;
    width: 700px;
  }
}
</style>

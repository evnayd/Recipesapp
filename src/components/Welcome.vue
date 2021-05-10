<template>
  <div class="welcome">
    <h2 class="welcome__words">
      Hey! Welcome to our cookbook! There are many recipes and cooking
      inspiration! <br />Enter any ingredient you like, see recipes from all
      over the world, watch video recipes and enjoy cooking!
    </h2>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.welcome {
  position: relative;
  padding: 0;
}

.welcome__words {
  width: 100%;
  background-color: #a1d73f;
  padding: 30px;
  border-radius: 6px;
  margin-top: 40px;
  right: 20px;
  text-align: left;
  color: #fff;
  font-size: 18px;
  line-height: 28px;
}

@media (min-width: 768px) {
  .welcome__words {
    width: 500px;
    position: absolute;
    margin-top: 40px;
    left: 0;
  }
}
</style>

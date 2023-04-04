<template>
  <div class="ct m-top">
    <div class="wrapper center">
      <div><img src="../assets/logo-play-header.png"></div>
      <ul><li v-for="l in loremLong" :key="l">{{ l }}</li></ul>
      <ul><li v-for="l in lorem" :key="l">{{ l }}</li></ul>
      <ul><li v-for="l in loremSmall" :key="l">{{ l }}</li></ul>
    </div>
  </div>
</template>

<script setup lang="ts">
const loremLong:string[] = ["Lorem ipsum dolor sit", "amet", "consectetur", "adipisicing", "elit.", "Dolor", "sit", "amet", "consectetur."];
const lorem:string[] = ["Lorem ipsum", "dolor sit amet consectetur", "adipisicing elit."];
const loremSmall:string[] = ["Lorem ipsum", "dolor", "sit amet."];

</script>

<style scoped lang="postcss">
.ct {
  background: url('../assets/play-footer-texture.jpg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  padding: 80px 0 120px 0;
}

.wrapper {
  display: flex;
  justify-content: center;

  color: white;
  text-transform: capitalize;
}

ul {
  margin: 0;
}

ul li:first-child {
  font-weight: bold;
  margin-bottom: 1rem;
}

img {
  min-height: 75px;
}

@media only screen and (max-width:980px) {
  .wrapper {
    flex-direction: column;
    align-items: center;
  }

  ul {
    margin: 2rem 0 0 0;
    padding: 0;
    text-align: center;
  }
}
</style>
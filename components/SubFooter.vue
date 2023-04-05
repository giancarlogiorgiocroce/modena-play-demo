<template>
  <div class="band-ct">
    <div class="icons-ct">
      <icon v-for="name in names" :key="name" :name="name" class="icon" />
    </div>
    <div v-for="btn in btns" :key="btn" class="btn-ct">
      <Button :value="btn" inverted-colorscheme fill-space></Button>
    </div>
  </div>
</template>

<script setup lang="ts">
const names = [
  "entypo-social:twitter",
  "entypo-social:facebook",
  "entypo-social:instagram",
  "entypo-social:youtube",
  "entypo-social:google",
];
const btns = ["NEWSLETTER", "SCOPRI MODENA"];
</script>

<style lang="postcss" scoped>
.band-ct {
  position: fixed; bottom: 0; right: 0; left: 0;
  display: flex; align-items: center;
  height: 80px;
  background: #b0082b;
}

.btn-ct, .icons-ct {
  margin: 0 1rem;
  width: 275px;
  height: 40px;
}

.icons-ct {
  display: flex; justify-content: space-around; align-items: center;

  color: white;
  background-color: #b0082b;

  padding: 10px 20px;
  border-radius: 20px;
  border: 4px solid#fff;

  transition: all 0.3s ease-out;
}

.icon {
  width: 20px;
  height: 20px;
}
.icon:hover {
  cursor: pointer;
  color: #000;
}

@media only screen and (max-width: 980px) {
  .scroll-progress {
    @apply hidden;
  }
}
</style>

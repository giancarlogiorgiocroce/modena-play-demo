<template>
  <div class="btn" :class="{'bg-red': !invertedColorscheme}">
    <div class="icon" v-if="name"> <font-awesome-icon icon="fa-solid fa-user" /> </div>
    <p>{{ value }}</p>
  </div>
</template>

<script setup lang="ts">
// PROPS
interface Props {
  value?: string,
  name?: string,
  invertedColorscheme?: boolean,
}
const props = withDefaults(defineProps<Props>(), {
  value: '',
  name: '',
  invertedColorscheme: false,
})
</script>

<style scoped>
.btn {
  color: white;
  height: fit-content;
  width: fit-content;
  padding: 10px 20px;
  border-radius: 20px;
}
.icon {
  height: 20px;
  width: 20px;
  fill: white;

}
p {
  font-weight: bold;
}
</style>
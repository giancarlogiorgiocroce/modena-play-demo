<template>
  <div class="btn flex-c" :class="{'inverted-color-scheme': invertedColorscheme, 'fill-space': fillSpace}">
    <Icon v-if="name" class="icon" :name="name"/>
    <p>{{ value }}</p>
  </div>
</template>

<script setup lang="ts">
// PROPS
interface Props {
  value?: string,
  name?: string,
  invertedColorscheme?: boolean,
  fillSpace?: boolean,
}
const props = withDefaults(defineProps<Props>(), {
  value: '',
  name: '',
  invertedColorscheme: false,
  fillSpace: false,
})
</script>

<style scoped>
@media only screen and (min-width: 1280px) {
  .btn {
    font-size: 1.3rem;
  }
}
.btn {
  color: white;
  background-color: #b0082b;

  height: 52px;
  width: fit-content;
  padding: 10px 20px;
  border-radius: 20px;
  border: 4px solid#b0082b;

  transition: all 0.3s ease-out;
}

.btn.fill-space {
  width: 100%;
  height: 100%;
}

.btn:hover {
  color: #b0082b;
  background-color: #fff;

  border: 4px solid#b0082b;

  cursor: pointer;
}

.btn.inverted-color-scheme {
  color: #fff;
  background-color: #b0082b;

  border: 4px solid #fff;

  cursor: pointer;
}

.btn.inverted-color-scheme:hover {
  color: #b0082b;
  background-color: #fff;

  border: 4px solid#fff;

  cursor: pointer;
}

.icon {
  width: 100%;
  height: 100%;
}
p {
  font-weight: bold;
}
</style>
<template>
  <div :class="{
    'modal': true,
    'visible': isVisible,
  }">
    <div class="bg" />
    <div class="box show-from-top">
      <div class="main">
        <div class="content">
          {{ value }}
        </div>
      </div>
      <div class="footer">
        <div class="btn-ct">
          <Button :value="btn" @click="next()" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Props {
  isVisible: boolean;
  value: string;
  btn?: string;
}
const props = withDefaults(defineProps<Props>(), {
  isVisible: false,
  value: "Sembra che tu non abbia ancora un account!",
  btn: "Continua",
});

const emit = defineEmits(['continue']);
const next = () => emit("continue");
</script>


<style lang="postcss" scoped>
.modal {
  position: fixed; top: 0; left: 0; z-index: 30;
  width: 100%; height: 100%; padding-top: 2.5rem;
  display: flex; justify-content: center;
  opacity: 0; transition: opacity 200ms; transition-timing-function: ease;
  pointer-events: none;
}

.modal .box {
  width: 500px; height: fit-content;
  background: white; border-radius: 1.5rem; overflow: hidden; box-shadow: 0 0 150px rgba(0, 0, 0, 0.1);
}

.box.show-from-top {
  transition-duration: 500ms;
  opacity: 0;
  transform: translateY(-50px);
  transition-property: transform, opacity;
}

.box .main {
  display: flex; justify-content: center; align-items: center;
  gap: 0.75rem; padding: 0.75rem; min-height: 50px;
  background: #b0082b; color:#fff;
}

.box .footer {
  display: flex; justify-content: flex-end; align-items: center;
  background: #fefefe;
  min-height: 75px; padding: 0 1rem;
}

.modal.visible {
  opacity: 100;
  pointer-events: auto;
}

.visible .box.show-from-top {
  opacity: 100;
  transform: translateY(0);
}

.bg {
  position: absolute; top: 0; right: 0; bottom: 0; left: 0;
  height: 100%;
  background: rgba(255, 255, 255, 0.8); backdrop-filter: blur(10px);
}

/* @media only screen and (max-width: 980px) {
  .modal {
    & .box {
      @apply absolute;

      &:not(.keep-height-inline-style) {
        @apply h-auto my-0 overflow-y-auto !important;

        top: 15px;
        bottom: 15px;
      }

      &:not(.keep-width-inline-style) {
        @apply w-auto mx-0 !important;

        right: 15px;
        left: 15px;
      }
    }
  }
} */
</style>

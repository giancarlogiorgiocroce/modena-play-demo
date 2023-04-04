<template>
  <div>
    <p class="label">{{ label }}</p>
    <input
      ref="input"
      type="text"
      :name="name"
      :value="modelValue"
      :disabled="disabled"
      @keypress="keypress($event)"
      @input="updateValue(($event.target as HTMLInputElement).value)"
    />
    <InputDescription v-if="description" :text="description" />
  </div>
</template>

<script lang="ts">
export default defineNuxtComponent({
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    name: {
      type: String,
      default: "",
    },
    description: {
      type: String,
      default: "",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    valid: {
      type: Boolean,
      default: true,
    },
  },

  methods: {
    updateValue(value: String) {
      this.$emit("update:modelValue", value);
    },

    focus() {
      (this.$refs.input as HTMLInputElement).focus();
    },

    keypress(event: KeyboardEvent) {
      switch (event.keyCode) {
        case 13:
          this.$emit("onEnter");
          break;
      }
    },
  },
});
</script>

<style lang="postcss" scoped>
.text-input {
  @apply relative;

  & input {
    @apply text-base px-5 bg-input resize-none text-black font-medium rounded-md;

    width: 300px;
    padding-top: 10px;
    padding-bottom: 10px;

    &:focus {
      @apply outline-none bg-input-focus;
    }

    &[type="search"] {
      padding-right: 50px;
    }
  }

  & .search-ico {
    @apply flex items-center justify-center absolute top-0 bottom-0 right-0;

    & svg {
      @apply w-6 h-6 text-grey fill-current;
    }

    width: 50px;
  }

  &.fill {
    & input {
      @apply w-full;
    }
  }

  &.not-valid {
    & input {
      @apply bg-red;
    }
  }

  &.disabled {
    @apply pointer-events-none opacity-50;
  }
}

@media only screen and (max-width: 980px) {
  .text-input {
    & input {
      @apply w-full;
    }
  }
}
</style>

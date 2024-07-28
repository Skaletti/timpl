<template>
  <label class="a-toggle">
    <input type="checkbox" :checked="modelValue" @change="handleToggle">
    <span class="a-toggle__slider"></span>
  </label>
</template>

<script setup lang="ts">
const props = defineProps<{
  modelValue: boolean;
}>();

const emit = defineEmits(['update:modelValue']);

const handleToggle = (event: Event) => {
  const target = event.target as HTMLInputElement;
  emit('update:modelValue', target.checked);
};
</script>

<style scoped lang="scss">
.a-toggle {
  position: relative;
  display: inline-block;
  width: 54px;
  height: 30px;

  input {
    opacity: 0;
    width: 0;
    height: 0;
  }

  &__slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(#8E6CEA, 0.4);
    transition: 0.4s;
    border-radius: 25px;

    &:before {
      position: absolute;
      content: "";
      height: 24px;
      width: 24px;
      left: 3px;
      top: 3px;
      background-color: white;
      transition: 0.4s;
      border-radius: 50%;
    }
  }

  & input:checked + .a-toggle__slider {
    background-color: var(--color-secondary);

    &:before {
      transform: translateX(24px);
    }
  }
}
</style>

<template>
  <component :is="props.as" v-bind="$attrs" :class="buttonClasses" @click="clickHandler">
    <slot v-if="$slots.suffix" name="suffix"/>
    <slot/>
    <slot v-if="$slots.postfix" name="postfix"/>
  </component>
</template>

<script lang="ts" setup>
import {computed} from 'vue'

type Props = {
  as?: 'button' | 'router-link'
  appearance?: 'primary' | 'secondary' | 'tertiary' | 'link'
}

const props = withDefaults(defineProps<Props>(), {
  as: 'button',
  appearance: 'primary',
})

const clickHandler = () => {
  console.log('click!')
}

const buttonClasses = computed(() => {
  return ['a-button', `a-button--${props.appearance}`]
})
</script>

<style scoped lang="scss">
.a-button {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  border: none;
  border-radius: 40px;
  padding: 10px;
  font-family: "Manrope", sans-serif;
  font-weight: 500;
  font-size: 16px;
  line-height: 24px;

  &--primary {
    color: var(--color-white);
    background-color: var(--color-primary);
  }

  &--secondary {
    color: var(--color-white);
    background-color: var(--color-secondary);
  }

  &--tertiary {
    color: #1F2A37;
    background-color: var(--color-white);
    border: none;
    border-radius: 12px;
    padding: 8px 24px;
  }

  &--llink {
    width: fit-content;
    background-color: inherit;
  }
}
</style>

<template>
  <router-link :to="props.to" :class="linkClass">
    <span class="a-link__icon">
      <slot name="icon" />
    </span>
    <slot />
  </router-link>
</template>

<script lang="ts" setup>
import { computed } from 'vue'

type Props = {
  to: string
  underline?: boolean
}

const props = withDefaults(defineProps<Props>(), {
  to: '/',
  underline: false,
})

const linkClass = computed(() => {
  return ['a-link', { 'a-link--underline': props.underline }]
})
</script>

<style scoped lang="scss">
.a-link {
  font-family: "Manrope", sans-serif;
  font-weight: 500;
  font-size: 11px;
  line-height: 15px;
  color: var(--color-secondary);

  &--underline {
    text-decoration: underline;
    text-underline-offset: 4px;
  }
}
</style>

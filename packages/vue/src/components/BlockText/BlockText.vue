<template>
  <div
    class="BlockText"
    :class="computedClass"
    v-html="text"
  ></div>
</template>
<script lang="ts">
import { defineComponent } from 'vue'

interface Variants {
  [key: string]: string
}

export interface BlockTextObject {
  blockType?: string
  value: string
}
export const variants: Variants = {
  small: 'text-body-sm -small',
  medium: 'text-body-md -medium',
  large: 'text-body-lg -large'
}

export default defineComponent({
  name: 'BlockText',
  props: {
    text: {
      type: String,
      required: false
    },
    variant: {
      type: String,
      required: false,
      default: 'large',
      validator: (prop: string): boolean => Object.keys(variants).includes(prop)
    }
  },
  computed: {
    computedClass(): string {
      return variants[this.variant]
    }
  }
})
</script>
<style lang="scss">
@import '@explorer-1/common/src/scss/components/BlockText';
</style>

<template>
  <component
    :is="tag"
    class="mx-button"
    :class="{
      [`mx-button--${variant}`]: variant,
      [`mx-button--${size}`]: size,
      [`mx-button--${behavior}`]: behavior,
      [`mx-button--is-disabled`]: isDisabled,
    }"
    :disabled="isDisabled"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <span
      v-if="hasText"
      class="mx-button__text"
    >
      <slot />
    </span>
  </component>
</template>

<script lang="ts">
import { Prop, Vue } from 'vue-property-decorator';

export default class MXButton extends Vue {
  @Prop({ type: Boolean, default: false }) isDisabled!: boolean;
  @Prop({ type: String, default: 'primary' }) variant!: string;
  @Prop({ type: String, default: 'medium' }) size!: string;
  @Prop({ type: String, default: 'button' }) tag!: string;
  @Prop({ type: String, default: '' }) behavior!: string;

  get hasText() {
    return this.$slots.default;
  }
}
</script>

<style lang="scss">
@import '../../node_modules/madrox-core/dist/madrox.min.css';
</style>

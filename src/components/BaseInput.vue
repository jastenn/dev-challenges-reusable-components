<template>
  <div
    class="base-input-container"
    :class="[{ 'start-icon': startIcon }, {'end-icon': endIcon}, { 'full-width': fullWidth}]"
  >
    <p
      v-if="helperText"
      class="helper-text"
      :class="{error: error}"
    >
      {{ helperText }}
    </p>
    <component
      :is="inputType"
      v-bind="{ ...$attrs }"
      :id="id"
      :class="[
        {error: error},
        size,
      ]"
      type="text"
      :disabled="disabled"
      :placeholder="placeholder"
    />
    <label
      :for="id"
    >
      {{ label }}
    </label>
    <span
      v-if="startIcon || endIcon"
      class="material-icons material-icons"
    >
      {{ startIcon || endIcon }}
    </span>
  </div>
</template>

<script lang="ts">
// eslint-disable-next-line import/no-duplicates
import { defineCustomElement } from 'vue';

export default defineCustomElement({
  inheritAttrs: false,
});
</script>

<script setup lang="ts">
// eslint-disable-next-line
import { computed } from 'vue';
// eslint-disable-next-line @typescript-eslint/no-unused-vars
const props = withDefaults(defineProps<{
  placeholder?: string;
  value?: string;
  size?: 'sm' | 'md';
  error?: boolean;
  disabled?: boolean;
  helperText?: string;
  startIcon?: boolean;
  endIcon?: boolean;
  fullWidth?: boolean;
  multiline?: boolean;
  id?: string;
  label?: string;
}>(), {
  placeholder: 'Placeholder',
  size: 'md',
  label: 'Label',
});

const inputType = computed(() => (props.multiline ? 'textarea' : 'input'));

</script>

<style scoped lang="scss">
@use '@/assets/scss/abstracts/_variables.scss' as var;

.base-input-container {
  position: relative;
  font-size: .875rem;
  display: flex;
  flex-direction: column-reverse;
  align-items: flex-start;
  width: 12.5rem;

  &.full-width {
    width: 100%;
  }

  &.start-icon,
  &.end-icon {
    .material-icons {
      position: absolute;
      top: 50%;
      transform: translateY(-10%);
      color: #828282;
    }
  }

  &.start-icon {
    input {
      padding-left: 2.75rem !important;
    }
    .material-icons {
      left: .75rem;
    }
  }

  &.end-icon .material-icons {
    right: .75rem;
  }

  input,
  textarea {
    display: block;
    width: 100%;
    font-family: inherit;
    color: #333333;
    border: 1px solid #828282;
    border-radius: 0.57rem;
    transition: border 200ms ease-out;

    &.sm {
      padding: 0.714em 0.857em;
    }

    &.md {
      padding: 1.286em 1em;
    }

    &::placeholder {
      color: #828282;
    }

    &:hover:not(:disabled) {
      border: 1px solid #333333;
    }
    &.error {
      border: 1px solid var.$clr-danger-400;

      &:hover {
        border: 1px solid var.$clr-danger-400;
      }

      & ~ label {
        color: var.$clr-danger-400;
      }
    }

    &:focus {
      outline: none;
      border: 1px solid var.$clr-primary-400 !important;
    }

    &:disabled {
      background-color: #f2f2f2;
      border: 1px solid #E0E0E0;

    }

  }

  textarea {
    resize: none;
  }

  label {
    font-size: .75rem;
    margin-bottom: .25em;
    transition: color 200ms ease-out;
  }

  input:focus ~ label,
  textarea:focus ~ label {
    color: var.$clr-primary-400;
  }

  .helper-text {
    font-size: 0.625rem;
    color: #828282;
    &.error {
      color: var.$clr-danger-400;
    }
  }
}

</style>

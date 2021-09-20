<template>
  <button
    :class="[
      {'start-icon': startIcon},
      {'end-icon': endIcon},
      {'disable-shadow': disableShadow},
      variant,
      size,
      color,
      'button',
    ]"
    :disabled="disabled"
  >
    <span
      v-if="startIcon || endIcon"
      class="material-icons material-icons"
    >
      {{ startIcon || endIcon }}
    </span>
    <slot />
  </button>
</template>

<script setup lang="ts">

// eslint-disable-next-line @typescript-eslint/no-unused-vars
const props = withDefaults(defineProps<{
  variant?: 'outline' | 'text',
  disableShadow?: boolean;
  disabled?: boolean;
  startIcon?: string;
  endIcon?: string;
  size?: 'sm' | 'md' | 'lg';
  color?: 'default' | 'primary' | 'secondary' | 'danger';
}>(), {
  size: 'md',
  color: 'default',
});

</script>

<style lang="scss" scoped>
@use '@/assets/scss/abstracts/_variables.scss' as var;

.button {
  font-size: 1rem;
  padding: .5em 1rem;
  border: none;
  border-radius: 0.375rem;
  box-shadow: 0 2px 3px rgba($color: #333, $alpha: .20);
  transition: background-color 200ms ease-out;

  &.default {
    color: var.$clr-default-text;
    background-color: var.$clr-default-400;

    &:hover:not(:disabled) {
      background-color: darken($color: var.$clr-default-400, $amount: 10);
    }

    &:disabled {
      color: var.$clr-default-disabled-text;
    }

    &.outline, &.text {
      color: var.$clr-default-text;
      background-color: unset;
      box-shadow: none;

      &:hover:not(:disabled) {
        background-color: rgba($color: var.$clr-default-400, $alpha: .50);
      }
    }
    &.text:disabled {
      color: var.$clr-default-disabled-text;
    }

    &.outline {
      border: 1px solid var.$clr-default-text;
    }
  }
  &.primary {
    color: var.$clr-primary-text;
    background-color: var.$clr-primary-400;

    &:hover:not(:disabled) {
      background-color: darken($color: var.$clr-primary-400, $amount: 06);
    }

    &:disabled {
      color: var.$clr-primary-text;
    }

    &.outline, &.text {
      color: var.$clr-primary-400;
      background-color: unset;
      box-shadow: none;

      &:hover:not(:disabled) {
        background-color: rgba($color: var.$clr-primary-400, $alpha: .20);
      }

      &:disabled {
        color: lighten($color: var.$clr-primary-400, $amount: 25) ;
      }
    }

    &.outline {
      border: 1px solid var.$clr-primary-400;
      &:disabled {
        border:1px solid lighten($color: var.$clr-primary-400, $amount: 25) ;
      }
    }
  }
  &.secondary {
    color: var.$clr-secondary-text;
    background-color: var.$clr-secondary-400;

    &:hover:not(:disabled) {
      background-color: darken($color: var.$clr-secondary-400, $amount: 06);
    }

    &:disabled {
      color: var.$clr-secondary-text;
    }

    &.outline, &.text {
      color: var.$clr-secondary-400;
      background-color: unset;
      box-shadow: none;

      &:hover:not(:disabled) {
        background-color: rgba($color: var.$clr-secondary-400, $alpha: .20);
      }
      &:disabled {
        color: lighten($color: var.$clr-secondary-400, $amount: 25) ;
      }
    }

    &.outline {
      border: 1px solid var.$clr-secondary-400;
      &:disabled {
        border: 1px solid lighten($color: var.$clr-secondary-400, $amount: 25) ;
      }
    }
  }

  &.danger {
    color: var.$clr-danger-text;
    background-color: var.$clr-danger-400;

    &:hover:not(:disabled) {
      background-color: darken($color: var.$clr-danger-400, $amount: 06);
    }

    &:disabled {
      color: var.$clr-danger-text;
    }

    &.outline, &.text {
      color: var.$clr-danger-400;
      background-color: unset;
      box-shadow: none;

      &:hover:not(:disabled) {
        background-color: rgba($color: var.$clr-danger-400, $alpha: .20);
      }
      &:disabled {
        color: lighten($color: var.$clr-danger-400, $amount: 25) ;
      }
    }

    &.outline {
      border: 1px solid var.$clr-danger-400;
      &:disabled {
        border: 1px solid lighten($color: var.$clr-danger-400, $amount: 25) ;
      }
    }
  }

  &.disable-shadow {
    box-shadow: none;
  }

  &.sm {
    padding: 0.375em .75rem;
  }

  &.md {
    padding: .5em 1rem;
  }

  &.lg {
    padding: 0.6875rem 1.375rem;
  }

  // Icon Styles
  &.start-icon,
  &.end-icon {
    > span.material-icons {
      font-size: 1.125rem;
    }
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &.start-icon {
    > span.material-icons {
      margin-right: .3em;
    }
  }

  &.end-icon {
    flex-direction: row-reverse;
    > span.material-icons {
      margin-left: .3em;
    }
  }
}
</style>

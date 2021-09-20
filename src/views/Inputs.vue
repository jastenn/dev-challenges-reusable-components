<template>
  <h3 class="page-heading">
    Buttons
  </h3>
  <article class="component-list">
    <div
      v-for="(componentPreviewGroup, i) in componentPreviewsArr"
      :key="i"
      class="component-col"
    >
      <div
        v-for="(componentPreview, j) in componentPreviewGroup"
        :key="j"
        class="component-row"
      >
        <p class="component-label">
          {{ componentPreview.label }}
        </p>
        <BaseInput
          v-bind="{
            ...componentPreview.props
          }"
        >
          Button
        </BaseInput>
      </div>
    </div>
  </article>
</template>

<script setup lang="ts">
import BaseInput from '@/components/BaseInput.vue';

const previewHelperText = 'Some interesting text';

// eslint-disable-next-line @typescript-eslint/no-explicit-any
const componentPreviewsArr: any = [
  [
    { label: '<BaseInput />', props: {} },
  ],
  [
    { label: '<BaseInput error />', props: { error: true } },
  ],
  [
    { label: '<BaseInput disabled />', props: { disabled: true } },
  ],
  [
    { label: `<BaseInput helper-text=${previewHelperText} />`, props: { 'helper-text': previewHelperText } },
    { label: `<BaseInput helper-text=${previewHelperText} error />`, props: { 'helper-text': previewHelperText, error: true } },
  ],
  [
    { label: '<BaseInput start-icon="phone" />', props: { 'start-icon': 'phone' } },
    { label: '<BaseInput end-icon="lock" />', props: { 'end-icon': 'lock' } },
  ],
  [
    { label: '<BaseInput size="sm" />', props: { size: 'sm' } },
    { label: '<BaseInput size="md" />', props: { size: 'md' } },
  ],
  [
    { label: '<BaseInput fullwidth />', props: { 'full-width': true } },
  ],
  [
    { label: '<BaseInput multiline rows="4" />', props: { multiline: true, rows: 4 } },
  ],
];
</script>

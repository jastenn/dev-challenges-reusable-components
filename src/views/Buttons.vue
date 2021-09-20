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
        <BaseButton
          v-bind="{
            ...componentPreview.props
          }"
        >
          Button
        </BaseButton>
      </div>
    </div>
  </article>
</template>

<script setup lang="ts">
import BaseButton from '@/components/BaseButton.vue';

// eslint-disable-next-line @typescript-eslint/no-explicit-any
const componentPreviewsArr: any = [
  [
    { label: '<BaseButton />', props: {} },
  ],
  [
    { label: '<BaseButton variant="outline" />', props: { variant: 'outline' } },
    { label: '<BaseButton variant="outline" color="primary" />', props: { variant: 'outline', color: 'primary' } },
    { label: '<BaseButton variant="outline" color="secondary" />', props: { variant: 'outline', color: 'secondary' } },
    { label: '<BaseButton variant="outline" color="danger" />', props: { variant: 'outline', color: 'danger' } },
  ],
  [
    { label: '<BaseButton variant="text" />', props: { variant: 'text' } },
    { label: '<BaseButton variant="text" color="primary" />', props: { variant: 'text', color: 'primary' } },
    { label: '<BaseButton variant="text" color="secondary" />', props: { variant: 'text', color: 'secondary' } },
    { label: '<BaseButton variant="text" color="danger" />', props: { variant: 'text', color: 'danger' } },
  ],
  [
    { label: '<BaseButton disableShadow />', props: { disableShadow: true } },
  ],
  [
    { label: '<BaseButton disabled />', props: { disabled: true } },
    { label: '<BaseButton variant="text" disabled />', props: { disabled: true, variant: 'text' } },
  ],
  [
    { label: '<BaseButton start-icon="local_grocery_store" color="primary" />', props: { 'start-icon': 'local_grocery_store', color: 'primary' } },
    { label: '<BaseButton end-icon="local_grocery_store" color="primary" />', props: { 'end-icon': 'local_grocery_store', color: 'primary' } },
  ],
  [
    { label: '<BaseButton size="sm" />', props: { size: 'sm' } },
    { label: '<BaseButton size="md" />', props: { size: 'md' } },
    { label: '<BaseButton size="lg" />', props: { size: 'lg' } },
  ],
  [
    { label: '<BaseButton color="default" />', props: { color: 'default' } },
    { label: '<BaseButton color="primary" />', props: { color: 'primary' } },
    { label: '<BaseButton color="secondary />', props: { color: 'secondary' } },
    { label: '<BaseButton color="danger" />', props: { color: 'danger' } },
  ],

];

</script>

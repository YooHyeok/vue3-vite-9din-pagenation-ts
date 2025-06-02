<template>
  <div class="basic-button">
    <img :src="`src/assets/icons/${data.icon}.svg`" alt="" class="basic-button__icon" />
    <span class="basic-button__label">{{ data.label }}</span>
  </div>
</template>
<script setup lang="ts">

import { defineProps, toRefs } from 'vue';

interface Button {
  icon: string;
  label: string;
}
interface Props {
  data: Button;
}

const props = defineProps<Props>();
const { data } = toRefs(props)

</script>
<style lang="scss" scoped>
.basic-button {
  display: flex;
  align-items: center;
  justify-content: flex-start;

  width: calc(100% - 24px);
  height: 40px;

  padding-left: 12px;
  gap: 16px;

  cursor: pointer;

  &__icon {
    width: 20px;
    height: 20px;
  }
  &__label {
    padding-top: 4px;

    font-weight: 400;
    font-size: 16px;

    font-family: 'MBC1961GulimM';

    color: $color-white-000
  }
  &:hover {
    width: 100%;

    background-color: rgba($color-white-000, 0.1);
    border-radius: 6px;
  }
}
</style>
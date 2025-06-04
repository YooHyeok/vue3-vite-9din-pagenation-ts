<template>
  <div class="pagination">
    <button class="pagination__button" @click="moveToPrev">
      <img src="@assets/icons/arrow-left.svg" alt="">
    </button>
    <button class="pagination__button" @click="moveToPrev"></button>
    <button class="pagination__button" @click="moveToNext">
      <img src="@assets/icons/arrow-right.svg" alt="">
    </button>
  </div>
</template>
<script setup lang="ts">

</script>
<style lang="scss" scoped>
.pagination {
  display: flex;
  align-items: center;
  justify-content: center;

  width: 100%;

  gap: 8px;

  &__button {
    display: flex;
    align-items: center;
    justify-content: center;

    width: 24px;
    height: 24px;

    padding: 3px 7px;
    color: $color-gray-500;
    font-size: 16px;
    font-weight: 700;
    line-height: 16px;

    background: transparent;
    border: none;
    outline: none;

    cursor: pointer;

    &:hover {
      background-color: $color-gray-100;
      border-radius: 4px;

      color: $color-black-900;
    }

    &:active {
      background-color: $color-gray-100;
            border-radius: 4px;

      color: $color-black-900;
    }
  }
}
</style>

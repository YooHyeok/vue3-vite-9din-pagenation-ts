<template>
  <div class="list">
    <div class="list__avatar">
      <img src="@/assets/images/arare.jpg" alt="" class="list__avatar__image">
      <div class="list__avatar__text-box">
        <span class="name">Marco</span>
        <span class="ducy">User Experience</span>
      </div>
    </div>
    <div class="list__item"></div>
    <div class="list__item"></div>
    <div class="list__item">
      <div class="list__item__chip">Senior</div>
    </div>
  </div>
</template>

<script setup lang="ts">

</script>

<style lang="scss" scoped>
.list {
  display: flex;
  align-items: center;

  width: calc(100% - 32px);
  height: 72px;
  min-height: 72px;

  padding: 0 16px;
  gap: 24px;

  background-color: rgba($color-white-200, 0.1);
  border-radius: 16px;

  &__avatar {
    display: flex;
    align-items: center;
    justify-content: flex-start;

    width: 25%;

    gap: 8px;

    &__image {
      width: 44px;
      height: 44px;

      border-radius: 50%;
      border: 1px solid rgba($color-white-200, 0.3);
    }

    &__text-box {
      display: flex;
      flex-direction: column;

      gap: 4px;

      .name {
        color: $color-black-900;
      }
      .duty {
        font-size: 14px;
        font-weight: 300;
        color: $color-white-200;
      }
    }
  }
  &__item {
    width: 25%;

    &__chip {
      display: flex;
      align-items: center;
      justify-content: center;

      width: 60px;
      height: 12px;

      padding: 8px;

      color: $color-blue-000;

      background-color: rgba($color-blue-000, 0.1);
      border-radius: 12px;
    }
  }
}
</style>
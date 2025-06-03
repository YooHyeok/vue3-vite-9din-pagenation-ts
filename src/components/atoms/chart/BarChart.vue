<template>
  <div class="bar-chart">
    <div class="bar-chart__container">
      <span class="bar-chart__container__value">89%</span>
      <div class="bar-chart__container__base">
        <div class="gauge"></div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts"></script>
<style lang="scss" scoped>
.bar-chart {
  display: flex;
  align-items: center;
  justify-content: center;

  width: 70%;

  &__container {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: center;

    width: 100%;

    gap: 4px;

    &__value {
      font-size: 16px;
    }
    &__base {
      position: relative;

      width: 100%;
      height: 12px;

      background-color: rgba($color-white-200, 0.3);
      border-radius: 10px;

      /* 
      position: absolute인 gauge 선택자는 position이 relative인 __base 선택자를 찾는다.
      __base 선택자 위치를 기준으로 좌표가 잡히며, width, height등 위치와 크기는 __base를 기준으로 계산된다.
      즉, .gauge는 __base안에 정확히 위치하게 되며, 부모 사이즈인 height12와 맞춰 가득 차거나 퍼센티지로 조절된 너비만큼 채워진다.
      */
      .gauge {
        position: absolute;

        width: 89%;
        height: 12px;

        background-color: $color-green-000;
        border-radius: 10px;

      }
    }
  }
}
</style>
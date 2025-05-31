<template>
  <div class="basic-layout">
    <slot></slot><!-- slot: BasicLayout 컴포넌트에 무엇이든 담길 수 있는 주머니 역할 -->
  </div>
</template>
<script setup lang="ts"></script>
<style lang="scss" scoped>
.basic-layout {
  display: flex;
  align-items: center;
  justify-content: center;

  padding: 20px;
  
  background-color: $color-white-000;
  border-radius: 24px;
}
</style>
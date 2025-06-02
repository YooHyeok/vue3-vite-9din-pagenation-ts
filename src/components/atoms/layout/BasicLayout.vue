<template>
  <div class="basic-layout" :layout-theme="theme">
    <slot></slot><!-- slot: BasicLayout 컴포넌트에 무엇이든 담길 수 있는 주머니 역할 -->
  </div>
</template>
<script setup lang="ts">
import { defineProps, toRefs } from 'vue';

/**
 * ?(Optional)의 경우 string외에 undefined를 허용 (타입스크립트 에러 방지를 위해)
 * - 데이터 로드후 prop으로 넘길 때 theme이름을 필수로 사용하지 않아도 문제가 되지 않게끔 하기위한 설정.
 * - ?를 사용하지 않고 theme 타입이 string이라고 정의해 버리면 theme값은 무조건 존재(required)해야 되기 때문 
 */
interface Props {
  theme?: string; // 
}
const props = defineProps<Props>()
const {theme} = toRefs(props)
</script>
<style lang="scss" scoped>
.basic-layout {
  display: flex;
  align-items: center;
  justify-content: center;

  padding: 20px;
  
  background-color: $color-white-000;
  border-radius: 16px;
  
  /* .basic-layout[layout-theme="blue"] {} 형태로 css효과가 */
  &[layout-theme="blue"] {
    background-color: $color-blue-000;
  }
}
</style>
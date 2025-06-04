<template>
  <div class="notice">
    <div class="notice__header">
      <div class="notice__header__total">
        <span class="count">142</span>
        <span class="label">Candidates</span>
      </div>
      <div class="notice__header__info">
        <div class="item">
          <div class="item__top">All</div>
          <div class="item__bottom">Best In</div>
        </div>
        <div class="item">
          <div class="item__top">All</div>
          <div class="item__bottom">Best In</div>
        </div>
        <div class="item">
          <div class="item__top">Default</div>
          <div class="item__bottom">Sort Results</div>
        </div>
      </div>
    </div>
    <div class="notice__body">
      <div class="notice__body__column">
        <span class="label">Name</span>
        <span class="label">Resume Score</span>
        <span class="label">Skill Match</span>
        <span class="label">Skill</span>
      </div>
      <div class="notice__body__list-box">
        <NoticeList v-for="item in tableData" :key="item.userName" :data="item"/>
      </div>
    </div>
    <div class="notice__footer">
      <pagination :totalPage="totalPage" @send-event="reset"/>
    </div>
  </div>
</template>
<script setup lang="ts">
import NoticeList from '@components/mocules/List.vue'
import pagination from '@components/mocules/common/pagination.vue'
import { onMounted, ref, watch } from 'vue';

interface List {
  userName: string;
  userRole: string;
  userResumeScore: number;
  userSkillMatch: number;
  userSkill: string;
}

const tableData = ref<List[]>([]);
const selectedPage = ref<number>(1); // 0페이지라는 UI는 없으므로 초기값을 1로 세팅
const totalPage = ref<number>(0); // tableData의 개수에 따라 페이지네이션 UI에 그려지는 숫자리스트.
const totalCount = ref<number | undefined>(); // 총 데이터 리스트 개수
const limit = ref<number>(10); // 한 페이지당 나타낼 데이터 개수

/* 컴포넌트 DOM이 렌더링 된 이후 실행 */
onMounted(() => {
  getData();
})

const getData = () => {
  tableData.value = [
    {
        userName: 'Marco',
        userRole: 'FrontEnd Developer',
        userResumeScore: 89,
        userSkillMatch: 80,
        userSkill: 'Junior',
    },
    {
        userName: 'Jeff',
        userRole: 'BackEnd Developer',
        userResumeScore: 72,
        userSkillMatch: 65,
        userSkill: 'Senior',
    },
    {
        userName: 'Eric',
        userRole: 'User Experience',
        userResumeScore: 90,
        userSkillMatch: 91,
        userSkill: 'Senior',
    },
    {
        userName: 'Merry',
        userRole: 'User Interface',
        userResumeScore: 56,
        userSkillMatch: 43,
        userSkill: 'Junior',
    },
    {
        userName: 'Harry',
        userRole: 'Project Manager',
        userResumeScore: 61,
        userSkillMatch: 81,
        userSkill: 'Junior',
    },
    {
        userName: 'John',
        userRole: 'Project Orner',
        userResumeScore: 100,
        userSkillMatch: 100,
        userSkill: 'Senior',
    },
    {
        userName: 'Maxwell',
        userRole: 'FrontEnd Developer',
        userResumeScore: 50,
        userSkillMatch: 60,
        userSkill: 'Senior',
    },
    {
        userName: 'Pole',
        userRole: 'BackEnd Developer',
        userResumeScore: 80,
        userSkillMatch: 76,
        userSkill: 'Senior',
    },
    {
        userName: 'Marco',
        userRole: 'FrontEnd Developer',
        userResumeScore: 89,
        userSkillMatch: 80,
        userSkill: 'Junior',
    },
    {
        userName: 'Jeff',
        userRole: 'BackEnd Developer',
        userResumeScore: 72,
        userSkillMatch: 65,
        userSkill: 'Senior',
    },
    {
        userName: 'Eric',
        userRole: 'User Experience',
        userResumeScore: 90,
        userSkillMatch: 91,
        userSkill: 'Senior',
    },
    {
        userName: 'Merry',
        userRole: 'User Interface',
        userResumeScore: 56,
        userSkillMatch: 43,
        userSkill: 'Junior',
    },
    {
        userName: 'Harry',
        userRole: 'Project Manager',
        userResumeScore: 61,
        userSkillMatch: 81,
        userSkill: 'Junior',
    },
    {
        userName: 'John',
        userRole: 'Project Orner',
        userResumeScore: 100,
        userSkillMatch: 100,
        userSkill: 'Senior',
    },
    {
        userName: 'Maxwell',
        userRole: 'FrontEnd Developer',
        userResumeScore: 50,
        userSkillMatch: 60,
        userSkill: 'Senior',
    },
    {
        userName: 'Pole',
        userRole: 'BackEnd Developer',
        userResumeScore: 80,
        userSkillMatch: 76,
        userSkill: 'Senior',
    },
    {
        userName: 'Marco',
        userRole: 'FrontEnd Developer',
        userResumeScore: 89,
        userSkillMatch: 80,
        userSkill: 'Junior',
    },
    {
        userName: 'Jeff',
        userRole: 'BackEnd Developer',
        userResumeScore: 72,
        userSkillMatch: 65,
        userSkill: 'Senior',
    },
    {
        userName: 'Eric',
        userRole: 'User Experience',
        userResumeScore: 90,
        userSkillMatch: 91,
        userSkill: 'Senior',
    },
    {
        userName: 'Merry',
        userRole: 'User Interface',
        userResumeScore: 56,
        userSkillMatch: 43,
        userSkill: 'Junior',
    },
    {
        userName: 'Harry',
        userRole: 'Project Manager',
        userResumeScore: 61,
        userSkillMatch: 81,
        userSkill: 'Junior',
    },
    {
        userName: 'John',
        userRole: 'Project Orner',
        userResumeScore: 100,
        userSkillMatch: 100,
        userSkill: 'Senior',
    },
    {
        userName: 'Maxwell',
        userRole: 'FrontEnd Developer',
        userResumeScore: 50,
        userSkillMatch: 60,
        userSkill: 'Senior',
    },
    {
        userName: 'Pole',
        userRole: 'BackEnd Developer',
        userResumeScore: 80,
        userSkillMatch: 76,
        userSkill: 'Senior',
    },
    {
        userName: 'Marco',
        userRole: 'FrontEnd Developer',
        userResumeScore: 89,
        userSkillMatch: 80,
        userSkill: 'Junior',
    },
    {
        userName: 'Jeff',
        userRole: 'BackEnd Developer',
        userResumeScore: 72,
        userSkillMatch: 65,
        userSkill: 'Senior',
    },
    {
        userName: 'Eric',
        userRole: 'User Experience',
        userResumeScore: 90,
        userSkillMatch: 91,
        userSkill: 'Senior',
    },
    {
        userName: 'Merry',
        userRole: 'User Interface',
        userResumeScore: 56,
        userSkillMatch: 43,
        userSkill: 'Junior',
    },
    {
        userName: 'Harry',
        userRole: 'Project Manager',
        userResumeScore: 61,
        userSkillMatch: 81,
        userSkill: 'Junior',
    },
    {
        userName: 'John',
        userRole: 'Project Orner',
        userResumeScore: 100,
        userSkillMatch: 100,
        userSkill: 'Senior',
    },
    {
        userName: 'Maxwell',
        userRole: 'FrontEnd Developer',
        userResumeScore: 50,
        userSkillMatch: 60,
        userSkill: 'Senior',
    },
    {
        userName: 'Pole',
        userRole: 'BackEnd Developer',
        userResumeScore: 80,
        userSkillMatch: 76,
        userSkill: 'Senior',
    },
  ]
  setPageData();
}

/**
 * 1. totalCount 세팅  
 *    - tableData가 undefined가 아니면 길이만큼, undefined라면 0을 저장  
 *    - 사실 ts에의해 undefined나 null은 human할당 할 수 없음
 * 2. totalPage 세팅  
 *    - 전체 카운트 / 한 페이지당 나타낼 데이터 개수  
 *    - Math.ceil()을 통해 올림 (크거나 같은 숫자중 가장 작은숫자 즉, 강제 올림)  
 *       - 0.9 => 1 | 0.4 => 1 
 *       - 0이 아닐경우 해당 값을, 0일경우 1을 저장
 *       - 만약 0이면 "조회 가능한 데이터가 없습니다." UI 발생 
 *          - 페이지네이션 숫자는 1로 출력
 */
const setPageData = () => {
  totalCount.value = tableData.value !== undefined ? tableData.value.length : 0;
  totalPage.value = Math.ceil(totalCount.value / limit.value) !== 0 ? Math.ceil(totalCount.value / limit.value) : 1
  tableData.value = dissemble(selectedPage.value - 1, tableData.value, limit.value)
}

/**
 * tableData 길이만큼 loop를 돌며 반복.  
 * size(한 페이지당 나타낼 데이터 개수 `limit`) 만큼 자른 결과 배열을 res 배열에 push.  
 * push로 쌓인 res에서 현재 선택된 페이지에 해당하는 데이터 반환
 * 
 * 
 * ```js
 * res.push(data.slice(i, i + size));
 * ```
 * 위 코드에 의해 targetData(data)가 11개일 경우가 있을 경우, limit(size) 값이 10이기 때문에  
 * data.slice(i, i+10) = 10개 / 1개 (총11개 2페이지) 로 쪼개진다.
 * 
 * 
 * @param index selectedPage(ref) - 1
 * @param data tableData(ref)
 * @param size limit(ref)
 * @return 2차원 배열
 */
const dissemble = (index: number, data: List[], size: number) => {
  const res = new Array();

  for(let i = 0; i < data.length; i += size) {
    res.push(data.slice(i, i + size));
  }
  console.log(res)
  return res[index]
}

const reset = (pageIdx: number) => {
  if (pageIdx === 0) selectedPage.value = 1;
  else selectedPage.value = pageIdx;
}

watch(selectedPage, (n, o) => {
  getData();
})

</script>
<style lang="scss" scoped>
.notice {
  display: flex;
  flex-direction: column; // header와 body를 세로로 배치
  align-items: center;
  justify-content: center;
  
  width: calc(100% - 36px);
  height: 100%;

  padding: 0 12px 0 24px;

  &__header {
    display: flex;
    align-items: center;
    justify-content: space-between;

    width: 100%;

    padding-bottom: 12px;

    border-bottom: 1px solid $color-white-200;


    &__total {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      justify-content: center;

      .count {
        font-family: 'MBC1961GulimM';
        font-size: 18px;
      }

      .label {
        font-family: 'SUITE-Regular';
        color: $color-white-200;
      }
    }
    &__info {
      display: flex;
      align-items: center;

      gap: 40px;
      
      .item {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;

        &__top {
          font-family: 'MBC1961GulimM';
          color: $color-blue-000;
        }
        &__bottom {
          font-family: 'SUITE-Regular';
          color: $color-white-200;
        }
      }
    }
  }

  &__body {
    width: 100%;
    height: calc(100% - 92px);

    &__column {
      display: flex;
      align-items: center;

      width: 100%;
      height: 60px;

      .label {
        display: flex;
        align-items: center;
        justify-content: flex-start;

        width: 25%;
        height: 100%;

        margin-left: 16px;

        font-weight: 300;
        color: $color-white-200;
      }
    }
    &__list-box {
        display: flex;
        flex-direction: column;
        justify-content: flex-start;

        width: 100%;
        height: calc(100% - 110px);

        gap: 12px;

        overflow-y: scroll;
    }
  }
}
</style>
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
      <pagination />
    </div>
  </div>
</template>
<script setup lang="ts">
import NoticeList from '@components/mocules/List.vue'
import { ref } from 'vue';

interface List {
  userName: string;
  userRole: string;
  userResumeScore: number;
  userSkillMatch: number;
  userSkill: string;
}

const tableData = ref<List[]>([
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
  //
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
])
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
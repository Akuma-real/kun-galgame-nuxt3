<script setup lang="ts">
import { asideItem } from '../utils/asideItem'
</script>

<template>
  <div class="item">
    <span v-for="kun in asideItem" :key="kun.index">
      <NuxtLinkLocale :to="{ path: kun.router }">
        <Icon class="icon" :name="kun.icon" />
        {{ $t(`home.asideActive.${kun.name}`) }}
      </NuxtLinkLocale>
    </span>
  </div>

  <HomeAsideTopic />
</template>

<style lang="scss" scoped>
.item {
  width: 100%;
  height: 150px;
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 2fr));
  grid-template-rows: repeat(3, minmax(0, 1fr));
  gap: 17px;
  font-size: 14px;
  margin-bottom: 17px;
  padding: 17px;

  @include kun-blur;

  a {
    font-weight: bold;
    text-wrap: nowrap;
    display: flex;
    justify-content: space-around;
    align-items: center;
    overflow: hidden;
    height: 100%;
    width: 100%;
    color: var(--kungalgame-font-color-2);
    border-bottom: 2px solid transparent;

    .icon {
      color: var(--kungalgame-blue-5);
      font-size: 20px;
      margin-right: 10px;
    }

    &:hover {
      border-bottom: 2px solid var(--kungalgame-blue-5);
    }
  }
}
</style>

<script setup lang="ts">
import { asideItem } from '../utils/asideItem'
</script>

<template>
  <div class="base">
    <span
      v-for="kun in asideItem"
      :key="kun.index"
      v-tooltip="{
        message: $t(`home.asideActive.${kun.name}`),
        position: 'right'
      }"
    >
      <NuxtLinkLocale
        :aria-label="$t(`home.asideActive.${kun.name}`)"
        :to="{ path: kun.router }"
      >
        <span>
          <Icon :name="kun.icon" />
        </span>
      </NuxtLinkLocale>
    </span>
  </div>
</template>

<style lang="scss" scoped>
.base {
  height: 100%;
  display: flex;
  flex-direction: column;
  border-radius: 20px;
  background-color: var(--kungalgame-trans-white-5);
  box-shadow: var(--shadow);

  span {
    width: 100%;
    height: 1px;
    flex-grow: 1;
    font-size: 25px;

    a {
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      color: var(--kungalgame-trans-blue-4);
      transition: color 0.2s;

      span {
        height: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        border-left: 3px solid transparent;
        border-right: 3px solid transparent;
        transition: border 0.2s;
      }
    }

    &:hover {
      a {
        color: var(--kungalgame-blue-5);

        span {
          border-left: 3px solid var(--kungalgame-blue-5);
        }
      }
    }
  }
}
</style>

<!--
 * @Author: 金婕
 * @Date: 2025-03-14 13:02:05
 * @LastEditTime: 2025-03-14 15:14:57
 * @LastEditors: 金婕
 * @Description: 
-->
<!--
 * @Author: 金婕
 * @Date: 2025-03-14 13:02:05
 * @LastEditTime: 2025-03-14 15:01:29
 * @LastEditors: 金婕
 * @Description: 
-->
<template>
  <aside class="main-aside">
    <Hello v-if="theme.aside.hello.enable && showInfo" class="weidgets" />
    <div class="sticky">
      <Toc v-if="theme.aside.toc.enable && showToc" class="weidgets" />
      <Countdown class="weidgets" v-if="showInfo" />
      <Tags v-if="theme.aside.tags.enable" class="weidgets" />
      <SiteData v-if="theme.aside.siteData.enable && showInfo" class="weidgets" />
    </div>
  </aside>
</template>

<script setup>
const { theme } = useData();
const props = defineProps({
  // 显示目录
  showToc: {
    type: Boolean,
    default: false,
  },

  showInfo: {
    type: Boolean,
    default: true,
  },
});
</script>

<style lang="scss" scoped>
.main-aside {
  padding-left: 1rem;
  display: flex;
  flex-direction: column;
  animation: fade-up 0.6s 0.3s backwards;
  .weidgets {
    padding: 18px;
    margin-bottom: 1rem;
    cursor: default !important;
    :deep(.title) {
      margin-bottom: 12px;
      font-weight: bold;
      display: flex;
      align-items: center;
      opacity: 0.75;
      .iconfont {
        opacity: 0.6;
        margin-right: 6px;
      }
      .title-name {
        opacity: 0.8;
      }
    }
  }
  .sticky {
    position: sticky;
    top: calc(60px + 1rem);
    .weidgets {
      animation: fade-up 0.6s 0.4s backwards;
      &:last-child {
        margin-bottom: 0;
      }
    }
  }
}
</style>

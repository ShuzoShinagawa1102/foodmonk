<template> 
    <view class="page-searchbar-view">
      <view class="page-searchbar-search-view">
        <input
          class="page-searchbar-search-input"
          v-model="searchText"
          confirm-type="search"
          placeholder="店舗名、食材名を入力"
          placeholder-style="font-size:13px;font-weight:500;color:#bbb"
          @confirm="onSearch"
        />
        <image
          class="page-searchbar-search-icon"
          src="/static/search_icon.png"
          @click="onSearch"
        />
      </view>
    </view>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";
import stocks from "./foodstocks.json";
//ここまで変更、以下コピペ段階
const props = defineProps<{
  items?: {
    pagePath: string;
    selectedIconPath: string;
    iconPath: string;
    text: string;
  }[];
  current: number;
}>();

const list = props.items || navs;

const currentIndex = ref<number>(props.current || 0);

const emit = defineEmits<{
  (e: "clickBarItem", path: string, index: number): void;
}>();

const onTabbarClick = (index: number) => {
  if (currentIndex.value !== index) {
    currentIndex.value = index;
    emit("clickBarItem", list[index].pagePath, index);
  }
};

watch(
  () => props.current,
  (val) => {
    if (val !== currentIndex.value) {
      currentIndex.value = val;
    }
  }
);
</script>


</script>

<style scoped>
.page-foodstock-view {
  position: fixed;
  left: 0;
  right: 0;
  height: 60px;
  height: calc(60px + env(safe-area-inset-bottom));
  height: calc(60px + constant(safe-area-inset-bottom));
  bottom: 0;
  padding-bottom: 0;
  padding-bottom: env(safe-area-inset-bottom);
  padding-bottom: constant(safe-area-inset-bottom);
  background: #fff;
  box-shadow: 0px -0.6px 3.3px 0.3px rgba(0, 0, 0, 0.1);
}

.page-foodstock-view {
  /* #ifndef APP-NVUE */
  display: flex;
  box-sizing: border-box;
  /* #endif */
  flex-direction: row;
  height: 60px;
  height: calc(60px + env(safe-area-inset-bottom));
  height: calc(60px + constant(safe-area-inset-bottom));
  overflow: hidden;
  /* #ifdef H5 */
  cursor: pointer;
  /* #endif */
}
.page-foodstock-food {
  /* #ifndef APP-NVUE */
  display: inline-flex;
  box-sizing: border-box;
  /* #endif */
  position: relative;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.page-foodstock-food__icon {
  display: inline-block;
  position: relative;
  margin-top: 9px;
  width: 38px;
  height: 38px;
}
.page-foodstock-food__image {
  width: 38px;
  height: 38px;
}
.page-foodstock-food__text {
  margin-bottom: 6px;
  flex: 1;
  font-size: 8px;
  line-height: normal;
  text-align: center;
}
</style>
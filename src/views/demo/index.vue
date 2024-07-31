<script setup lang="ts" name="Demo">
import { computed, reactive, ref } from "vue";
import YB from "@/assets/images/yb.png";
const wechat = reactive({
  moments: "一二布布的熊友圈",
  friends: [
    { name: "蜜桃", imgUrl: "" },
    { name: "灰灰", imgUrl: "" },
    { name: "小胖", imgUrl: "" },
    { name: "大胖", imgUrl: "" },
    { name: "小猪", imgUrl: "" },
    { name: "大猪", imgUrl: "" }
  ]
});
const friendsNum = computed({
  get() {
    return wechat.friends.length;
  },
  set() {}
});
</script>

<template>
  <div class="demo-content">
    <p class="text-center mt-2 font-bold">{{ wechat.moments }}</p>
    <van-image :src="YB" width="100%" height="180" class="mt-5" />
    <div class="grid grid-cols-3 gap-4 mt-5 pl-5">
      <div
        v-for="(item, index) in wechat.friends"
        :key="index"
        class="w-20 text-center"
      >
        <span class="block">{{ item.name }}</span>
        <van-image width="80" height="80" :src="item.imgUrl" />
      </div>
    </div>
    <p class="mt-5">一二布布一共有{{ friendsNum }}个熊友</p>
  </div>
</template>

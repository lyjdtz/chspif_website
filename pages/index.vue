<template>
  <NuxtLayout>
    <UiContainer class="relative flex flex-col items-center justify-center gap-y-12 py-10 lg:h-[720px] lg:flex-row ">
      <div class="flex h-full items-center justify-center">
        <div>
          <h3 class="text-3xl font-semibold lg:text-5xl ">
            Chspif
          </h3>
          <h2 class="mt-8 flex flex-col text-2xl text-muted-foreground">追求 纯净 快乐 与 爱</h2>
          <div class="grid mt-8 md:flex w-full shrink-0 flex-col-reverse gap-3 md:mt-12 lg:w-auto lg:flex-row">
            <UiButton size="lg" class="w-full shrink-0 whitespace-nowrap md:w-auto" to="join" v-wave>加入</UiButton>
            <a href="https://lyjdtz.life/chspif" target="_blank">
              <UiButton size="lg" class="w-full lg:w-auto" variant="outline">公告与更新
                <Icon name="lucide:external-link" class="h-4 w-4" />
              </UiButton>
            </a>
          </div>
        </div>
      </div>
      <!-- eslint-disable-next-line vue/html-self-closing -->

    </UiContainer>
    <UiContainer>
      <template v-for="(f, i) in features" :key="i">
        <section class="mt-12 grid grid-cols-1 items-center gap-10 lg:mt-20 lg:h-[450px] lg:grid-cols-2 lg:gap-20">
          <div :class="[i % 2 == 0 ? 'lg:order-none' : 'lg:order-1']">
            <h3 class="mb-2 text-2xl font-semibold lg:mb-4 lg:text-3xl" v-html="f.title" />
            <p class="text-muted-foreground lg:text-lg" v-html="f.description" />
          </div>
          <!-- eslint-disable-next-line vue/html-self-closing -->
          <img :src="f.imageUrl" :alt="f.title"
            class="h-[250px] w-full rounded-lg object-cover shadow-sm lg:h-[330px]" />
        </section>
      </template>
    </UiContainer>
    <UiContainer class="py-16 lg:py-24">
      <h2 class="mb-4 mt-3 text-center text-3xl font-semibold lg:mb-5 lg:text-4xl">
        我们的特点
      </h2>
      <!-- <p class="mx-auto max-w-[760px] text-center text-lg text-muted-foreground lg:text-xl">
      Powerful, self-serve product and growth analytics to help you convert, engage, and retain more
      users. Trusted by over 4,000 startups.
    </p> -->

      <div class="grid grid-cols-1 gap-y-10 py-10 md:grid-cols-2 lg:grid-cols-3 lg:gap-8 lg:gap-y-16 lg:py-16">
        <template v-for="(f1, i1) in features1" :key="i1">
          <div class="group flex flex-col items-center justify-center">
            <div class="flex h-12 w-12 items-center justify-center rounded-md border">
              <Icon :name="f1.icon" class="h-5 w-5 transition-colors group-hover:text-primary lg:h-6 lg:w-6" />
            </div>
            <h3 class="mt-4 text-balance text-center text-lg font-semibold lg:mt-5 lg:text-xl" v-html="f1.title" />
            <p class="mt-1 max-w-[400px] text-balance text-center text-muted-foreground lg:mt-2"
              v-html="f1.description" />
          </div>
        </template>
      </div>
    </UiContainer>

    <UiContainer class="">
      <UiContainer class="py-16 text-center lg:py-24">
        <slot name="title">
          <h2 class="mb-4 mt-2 text-4xl font-bold lg:mb-6 lg:mt-3 lg:text-5xl">{{ title }}</h2>
        </slot>
        <slot name="description">
          <p class="mx-auto max-w-[768px] text-lg text-muted-foreground lg:text-xl">
            {{ description }}
          </p>
        </slot>
      </UiContainer>


      <section class="grid grid-cols-1 gap-10 md:grid-cols-2 lg:grid-cols-3 lg:gap-y-12">
        <template v-for="m in members">
          <div class="flex flex-col items-center w-max-1250">
            <UiAvatar class="mb-5 h-24 w-24 ring-1 ring-ring/20" :src="m.avatar" />
            <p class="text-lg font-semibold" v-html="m.name" />
            <p class="" v-html="m.position" />
            <ul class="mt-2 text-muted-foreground">
              <li v-for="intro in m.introduce" v-html="intro" />
            </ul>
            <div class="mt-2 flex items-center gap-3">
              <NuxtLink v-for="links in m.contact" :to="links.link" target="_blank">
                <Icon :name="links.icon" class="h-5 w-5 text-muted-foreground" />
              </NuxtLink>
            </div>
          </div>
        </template>
      </section>
    </UiContainer>
  </NuxtLayout>
</template>

<script lang="ts" setup>
import axios from 'axios';
// 在线玩家显示的数据获取部分


onMounted(async () => {
  const response = await axios.get('https://api.mcsrvstat.us/3/mc.craft233.top');
  const playersNum = response.data.players.online;
  const players: number = playersNum as number;
  if (players > 2) {
    var playerInfo = players + "名";
  } else {
    var playerInfo = "";
  }
  document.getElementById('playerdata')!.textContent = playerInfo
})

const features = [
  {
    title: "纯净生存",
    icon: "heroicons:chat-bubble-left-right",
    description:
      `由Fabric系服务端驱动的原版生存服务器. `,
    imageUrl:
      "/assets/img/index/hub.png",
  },
];

// 特点部分

const features1 = [
  {
    icon: "lucide:cat",
    title: "生电玩家友好",
    description: `不修改原版特性，配置Carpet等调试类mod`,
  },
  {
    icon: "lucide:circle-arrow-up",
    title: "定时备份",
    description: `采用高效算法压缩备份空间，使备份可以快速频繁进行`,
  },
  {
    icon: "lucide:leaf",
    title: "线程优化",
    description: "服务器借助Lithium、Spark等不断优化, 减少卡顿"
  },
  {
    icon: "lucide:cloud-sun",
    title: "运维稳定",
    description: "管理人员响应迅速专业，服务器运行稳定"
  },
  {
    icon: "lucide:shield-check",
    title: "数据安全",
    description:
      "正版玩家使用官方UUID加密，离线玩家使用密码加密",
  },
  {
    icon: "lucide:terminal",
    title: "开源",
    description: "大部分修改内容会开源在GitHub平台"
  },
];

// 团队部分
// 上部分标题
const title = "我们的团队";

// 人物信息部分
const members = [
  {
    avatar: "https://img.cdn1.vip/i/68fc8c845a1e9_1761381508.webp",
    name: "兔子",
    position: "服主",
    introduce:
    {
      line1: "爱你们",
    },
    contact: [
      {
        icon: "lucide:github",
        link: "https://lyjdtz.life",
      },
    ],

  },

];

// 页面标题
useHead({
  titleTemplate: (titleChunk) => {
    return titleChunk ? '' : 'Chspif';
  }
})

</script>

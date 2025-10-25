<template>
    <NuxtLayout>
        <UiContainer class="py-16 text-center lg:py-24">
            <slot name="title">
                <h2 class="mb-4 mt-2 text-4xl font-bold lg:mb-6 lg:mt-3 lg:text-5xl">服务器规则</h2>
            </slot>
            <slot name="description">
                <div class="flex w-full justify-center px-10">
                    <div class="space-y-2 ">
                        <span class="text-lg text-muted-foreground lg:text-xl">了解服务器内规则以更好地在服务器中游玩</span>
                    </div>
                </div>
            </slot>
        </UiContainer>
        <p v-html="serverRules" class="text-lg text-muted-foreground lg:text-xl
        px-10"> </p>
    </NuxtLayout>
</template>

<script setup lang="ts">
const serverRules = `
1. 尊重社区成员<br>我们致力于建立一个友善且尊重所有人的游戏环境。以下行为严厉禁止：
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·禁止歧视言论：避免基于种族、性别、年龄的歧视性话语。
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·严禁骚扰与欺凌：不得实施任何形式的骚扰、欺凌及人身攻击。
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·保护隐私：不可泄露他人个人信息。
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·禁止刷屏：不允许重复发送相同或相似消息。
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·禁止不良内容：不准发布不当性内容或裸露图片。
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·禁止恶意信息：不传播恶意软件、病毒，不从事欺诈活动。
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·反对虚假信息：不得散布虚假信息或诽谤他人。
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·杜绝负面内容：不鼓励发布任何可能诱导自伤或伤害他人的信息。<br>
2.维持服务器稳定<br>
请勿执行消耗服务器资源的极端行为：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·实体数量控制：避免积累过多实体，不建设导致服务器过载的设施。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·合理安排逻辑：优化您的设计网络，减少同时运行的逻辑节点数量。<br>
3.保护他人建筑<br>
尊重并守护他人的创造成果：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·禁止破坏建筑：不得损毁或擅自改动他人建筑物。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·避免损害：不得以任何形式对他人建筑造成伤害。<br>
4.公正游戏体验<br>
倡导公平竞争：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·反对作弊：禁止修改游戏数据或利用漏洞。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·拒绝非法软件：不允许使用未经授权的第三方软件影响游戏。<br>
5.尊重财产权<br>
勿盗取他人财物：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·禁止偷窃：未经允许，不得取用他人物品。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·禁止侵占：不可盗取他人的宠物或物品。<br>
6.杜绝恶意伤害<br>
不得无理由伤害玩家及其宠物：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·反对恶意攻击：不可设置陷阱或使用爆炸物伤害他人。<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·PVP须同意：经双方同意的PVP除外。<br>
7.促进健康创作<br>
鼓励创意与自由表达，但需得体：<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·不适当创作禁令：不可创作含有不适宜内容的像素艺术、书籍、用户名或装备名。<br><br><br>

任何违规行为将依法处理。<br>

我们珍视您的理解与合作，共同营造Chspif的良好秩序与和谐氛围。祝您游戏愉快！<br>
`;
</script>
<template>
    <NuxtLayout>
        <UiContainer>
            <div class="text-center py-12">
                <h1 class="text-4xl font-bold mb-4">进入 Chspif</h1>
                <p class="text-xl text-muted-foreground">在获取服务器地址之前，我们希望你能认真阅读以下玩家守则</p>
                <p class="text-xl text-muted-foreground">若出现违反玩家守则，可能会遭到警告或封禁</p>
            </div>
            <template v-for="(s, i) in steps" :key="i">
                <section
                    class="mt-12 grid grid-cols-1 items-center gap-10 lg:mt-24 lg:grid-cols-1">
                    <div class="w-full">
                        <div class="mb-2 flex h-10 w-10 items-center justify-center rounded-full bg-primary/10">
                            <span class="text-lg font-bold text-primary">{{ [2, 3, 1, 1, 6][i] }}</span>
                        </div>
                        <h3 class="mb-2 text-2xl font-semibold lg:mb-4 lg:text-3xl" v-html="s.title" />
                        <p class="text-muted-foreground lg:text-lg mb-4" v-html="s.description" />
                        <div v-if="s.details && s.details.length > 0">
                            <ul class="list-disc pl-5 space-y-2">
                                <li v-for="(detail, index) in s.details" :key="index" v-html="detail" />
                            </ul>
                        </div>
                        
                        <!-- 密码验证部分 - 仅在第五步显示 -->
                        <div v-if="i === 4" class="mt-6">
                            <div v-if="!passwordVerified" class="space-y-4">
                                <p class="text-yellow-600 font-medium">请输入密码以查看服务器地址</p>
                                <p class="text-sm text-muted-foreground">提示：你有没有注意到每一条内容的标号都不太对，把他们连起来试试</p>
                                <div class="flex items-center space-x-4">
                                    <input 
                                        v-model="passwordInput" 
                                        type="text" 
                                        placeholder="请输入密码" 
                                        class="px-4 py-2 border rounded-md focus:outline-none focus:ring-2 focus:ring-primary"
                                    />
                                    <button 
                                        @click="verifyPassword" 
                                        class="px-6 py-2 bg-primary text-white rounded-md hover:bg-primary/90 transition"
                                    >验证密码</button>
                                </div>
                                <div v-if="passwordError" class="text-red-500 mt-2">
                                    密码错误，请重新输入！</div>
                            </div>
                            <div v-else class="mt-6 p-4 bg-green-50 border border-green-200 rounded-lg">
                                <h4 class="font-semibold text-green-700 mb-2">服务器地址已解锁</h4>
                                <p class="mb-3">服务器IP：<span class="font-mono font-bold">mc.chspif.xyz</span></p>
                                <button 
                                    @click="copyServerAddress" 
                                    class="px-4 py-2 bg-primary text-white rounded-md hover:bg-primary/90 transition flex items-center"
                                >
                                    <span class="mr-2">复制地址</span>
                                    <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 16H6a2 2 0 01-2-2V6a2 2 0 012-2h8a2 2 0 012 2v2m-6 12h8a2 2 0 002-2v-8a2 2 0 00-2-2h-8a2 2 0 00-2 2v8a2 2 0 002 2z"></path>
                                    </svg>
                                </button>
                            </div>
                        </div>
                        
                        <!-- 服务器规则链接 - 在尊重理念部分显示 -->
                        <div v-if="i === 1" class="mt-6">
                            <a href="/rules" target="_blank" class="inline-flex items-center text-green-600 hover:underline">
                                <span class="mr-1">查看详细服务器规则</span>
                                <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14"></path>
                                </svg>
                            </a>
                        </div>
                    </div>
                </section>
            </template>
        </UiContainer>
    </NuxtLayout>
</template>

<script lang="ts" setup>
import '~/assets/css/global.css'
import { ref } from 'vue'

// 步骤数据
const steps = [
    {
        title: "准备工作",
        description: "",
        details: [
            "你可以点击 <a href='http://202.189.9.217:38100/' target='_blank'>这里</a> 查看服务器的网页地图",
            "你可以点击 <a href='http://lyjdtz.life/chspif/' target='_blank'>这里</a> 查看服务器以往更新的内容",
            "服务器为fabric服务端，版本为1.21.10，包含正版验证和白名单，无需专门客户端进入",
            "当然，我们也提供了推荐的mod包和增强材质包。",
            "点击 <a href='https://lyjdtz-1300831543.cos.ap-nanjing.myqcloud.com/chspif_mods.zip' target='_blank'>这里</a> 下载辅助mod，这些mod包含了客户端性能优化、生电辅助mod等,但它并不会让你的游戏界面过于臃肿",
            "点击 <a href='https://lyjdtz-1300831543.cos.ap-nanjing.myqcloud.com/chspif_resourcepacks.zip' target='_blank'>这里</a> 下载增强材质包，它修改了游戏内部分材质使得界面更加舒适，但该增强材质包并不包含主材质包，如需修改整体材质，你需要手动添加主材质包",
        ]
    },    {
        title: "尊重理念",
        description: "chspif是一个充满爱的家庭，在进入前，我们希望你树立起尊重理念",
        details: [
            "在方方面面尊重其他玩家和管理人员，主动构建和谐的交流氛围",
            "游戏内尊重游戏内容和其他玩家的劳动成果，遇到问题请主动与他人交流，不要随便修改其他玩家的建筑/机器",
            
        ]
    },
    {
        title: "生电/建筑玩家",
        details: [
            "如果你对生电/建筑有一定兴趣或是研究，欢迎联系群主加入服务器的工程群，那里负责服务器内大型项目的设计和落地",      
        ]
    },
        {
        title: "绑定白名单",
        details: [
            "群内有机器人会帮助你绑定白名单", 
            "你只需要在群内发送指令“    #绑定 游戏名字   ” 即可自动绑定白名单",
        ]
    },
    {
        title: "进入服务器",
        description: "从任意启动器启动游戏，加入服务器",
        details: [
            // 服务器地址将在密码验证后显示
        ]
    },
]

// 密码验证相关状态
const passwordInput = ref('')
const passwordVerified = ref(false)
const passwordError = ref(false)

// 正确的密码 - 从规则中提取的关键词
const CORRECT_PASSWORD = '23116'

// 验证密码函数
function verifyPassword() {
    if (passwordInput.value === CORRECT_PASSWORD) {
        passwordVerified.value = true
        passwordError.value = false
    } else {
        passwordError.value = true
    }
}

// 复制服务器地址函数
function copyServerAddress() {
    const address = "mc.chspif.xyz"
    navigator.clipboard.writeText(address).then(() => {
        const button = event?.target as HTMLElement
        if (button) {
            const originalText = button.innerText
            button.innerText = "已复制！"
            setTimeout(() => {
                button.innerText = originalText
            }, 2000)
        }
    })
}

function getImageNodeByWidth(node: String){
    if (window.innerWidth <= 1024) {
        return "s.peImage"
    } else{
        return "s.jeImage"
    }
}

// 页面标题
useHead({
    titleTemplate: (titleChunk) => {
        return titleChunk ? `` : 'Chspif - 加入服务器';
    }
})
</script>
<template>
    <NuxtLayout>
        <UiContainer>
            <div class="text-center py-12">
                <h1 class="text-4xl font-bold mb-4">进入 Chspif</h1>

            </div>

            <template v-for="(s, i) in steps" :key="i">
                <section
                    class="mt-12 grid grid-cols-1 items-center gap-10 lg:mt-24 lg:grid-cols-1">
                    <div class="w-full">
                        <div class="mb-2 flex h-10 w-10 items-center justify-center rounded-full bg-primary/10">
                            <span class="text-lg font-bold text-primary">{{ i + 1 }}</span>
                        </div>
                        <h3 class="mb-2 text-2xl font-semibold lg:mb-4 lg:text-3xl" v-html="s.title" />
                        <p class="text-muted-foreground lg:text-lg mb-4" v-html="s.description" />
                        <div v-if="s.details && s.details.length > 0">
                            <ul class="list-disc pl-5 space-y-2">
                                <li v-for="(detail, index) in s.details" :key="index" v-html="detail" />
                            </ul>
                        </div>
                    </div>
                </section>
            </template>
        </UiContainer>
    </NuxtLayout>
</template>

<script lang="ts" setup>
import '~/assets/css/global.css'
import axios from 'axios';

// 获取玩家数
async function getServerStatus() {
    // 初始记录值，用于判断是否所有服务器都在线
    let onlineServers = 0
    // 获取用于显示检测状态的元素
    const statusGetterText = document.getElementById("status_text")
    // 使用循环进行获取
    for (let i = 0; i < serverAddressList.length; i++) {
        // api地址
        const apiAddress = "https://api.mcsrvstat.us/3/"
        // 组合为正确的api服务器请求地址
        const serverInfo = await axios.get(apiAddress + await serverAddressList[i].address)
        // 定义初始空时的值
        let serverStatus = "Null"
        let playerNum = "0"
        let serverVer = "Null"
        // 不在线就没必要再转了
        if (serverInfo.data.online == true) {
           try {
             // 获取在线人数
             playerNum = serverInfo.data.players.online
            // 处理服务端类型(Leaves, Fabric, Forge等等)
            if (serverAddressList[i].serverType == "Fabric"){
                serverVer = "Fabric " + serverInfo.data.version
            }
            else{
                serverVer = serverInfo.data.version
            }
            // 在线状态
            serverStatus = "在线"
            onlineServers++ // 服务器在线，记录下来
           } catch (e) {
            serverStatus = "离线"
            playerNum = "0"
            serverVer = "无法获取"
           }
        }else {
            // 离线服务器直接跳过从检测中赋值
            serverStatus = "离线"
            playerNum = "0"
            serverVer = "无法获取"
        }
        // 获取当前检测服务器对应的显示元素
        const skeleton = document.getElementById(serverAddressList[i].id + "-Skeleton")
        const status = document.getElementById(serverAddressList[i].id + "-Text")
        // 更改显示状态
        skeleton?.parentNode?.removeChild(skeleton)
        if (i == 0) {// 这里是检测代理端的，显示出来会不太一样，所以改写文字
            if(status) {status.innerText = serverAddressList[i].name + ": " + serverStatus + " | 总在线人数" + playerNum}
        }else{// 正常的服务器的显示
            if(status) {status.innerText = serverAddressList[i].name + ": " + serverStatus + " | 在线人数" + playerNum + " | 服务器版本:" + serverVer}
        }
    }
    // 更改显示检测状态与结果的文字
    if (onlineServers == 0){// 一直没加过数，无在线
        if (statusGetterText) {statusGetterText.innerText = "坏极了，离线！"}
        statusGetterText?.classList.add("text-red-500")
        statusGetterText?.classList.remove("text-muted-foreground")
    }else if (onlineServers == serverAddressList.length){// 数值一样，都在线
        if (statusGetterText) {statusGetterText.innerText = "全部在线！"}
        statusGetterText?.classList.add("text-green-500")
        statusGetterText?.classList.remove("text-muted-foreground")
    }else{ // 数值不一样，有离线
        if (statusGetterText) {statusGetterText.innerText = "有些家伙在睡觉！"}
        statusGetterText?.classList.add("text-yellow-500")
        statusGetterText?.classList.remove("text-muted-foreground")
    }
}




const steps = [
    {
        title: "加入社区",
        description: "在进入服务器前请确保您已经加入了QQ群，以防被当作异常玩家踢出",
        details: [
            "QQ群号：906380735",
            "点击 <a href='https://www.kookapp.cn/app/invite/0idhG6' target='_blank'>这里</a> 加入我们的语音频道",
        ]
    },    {
        title: "下载辅助mod和增强材质包（可选）",
        description: "这里整理了一些适用于1.21.10 Fabric客户端的mod和增强材质包",
        details: [
            "点击 <a href='https://lyjdtz-1300831543.cos.ap-nanjing.myqcloud.com/chspif_mods.zip' target='_blank'>这里</a> 下载辅助mod，这些mod包含了客户端性能优化、生电辅助mod等,但它并不会让你的游戏界面过于臃肿",
            "点击 <a href='https://lyjdtz-1300831543.cos.ap-nanjing.myqcloud.com/chspif_resourcepacks.zip' target='_blank'>这里</a> 下载增强材质包，它修改了游戏内部分材质使得界面更加舒适，但该增强材质包并不包含主材质包，如需修改整体材质，你需要手动添加主材质包",
        ]
    },
    {
        title: "进入服务器",
        description: "从任意启动器启动游戏，加入服务器",
        details: [
            "游戏版本为 1.21.10",
            "服务器同时兼容正版和离线玩家，我们更推荐前者",
            "服务器ip：chspif.xyz:666"
        ]
    },
    {
        title: "开始您的旅程",
        details: [
            "探索属于您的玩法",
            "与其他玩家友好交流互动",
            "遵守服务器规则，共同维护良好的游戏环境"
        ]
    }
]

function copyServerAddress() {
    const address = "v4.mc.craft233.top:25565"
    navigator.clipboard.writeText(address).then(() => {
        // 这里可以添加一个提示，告诉用户复制成功
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

onMounted(async () => {
    getServerStatus()
})



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
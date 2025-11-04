<template>
    <div>
        <header class="z-20 bg-background/80 backdrop-blur fixed w-full max-w-[1280px]">
            <UiContainer class="flex h-16 items-center justify-between lg:h-20">
                <div class="flex items-center gap-10">
                    <NuxtLink to="/" class="flex items-center gap-3">
                        <!-- eslint-disable-next-line vue/html-self-closing -->
                        <img src="/assets/img/index/1111.png" fit="contain"
                            alt="Craft233 Logo" title="Craft233 Logo" class="h-6 object-contain lg:h-8" />
                        <!-- <span class="font-semibold lg:text-lg">Craft233</span> -->
                    </NuxtLink>
                    <UiNavigationMenu as="nav" class="hidden items-center justify-start gap-8 lg:flex">
                        <UiNavigationMenuList class="gap-2">
                            <UiNavigationMenuItem>
                                <UiNavigationMenuLink as-child>
                                    <UiButton to="/" variant="ghost" size="sm">首页</UiButton>
                                </UiNavigationMenuLink>
                            </UiNavigationMenuItem>
                            <UiNavigationMenuItem>
                                <UiNavigationMenuLink as-child>
                                    <a href="http://202.189.9.217:38100/" target="_blank">
                                        <UiButton variant="ghost" size="sm">网页地图
                                            <Icon name="lucide:external-link" class="h-4 w-4" />
                                        </UiButton>
                                    </a>

                                </UiNavigationMenuLink>
                            </UiNavigationMenuItem>
                            <UiNavigationMenuItem>
                                <UiNavigationMenuLink as-child>
                                    <a href="https://lyjdtz.life/chspif" target="_blank">
                                        <UiButton variant="ghost" size="sm">公告与更新
                                            <Icon name="lucide:external-link" class="h-4 w-4" />
                                        </UiButton>
                                    </a>

                                </UiNavigationMenuLink>
                            </UiNavigationMenuItem>
                        </UiNavigationMenuList>
                    </UiNavigationMenu>
                </div>
                <div class="lg:hidden">
                    <UiSheet>
                        <ColorMode size="icon-sm"/>
                        <UiSheetTrigger as-child>
                            <UiButton variant="ghost" size="icon-sm">
                                <Icon name="lucide:menu" class="h-5 w-5" />
                            </UiButton>
                            <UiSheetContent class="w-[90%] p-0">
                                <template #content>
                                    <UiSheetTitle class="sr-only" title="Mobile menu" />
                                    <UiSheetDescription class="sr-only" description="Mobile menu" />
                                    <UiSheetX class="z-20" />

                                    <UiScrollArea class="h-full p-5">
                                        <div class="flex flex-col gap-2">
                                            <UiButton variant="ghost" class="justify-start text-base" to="/">首页
                                            </UiButton>
                                            <a href="http://202.189.9.217:38100/" target="_blank">
                                                <UiButton variant="ghost" class="justify-start text-base">网页地图
                                                    <Icon name="lucide:external-link" class="h-4 w-4" />
                                                </UiButton>
                                            </a>
                                            <a href="https://lyjdtz.life/chspif" target="_blank">
                                                <UiButton variant="ghost" class="justify-start text-base">公告与更新
                                                    <Icon name="lucide:external-link" class="h-4 w-4" />
                                                </UiButton>
                                            </a>
                                        </div>
                                    </UiScrollArea>
                                </template>
                            </UiSheetContent>
                        </UiSheetTrigger>
                    </UiSheet>
                </div>
                <UiNavigationMenu as="nav" class="hidden items-center justify-start gap-8 lg:flex">
                    <ColorMode />
                </UiNavigationMenu>
            </UiContainer>
        </header>
        <div class="h-16 lg:h-20"></div>
        <slot />
        <!------------------------ 下面是脚页 ------------------------------>
        <UiContainer as="footer" class="py-16 ">
            <section class="grid grid-cols-2 gap-8 lg:grid-cols-6">
                <div class="col-span-full pb-10 lg:col-span-2">
                    <NuxtLink to="/" class="flex items-center gap-3">
                        <!-- eslint-disable-next-line vue/html-self-closing -->
                        <img src="https://res.neokoni.ink/craft233/img/craft233_logo.svg" fit="contain"
                            alt="Company Logo" title="Company Logo" class="h-7 object-contain lg:h-10" />
                        <span class="text-xl font-semibold">特别感谢</span>
                    </NuxtLink>
                    <p class="mt-5 text-muted-foreground">
                        网站源码来源于
                        <NuxtLink class="font-semibold hover:text-primary" target="_blank"
                                    to="https://github.com/Craft233MC/website?tab=readme-ov-file">Craft233
                                    <Icon name="lucide:external-link" class="h-4 w-4" />
                                </NuxtLink>
                    </p>
                </div>
                <template v-for="n in 1">
                    <div>
                        <p class="mb-4 text-sm text-muted-foreground">交流</p>
                        <ul class="flex flex-col gap-3">
                            <li>
                                <NuxtLink target="_blank" class="font-semibold hover:text-primary"
                                    to="https://qm.qq.com/q/WXh5Cj63Om">
                                    QQ群
                                    <Icon name="lucide:external-link" class="h-4 w-4" />
                                </NuxtLink>
                                <br/>
                                <NuxtLink class="font-semibold hover:text-primary" target="_blank"
                                    to="https://www.kookapp.cn/app/invite/0idhG6">kook频道
                                    <Icon name="lucide:external-link" class="h-4 w-4" />
                                </NuxtLink>
                                <br/>
                                <NuxtLink class="font-semibold hover:text-primary" target="_blank"
                                    to="https://oopz.cn/i/7XZYQD">oopz频道
                                    <Icon name="lucide:external-link" class="h-4 w-4" />
                                </NuxtLink>
                            </li>
                        </ul>
                    </div>
                </template>
                <template v-for="n in 1">
                    <div>
                        <p class="mb-4 text-sm text-muted-foreground">相关链接</p>
                        <ul class="flex flex-col gap-3">
                            <li>
                                <NuxtLink class="font-semibold hover:text-primary" target="_blank"
                                    to="https://lyjdtz.life">服主博客
                                    <Icon name="lucide:external-link" class="h-4 w-4" />
                                </NuxtLink>
                            </li>
                        </ul>
                    </div>
                </template>
            </section>

        
        </UiContainer>
    </div>
</template>
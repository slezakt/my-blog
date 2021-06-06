<template>
    <nav class="container mx-auto flex justify-between py-4">
        <div class="font-bold">
            <NuxtLink to="/" class="text-black">
                <span class="font-light">Tomův</span>WebDev
            </NuxtLink>
        </div>
        <ul class="flex">
            <li class="ml-2">
                <NuxtLink to="/" :class="{'text-purple-500':$route.path=='/'}">Domů</NuxtLink>
            </li>
            <li class="ml-2">
                <NuxtLink to="/omne" :class="{'text-purple-500':$route.path=='/omne'}">O mně</NuxtLink>
            </li>
        </ul>
    </nav>
</template>
<script>
export default {

}
</script>
<style>
</style>
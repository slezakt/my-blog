<template>
    <nav class="container mx-auto flex justify-between py-4">
        <div class="font-bold">
            <NuxtLink to="/" class="text-black">
                <span class="font-light">Tomův</span>WebDev
            </NuxtLink>
        </div>
        <ul class="flex">
            <li class="ml-2">
                <NuxtLink to="/">Domů</NuxtLink>
            </li>
            <li class="ml-2">
                <NuxtLink to="/omne">O mně</NuxtLink>
            </li>
        </ul>
    </nav>
</template>
<script>
export default {
    
}
</script>
<style>
    .nuxt-link-exact-active {
        @apply text-purple-500;
    }
</style>
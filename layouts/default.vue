<template>
    <div>
        <header class="shadow-sm bg-white">
            <nav class="container mx-auto p-4 flex justify-between">
                <NuxtLink to="/" class="font-bold"> Nuxt Demo</NuxtLink>
                <img class="logo" src="/logo/logo.png">

                <ul class="flex gap-4">
                    <li>
                        <NuxtLink to="/">Home</NuxtLink>
                    </li>
                    <li>
                        <NuxtLink to="/register">Register</NuxtLink>
                    </li>
                </ul>
            </nav>
        </header>
        <div class="container mx-auto p-4">
            <slot />
        </div>
    </div>
</template>

<script setup>

</script>

<style scoped>
.router-link-exact-active {
    color: #12b488;
}
nav {
    background: rgba(0, 255, 42, 0.432);
}
.logo{
    margin-right: 10px;
    block-size: 50px;
} 
</style>
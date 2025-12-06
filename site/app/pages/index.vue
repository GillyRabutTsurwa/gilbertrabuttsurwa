<script setup lang="ts">
const Loader = resolveComponent("Loader");
const Home = resolveComponent("Home");

const currentComponent = shallowRef(Loader);

onMounted(() => {
    const body = document.body;
    body.style.backgroundColor = "#101d2c";
    setTimeout(() => {
        currentComponent.value = Home;
    }, 3000);
    setTimeout(() => {
        body.style.backgroundColor = "#e6b376";
     }, 5000);
});
</script>

<template>
    <Transition mode="out-in">
        <component :is="currentComponent"></component>
    </Transition>
</template>


<style lang="scss" scoped>
.v-enter-active,
.v-leave-active {
    transition: opacity 0.25s ease-out;
}

.v-enter-from,
.v-leave-to {
    opacity: 0;
}
</style>

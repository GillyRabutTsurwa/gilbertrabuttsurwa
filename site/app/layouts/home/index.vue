<script setup>
import { useBreakpoints } from "@/composables/useBreakpoints";

const { pixels, toggleElementOnResize } = useBreakpoints();
const show = ref(null);


onMounted(() => {
    if (import.meta.client) {
        toggleElementOnResize(767);
        const body = document.querySelector("body");
        show.value = pixels.value < body.clientWidth ? true : false;
    }
});
</script>

<template>
    <HomeNav/>
    <div class="corps">
        <slot />
    </div>
    <Footer/>
</template>
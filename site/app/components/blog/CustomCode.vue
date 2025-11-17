<script setup>
import hljs from "highlight.js";
import "~~/node_modules/highlight.js/styles/base16/atelier-seaside.css";

const props = defineProps(["value", "index"]);

onMounted(() => {
    hljs.highlightAll();
    console.log(props);
    console.log(props.value.language);
    console.log(props.value.code);
    console.log(props.index);
})
</script>

<template>
    <pre>
        <code :class="`language-${props.value.language}`" :data-language="props.value.language">{{ props.value.code }}</code>
    </pre>
</template>
  
<style lang="scss" scoped>
code {
    // NOTE: styling that will display indicator as intended and NOT affect general styling provided by package
    position: relative;

    &::after {
        content: attr(data-language);
        position: absolute;
        top: 1rem;
        right: 1rem;
        color: #f0f0f0;
    }
}
</style>
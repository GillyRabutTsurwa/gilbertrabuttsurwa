<script lang="ts" setup>
const props = defineProps(["value"]);
console.log(props);
</script>

<template function>
    <a :href="props.value.href" target="_blank" rel="noopener noreferrer">
        <slot />
    </a>
</template>

<style lang="scss" scoped>
a,
a:link,
a:visited {
    color: $colour-primary;
    font-style: italic;
    text-decoration: none;
}
</style>

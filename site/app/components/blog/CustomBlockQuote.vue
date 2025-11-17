<script lang="ts" setup></script>

<template function>
    <blockquote class="test">
        <p>
            <slot />
        </p>
    </blockquote>
</template>

<style lang="scss" scoped>
blockquote {
   margin-bottom: 3.5rem;

   p {
        font-weight: bold;
        font-style: italic;
        font-size: 200%;
        color: $colour-primary;
        text-align: center;
        display: block;

    &::before,
    &::after {
        display: inline-block;
        top: 0;
        position: relative;
        padding: 0.1rem;
    }

    &::before {
        content: open-quote;

    }

    &::after {
        content: close-quote;
        margin-left: -0.2rem;

    }
   }
}
</style>

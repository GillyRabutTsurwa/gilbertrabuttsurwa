<script setup lang="ts">
import type { PostInt } from "~~/interfaces/post";

const { post } = defineProps({
    post: {
      type: Object as PropType<PostInt>,
      required: true
    }
});
</script>

<template>
  <header class="header">
    <div class="header__blog-intro">
      <h2>Featured Post</h2>
    </div>
    <div class="header__post">
      <div class="header__post--content">
        <h2 class="title">{{ post.title }}</h2>
        <p class="text">{{ post.excerpt }}</p>
        <Button isLink :path="`/blog/personal/${post.slug.current}`" colourPrimary="#101d2c"
          colourSecondary="#e6b376" />
      </div>
    </div>
    <figure class="header__post--img">
      <SanityImage :asset-id="post.thumbnail?.asset?._ref" auto="format" />
    </figure>
  </header>
</template>


<style lang="scss" scoped>
.header {
  position: relative;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: -webkit-min-content 1fr;
  grid-template-rows: min-content 1fr;
  padding: 0 5rem;
  color: $colour-primary;

  @include breakpoint(1023) {
    height: auto; // au cas ou
    row-gap: 2rem;
    grid-template-columns: 1fr;
  }

  &__blog-intro {
    grid-column: 1 / -1;
    margin: 3rem 0;

    @include breakpoint(1023) {
      text-align: center;
    }
  }

  &__post {
    @include breakpoint(1023) {
      display: grid;
      grid-template-columns: 1fr;
      grid-column: 1 / -1;
      grid-row: 3 / 4;
    }

    &--content {
      padding-right: 4rem;

      @include breakpoint(1023) {
        grid-column: 1 / -1;
        grid-row: 3 / 4;
      }

      @include breakpoint(767) {
        text-align: center;
      }

      &>*:not(:last-child) {
        margin-bottom: 3rem;
      }

      .title {
        font-size: 6rem;
        font-weight: 600;
      }

      .text {
        font-size: 2.25rem;
        line-height: 1.75;
      }

      .button {
        font-size: 1.8rem;
        text-decoration: none;
        padding: 1.5rem 2.2rem;
      }
    }

    &--img {
      width: 100%;
      height: 65rem; //TESTING

      @include breakpoint(1023) {
        grid-column: 1 / -1;
        grid-row: 2 / 3;
        margin: 0 auto; // au cas ou
      }

      @include breakpoint(1023) {
        height: 35rem;
      }

      img {
        border-radius: 1.5rem;
        width: inherit;
        height: inherit;
        -o-object-fit: cover;
        object-fit: cover;
      }
    }
  }

  &__title {
    position: absolute;
    top: 45%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    // animation config
    opacity: 0;
    -webkit-animation-name: appear;
    animation-name: appear;
    -webkit-animation-duration: 2s;
    animation-duration: 2s;
    -webkit-animation-delay: 3s;
    animation-delay: 3s;
    -webkit-animation-timing-function: ease-in;
    animation-timing-function: ease-in;
    //IMPORTANT:
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
    z-index: 1000;

    &--primary,
    &--secondary {
      color: $colour-primary;
    }

    &--secondary {
      font-family: $Lexend;
      font-size: 4.5rem;
      margin-bottom: 5rem;
    }

    &--primary {
      font-family: "Abel", cursive;
      font-size: 3.5rem;
    }
  }
}

@include fadeAnimation("appear", 0, 1);

// NOTEIMPORTANT: this is for the instance of the spinner component in this component.
// i am overwriting the normal height
.loader {
  height: 50dvh;
}
</style>
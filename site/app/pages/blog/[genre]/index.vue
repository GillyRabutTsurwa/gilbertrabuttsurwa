<script setup lang="ts">
import { posts } from "~~/queries";
import type { PostInt } from "~~/interfaces/post";
import type { StateTree, Store } from "pinia";
import { usePostsStore } from '@/stores/posts';
import { useRoute } from "vue-router";

interface Page {
    currentPage: number;
    postsPerPage: number;
}

// VARIABLES
const route = useRoute();
const genre = route.params.genre;
const query: string = posts(genre);
const state: Page = reactive({
    currentPage: 1,
    postsPerPage: 5
});

// COMPOSABLES
const store: Store<"posts", StateTree> = usePostsStore();
const { data: blogs } = await useSanityQuery<PostInt>(query);

const renderPagination = (eventPayload: number) => {
    state.currentPage = eventPayload;
}

// COMPUTED VALUES
const indexOfLastPost: ComputedRef<number> = computed(() => {
    return state.currentPage * state.postsPerPage;
});

const indexOfFirstPost: ComputedRef<number> = computed(() => {
    return indexOfLastPost.value - state.postsPerPage;
});

const currentPosts = computed(() => {
    return store.filteredPosts.slice(indexOfFirstPost.value, indexOfLastPost.value);
});

const featuredPost = computed(() => {
    return store.posts[Math.floor(Math.random() * (store.posts.length))];
});

store.posts = blogs.value;
store.filteredPosts = blogs.value;
</script>

<template>
    <BlogHeader :post="featuredPost"/>
    <FlexContainer layout="row-reverse">
        <Aside>
            <template #categories>
                <Categories :posts="store.posts" />
            </template>
            <template #newsletter>
                <Newsletter/>
            </template>
        </Aside>
        <Posts :posts="currentPosts" />
    </FlexContainer>
    <Pagination :postsPerPage="state.postsPerPage" :postsLength="store.filteredPosts.length"
        @paginate="renderPagination($event)" />
</template>


<style lang="scss" scoped>
.grid-test {
    display: grid;
    grid-template-columns: 1fr 50rem;
    grid-template-rows: subgrid;
    overflow: hidden;

    @include breakpoint(767) {
        display: flex;
        flex-direction: column;
        margin-bottom: 4rem;
    }
}

.body-tings {
    display: flex;
    // margin: 2.5rem;

    @include breakpoint(1023) {
        flex-direction: column;
    }
}

.posto {
    grid-area: posts;

    @include breakpoint(767) {
        grid-area: unset;
        order: 2;
    }
}

.pago {
    grid-area: pagination;

    @include breakpoint(767) {
        grid-area: unset;
        order: 3;
    }
}

.catego {
    grid-area: categories;
    align-self: center;

    @include breakpoint(767) {
        width: 100%;
        grid-area: unset;
        order: 1;
    }
}

.insto {
    grid-area: insta;
    place-self: center;

    @include breakpoint(767) {
        grid-area: unset;
        align-self: center;
        order: 4;
        margin: 0 auto;
    }
}

.newso {
    grid-area: newsletter;

    @include breakpoint(767) {
        grid-area: unset;
        order: 5;
        margin: 0 auto;
    }
}
</style>
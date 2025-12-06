<template>
    <Navigation>
        <template #logo>
            <LogoX />
        </template>
        <template #links>
            <li class="navigation__list--item">
                <NuxtLink to="/">Home</NuxtLink>
            </li>
            <li class="navigation__list--item">
                <NuxtLink to="/blog">Blogs</NuxtLink>
            </li>
            <li class="navigation__list--item">
                <NuxtLink to="/blog/authours/gilbert-rabut-tsurwa">About Me</NuxtLink>
            </li>
            <DevOnly>
                <li class="navigation__list--item">
                <NuxtLink to="/blog/uncensored">Uncensored Posts</NuxtLink>
                </li>
            </DevOnly>
            <li class="navigation__list--item">
                <NuxtLink to="/shop" target="_blank" rel="noreferrer noopener">Shop</NuxtLink>
            </li>
        </template>
    </Navigation>
    <div class="blogsettings">
        <slot />
    </div>
    <Footer />
</template>

<style lang="scss">
.blogsettings {

    &,
    & * {
        font-family: "League Spartan", sans-serif !important;
    }
}
</style>
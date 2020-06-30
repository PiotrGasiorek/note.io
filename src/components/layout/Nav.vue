<template>
    <nav>
        <router-link to="/">
            <img src="@/assets/logo.svg" alt="">
        </router-link>
        <div>
            <router-link to="/features" class='link'>Features</router-link>
            <br>
            <router-link to="/board" class='link'>Board</router-link>
            <br>
            <router-link to="/contact" class='link'>Contact</router-link>
        </div>
    </nav>
</template>

<script>
    export default {
        name: 'Nav',
    }
</script>

<style scoped lang='sass'>
    nav
        width: 100%
        display: flex
        height: 50px
        align-items: center

        div
            display: flex
            margin-left: auto

            *
                padding: 0 0 0 60px
</style>
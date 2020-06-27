<template>
    <nav>
        <router-link to="/">
            <img src="@/assets/logo.svg" alt="">
        </router-link>
        <div>
            <router-link to="/features">Features</router-link>
            <br>
            <router-link to="/board">Board</router-link>
            <br>
            <router-link to="/contact">Contact</router-link>
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
            padding: 0 0 0 20px
</style>
<template>
    <div class="container">
        <h1 v-if="error.statusCode === 404">А ну ушел отсюда</h1>
        <h1 v-else>Произошла ошибка</h1>
        <nuxt-link to="/">Вернуться на главную</nuxt-link>
    </div>
</template>

<script>
    export default {
        props: ['error'],
        head: {
            title: '404 ошибка'
        }
    }
</script>

<style>
    .container {
        display: flex;
        flex-direction: column;
    }
    h1 {
        color: red;
        margin: auto;
    }

</style>
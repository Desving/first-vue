<template>
    <div>
        <ul class="rate">
            <li class="star"></li>
            <li class="star"></li>
            <li class="star"></li>
            <li class="star"></li>
        </ul>
        <p>{{ rating }}</p>
    </div>
</template>

<script>
    export default {
        props: {
            rating: Number,
        },
    }
</script>

<style>
    .rate {
        margin: 0;
        padding: 0;
        font-size: 0;
    }
    .rate:hover .star {
        color: #58a080;
    }
    .rate .star {
        margin: 0;
        padding: 0;
        display: inline-block;
        font-size: 20px;
        cursor: pointer;
        color: #fff;
        text-shadow:
                0 1px #58a080,
                0 -1px #58a080,
                1px 0 #58a080,
                -1px 0 #58a080;
    }
    .rate .star:before {
        content: '\2605';
    }
    .rate .star:hover ~ .star {
        color: #fff;
    }
</style>


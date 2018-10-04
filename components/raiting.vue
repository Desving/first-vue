<template>
    <div class='rating'>
        <p class='rating-count'>{{ countRating }}</p>
        <ul class="rate">
            <li class="star"></li>
        </ul>
    </div>
</template>

<script>
    export default {
        props: {
            rating: Number,
            countRating: Number,
        },
    }
</script>

<style>
    .rating {
        display: flex;
        align-items: center;
    }
    .rate {
        margin: 0;
        padding: 0;
        font-size: 0;
        align-items: left;
        padding-left: 5px;

    }
    .rate:hover .star {
        color: #58a080;
    }
    .rate .star {
        margin: 0;
        padding: 0;
        display: inline-block;
        font-size: 22px;
        cursor: pointer;
        color:  #58a080;
    }
    .rate .star:before {
        content: '\2605';
    }
    .rating-count {
        vertical-align: bottom;
        font-family: "HelveticaCE";
        color: rgb(56, 68, 82);
    }
</style>


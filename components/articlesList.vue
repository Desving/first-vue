<template>
    <div class="articles-list">
        <button v-on:click="shuffle">перемешать</button>
        <transition-group name="list-complete" tag="div">
            <div v-for="article in this.arArticles" :key="article.id" class="item">
                <div class="item__img">
                    <img v-bind:src="article.scrPrewPicture" alt="">
                </div>
                <div class="item__description">
                    <h2 class="item__description_name">{{ article.articleName }}</h2>
                    <p  class="item__description_txt">{{ article.articlePewText}}</p>
                </div>
                <div class="item__btn">
                    <button>Lets me</button>
                </div>
            </div>
        </transition-group>
    </div>
</template>

<script>
    import img from '~/assets/142.jpg/';
    var _ = require('lodash');
    export default {
        data: function () {
            return {
                //массив статей
                arArticles: [
                    {
                        id: 0,
                        articleName: 'First Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 1,
                        articleName: 'Second Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 2,
                        articleName: 'third Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 3,
                        articleName: 'fours Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 4,
                        articleName: 'fives Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 5,
                        articleName: 'sixs Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 6,
                        articleName: 'sevens Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 7,
                        articleName: 'eithins Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 8,
                        articleName: 'nines Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 9,
                        articleName: 'tens Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 10,
                        articleName: '11s Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                ],
            }
        },
        methods: {
            //функция перемешивания
            shuffle: function(){
                this.arArticles = _.shuffle(this.arArticles);
            }
        }
    }
</script>

<style lang="less">
    .list-complete-enter, .list-complete-leave-to
        /* .list-complete-leave-active до версии 2.1.8 */ {
        opacity: 0;
        transform: translateY(30px);
    }
    /*список статей*/
    .articles-list {
        display: flex;
        flex-direction: column;
        padding: 20px 20px;
        width: 80%;
        margin: auto;
        /*элемент списка*/
        & .item {
            display: flex;
            flex-direction: row;
            padding: 10px 10px 10px 0;
            /*background: red;*/
            margin-bottom: 10px;
            /*Анимация списка*/
            transition: all 1s;
            /*контейнер для картинки статьи*/
            &__img {
                width: 150px;
                margin-right: 50px;
               & img {
                   width: 100%;
                   height: auto;
               }
           }
            /*весь провью текст статьи*/
            &__description {
                /*background: blue;*/
                display: flex;
                flex-direction: column;
                justify-content: flex-start;
                &_name {
                    /*background: green;*/
                    padding-bottom: 10px;
                    text-align: start;
                    font-size: 16px;
                    font-family: "HelveticaCE";
                    color: rgb(56, 68, 82);
                }
                &_txt {
                    /*background: green;*/
                    text-align: start;
                    font-size: 16px;
                    font-family: "HelveticaCE";
                    color: rgb(56, 68, 82);
                    line-height: 1.875;

                }
            }
            /*кнопка для перехода на детальную*/
            &__btn {
              width: 120px;
                & button{
                    color: #f2f2f2;
                    width: 100%;
                    background-color: #384452;
                    transition: 0.5s;
                    border: 1px solid #384452;
                    border-radius: 5px;
                    height: 40px;
                    text-align: center;
                    &:hover {
                        background-color: #58a080;
                        border: 1px solid #58a080;
                    }
                }
            }
            &:hover{
                transform: scale(1.1);
                transition: 1s;
            }
        }
    }
</style>


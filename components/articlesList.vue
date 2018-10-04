<template>
    <div class="articles-list" id="#start">
        <div class="sort-btn">
            <button v-on:click="shuffle" class="btn">перемешать</button>
            <button v-on:click="sortName" class="btn">Сортировать по названию</button>
            <button v-on:click="sortRating" class="btn">Сортировать по рейтингу</button>
        </div>
        <transition-group name="list-complete" tag="div">
            <div v-for="article in paginatedData" :key="article.id" class="item">
                <div class="item__img">
                    <img v-bind:src="article.scrPrewPicture" alt="">
                </div>
                <div class="item__description">
                    <h2 class="item__description_name">{{ article.articleName }}</h2>
                    <raiting-article v-bind:rating="4" v-bind:countRating="4"></raiting-article>
                    <p  class="item__description_txt">{{ article.articlePewText}}</p>
                </div>
                <div class="item__btn">
                    <button>Lets me</button>
                </div>
            </div>
        </transition-group>
        <div class="pag-btn">
            <button v-bind:disabled="disabledPrev" v-bind:class="{ btn_red: disabledPrev }" @click="prevPage" class="btn prev">
                Туды
            </button>
            <button v-bind:disabled="disabledNext" v-bind:class="{ btn_red: disabledNext }" @click="nextPage" class="btn next">
                Сюды
            </button>
        </div>
    </div>
</template>

<script>
    import img from '~/assets/142.jpg/';
    import raitingArticle from '~/components/raiting.vue';
    var _ = require('lodash');
    export default {
        data: function () {
            return {
                //начальная страница
                pageNumber: 0,
                maxPostInPage: 10,
                orderSortName: '',
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
                    {
                        id: 11,
                        articleName: 'sixs Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 12,
                        articleName: 'sevens Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 13,
                        articleName: 'eithins Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 14,
                        articleName: 'nines Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 15,
                        articleName: 'tens Projext',
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                    {
                        id: 16,
                        articleName: '11s Projext',
                        articleRaiting: 1,
                        articlePewText: 'Lorem ipsum dolor sit amet, ' +
                        'consectetur adipisicing elit. Ea nobis non perferendis ' +
                        'possimus quia. Consectetur et iste labore libero quae.',
                        articleDetailButton: 'ss',
                        scrPrewPicture: img
                    },
                ],
            }
        },
        components: {
            raitingArticle
        },
        methods: {
            //функция перемешивания
            shuffle: function(){
                this.arArticles = _.shuffle(this.arArticles);
            },
            sortName: function(){
                this.arArticles.sort(function (a, b) {
                    if (a.articleName > b.articleName) {
                        return 1;
                    }
                    if (a.articleName < b.articleName) {
                        return -1;
                    }
                    // a должно быть равным b
                    return 0;
                });
            },
            sortRating: function(){
                this.arArticles.sort(function (a, b) {
                    if (a.articleRaiting > b.articleRaiting) {
                        return 1;
                    }
                    if (a.articleRaiting < b.articleRaiting) {
                        return -1;
                    }
                    // a должно быть равным b
                    return 0;
                });
            },
            nextPage(){
                this.scrollToElement('#start');
                this.pageNumber++;
            },
            prevPage(){
                this.scrollToElement('#start');
                this.pageNumber--;
            },
            scrollToElement(elementId) {
                var selectedPosX = 0;
                var selectedPosY = 0;
                var theElement =  document.getElementById(elementId);
                while (theElement != null) {
                    selectedPosX += theElement.offsetLeft;
                    selectedPosY += theElement.offsetTop;
                    theElement = theElement.offsetParent;
                    window.scrollTo(selectedPosX,selectedPosY)
                }

            }
        },
        computed: {
            //Количество страниц
            totalPages(){
                let l = this.arArticles.length,
                    s = this.maxPostInPage;
                return Math.floor(l/s);
            },
            //Массив для пагинации
            paginatedData(){
                const start = this.pageNumber * this.maxPostInPage,
                    end = start + this.maxPostInPage;
                return this.arArticles.slice(start, end);
            },
            //флаг оключении кнопки
            disabledPrev() {
                return this.pageNumber < 1
            },
            //флаг оключении кнопки
            disabledNext() {
                return (this.pageNumber > (this.totalPages-1))
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
        & .pag-btn {
            display: flex ;
            justify-content: space-between;
        }
        & .btn {
            background-color: white;
            width: 100px;
            height: 50px;
            border: 1px solid grey;
            border-radius: 10px;
            color: rgb(56, 68, 82);
            outline: none;
            &:hover {
                transform: translateY(-5px);
                transition: 0.5s;
                border: 1px solid #58a080;
                color: #58a080;
            }
            &.btn_red{
                border: 1px solid #A02F34;
                color: rgb(56, 68, 82);
                &:hover {
                    background-color: #A02F34;
                    color: white;
                }
            }
        }
        & .sort-btn {
            display: flex;
            flex-direction: row;
            justify-content: space-between;
            padding: 20px 0;
        }

        @media (min-width: 0px) and (max-width: 419px) {
            .articles-list {
                width: 100%;
                & .item {
                    flex-direction: column;
                    margin: 30px 0;
                    border-bottom: 1px solid grey;
                    &__img{
                        margin: auto;
                    }
                    &__description{
                        margin: 20px 0;
                        &_name{
                            margin: auto;
                        }
                        &_txt {
                            text-align: center;
                        }
                    }
                    &__btn{
                        margin: 20px auto;
                    }
                }
            }
        }

        /*----------------------------------------------*/
        @media (min-width: 420px) and (max-width: 767px) {

        }

        /*----------------------------------------------*/
        @media (min-width: 768px) and (max-width: 991px) {

        }

        /*----------------------------------------------*/
        @media (min-width: 992px) and (max-width: 1199px) {

        }

        /*----------------------------------------------*/
        @media (min-width: 1199px) and (max-width: 1400px) {

        }

    }
</style>


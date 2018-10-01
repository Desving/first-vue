<template>
    <div class="articles-list">
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
    </div>
</template>

<script>
    import img from '~/assets/142.jpg/'
    export default {
        data: function () {
            return {
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
                ],
            }
        }
    }
</script>

<style lang="less">
    .articles-list {
        display: flex;
        flex-direction: column;
        padding: 20px 20px;
        width: 80%;
        margin: auto;
        & .item {
            display: flex;
            flex-direction: row;
            padding: 10px 10px 10px 0;
            /*background: red;*/
            margin-bottom: 10px;
            &__img {
                width: 150px;
                margin-right: 50px;
               & img {
                   width: 100%;
                   height: auto;
               }
           }
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


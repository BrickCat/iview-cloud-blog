<template>
    <Row type="flex" justify="center" align="middle" style="margin-bottom: 1.5em;">
        <Col span="22">
            <Card :bordered="False" dis-hover :padding="0">
                <div>
                    <a>
                        <Row type="flex">
                            <Col :xs="24" :sm="24">
                                <div>
                                    <time class="post-time" title="2018-4-28 15:30:01">{{article.ago}}</time>
                                    <span class="post-dian">·</span>
                                    <div class="category-list" v-for="tag in article._f_tags" v-on:click="tagTo(tag.id)">
                                        <a class="category-list-item" href="javascript:void(0)">{{tag.name}}</a>
                                    </div>
                                </div>
                            </Col>
                            <div v-on:click="ToArticle(article.id)" style="width: 100%;">
                                <Col :xs="24" :sm="24">
                                    <h2 class="post-title">
                                        <a class="post-title-link">
                                            {{article.title}}
                                        </a>
                                    </h2>
                                </Col>
                                <Col :xs="24" :sm="24">
                                    <div class="post-content">
                                        {{article.desc}}...
                                        <span><a href="">
                                            阅读更多...
                                        </a></span>
                                    </div>
                                </Col>
                            </div>
                            <Col :xs="24" :sm="24" style="height: 1px;background-color: #CFCfCf;"></Col>
                            <Col :xs="24" :sm="24" style="margin-top: 1em;">
                                <ul class="article-tag-list">
                                    <li class="article-tag-list-item" v-for="category in article._f_categories">
                                        <a href="" class="article-tag-list-link waves-effect waves-button">{{category.name}}</a>
                                    </li>
                                </ul>
                            </Col>
                        </Row>
                    </a>
                </div>
            </Card>
        </Col>
    </Row>
</template>

<script>
    const ARTICLE_TYPE_NO_IMAGE = 0;
    const ARTICLE_TYPE_NORMAL_IMAGE = 1;
    const ARTICLE_TYPE_BIG_IMAGE = 2;

    export default {
        name: 'articleListCell',
        data () {
            return {
                color: '#FE4580',
                False:false,
            }
        },
        props: {
            article: {
                Type: Object
            }
        },
        computed: {

        },
        methods: {
            tagTo (tag){
                alert(tag);
            },
            ToArticle (id){
                this.$router.push({
                    name:'article-detail',
                    params:{
                        articleId:id
                    }
                })
            },
        },
        mounted (){
        }
    };
</script>

<style scoped>
 .post-time{
     line-height: 24px;
     font-weight: bold;
     color: #717171;
     font-size: 13px;
 }
 .post-dian {
     font-weight: bold;
     color: #717171;
 }
 .category-list{
     font-weight: bold;
     font-size: 16px;
     line-height: 24px;
     display: inline-block;
     margin-left: 4px;
     margin-right: 4px;
     font-size: 13px;
 }
 .category-list-item{
    color: #FE4580;
}
 .post-title {
     margin: 0 0 16px;
 }
 .post-title-link {
     color: #3f51b5;
     position: relative;
     display: inline-block;
 }
 .post-content{
     word-break: break-all;
     padding-bottom: 20px;
     line-height: 1.8;
     box-sizing: border-box;
     font-size: 1.2em;
     cursor: default;
     color: #212121;
 }
 .article-tag-list {
     overflow: hidden;
     margin: 0;
     padding: 0;
     font-size: 13px;
 }
 .article-tag-list-item {
     display: inline-block;
     margin: 0 8px 8px 0;
     border-radius: 2px;
 }
 .article-tag-list-item:nth-child(n+1) {
     background: #8bc34a;
 }
 .waves-button, .waves-button:hover, .waves-button:visited, .waves-button-input {
     white-space: nowrap;
     vertical-align: middle;
     cursor: pointer;
     border: none;
     outline: none;
     background-color: rgba(0, 0, 0, 0);
     font-size: 1em;
     text-align: center;
     text-decoration: none;
     z-index: 1;
 }
 .article-tag-list-link {
     display: block;
     padding: 0 14px;
     line-height: 28px;
     color: rgba(255, 255, 255, 0.8);
     -webkit-transition: 0.2s ease-in-out;
     transition: 0.2s ease-in-out;
 }
 .waves-button {
     padding: 0 1.1em;
     border-radius: 0.2em;
 }
 .waves-button, .waves-circle {
     -webkit-transform: translateZ(0);
     transform: translateZ(0);
 }
 .waves-effect {
     position: relative;
     cursor: pointer;
     display: inline-block;
     overflow: hidden;
     -webkit-user-select: none;
     -moz-user-select: none;
     -ms-user-select: none;
     user-select: none;
     -webkit-tap-highlight-color: transparent;
 }
 a {
     background-color: transparent;
     background-image: none;
     color: #3f51b5;
     text-decoration: none;
     outline: 0;
 }
</style>

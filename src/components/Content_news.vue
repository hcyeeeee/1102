<template >
    <div class="section" id="news">
        <h3>{{ title }}</h3>
        <ul class="desktop">
            <li @click="getData_ftvNews">最新新聞</li>
            <li @click="getData_ftvNews1">政治新聞</li>
            <li @click="getData_ftvNews2">修憲公投</li>
            <li><a href="#district">地方選戰</a></li>
            <!-- <li @click="getData_ftvNews4">新竹選戰</li> -->
        </ul>

        <ul class="mobile" :class="{ fixed: active }">

            <li @click="getData_ftvNews5">最新新聞</li>
            <li @click="getData_ftvNews6">政治新聞</li>
            <li @click="getData_ftvNews7">修憲公投</li>
            <li><a href="#district">地方選戰</a></li>
        </ul>

        <div class="line">
            <img src="../assets/選舉章icon.png" alt="">
            <hr>
            <img src="../assets/選舉章icon.png" alt="">


        </div>

        <div class="section-box">
            <div class="news-layout desktop">
                <div class="news" v-for="(item, index) of newsInfo" :key="index">
                    <a :href="'https://www.ftvnews.com.tw/news/detail/' + item.ID" target="blank">
                        <div>
                            <img :src="item.Image" alt="新聞封面照" />
                        </div>
                        <div>
                            <h2 class="title">{{ item.Title }}</h2>
                        </div>
                        <div>
                            <p>{{ item.CreateDate }}</p>
                        </div>
                    </a>
                </div>
            </div>
            <div class="news-layout mobile1">
                <div class="news" v-for="(item, index) of newsInfo" :key="index">
                    <a :href="'https://www.ftvnews.com.tw/news/detail/' + item.ID" target="blank">
                        <div>
                            <img :src="item.Image" alt="新聞封面照" />
                        </div>
                        <div>
                            <h2 class="title">{{ item.Title }}</h2>
                        </div>
                        <div>
                            <p>{{ item.CreateDate }}</p>
                        </div>
                    </a>
                </div>
            </div>
            <div class="btn_more">
                <a href="https://www.ftvnews.com.tw/tag/九合一選舉/" target="blank">更多新聞</a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            title: '最新新聞',
            newsInfo: [],
            active: false, // 控制nav高度到達條件就轉成true，並加入class="fixed"
        }
    },
    created() {
        window.addEventListener('scroll', this.handleScroll)
    },
    methods: {
        getData_ftvNews() {
            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=九合一選舉&Page=1&sp=6')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews1() {

            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=政治&Page=1&sp=9')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews2() {

            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=18歲公民權&Page=1&sp=9')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews3() {

            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=桃園市選戰&Page=1&sp=9')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews4() {

            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=新竹市選戰&Page=1&sp=9')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },

        getData_ftvNews5() {
            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=九合一選舉&Page=1&sp=6')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews6() {
            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=政治&Page=1&sp=6')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews7() {
            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=18歲公民權&Page=1&sp=6')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews8() {

            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=桃園市選戰&Page=1&sp=6')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_ftvNews9() {

            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://ftvnews-api2.azurewebsites.net/API/FtvGetNewsWeb.aspx?Cate=新竹市選戰&Page=1&sp=6')
                .then((response) => {
                    // console.log(response)
                    let data = response.data.ITEM
                    data.forEach((item) => {
                        this.newsInfo.push(item)
                    })
                    // console.log(this.newsInfo)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        // handleScroll() {
        //     this.active = window.scrollY < 2400 && window.scrollY > 700 ? true : false

        // },
    },

    mounted() {
        this.getData_ftvNews()
    },
}
</script>

<style scoped>
.fixed {
    z-index: 999 !important;
    position: fixed !important;
    top: 0 !important;
    overflow-y: hidden;
    width: 100%;
    cursor: pointer;
    text-decoration: none;
    background-color: #f3fef5;
    box-shadow: rgb(0 0 0 / 12%) 0px 1px 3px, rgb(0 0 0 / 24%) 0px 1px 2px;
    opacity: .9;
}

.news-layout {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 1.5rem;
    padding: 1rem;
}

@media screen and (max-width: 768px) {
    .news-layout {
        grid-template-columns: 1fr 1fr;
    }
}

@media screen and (max-width: 500px) {
    .news-layout {
        grid-template-columns: 1fr;
        overflow-x: scroll;
    }

}

.line {
    display: flex;
    padding: 0px 30px;
}

.line img {
    width: 50px;
    padding: 5px;
}



hr {
    align-items: center;
    color: rgb(67, 67, 67);
    font-weight: bolder;
    width: 95%;

    margin: auto;
}



.news {
    transition: 0.5s;
    border-radius: 0 0 10px 10px;
    background-color: #ffffff;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}

.news:hover {
    display: block;
    background-color: #cae3bb;
    text-decoration: none !important;
}

.news:hover h2,
.news:hover p {
    color: rgb(42, 42, 42);
}

.news h2 {
    padding: 0.3rem 1rem;
}

.news p {
    text-align: left;
    margin: 20px 0 0 0;
    padding: 0.3rem 1rem;
    font-size: 0.8rem;
    font-weight: lighter;
}

.news img {
    width: 100%;
}

ul {
    margin: 2rem;
}

.title {
    display: -webkit-box;
    overflow: hidden;
    text-overflow: ellipsis;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    /* 解決firefox不支援-webkit-line-clamp的問題 */
    line-height: 30px;
    max-height: 60px;
    text-align: left;
    font-size: 1.2rem;
    font-weight: normal;
    padding: 0.3rem;
}

.mobile {
    display: none;
}

.mobile1 {

    display: none;
}



ul {
    display: flex;
    margin: auto;
    justify-content: center;
    flex-wrap: no-wrap;


}

ul li {
    text-align: center;
    margin: 0.5rem;
    border: 1px solid;
    border-radius: 30px;
    padding: 0.5rem 1rem;
    opacity: .9;
    box-shadow: rgba(0, 0, 0, 0.2) 0px 1px 4px;
    cursor: pointer;
    color: #2e2e2e
}

ul li:before {
    content: '';
}


ul li:hover {
    background-color: rgb(217, 246, 201);
    background-color: rgb(217, 246, 201);
    color: #000000;
    opacity: 1;
}

ul li:active {
    background-color: rgb(217, 246, 201);
    color: #000000;
}

.news a div:nth-child(1) {
    overflow-y: hidden;
    max-height: 150px;
}

.btn_more {
    max-width: 300px;
    margin: 2rem auto;

    padding: 0.6rem;
    display: block;
    cursor: pointer;
    text-align: center !important;

}

.btn_more a {

    border: 1px solid #595757;
    border-radius: 30px;
    padding: 0.5rem 1rem;
    box-shadow: 1px 2px 3px gray;
    cursor: pointer;
    font-size: 1.2rem;
    opacity: .9;

}

.btn_more a:hover {
    background-color: rgb(217, 246, 201);
    color: #000000;
    opacity: 1;
}

.btn_more a:active {
    background: rgb(255, 255, 255, .8);
}

a {
    color: #2e2e2e;
}

@media screen and (max-width: 500px) {
    .title {
        font-size: 1.2rem;
    }

    .line {
        display: flex;
        padding: 0px;
    }

    .desktop {
        display: none;
    }

    .mobile {
        display: flex;

        margin: auto -1rem;
    }

    .mobile1 {
        display: grid;
    }

    ul li {
        text-align: center;
        margin: .5rem;
        border: 1px solid;
        border-radius: 30px;
        padding: .5rem 1rem;
        width: fit-content;
        opacity: .9;
        box-shadow: rgba(0, 0, 0, 0.2) 0px 1px 4px;
        cursor: pointer;
        color: #2e2e2e;
        font-size: 16px;
        width: 78px
    }


}

.section-box {
    max-height: fit-content;
}
</style>

<template>
    <div>
        <div class="section" id="board">
            <h3>選情儀表板</h3>
            <div class="board">
                <div class="box" :class="item.partyColor" v-for="(item, idx) in all" :key="idx" @click="goCand(item)">
                    <div class="ct">
                        <P> {{ item.cityName }}</P>
                    </div>
                    <div>
                        <p> {{ item.candName }}</p>
                        <p> {{ item.ticket }}</p>
                    </div>
                </div>
            </div>
          
        </div>
    </div>


</template>

<!-- 功能 -->
<!-- 票數最高的在上面 -->
<!-- 票數前三世大的 -->
<!-- option傳值 -->
<!-- 儀表板顏色 -->
<!-- 最高票取代在前面 -->


<script>

export default {
    data() {
        return {
            title: '縣市議員候選人',
            taipei: [],
            all: null,
            counter: null
        }
    },
    methods: {
        preOrderData(data) {
            let t1 = data.T1.detail
            let all = {}
            t1.forEach(function (city) {
                // console.log('source', citys)
                if (city !== null) {
                    city.tickets.sort(function (a, b) {
                        return b.ticket - a.ticket
                    })
                    let partyColor = null;
                    switch (city.tickets[0].party) {
                        case "國民":
                            partyColor = 'party-blue';
                            break;
                        case "民進":
                            partyColor = 'party-green';
                            break;
                        case "無":
                            partyColor = 'party-gray';
                            break;
                        default:
                            partyColor = 'party-white';
                    }
                    all[city.cityName] = {
                        cityName: city.cityName,
                        candName: city.tickets[0].candName,
                        cityNo: city.cityNo,
                        ticket: city.tickets[0].ticket,
                        partyColor: partyColor
                    }
                }
            })
            this.all = all
            //  console.log('all', this.all)
            // console.log('order',this.citys)
        },
        goCand(city) {
            //  console.log(city)
            location.href = `/#/ing?city=${city.cityNo}`
        }
        ,

        getData_vote() {
            document.querySelectorAll('.news').forEach((e) => e.remove())
            // eslint-disable-next-line no-undef
            axios
                .get('https://melect-api.ftvnews.com.tw/Tickets/ftvelect.json')                .then((response) => {
                    // console.log(response)
                    // let data = response.data.T1.detail[1].tickets
                    // console.log('dataaaaa', data)
                    // data.forEach((item) => {
                    //     this.taipei.push(item)
                    // })
                    this.preOrderData(response.data)
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
        getData_vote1() {
            // eslint-disable-next-line no-undef
            axios
                // .get('https://melect-api.ftvnews.com.tw/Tickets/ftvelect.json')
                .get('https://melect-api.ftvnews.com.tw/Tickets/ftvelect.json')
                .then((response) => {
                    console.log(response)
                    let data = response.data.T1.detail
                    console.log('dataaaaa', data)
                    data.forEach((item) => {
                        this.all.push(item)
                    })
                })
                .catch((error) => {
                    console.log('error' + error)
                })
        },
    },
    mounted() {
        this.getData_vote(),
            this.getData_vote1()
        this.counter = setInterval(() => {
            this.getData_vote()
        }, 10000);
    },

}
</script>



<style scoped>
.party-blue {
    background: lightblue;
}

.section {
    max-width: 1000px;
    padding: .5rem 1rem;
    background-color: rgb(255, 255, 255);
    margin: 1rem auto;
    border-radius: 20px;
    box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
}

.board {
    margin: .1rem;
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
}

.box {
    display: grid;
    grid-template-columns: 1fr 2fr;
    border: 3px solid rgb(224, 242, 222);
    border-radius: 1rem;
    margin: .4rem;
    cursor: pointer;

}

p {
    width: fit-content;
    text-align: center;
    margin: auto;
    padding: .8rem;
}

h3 {
    margin: auto;
    padding: .5rem;
}

@media screen and (max-width: 900px) {
    .board {
        grid-template-columns: 1fr 1fr 1fr 1fr;
    }

    .section {
        margin: 1rem;
    }



}

@media screen and (max-width: 768px) {
    .board {
        grid-template-columns: 1fr 1fr 1fr;
        margin: .5rem auto;
    }

    p {
        padding: .3rem;
    }

}


.ct {
    border-radius: .8rem 0rem 0rem .8rem;
    background: rgb(227, 242, 180);
    text-align: center;
    background-size: cover;


}

.progress_class {
    width: 100%;
    height: 2rem;
    overflow: hidden;
    /*设置iOS下清除灰色背景*/
    appearance: none;
    border-radius: 1rem;
    -webkit-appearance: none;
}

.progress {
    border-radius: 1rem;

}

.progress_class::-webkit-progress-value {
    background: linear-gradient(90deg, rgb(248, 219, 176) 0%, rgb(248, 177, 34) 100%);
    border-radius: 8px;
}


.progress_class::-webkit-progress-bar {
    background-color: #d7d7d7;
}


.aaa {
    display: grid;
    grid-template-columns: 1fr 3fr 1fr;
}

.vote {
    display: grid;
    grid-template-columns: 1fr 1fr;
    margin: auto;
}







.photo {
    width: 100px;
    height: 100px;
}

.layout_voting {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr;
}
</style>

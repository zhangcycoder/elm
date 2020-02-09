<template>
    <div>
        <div class="swiper_box">
            <van-swipe :touchable=a :width="404" :height="220">

            <van-swipe-item v-for="(a,b) in list" :key="b">
                <div class="single">
                        <div v-for="(item,index) in a.arr" :key="index" class="cycleBox">
                        <p>
                            <img :src="item.image" alt="">
                        </p>
                        <div>
                            {{item.title}}
                        </div>
                    </div>
                </div>

            </van-swipe-item>
            </van-swipe>
        </div>
        <div class="adv">
                <img src="https://dss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=2936920306,2232978171&fm=26&gp=0.jpg" alt="">
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            list:[],
            a:true
        }
    },
    mounted(){
        axios.get('http://localhost:8081/data.json').then((res)=>{
            window.console.log(res)
            this.list=res.data
        window.console.log(this.list)

        })
    }
}
</script>


<style scoped>
.swiper_box
{
    width: 100%;
    height: 200px;
    /* background-color: violet; */
}
.single
{
    /* margin: 20px auto; */
    display: inline-flex;
    justify-content: left;
    align-items: center;
    flex-wrap: wrap;
}
.cycleBox
{
    width: 20%;
    margin: 0 10px;
}
.cycleBox img
{
    width: 50%;
}
.adv
{
    width: 90%;
    height: 200px;
    margin: 0 auto;
}
.adv img
{
    width: 100%;
    height: 100%;
}
</style>
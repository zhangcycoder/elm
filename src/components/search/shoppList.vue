<template>
    <div>
        <div class="shopp_box" v-for="(items,index) in list" :key="index">
            <div class="single">
                <div class="single_left">
                <img :src="items.image" alt="">
                </div>
                <div class="single_right">
                    <div class="single_right_title">{{items.title}}</div>
                    <div>月售{{items.sales}}</div>
                    <div>￥{{items.price}}起送|配送费￥{{items.delivery}}</div>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
// 
import axios from 'axios'
export default {
    data() {
        return {
          list:[]  
        }
    },
    mounted(){
        axios.get('http://localhost:8081/shopp.json').then((res)=>{
            this.list=res.data
        })
    }
}
</script>

<style  scoped>
.shopp_box
{
    width: 90%;
    margin: 20px auto;
}
.single
{
    width: 100%;
    height: 100px;
    display: inline-flex;
    justify-content: space-between;
    align-items: center;
}
.single_left
{
    width: 30%;
    height: 100%;
}
.single_left img
{
    width: 100%;
}
.single_right
{
    width: 68%;
    height: 100%;
}
.single_right_title
{
    font-weight: 600;
    font-size: 20px;
    color: red;
}
</style>
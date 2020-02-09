<template>
    <div>
        <div class="history">
            <div class="history_title" >历史搜索</div>
            <div v-for="(items,index) in historyArr" :key="index">
                {{items.name}}
            </div>
        </div>
        <div class="hotSearch">
            <div class="hotSearch_title">
                热门搜索
            </div>
            <div class="hotSearch_content">
                <div class="items" v-for="(item,index) in list" :key="index">{{item.name}}</div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data() {
        return {
            list:[],
            historyArr:JSON.parse(window.localStorage.getItem('examElm'))||[]
        }
    },
   
    mounted(){
        axios.get('http://localhost:8081/site.json').then((res)=>{
            this.list=res.data
        })
    }
}
</script>


<style scoped>
.history,.hotSearch
{
    border: 1px solid red;
    width: 100%;
    margin: 10px;
}
.history_title , .hotSearch_title
{
    font-size: 20px;
    font-weight: 500;
    margin: 20px 0;
}
.hotSearch_content
{
    display: inline-flex;
    width: 100%;
    flex-wrap: wrap;
    height: 75px;
    overflow: hidden;
}
.items
{
    margin: 5px 10px;
    background-color: aquamarine;
    padding: 2px 4px;
    
}
</style>
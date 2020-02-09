<template>
    <div>
        <div v-for="(item,index) in search()" @click="toHistory(item)" :key="index" class="singleText" v-html="test(item)">
        </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    props:{
        text:String
    },
    data() {
        return {
            list:[],
            histArr:[]
        }
    },
    
    mounted(){
    axios.get('http://localhost:8081/site.json').then((res)=>{
        this.list=res.data
    })
    },
    methods:{
        search(){
            let temp = []
            this.list.forEach(e=>{
               if(e.name.includes(this.text)){
                    temp.push(e)
               }
            })
            return temp
        },
        test(item){//改变字体
            let textReg = item.name;
            let testReg = new RegExp(this.text,'g');
            let htmlText = `<span class='a'>${this.text}</span>`
            return textReg.replace(testReg,htmlText)
        },
        toHistory(value){
            window.console.log(this.histArr)
             this.histArr=JSON.parse(window.localStorage.getItem('examElm'))||[]
            if(this.histArr.length==0){
                window.console.log('2')
                this.histArr.unshift(value)
            }else{
                let i = this.histArr.findIndex(e=> e.name===value.name)
               if(this.histArr.length<5){
                if(i==-1){
                    this.histArr.unshift(value)
                }else{
                    this.histArr.splice(i,1);
                    this.histArr.unshift(value)
                }
               }else{
                   if(i==-1){
                    this.histArr.pop();
                    this.histArr.unshift(value)
                   }else{
                    this.histArr.splice(i,1);
                    this.histArr.unshift(value)
                   }
               }
            }
            window.localStorage.setItem('examElm',JSON.stringify(this.histArr))

        },
        // mounted(){
        //     this.histArr=JSON.parse(window.localStorage.getItem('examElm'))||[]
        //     window.console.log(this.histArr)
        // }
    }

}
</script>

<style >
    .a
    {
        color: red;
    }
    .singleText
    {
        margin: 10px 0;
    }
</style>
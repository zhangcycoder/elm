<template>
    <div class="box">
            <van-search background='blue' placeholder="搜索饿了么商家、商品名称" v-model="value" @click="toAbout"/>
    </div>
</template>

<script>
export default {
    data() {
        return {
            value:''
        }
    },
   methods:{
   toAbout(){
       this.$router.push('/about')
   }
   }
 
}
</script>


<style scoped>
/* .box
{
    background-color: blue;
    padding: 5px 20px;
} */
</style>
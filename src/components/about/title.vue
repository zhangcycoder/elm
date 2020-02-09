<template>
    <div>
        <div class="navtiation_bar">
            <div>
                <img src="../../assets/左箭头.png" alt="" @click="go">
            </div>
            <div class="nav_serch">
                <van-search placeholder="输入商家、商品名称" v-model="value" @input='handlechange'/>
            </div>
            <div>搜索</div>
        </div>
    </div>
</template>

<script>
export default {
    props:{
        searchLength:Function
    },
    data() {
        return {
            value:''
        }
    },
    methods:{
        handlechange(){
            this.$emit('searchLength',this.value)
        },
        go(){
            window.console.log('1')
            this.$router.go(-1)
        }
    }
}
</script>


<style scoped>
.navtiation_bar
{
    display: inline-flex;
    width: 100%;
    align-items: center;
    background-color: white;
    justify-content: space-around;
}
.nav_serch
{
    width: 80%;
}
</style>
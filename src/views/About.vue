<template>
  <div class="about">
      <Title @searchLength='searchLength'/>
      <component :text='text' :is="isPage"></component>
  </div>
</template>

<script>
import Title from '../components/about/title'
import History from './History'
import HotSearch from './HotSearch'
export default {
    components:{
      Title
    },
    data() {
      return {
        isPage:History,
        text:''
      }
    },
    methods:{
      searchLength(value){
        if(value.length!==0){
          this.text=value
          this.isPage=HotSearch
        }else{
          this.isPage=History
        }
      }
    }
}
</script>

<style scoped>

</style>
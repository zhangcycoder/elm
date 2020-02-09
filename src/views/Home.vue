<template>
  <div class="home">
    <SearchTitle/>
    <SearchSwiper/>
    <Shopp/>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchTitle from '../components/search/search_title'
import SearchSwiper from '../components/search/search_swiper'
import Shopp from '../components/search/shoppList'
export default {
  name: 'home',
  components: {
    SearchTitle,
    SearchSwiper,
    Shopp
  }
}
</script>

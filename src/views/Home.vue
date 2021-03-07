<template>
  <div class="home">
    <div class="row">
      <MainPage
      v-for="(item,index) in mangaList.manga"
      :key="index"
      :Name="item.title"
      :Img="item.image_url"
      :id="item.mal_id"
      class="col-3"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import MainPage from "@/components/MainPage.vue";

export default {
  name: 'Home',
  components: {
    MainPage
  },
  props:{
    page: Number
  },
  data(){
    return{
      mangaList:null,
      url:"https://api.jikan.moe/v3/magazine/1/1 "
    };
  },
  mounted(){
    axios
    .get(this.url)
    .then(result => {
      this.mangaList = result.data;
    })
    .catch(err => {
      console.log(err);
      alert(err);
    });
  }
};
</script>

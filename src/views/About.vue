<template>
  <div class="container">
  <b-card style="max-width: 80rem; "
  :img-src="mangaList.image_url" 
  img-left
  :title="mangaList.title"
  :sub-title="mangaList.title_english">
   status : <b-badge variant="info">{{mangaList.status}}</b-badge> <br>
   published : {{mangaList.published.string}} <br>
   Synopsis : {{mangaList.synopsis}} <br>
   
  </b-card>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      mangaList: null,
      url: `https://api.jikan.moe/v3/manga/${this.$route.params.id} `,
    };
  },
  mounted() {
    axios
      .get(this.url)
      .then((result) => {
        this.mangaList = result.data;
      })
      .catch((err) => {
        console.log(err);
        alert(err);
      });
  },
};
</script>

<style>

</style>
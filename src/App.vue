<template>
  <div id="app">
    <b-navbar id="nav" toggleable="lg" type="dark">
      <b-navbar-brand to="/">Home</b-navbar-brand>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">
        <b-nav-form >
          <b-form-input
            size="sm"
            class="mr-sm-2 col-8"
            placeholder="Search"
            v-model="sh"
          ></b-form-input>
          <b-button
            size="sm"
            class="my-2 my-sm-0"
            type="submit"
            @click="Search()"
            >Search</b-button
          >
        </b-nav-form>
      </b-navbar-nav>
    </b-navbar>
    <router-view 
    />
  </div>
</template>
<script>
import axios from "axios";
export default {
  data(){
    return{
      page:1,
      sh:"",
      mangaList:null,
      url:"https://api.jikan.moe/v3/magazine/1/1"
    };
  },
  methods:{
    Search(){
      const router = this.$router;
      for(let i = 0; i<= this.mangaList.manga.length; i++){
        if (this.sh == this.mangaList.manga[i].title){
          alert(this.mangaList.manga[i].title);
          router.push({
            path:`/about/${this.mangaList.manga[i].mal_id}`
          });
          break;
        } else if (99 == i ){
          router.push({
            path:`/`
          });
        }
      }
    }
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
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: rgb(59, 59, 59);
}

#nav {
  padding: 30px;
  background: #000;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #1784e9;
}
</style>

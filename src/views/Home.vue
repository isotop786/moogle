<template >

    <div id="page_style" class="Site-content page__style page__description">
<div id="home_content">
<div class="content column is-half is-offset-6" style="text-align: right">
itme  
itme 3
</div>
<div id="home_padding"></div>
<div style="text-align: center;">

<h1 class="title is-1 has-text-primary">Moogle</h1>

</div>
<div class="content column is-half is-offset-one-quarter" style="margin-top: 30px; padding-bottom: 0; margin-bottom: 15px;">
<form>
<div class="field has-addons">
<div class="control is-expanded">
<input v-model="keyword"
  @keydown.enter.prevent="search"
 id="search_query" class="input is-primary is-medium" type="search" placeholder="Search for any Movie, TV Shows" name="Search" autofocus="autofocus" onfocus="this.select()" required>
</div>
<div class="control">
<button @click.prevent="search" class="button is-primary input is-medium search-button-icon">
  <i class="fas fa-search"></i>
</button>
</div>

</div>
</form>
</div>
<div v-if="error">
  <p>{{error}}</p>
</div>
<div class="content column is-half is-offset-one-quarter" style="margin-top: 30px; padding-bottom: 0; margin-bottom: 15px;">

<div class="columns">
  <div class="column is-one-third my-3" v-for="movie in movies" :key="movie.id">
    <div class="box mp">
        <router-link :to="{name:'Single', params:{id:movie.id}}"><img class="image" :src="movie.image" alt=""></router-link>
    </div>  
    </div>
  
</div>

</div>

<div v-if="loading">
data loading...
</div>
<div id="mobile_home"></div>
</div>
<noscript>It appears that your Javascript is disabled. You might want to visit our
                            <a href="/lite/results">lite results</a>.
                        </noscript>

</div>
    
 
</template>
<style scoped>
.mv-img{
  height: 200px !important;
  width: 200px !important;
}

.mp{
  margin: 0  !important;
  padding: 0 !important;
}
</style>
<script>

// import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    // HelloWorld
  },
  data(){
    return{
      movies:[],
      loading:false,
      keyword: null,
      error:null
    }
  },

  methods:{
    search(){
      if(this.keyword){
        this.error = null
         this.loading = true
       const options = {
                    method: 'GET',
                    url: `https://imdb-internet-movie-database-unofficial.p.rapidapi.com/search/${this.keyword}`,
                    headers: {
                      'x-rapidapi-key': '3f0e48ed75mshbf44f2536d6d4afp116bd6jsna823a38279d6',
                      'x-rapidapi-host': 'imdb-internet-movie-database-unofficial.p.rapidapi.com'
                    }
                  };
                  
                  axios.request(options).then( (response)=> {
                      // console.log(response.data);
                      this.movies = response.data.titles
                      console.log(this.movies)
                      this.loading = false
                  }).catch((error)=> {
                    this.error = error
                      console.error(error);
                  });
                  
                  console.log(this.loading)
      }else{
        this.error = "Can not be empty."
      }
     


    }
  }
}
</script>
<style >

</style>

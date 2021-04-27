<template>
<div>
<div class="columns p-4" v-if="!loading">
  <Loading/>
</div>
  <div v-else class="">
     <Navbar/>
     <div class="container bm">

    
       <div class="columns mt-5 px-4">
           <div class="column">
               <router-link to="/" class="button is-warning ">Back to Search</router-link> 
           </div>
       </div>
         <div class="columns px-4"  style="margin-top: 10px; padding-bottom: 0; margin-bottom: 15px;">
  <div class="column is-half">
      <img class="image" :src="movie.poster" alt="">
  </div>
  <div class="column is-half">

<div class="content">
  <h1 class="title is-1 has-text-primary">{{movie.title}}</h1>
  <p>{{movie.plot}}</p>
  <h2 v-if="movie.year" class="has-text-success">Release Year: {{movie.year}}</h2>
  <h3 class="has-text-info">Rating: {{movie.rating}}</h3>
  <h3 class="has-text-danger">Length: {{movie.length}}</h3>
  <a :href="movie.trailer.link" target="_blank" v-if="movie.trailer.link" class="button is-link">Watch Trailer</a>
 <h2 class="title is-2 has-text-primary">Casts</h2>
  <ul>
    <li v-for="c in movie.cast" :key="c.id"> <span class="has-text-dark"> <a target="_blank" :href="wiki+c.actor">{{c.actor}}</a>  </span> as <span class="has-text-danger"> {{c.character}} </span></li>
  </ul>
  <h3 class="title is-2 has-text-primary">Technical Spcifications</h3>
  <ol>
    <li v-for="s in movie.technical_specs" :key="s.id">{{s[0]}} : {{s[1]}} </li>
  </ol>
</div>

  </div>
 
</div>
  </div>
   </div>
 </div>
</template>

<script>
import Navbar from '../components/Nav'
import Loading from '../components/Loading'
import axios from 'axios';
export default {
name:"Single",
components:{
  Navbar,
  Loading
},
data(){
    return{
        movie:{},
        wiki: 'https://en.wikipedia.org/wiki/',
        loading:false
    }
},
created(){
    console.log('created')
  
const options = {
  method: 'GET',
  url: `https://imdb-internet-movie-database-unofficial.p.rapidapi.com/film/${this.$route.params.id}`,
  headers: {
    'x-rapidapi-key': '3f0e48ed75mshbf44f2536d6d4afp116bd6jsna823a38279d6',
    'x-rapidapi-host': 'imdb-internet-movie-database-unofficial.p.rapidapi.com'
  }
};

axios.request(options).then( (response)=> {
	// console.log(response.data);

    this.loading = true
    this.movie = response.data
}).catch(function (error) {
	console.error(error);
});

this.loading = false
}
}
</script>

<style scoped>
    .bm{
        margin-bottom: 3rem;
    }
    
</style>
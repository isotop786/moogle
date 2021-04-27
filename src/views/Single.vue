<template>
  <div class="">
     <Navbar/>
     <div class="container bm">

    
       <div class="columns mt-5 px-4">
           <div class="column">
               <router-link to="/" class="button is-primary ">Back to Search</router-link> 
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
  <a :href="movie.trailer.link" target="_blank" class="button is-link">Watch Trailer</a>
 <h2 class="title is-2 has-text-primary">Casts</h2>
  <ul>
    <li v-for="c in movie.cast" :key="c.id"> <span class="has-text-dark"> <a :href="'//'"></a> {{c.actor}} </span> as <span class="has-text-danger"> {{c.character}} </span></li>
  </ul>
  <h3 class="title is-2 has-text-primary">Technical Spcifications</h3>
  <ol>
    <li v-for="s in movie.technical_specs" :key="s.id">{{s[0]}} : {{s[1]}}} </li>
  </ol>
</div>

  </div>
 
</div>
  </div>
   </div>
 
</template>

<script>
import Navbar from '../components/Nav'
import axios from 'axios';
export default {
name:"Single",
components:{
  Navbar
},
data(){
    return{
        movie:{}
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
	console.log(response.data);

    this.movie = response.data
}).catch(function (error) {
	console.error(error);
});
}
}
</script>

<style scoped>
    .bm{
        margin-bottom: 3rem;
    }
    
</style>
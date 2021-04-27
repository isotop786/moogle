<template>
  <div >
    <Navbar/>
    <div class="container mt-6 p-3">
     <div class="content is-medium">
    <h1 class="title ">About the Application</h1>
    <p>
      Moogle is Movie and TV show search engine. Which search content based on the title of Movie or TV show.
      This application is developed by <a href="https://github.com/isotop786">Maruf</a>.
    </p>
    <p>
      <a class="button is-danger" target="_blank" href="http://maruf-portfolio-app.herokuapp.com/">Visit developer site</a>
    </p>
     <p>
      <a class="button is-link" target="_blank" href="mailto:marufislam77@gmail.com">Contact Maruf</a>
    </p>
    <h4 class="title is-4 has-text-primary mt-6">Technologies used to develop the application</h4>
    <ul>
      <li>JavaScript</li>
      <li>Vue.js</li>
      <li>Vue Router</li>
      <li>Vuex</li>
      <li>Bulma CSS framework</li>
    </ul>
  </div>
    </div>
  </div>
</template>

<script>
import Navbar from '../components/Nav'
export default {
  name:"About",
  components:{
    Navbar
  }
}
</script>

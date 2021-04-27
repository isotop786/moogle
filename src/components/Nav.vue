<template>
  <div>
     <nav class="navbar is-dark">
  <!-- navbar brand, navbar menu... -->
  <div class="navbar-brand">
      <router-link to="/" class="navbar-item title is-1 has-text-primary">
        Moogle
      </router-link>
  </div>

  <div class="navbar-end">
      <div class="navbar-item">
        <div class="">
          
          <router-link to="/about" class="button is-danger">
            About
          </router-link>
        </div>
      </div>
    </div>

</nav>
  </div>
</template>

<script>
export default {
name:"Navbar"
}
</script>

<style>

</style>
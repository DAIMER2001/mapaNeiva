<template>
<div>
  <b-navbar toggleable="lg" type="dark" variant="info">
    <b-navbar-brand href="#">
      <img  src="@/assets/images/imagen_neiva.jpg" width="150" height="50"/></b-navbar-brand>
    <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav>
        <b-nav-item href="#"><NuxtLink to="/">
              Neiva
            </NuxtLink></b-nav-item>
      </b-navbar-nav>

      <!-- Right aligned nav items -->
      <b-navbar-nav class="ml-auto">

        <b-nav-item-dropdown right>
          <!-- Using 'button-content' slot -->
          <template #button-content>
            <em>Información</em>
          </template>
          <b-dropdown-item>
            <NuxtLink to="videos">
              Videos
            </NuxtLink>
          </b-dropdown-item>
          <b-dropdown-item href="#"><NuxtLink to="imagenes">
              Imagenes
            </NuxtLink>
          </b-dropdown-item>
        </b-nav-item-dropdown>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>
</template>
<script>
import img from "@/assets/images/imagen_neiva.jpg"
export default {
  data(){
    return {
          img: img
    }
  }
}
</script>
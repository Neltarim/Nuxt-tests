<template>
  <div>
    <div class="text-center">
      <h1 class="title">Pandacraft</h1>
      <h4 class="sub-title">The goal of this app is to build a carousel using flickity and picsum, and a simple admin dashboard.</h4>
    </div> 

    <div class="overview">
      <NuxtLink to="/Carousel" class="project-link">
        <div></div>      
      </NuxtLink>

      <NuxtLink to="/Dashboard" class="project-link">
        <div></div>
      </NuxtLink>
    </div>   
  </div>


</template>

<script>
export default {
  name: 'IndexPage',
}
</script>

<style lang="scss">
  html {
    background-color: #1c242c;
    font-family: helvetica, arial, sans-serif;
  }

  .title {
    font-size: 56px;
    color: $white;
  }

  .sub-title {
    font-size: 26px;
    color: $gray;
  }

  /* Project Link's group */
  .overview {
    margin: auto;
    width: 60rem;
    display: flex;
  }

  .project-link {
    margin: 20px;
    background-color: $green-dark;
    width: 500px;
    height: 500px;
    transition: 0.3s;
  }

  .project-link:hover {
    padding: 20px;
    background-color: $green;
  }

  .text-center {
    text-align: center;
  }

  @media only screen and (max-width:415px) {
    .overview {
      display: inline;
      margin: 0;
    }

    .project-link {
      margin-left: 0px;
      width: 100%;
      height: 500px;
      margin-top: 10px;
    }
  }

</style>

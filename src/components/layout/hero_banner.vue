<template>
    <b-carousel>
        <b-carousel-item v-for="(carousel, i) in carousels" :key="i">
            <section :class="`hero is-large is-${carousel.color}`">
                <div class="hero-body has-text-centered">
                    <h1 class="title">{{carousel.text}}</h1>
                </div>
            </section>
        </b-carousel-item>
    </b-carousel>
</template>
<script>
export default {
  name: "HeroBanner",
    data(){
        return {
            carousels: [
                { text: 'Slide 1', color: 'primary' },
                { text: 'Slide 2', color: 'info' },
                { text: 'Slide 3', color: 'success' },
                { text: 'Slide 4', color: 'warning' },
                { text: 'Slide 5', color: 'danger' }
            ]
        }
    },
  components: {
  
  }
}
</script>

<style lang="scss" scoped>
.hero {
  position: relative;
  margin-bottom: 2.5em;
}
.hero-body {
  background-size: cover;
  background-repeat: no-repeat;
  &::before {
    content: "";
    height: 100%;
    width: 100%;
    left: 0;
    top: 0;
    position: absolute;
    background-color: rgba($color: #000000, $alpha: 0.5);
  }
  // @media screen(min-width: 500px) {
  //   .hero-body{
  //     background-size : c;
  //   }
  // }
}

</style>

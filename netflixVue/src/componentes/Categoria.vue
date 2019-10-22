<template>
  <div class="slider">
      <h3>{{ titulo }}</h3>
      <span v-on:mouseover="scrollEsquerda()" v-on:mouseout="clearScroll()" class="handle handlePrev active">
        <i class="fa fa-caret-left" aria-hidden="true"></i>
      </span>

      <div ref="scroller" class="row">
        <div class="row__inner">

          <Filme v-for="filme in filmes"
                 v-bind:key="filme.id"
                 v-bind:titulo="filme.title"
                 v-bind:imagem="filme.imagem">
          </Filme>

        </div>
      </div>

      <span v-on:mouseover="scrollDireita()" v-on:mouseout="clearScroll()" class="handle handleNext active">
        <i class="fa fa-caret-right" aria-hidden="true"></i>
      </span>

    </div>
</template>
<script>
import Filme from "./Filme.vue"
export default {
  name: 'Categoria',
  props:['titulo', 'filmes'],
  components: {
    Filme
  },
  methods:{
    scrollDireita(){
      console.log(this.titulo);
      this.interval = setInterval(() => { this.$refs.scroller.scrollLeft += 1 }  , 5);
    },
    scrollEsquerda(){
      this.interval = setInterval(() => { this.$refs.scroller.scrollLeft -= 1 }  , 5);
    },
    clearScroll(){
      clearInterval(this.interval)
    }
  }
}

</script>
<style lang="scss">

</style>

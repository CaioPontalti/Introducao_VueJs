<template>

  <div class="gui-card" :style="efeito" v-on:click="clickSelected()" v-on:mouseout="removeSelected()">
      <div class="gui-card__media">
        <img class="gui-card__img" :src="imagem" alt=""  />
      </div>
      <div class="gui-card__details">
        <div class="gui-card__title">
          {{ nome }}
        </div>
      </div>
  </div>

</template>

<script>
export default {
  name: 'Filme',
  props:['id', 'nome', 'imagem'],
  data(){
    return{
      efeito:null,
      click:0
    }
  },
  methods: {
    clickSelected: function() {
        //debugger;
        this.click ++;
        this.efeito ='transform: scale(1.9); margin-right: 110px;';
        if(this.click > 1){
            this.efeito ='transform: scale(1.5); margin-right: 10px;';
            this.click = 0;
        }
    },
    removeSelected: function() {
        //debugger;
        this.efeito = 0;
        this.click = 0;
    }
  },
}
</script>

<style lang="scss">


</style>

<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroForms :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>


<script lang="ts">
import { defineComponent } from 'vue';
import CronometroForms from './Cronometro.vue'

export default defineComponent({
    name: "TemporazidorForms",
    emits: ['aoTemporizadorFinalizado'],
    components:{
        CronometroForms
    },
    data(){
        return{
        tempoEmSegundos: 0,
        cronometro: 0,
        cronometroRodando: false,
        }
    },
    computed: {
       

    },
    methods:{
        iniciar(){
            this.cronometroRodando = true
            this.cronometro=   setInterval(() =>{
                this.tempoEmSegundos +=1;
            }, 1000)
        },
        finalizar(){
            console.log('passou aqui finaliazar temporizador')
            this.cronometroRodando= false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundos)
            this.tempoEmSegundos = 0

        }

    }
})
</script>
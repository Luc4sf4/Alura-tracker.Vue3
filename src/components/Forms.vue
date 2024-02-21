<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="Formulário para criação de uma nova tarefa"
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefa você deseja iniciar?"
          v-model="descricao"
        />
      </div>
      <div class="column">
        <TemporizadorForms @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import TemporizadorForms from './Temporizador.vue'

export default defineComponent({
    name: 'FormsList',
    emits:['inSaveTask'],
    components:{
        TemporizadorForms
    },
    data(){
        return{
            descricao: ''
        }
    },
    methods:{
        finalizarTarefa(tempoDecorrido: number) : void{
            console.log('tarefa Finalizada');
            this.$emit('inSaveTask',{ 
                duration: tempoDecorrido,
                description: this.descricao
            });
            
            this.descricao = ''
        }
    },
})
</script>
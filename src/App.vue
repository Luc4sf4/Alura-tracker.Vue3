<template>
  <main class = "columns is-gapless is-multiline" :class="{ 'dark-mode': darkModeActived }">
    <div class="column is-one-quarter">
      <BarraLateral @toThemeChanged="changeTheme"/>
    </div>
    <div class ="column is-three-quarter content">
      <FormsList @inSaveTask= "saveTask" />
      <div class="lista">
        <TaskForms v-for="(task, index) in tasks" :key="index" :task ="task"/>
        <BoxTask v-if="listaEstaVazia">
        Você não está produtivo Hoje :(
        </BoxTask>
      </div>
    

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import FormsList from './components/Forms.vue'
import TaskForms from './components/Task.vue'
import ITask from '@/interfaces/ITask'
import BoxTask from './components/Box.vue'

export default defineComponent({
  name: 'App',
  components:{
    BarraLateral,
    FormsList,
    TaskForms,
    BoxTask
  },
  data(){
    return{
      tasks: [] as ITask[],
      darkModeActived: false
    }

  },
  computed:{
      listaEstaVazia() : boolean{
        return this.tasks.length === 0

      }

  },
  methods:{

    saveTask(task: ITask){
      console.log('passou aqui savetask')
      this.tasks.push(task)
    },
    changeTheme(darkModeActived: boolean){
      this.darkModeActived = darkModeActived
    }

  }
 });
</script>

<style>
  .lista{
    padding: 1.75rem;
  }

  main{
    --primary-bg: #fff;
    --primary-text: #000;

  }

  main.dark-mode{
    --primary-bg: #2b2d42;
    --primary-text: #ddd;

  }

  .content{
    background-color: var(--primary-bg);
  }

</style>

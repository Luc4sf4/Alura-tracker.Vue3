<template>
  <main class = "columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class ="column is-three-quarter">
      <FormsList @inSaveTask= "saveTask" />
      <div class="lista">
        <TaskForms v-for="(task, index) in tasks" :key="index" :task ="task"/>
    
     
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

export default defineComponent({
  name: 'App',
  components:{
    BarraLateral,
    FormsList,
    TaskForms
  },
  data(){
    return{
      tasks: [] as ITask[]
    }

  },
  methods:{

    saveTask(task: ITask){
      console.log('passou aqui savetask')
      this.tasks.push(task)
    }

  }
 });
</script>

<style>
  .lista{
    padding: 1.75rem;
  }

</style>

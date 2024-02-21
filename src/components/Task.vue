<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <BoxTask>
        <div class="column is-7">
                {{ task.description || 'Tarefa sem descrição' }}
        </div>
        <div class="column">
           <CronometroForms :tempoEmSegundos="task.duration" />
        </div>
    </BoxTask>
</template>

<script lang="ts">
import { PropType, defineComponent } from 'vue';
import CronometroForms from './Cronometro.vue'
import ITask from '@/interfaces/ITask';
import BoxTask from './Box.vue'



export default defineComponent({
    name: 'TaskForms',
    components:{
        CronometroForms,
        BoxTask
    },
    props:{
        task:{
            type: Object as PropType<ITask>,
            required: true
        }
    }

})
</script>

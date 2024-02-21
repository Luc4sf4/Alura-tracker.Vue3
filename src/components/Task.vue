<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div class="box has-text-weight-bold">
        <div class="column is-7">
                {{ task.description }}
        </div>
        <div class="column">
           <CronometroForms :tempoEmSegundos="task.duration" />
        </div>
    </div>
</template>

<script lang="ts">
import { PropType, defineComponent } from 'vue';
import CronometroForms from './Cronometro.vue'
import ITask from '@/interfaces/ITask';



export default defineComponent({
    name: 'TaskForms',
    components:{
        CronometroForms
    },
    props:{
        task:{
            type: Object as PropType<ITask>,
            required: true
        }
    }

})
</script>
<style scoped>
    .box {
        background: #faf0ca;

    }

</style>
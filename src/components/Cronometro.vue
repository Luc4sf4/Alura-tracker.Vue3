<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <section>
        <strong class="display">{{ tempoDecorrido }}</strong>
        
    </section>
</template>
<script lang="ts">
    import {defineComponent} from 'vue'

    export default defineComponent({
        name:'CronometroForms',
        props:{
            tempoEmSegundos: {
                type: Number,
                default:0,
            }
        },
        computed:{
            tempoDecorrido() : string{
                console.log('passou aqui, em Tempo Decorrido');
            return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11,8)
        }
        },
    })
</script>
<style>
    .display{
        color: var(--primary-text);
        background-color:var(--primary-bg);
    }

</style>
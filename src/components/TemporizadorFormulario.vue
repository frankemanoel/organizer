<template>
    <section class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroFormulario :tempoEmSegundos="tempoEmSegundos" />
        <BotaoFormulario @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
        <BotaoFormulario @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" />   
    </section>
</template>

<script lang="ts">
import {defineComponent} from 'vue'
import CronometroFormulario from './CronometroFormulario.vue'
import BotaoFormulario from './BotaoFormulario.vue'
export default defineComponent ({
    name: 'TemporizadorFormulario',
    components:{
      CronometroFormulario, BotaoFormulario
    },
    data(){
        return{
            tempoEmSegundos: 0,
            cronometro:0,
            cronometroRodando:false
        }
    },
    emits:
        ['aoFinalizarTemporizador']
    ,
    methods:{
        iniciar (){
            this.cronometroRodando = true
           this.cronometro = setInterval(() =>{
                this.tempoEmSegundos += 1
           }, 1000)
        },
        finalizar(){
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoFinalizarTemporizador', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})
</script>

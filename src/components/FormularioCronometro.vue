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
        <TemporizadorFormulario @aoFinalizarTemporizador="finalizarTarefa"/>
          </div>
        </div>
  </div>
</template>

<script lang="ts">
import {defineComponent} from 'vue'
import TemporizadorFormulario from './TemporizadorFormulario.vue'
export default defineComponent ({
    name: 'FormularioCronometro',
    components:{
      TemporizadorFormulario
    },
    data(){
      return{
        descricao: ''
      }
    },  
    methods:{
      finalizarTarefa(tempoDecorrido: number) : void{
        console.log('Tempo da Tarefa: ',tempoDecorrido)
        console.log('Nome da Tarefa: ', this.descricao)
        this.descricao = ''
      }
    }
})
</script>

<style scoped></style>

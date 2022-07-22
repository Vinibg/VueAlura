<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between ">
        <CronometroVue :tempoEmSegundos="tempoEmSegundos" />
        <button class="button" @click="iniciar" :disabled="cronometrando">
            <span class="icon">
                <i class="fas fa-play"></i>
            </span>
            <span>play</span>
        </button>
        <button class="button" @click="finalizar" :disabled="!cronometrando">
            <span class="icon">
                <i class="fas fa-stop"></i>
            </span>
            <span>stop</span>
        </button>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CronometroVue from "./Cronometro.vue";

export default defineComponent({
    name: 'TemporizadorVue',
    emits: ['aoTemporizadorFinalizado'],
    components:{
        CronometroVue
    },
    data(){
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometrando: false
        }
    },
    methods:{
        iniciar(){
            this.cronometro = setInterval(()=>{
                this.tempoEmSegundos += 1
                this.cronometrando = true
            }, 1000)
        },
        finalizar(){
            this.cronometrando = false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})

</script>
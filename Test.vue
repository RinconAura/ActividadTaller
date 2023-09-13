<script setup lang="ts"> 
import{ref} from 'vue'
import Numero from '../components/Numero.vue';
const contador = ref<number>(0);
const numeros = ref<Array<number>>([]);
const longListaNumeros = ref<number>(0);
function incrementar(): void{
    contador.value++;
}
function generarListaNumeros(): void{
    for( let index = 0; index <longListaNumeros.value; index++>) {
        numeros.value.push(index);
    }
}
</script>

<template>
    <h1>contador: {{ contador }}</h1>
    <button @click="">Incrementar</button>
    <br>
    <form action="">
        <input v-model="longListaNumeros">
        <button @click="generarListaNumeros" type="button">Generar</button>
    </form>
    <div>
        <ul>
            <li v-for="item of numeros">
                <!-- {{ numero }}-->
                <Numero :numero= "item"/>

            </li>
        </ul>
    </div>
</template>
<style scoped></style>
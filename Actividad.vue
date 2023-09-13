<script setup lang="ts"> 
import{ref} from 'vue'

export default: {
    setup(){
        const nuevoArticulo = ref("");
        const nuevaCantidad = ref(0);
        const nuevoValorUnitario = ref(0);
        const listaArticulos = ref([]);

        const agregarArticulo = ( )=> {
            if(nuevoArticulo.value && nuevaCantidad.value > && nuevoValorUnitario.value > 0  ){
                listaArticulos.value.push({
                    nombre: nuevoArticulo.value,
                    cantidad: nuevaCantidad.value,
                    nuevoValorUnitario: nuevoValorUnitario.value,
                });
//al borrar recoja estos valores
                nuevoArticulo.value =  "";
                nuevaCantidad.value = (0);
                nuevoValorUnitario = (0);
           }
        };
        const borrarArticulo = (index)=>{
            listaArticulos.value.splice(index , 1);
        };
        return{
            nuevoArticulo,
            nuevaCantidad,
            nuevoValorUnitario,
            listaArticulos,
            agregarArticulo,
            borrarArticulo,
        };
    };


</script>

<template>
    <div>
        <h1>Lista de articulos</h1>
        <div>
            <label for="articulo"> Articulo</label>
            <input type="text" id="artiulo">
            <label for="cantidad">Cantidad</label>
            <input type="number" id="cantidad">
            <label for="valorUnitario">Valor Unitario</label>
            <input type="number" id="valorUnitario">

            <button @click="agregar">Agregar</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>#</th>
                    <th>Articulo</th>
                    <th>Cantidad</th>
                    <th>V. Unitario</th>
                    <th>Total</th>
                    <th>Borrar</th>
                </tr>
            </thead>
                
            <tbody>
                <tr v-for="(articulo, index) of listaArticulos" :key="index">
                    <td>{{ index +1 }}</td>
                    <td>{{articulo.nombre}}</td>
                    <td>{{articulo.cantidad}}</td>
                    <td>{{articulo.valorUnitario}}</td>
                    <td>{{articulo.cantidad * articulo.valorUnitario}}</td>
                    <td>
                        <button @click="borrarArticulo(index)">X</button>
                    </td>  
                </tr>
            </tbody>
        </table>
    </div>
</template>
<style scoped>

</style>
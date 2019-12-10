<template>
    <div>
        <h2>Hamburguesas</h2>
        <ul>
             <li v-for="hamburguer in compras" :key="hamburguer.id">
                        {{hamburguer.desc}} {{hamburguer.precio}}

                 <button @click="agregarAlCarrito(hamburguer)"> Agregar al carrito</button>
            </li>
        </ul>
        <h2>Compras</h2>
        <ul>
             <li v-for="(hamburguer,i) in carrito">
                        {{hamburguer.desc}} {{hamburguer.precio}}

                 <button @click="quitarCarrito(i)">Eliminar</button>
            </li>
        </ul>
    </div>
</template>

<script>
import axios from 'axios'

let ProductosDePrueba= [

    {
        id:1 , 
        desc: "Hamburguesa Clasica" , 
        precio: 15.90
    },
    {
        id:2 , 
        desc: "Papas Fritas" , 
        precio: 5.90
    },
    {
        id:3 , 
        desc: "Inka Cola 250ml" , 
        precio: 4.90
    },
    {
        id:4 , 
        desc: "Cheese Burger" , 
        precio: 13.90
    }
]
export default {
    name: "CarritoCompras",
    data(){
        return {
            compras: ProductosDePrueba,
            carrito:[]
        }
    },
    computed:{},
    methods:{
        agregarAlCarrito: function(e) {
            console.log("carrito , agregar", e.desc);
            this.carrito.push(e);
            
            console.log("carrito , agregado" , e.desc , JSON.stringify(this.carrito,1))
        },
        quitarCarrito:function(e){
            console.log("carrito, quitar", e)
            let quitar = this.carrito[e]
            this.carrito.splice(e,1);
        console.log("carrito , quitado" , e , quitar , JSON.stringify(this.carrito,1))
        }
    },
    // created(){console.log("created".this);}

}
</script>

<style>

</style>
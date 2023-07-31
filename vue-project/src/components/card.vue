<script setup>
defineProps({
    nombre: String,
    edad: Number,
    ocupacion: String,
    pais: String,
    
    body: {
        type : String,
        default: "Esta api fue creada para mostrar datos de una persona",
    }

})
const emit = defineEmits(['añadirFavorito'])
</script>

<template>
    <div class="col">
        <div class="card">
            <div class="card-body">
                    <h5 class="card-title">{{ nombre }} - {{ edad }} - {{ ocupacion }} - {{ pais }}</h5>
                        <p class="card-text">{{body}}</p>
                        <div class="d-grid">
                            <button class="btn btn-primary" type="button" @click="emit('añadirFavorito', id)">Añadir a favoritos</button>
                        </div>
                    </div>
                </div>    
        </div>
</template>
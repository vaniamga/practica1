<script setup>
defineProps({
    title: String,
    author: String,
    year: Number,
    body: {
        type : String,
        default: "sin descripcion",
    }

})
const emit = defineEmits(['añadirFavorito'])
</script>

<template>
    <div class="col">
        <div class="card">
            <div class="card-body">
                    <h5 class="card-title">{{title}} - {{ year }} - {{ author }} </h5>
                        <p class="card-text">{{body}}</p>
                        <div class="d-grid">
                            <button class="btn btn-primary" type="button" @click="emit('añadirFavorito', id)">Añadir a favoritos</button>
                        </div>
                    </div>
                </div>    
        </div>
</template>
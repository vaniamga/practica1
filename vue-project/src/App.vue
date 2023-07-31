<script setup>
import { ref } from 'vue';
import Cards from './components/card.vue'

let favorito = ref('')
let posts = ref([])
let loading = ref(true)

const añadirFavorito = (cardFavorito) => {
  favorito.value = cardFavorito
}

const getData = async () => {
  try {
    const res = await fetch('https://raw.githubusercontent.com/vaniamga/api/main/json/personas.json')
    posts.value = await res.json()
  } catch (error) {
    console.log(error)
  } finally {
    setTimeout(() => {
      loading.value = false
    }, 1000)
  }
}

getData()
</script>

<template>
  <LoadingSpinner v-if="loading" />
  <div v-else>
    <h1> User Favorito {{ favorito }}</h1>
    <div class="container"> 
      <section class="row row-cols-1 row-cols-md-2 g-4">
        <Cards 
          v-for="item in posts"
          :key="item.id" 
          :nombre="item.nombre"
          :edad="item.edad"
          :ocupacion="item.ocupacion"
          :pais="item.pais"
          :body="item.body"
        />
      </section>
    </div>
  </div>
</template>

<style>
body {
  display: flex;
  justify-content: center;
  background-color: rgb(19, 16, 16);
  text-align: center;
  margin: 20px;
  padding: 0;
  font-family: Georgia, 'Times New Roman', Times, serif;
}

h1 {
  color: white;
  font-family:Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif
}

.card {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 400px;
  background-color: rgb(92, 90, 90);
  border: 1px solid rgb(3, 36, 3);
  border-radius: 8px;
  margin: 35px;
  padding: 16px;
  margin-bottom: 16px;
  color: bisque;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.card-title {
  font-weight: bold;
}

.card-text {
  font-size: 14px;
}
</style>

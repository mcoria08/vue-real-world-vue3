<script setup>
  import { ref, onMounted } from 'vue';
  import axios from 'axios';
  import EventCard from '@/components/EventCard.vue';

  const events = ref(null)
  onMounted(() => {
    axios.get('https://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/db')
      .then((response) => {
        events.value = response.data.events;
      })
      .catch((error) => {
        console.log(error);
      })
  });
</script>

<template>
  <h1 class="title">Events For Good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event"/>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.title{
  text-align: center;;
}
</style>
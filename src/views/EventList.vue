<template>
  <div class="events">
    <h1>Events for Good</h1>
    <EventCard :event="event" v-for="event in events" :key="event.id"/>
  </div>
</template>

<script>

import EventCard from '@/components/EventCard.vue';
import EventService from '@/services/EventService.js';

export default {
  name: 'EventList',
  components: {
    EventCard
},
  data() {
      return {
        events: null
      }
    },
    created() {
      EventService.getEvents()
      .then(response => {
        this.events = response.data;
      })
      .catch(error => {
        console.log(error);
      })
    }
}
</script>

<style scoped>
  .events {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>

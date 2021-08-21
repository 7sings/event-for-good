<template>
  <div class="home">
    <h1>Events For Good</h1>
    <div class="events">
      <EventCard v-for="event in events" :key="event.id" :event="event" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from '@/components/EventCard.vue'
import EventService from '@/services/EventService.js'

export default {
  name: 'EventList',
  components: {
    EventCard,
  },
  data() {
    return {
      events: [],
    }
  },
  created() {
    EventService.getEvents()
      .then((res) => {
        this.events = res.data
      })
      .catch((err) => {
        console.log(err)
      })
  },
}
</script>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>

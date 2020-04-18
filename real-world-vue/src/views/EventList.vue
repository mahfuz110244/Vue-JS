<template>
  <div>
    <h1>Event Listing</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
import EventCard from "@/components/EventCard.vue";
import axios from "axios";

export default {
  components: {
    EventCard
  },

  data() {
    return {
      events: []
    };
  },

  created() {
    axios
      .get("http://localhost:3000/events") // Does a get request
      .then(response => {
        this.events = response.data;
        console.log(response.data); // For now, logs out the response
      })
      .catch(error => {
        console.log("There was an error:", error.response); // Logs out the error
      });
  }
};
</script>

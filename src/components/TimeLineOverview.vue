<template>
  <div class="timeline-overview">
    <div
      v-for="event in eventsWithPositionValues"
      :key="event.id"
      class="timeline-overview__item"
      :aria-current="event.id === activeEventId"
      :style="`--offset: ${event.position}%`"
    />
  </div>
</template>

<script>
export default {
  props: {
    events: {
      type: Array,
      default: () => [],
    },
    activeEventId: {
      type: String,
      default: "",
    },
  },
  computed: {
    eventsWithPositionValues() {
      const firstEvent = this.events.reduce((current, previous) =>
        current.date < previous.date ? current : previous
      );
      const lastEvent = this.events.reduce((current, previous) =>
        current.date < previous.date ? previous : current
      );
      const firstDate = firstEvent.date;
      const lastDate = lastEvent.date;
      const delta = lastDate - firstDate;

      const result = this.events.map((event) => ({
        ...event,
        position: ((event.date - firstDate) / delta) * 100,
      }));

      console.log(result);
      return result;
    },
  },
};
</script>

<style>
.timeline-overview {
  margin: 3rem;
  position: relative;
}
.timeline-overview::before {
  content: "";
  display: block;
  width: 100%;
  height: 5px;
  background-color: rebeccapurple;
}

.timeline-overview__item {
  width: 15px;
  height: 15px;
  border-radius: 100%;
  background-color: rebeccapurple;
  position: absolute;
  top: -5px;
  left: var(--offset);
  transition: background-color 0.15s ease-in-out, transform 0.15s ease-in-out;
}
.timeline-overview__item[aria-current] {
  background-color: hotpink;
  transform: scale(2);
}
</style>

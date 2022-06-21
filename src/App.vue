<template>
  <div id="app">
    <TimeLineOverview :events="events" :active-event-id="activeId" />
    <MapViewer :events="events" :active-event-id="activeId" />
    <TimeLine @change="handleChange">
      <TimeLineItem v-for="event in events" :key="event.id" :id="event.id">
        {{ event.title }}
      </TimeLineItem>
    </TimeLine>
  </div>
</template>

<script>
import MapViewer from "./components/MapViewer.vue";
import TimeLine from "./components/TimeLine.vue";
import TimeLineItem from "./components/TimeLineItem.vue";
import TimeLineOverview from "./components/TimeLineOverview.vue";
import events from "./data/data.json";

export default {
  name: "App",
  components: { MapViewer, TimeLine, TimeLineItem, TimeLineOverview },
  data: () => ({
    events,
    activeId: "",
  }),
  mounted() {
    const vh = window.innerHeight * 0.01;
    document.documentElement.style.setProperty("--vh", `${vh}px`);
  },
  methods: {
    handleChange(event) {
      this.activeId = event;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}

#app {
  display: grid;
  grid-template-rows: auto 1fr auto;
  grid-template-areas: "timeline-overview" "map" "timeline";
  height: calc(var(--vh, 1vh) * 100);
}

#app .timeline-overview {
  grid-area: timeline-overview;
}

#app .map-viewer {
  grid-column: 1;
  grid-row: 1 / -1;
  z-index: -1;
}

#app .timeline {
  grid-area: timeline;
}
</style>

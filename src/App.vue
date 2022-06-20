<template>
	<div id="app">
		<MapViewer :events="events" :active-event-id="'a'" />
		<TimeLine>
			<TimeLineItem v-for="event in events" :key="event.id">
				{{ event.title }}
			</TimeLineItem>
		</TimeLine>
	</div>
</template>

<script>
import MapViewer from "./components/MapViewer.vue";
import TimeLine from "./components/TimeLine.vue";
import TimeLineItem from "./components/TimeLineItem.vue";
import events from "./data/data.json";

export default {
	name: "App",
	components: { MapViewer, TimeLine, TimeLineItem },
	data: () => ({
		events,
	}),
};
</script>

<style>
html {
	background-color: yellow;
}
body {
	background-color: yellow;
	min-height: 100vh;
}
#app {
	display: grid;
	grid-template-rows: 1fr auto;
	height: 100vh;
}
</style>

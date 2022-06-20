<template>
	<div class="map-viewer">
		<div
			class="map-viewer__item"
			v-for="event in events"
			:key="event.id"
			:aria-current="event.id === activeEventId"
		>
			{{ event.id }}
		</div>
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
		activeEvent() {
			return this.events.find((event) => event.title === this.activeEventId);
		},
	},
};
</script>

<style>
.map-viewer {
	width: 100%;
	height: 100%;
	position: relative;
	background-color: magenta;
}

.map-viewer__item {
	display: none;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	font-size: 10rem;
}

.map-viewer__item[aria-current] {
	display: initial;
}
</style>

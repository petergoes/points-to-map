<template>
	<div id="app">
		<div />
		<TimeLine>
			<TimeLineItem />
			<TimeLineItem />
			<TimeLineItem />
		</TimeLine>
	</div>
</template>

<script>
import TimeLine from "./components/TimeLine.vue";
import TimeLineItem from "./components/TimeLineItem.vue";
import data from "./data/data.json";
console.log({ data });

export default {
	name: "App",
	components: { TimeLine, TimeLineItem },
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

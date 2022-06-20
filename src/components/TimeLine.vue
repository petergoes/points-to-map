<template>
	<div class="timeline">
		<ul class="timeline__list">
			<slot />
		</ul>
	</div>
</template>

<style>
.timeline {
	background-color: transparent;
}
.timeline__list {
	list-style: none;
	padding: 0;
	display: flex;
	scroll-snap-type: x mandatory;
	overflow-x: scroll;
}

.timeline__list > * {
	width: 100%;
	flex-shrink: 0;
	scroll-snap-align: center;
	scroll-snap-stop: always;
	padding: 0;
}
</style>

<template>
	<li class="timeline-item">
		<div class="timeline-item__content">Timeline item</div>
	</li>
</template>

<style>
.timeline-item {
	display: flex;
	justify-content: center;
	background-color: blue;
	color: white;
	position: relative;
	z-index: 0;
	padding-top: 40px;
}

.timeline-item::before {
	content: "";
	display: block;
	width: 30px;
	height: 30px;
	background-color: hotpink;
	border-radius: 100%;
	position: absolute;
	top: 5px;
	left: 50%;
	transform: translateX(-50%);
	z-index: 1;
}
.timeline-item::after {
	content: "";
	display: block;
	width: 100%;
	height: 10px;
	background-color: white;
	position: absolute;
	top: 15px;
}

.timeline-item:first-child::after {
	width: 50%;
	left: 0;
	transform: translateX(100%);
}
.timeline-item:last-child::after {
	width: 50%;
	left: 0;
}

.timeline-item__content {
	background-color: rebeccapurple;
	width: 100%;
	padding-block: 4rem;
	display: flex;
	justify-content: center;
}
</style>

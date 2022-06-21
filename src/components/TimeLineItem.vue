<template>
  <li class="timeline-item" :data-id="id">
    <div class="timeline-item__content">
      <slot />
    </div>
  </li>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true,
    },
  },
};
</script>

<style>
.timeline-item {
  display: flex;
  justify-content: center;
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
  background-color: rebeccapurple;
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
  margin: 2rem;
}
</style>

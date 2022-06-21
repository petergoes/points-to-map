<template>
  <div class="timeline">
    <ul ref="list" class="timeline__list">
      <slot />
    </ul>
  </div>
</template>

<script>
export default {
  mounted() {
    const options = {
      root: this.$refs.list,
      rootMargin: "-40%",
    };

    const handler = (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          this.$emit("change", entry.target.dataset.id);
        }
      });
    };
    const observer = new IntersectionObserver(handler, options);
    this.$refs.list.querySelectorAll(".timeline-item").forEach((child) => {
      observer.observe(child);
    });
  },
};
</script>

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

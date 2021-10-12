<template>
  <div class="hoverlist">
    <li
      class="list-group-item d-flex justify-content-between align-items-start"
    >
      <div class="ms-2 me-auto">
        <div class="fw-bold">{{ item.tags }}</div>

         {{ item.date }} {{ item.where }} {{ item.how }}
      </div>
      <span class="badge bg-primary rounded-pill"> {{ item.amount }}</span>
    </li>
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: {
    item: Object,
  },
};
</script>

<style scoped>
.hoverlist:hover {
  background-color: brown;
}
</style>
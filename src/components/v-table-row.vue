<template>
  <div class="v-table-row">
    <div class="row-name row">{{ row_data.name }}</div>
    <div class="row-earned row">{{ row_data.points_earned }}</div>
    <div class="row-spent row">{{ row_data.points_spent }}</div>
    <div class="row-date row">{{ row_data.registration_date }}</div>
  </div>
</template>


<script>
export default {
  name: "v-table-row",
  props: {
    row_data: {
      type: Object,
      default: () => {
        return {}
      }
    }
  },
  data() {
    return {}
  },
  computed: {}
}
</script>

<style>
.v-table-row {
  display: flex;
    justify-content: space-around;
}
.row{
  display: flex;
  flex-basis: 25%;
  padding: 8px 16px;
}
</style>
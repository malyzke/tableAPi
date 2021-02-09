<template>
  <div class="v-table">
    <div class="v-table__header">
      <p>Name</p>
      <p>Points earned</p>
      <p>Points spent</p>
      <p>Registretion date</p>
    </div>
    <div class="v-table__body">
      <v-table-row
        v-for="row in paginatedUsers"
        :key="row.id"
        :row_data="row"
      />
    </div>
    <div class="v-table__pagination">
      <div class="page"
        v-for="page in pages"
        :key="page"
        :class="{'page__selected': page === pageNumber}"
        @click="pageClick(page)"
      >
      {{page}}
      </div>
    </div>
  </div>
</template>

<script>

import vTableRow from './v-table-row'

export default {
  name: 'v-table',
  components: {
    vTableRow
  },
  props: {
    users_data: {
      type: Array,
      default: () => {
        return []
      }
    }
  },
  data() {
    return {
       usersPerPage: 10,
       pageNumber: 1
      }
    },
  methods: {
    pageClick(page){
      this.pageNumber = page
    }
  },
  computed: {
    pages() {
      return Math.ceil(this.users_data.length / 10)
    },
    paginatedUsers() {
      let from = (this.pageNumber - 1) * this.usersPerPage
      let to = from + this.usersPerPage
      return this.users_data.slice(from, to)
    }
  }
}

</script>

<style>
  .v-table{
    max-width: 900px;
    margin: 0 auto;
  }
 .v-table__header{
   display: flex;
   justify-content: space-around;
   border-bottom: solid #e7e7e7;
    }
  .v-table__header p {
    flex-basis: 25%;
    text-align: left;
  }
  .v-table__pagination {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 30px;
  }
  .page {
    padding: 8px;
    border: solid 1px #e7e7e7;
    margin: 5px;
  }
  .page:hover {
    background: #aeaeae;
    cursor: pointer;
    color: #ffff;
  }
  .page__selected {
    background: #aeaeae;
    cursor: pointer;
    color: #ffff;
  }
</style>
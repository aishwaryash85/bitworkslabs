<template>
  <div class="q-pa-md">
    <div>
      <h5>airlines</h5>
    </div>

    <q-table separator="horizontal" :columns="table.columns" :rows="table.rows">

    </q-table>
  </div>
</template>

<script>
export default {
  data () {
    return {
      table: {
        rows: [
        ],
        columns: [
        { label: "Airline Id", field: "id"},
        { label: "Airline Name", field: "name"},
        { label: "Headquater", field: "head_quaters"},
        { label: "Established", field: "established"},
        { label: "Slogan", field: "slogan"},
        { label: "Country", field: "country"}
        ],
      }
    }
  },
  methods: {
    insertData (data) {
      this.table.rows.push(data)
    },
    async fetchData(){
       let response = await this.$api.get('https://api.instantwebtools.net/v1/airlines')
       this.table.rows = response.data;
    }
  },
  created (){
    this.fetchData()
  },
};
</script>

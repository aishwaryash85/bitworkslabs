<template>
  <div class="q-pa-md">
    <div>
      <h5>parties</h5>
    </div>

    <q-table separator="horizontal" :columns="table.columns" :rows="filteredRows">
    <template v-slot:body-cell-phone_number="props">
    <q-td>
    <q-btn v-if="props.value" flat icon="phone" color="primary" type="a" :label="props.value" :href="'tel:' +props.value">
    </q-btn>
   </q-td>

    </template>

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
          { label: 'Member Card', field: 'member_card' },
          { label: 'Aadhar Number', field: 'aadhar_number' },
          { label: 'First name', field: (row) => row.user_id.first_name},
          { label: 'Phone number', field: (row) => row.user_id.mobile_number, name: 'phone_number'}

        ]
      }
    }
  },
  computed: {
    filteredRows () {
        return this.table.rows.filter((row) => {
        return row.user_id.first_name ? true : false
      })

    }
  },
  methods: {
    insertData (data) {
      this.table.rows.push(data)
    },
    async fetchData(){
      //  this.$api.get('https://dhairya-api.brainysoftwares.com/items/parties').then((response) => {
      //     response.data
      //  })
       let response = await this.$api.get('https://dhairya-api.brainysoftwares.com/items/parties?fields=*.*')

       this.table.rows = response.data.data
    }
  },
  created (){
    this.fetchData()
  }
}

</script>

<template>
  <div class="q-pa-md">
    <div>
      <h5>Accounts</h5>
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
          { label: 'Id', field: 'id' },
          { label: 'Account Name', field: 'account_name' },
          { label: 'Account Number', field: 'account_number'},
          { label: 'Contact Number', field: 'contact_number'},
          { label: 'Email', field: 'email'},
          { label: 'City', field: 'city'},
          { label: 'State', field: 'state'},
          { label: 'Pin Code',field: 'pin_code'},
          { label: 'Country', field: 'country'},
          { label: 'Accounting Receipts', field: 'accounting_receipts'},
          { label: 'Status', field: 'status'},
          { label: 'User Created', field: 'user_created'},
          { label: 'Data Created', field: 'data_created'},
          { label: 'User Udate', field: 'user_updated'},
          { label: 'Data update', field: 'data_updated'},
          { label: 'Invoices', field: 'invoices'},
          { label: 'Contacts', field: 'contacts'},
          { label: 'Log Book', field: 'log_book'},
          { label: 'Contracts', field: 'contracts'},
          { label: 'GST', field: 'gst'}



        ]
      }
    }
  },
  methods: {
    insertData (data) {
      this.table.rows.push(data)
    },
    async fetchData(){
       let response = await this.$api.get('https://gangotri-api.brainysoftwares.com/items/accounts?fields=*.*')
       this.table.rows = response.data.data
    }
  },
  created (){
    this.fetchData()
  }
}

</script>

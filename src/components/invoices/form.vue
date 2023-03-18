<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <form>
    <div class="column">

      <q-input v-model="formData.id" label="ID" />
      <q-select v-model="formData.account_id" label="Account ID" :options="accounts" option-label="account_name"
       option-value="id" map-options emit-value />
      <q-input v-model="formData.invoice_number" label="Invoice number" />
      <q-input v-model="formData.grand_total" label="Grand total" />
      <q-input v-model="formData.invoice_status" label="Invoice status" />
      <q-input v-model="formData.payment_status" label="Payment Status*" />
      <q-input v-model="formData.user_created" label="User created" />
      <q-input v-model="formData.user_updated" label="User Updated" />
      <q-input v-model="formData.date_created" label="Date Created" />
      <q-input v-model="formData.date_updated" label="Date Updated" />
      <q-input v-model="formData.organisation_id" label="Organisation ID" />
      <q-input v-model="formData.invoice_details" label="Invoice Details" />
      <q-input v-model="formData.invoice_settlement" label="Invoice settlment" />
      <q-input v-model="formData.period" label="Period" />
      <q-input v-model="formData.bank_id" label="Bank ID" />
      <q-input v-model="formData.booked_by" label="Booked by" />
      <q-input v-model="formData.oncall_plan" label="Oncall plan" />
      <q-input v-model="formData.vehicle_number" label="Vehicle number" />
      <q-input v-model="formData.log_type" label="Log type" />
      <q-input v-model="formData.journey_date" label="Journey date" />

    </div>
  </form>
    <div class="q-py-md">
      <q-btn color="red" label="submit" @click="submitData"></q-btn>
    </div>
    <div class="q-py-md">
      <q-btn color="red" label="close" to="./"></q-btn>
    </div>
  </q-card>

</template>
<script>


export default {
  data () {
    return {
      formData: {},
      accounts: [],
      organisation: [],
      banks: []
    }
  },
  created () {
    this.fetchAccounts()
    this.fetchOrganisation()
    this.fetchBanks()
  },
  methods: {

   async fetchAccounts(){
      let response = await this.$api.get('items/accounts')
      this.accounts = response.data.data
    },
    async fetchOrganisation() {
      let response = await this.$api.get('items/organisation')
      this.organisation = response.data.data
    },
    async fetchBanks() {
      let response = await this.$api.get('items/banks')
      this.banks = response.data.data
    },
    submitData () {
      console.log('Emitting Event of submitting form with data')
      alert()
      this.$emit('formSubmit', this.formData)
      console.log('Resetting Form')
      alert()
      this.formData = {}
    }
  }
}
</script>

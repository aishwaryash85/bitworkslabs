<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.name" label="Name" />
      <q-input v-model="formData.account" label="Account" />
      <q-input v-model="formData.vehicle_type" label="Vehicle Type" />
      <q-input v-model="formData.rent_per_month" label="Rent Per Month" />
      <q-select v-model="formData.fuel" label="Fuel" :options="['Including', 'Excluding']" />
      <q-input v-model="formData.date_created" label="Date Created" />
      <q-input v-model="formData.data_updated" label="Date Updated" />
      <q-input v-model="formData.log_book" label="Log Book*" />
      <q-toggle v-model="formData.is_tax_included" label="Is Tax Included" :false-value="true"
      :label="'Model is ${redModel} (flipped boolean)'"
      :true-value="false"
      color="primary"
      type="redModel" />
    </div>
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
      accounts:[],
      vehicle_type:[],
      log_book:[]
    }
  },
  created (){
    this.fetchAccounts()
    this.fetchVehicle_type()
    this.fetchLog_book()
  },
  methods: {
    async fetchAccounts(){
      let response = await this.$api.get('items/accounts')
      this.accounts = response.data.data
    },
     async fetchVehicle_type(){
       let response = await this.$api.get('items/vehicle_type')
       this.vehicle_type = response.data.data
     },
     async fetchLog_book(){
      let response = await this.$api.get('items/log_book')
      this.log_book = response.data.data
     },
  methods: {
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
}
</script>

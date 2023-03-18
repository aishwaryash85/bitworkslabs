<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.account_id" label="Account ID" />
      <q-input v-model="formData.vehicle_id" label="Vehicle ID" />
      <q-input v-model="formData.contract_id" label="Contract ID" />
      <q-input v-model="formData.date_from" label="Date from" />
      <q-input v-model="formData.contact_id" label="Contact ID" />
      <q-input v-model="formData.driver_id" label="Driver ID" />
      <q-input v-model="formData.log_type" label="Log type*" />
      <q-input v-model="formDate.date_form" label="Date Form*" />
      <q-input v-model="formData.date_to" label="Date to*" />
      <q-input v-model="formData.rent" label="Rent" />
      <q-input v-model="formData.initial_reading" label="Initial reading" />
      <q-input v-model="formData.final_reading" label="Final reading" />
      <q-input v-model="formData.running_kms" label="Running kms" />
      <q-input v-model="formData.on_call_details" label="On call details" />
      <q-input v-model="formData.extra_kms" label="Extra kms" />
      <q-input v-model="formData.days" label="Days" />
      <q-input v-model="formData.night_halt_charges" label="Night halt charges" />
      <q-input v-model="formData.amount" label="Amount" />
      <q-input v-model="formData.status" label="Status" />
      <q-toggle v-model="formData.is_invoiced" label="Is invoiced" :false-value="true"
      :label="`Model is ${redModel} (flipped boolean)`"
      :true-value="false"
      color="primary"
      type="redModel" />
      <q-toggle v-model="formData.is_paid" label="Is paid" :false-value="true"
      :label="'Model is ${redModel} (flipped boolean)'"
      :true-value="false"
      color="primary"
      type="redModel" />
      <q-input v-model="formData.sort" label="Sort" />

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
      formData: {}
    }
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
</script>

<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.vehicle_no" label="Vehicle No." />
      <q-select v-model="formData.vehicle_type" label="Vehicle type" :options="vehicle_type" option-label="id"
       option-value="id" map-options emit-value />
      <q-input v-model="formData.status" label="Status" :options="['Published','Draft','Archived']"
       option-label="Standard"  />
      <q-input v-model="formData.sort" label="Sort" />
      <q-input v-model="formData.fuel_avg" label="Fuel" />
      <q-input v-model="formData.log_book" label="Log book" />


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
      vehicle_type: []
    }
  },
  created(){
    this.fetchVehicle
  },
  methods: {

    async fetchVehicle(){
      let response = await this.$api.get('items/vehicle_type')
      this.vehicle_type = response.data.data
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

<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.item_id" label="Item ID" />
      <q-input v-model="formData.rate" :rules="[validationRequired, validationcharacters]" label="Rate" />
      <q-input v-model="formData.quantity" mask="####" label="Quantity*" :rules="[val => !!val || 'Quantity is required']" />
      <q-input v-model="formData.amount" :rules="[validationRequired, validationcharacters]" label="Amount*" />
      <q-input v-model="formData.tax_rate" label="Tax Rate" />
      <q-input v-model="formData.tax_amount" label="Tax amount" />
      <q-input v-model="formData.total_amount" label="Total amount" />
      <q-input v-model="formData.status" label="Status" />
      <q-input v-model="formData.invoice_id" label="Invoice ID" />
      <q-input v-model="formData.description" label="Description" />

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
    validationRequired(val) {
      if(val.length <= 10) {
        return true
      } else {
        return 'plz use maximum 10 characters'
        return
      }
       return val ? true : 'plz use maximum 10 characters'
    },
    validationcharacters(val) {
      let patternResult = val.match(/[a-z]/i)
      if(patternResult === null) {
        return true
      } else {
        return 'characters not allowed'
      }

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

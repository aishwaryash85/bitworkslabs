<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.organisation_name" label="Organisation Name" />
      <q-input v-model="formData.prefix" label="Prefix*" />
      <q-input v-model="formData.description" label="Description" />
      <q-input v-model="formData.address" label="Address" filledtype="textarea"/>
      <q-input v-model="formData.city" :rules="[validationRequired, validationcharacters, validationspecialcharacters]" label="City" />
      <q-input v-model="formData.state" label="State" />
      <q-input v-model="formData.pin_code" :rules="[validationnumbers]" label="Pin code" />
      <q-input v-model="formData.contact_number" label="Contact" />
      <q-input v-model="formData.email" :rules="[]" label="Email" />
      <q-input v-model="formData.gst_number" label="GST number" />
      <q-input v-model="formData.pan_no" label="PAN no" />
      <q-input v-model="formData.invoices" label="Invoices" />
      <q-select clearable v-model="formData.status" label="status" :options="['Public','Draft','Archieved']" />
       <q-input v-model="formData.banks" label="banks" />
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
      }
    },
    validationcharacters(val) {
      let patternResult = val.match(/[0-9]/i)
      if(patternResult === null) {
        return true
      } else {
        return 'Number not allowed'
      }
    },
    validationspecialcharacters(val) {
      let patternResult = val.match(/[\W]/i)
      if(patternResult === null) {
        return true
      } else {
        return 'special characters not allowed'
      }

    },
    validationnumbers(val) {
     let patternResult = val.match(/[a-z]/i)
     if(patternResult === null) {
      return true
      } else {
        return 'alphabets not allowed'
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

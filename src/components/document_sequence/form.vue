<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.date_created" label="Date Created" />
      <q-input v-model="formData.organisation_id" label="Organisation Id" />
      <q-input v-model="formData.document_type" label="Document  Type*" />
      <q-input v-model="formData.sequence_no" label="Sequence No" />

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
      organisation:[]
    }
  },
  created() {
    this.fetchOrganisation()
  },
  methods: {
    async fetchOrganisation() {
      let response = await this.$api.get('items/organisation')
      this.organisation = response.data.data
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

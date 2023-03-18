<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.item_name" label="Item Name*" />
      <q-input v-model="formData.item_type" label="Item type" />
      <q-input v-model="formData.status" label="Status" />
      <q-input v-model="formData.user_created" label="User created" />
      <q-input v-model="formData.user_updated" label="User Updated" />
      <q-input v-model="formData.date_created" label="Date Created" />
      <q-input v-model="formData.date_updated" label="Date Updated" />

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

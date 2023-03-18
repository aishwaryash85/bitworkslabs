<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-select v-model="formData.account_id" label="Account ID" :options="accounts" option-label="account_id"
      option-value="id" map-options emit-value />
    <q-input filled v-model="formData.receipt_date" label="Receipt Date*" mask="date">
     <template v-slot:append>
        <q-icon name="event" class="cursor-pointer">
          <q-popup-proxy cover transition-show="scale" transition-hide="scale">
            <q-date v-model="date">
              <div class="row items-center justify-end">
                <q-btn v-close-popup label="Close" color="primary" flat />
              </div>
            </q-date>
          </q-popup-proxy>
        </q-icon>
      </template>
    </q-input>
      <q-input v-model="formData.receipt_number" mask="#" reverse-fill-mask label="Receipt Number*"  :rules="[val => !!val || 'Field is required']" />
      <q-select v-model="formData.receipt_mode" label="Receipt Mode*" :options="['Cheque','Cash','Bank transfer','UPI']" :rules="[val => !! val|| 'Receipt mode required']"
       option-label="Standard"  />
      <q-input v-model="formData.receipt_amount" mask="#" reverse-fill-mask label="Receipt Amount*" :rules="[val => !!val || 'Receipt Amount is required']" />
      <q-input v-model="formData.transaction_number" label="Transaction Number" />
      <q-select v-model="formData.receipt_status" label="Receipt Status" :options="['Received', 'Cleared', 'Declined']"/>
      <q-input v-model="formData.receipt_settlement" label="Receipt Setttlement" />

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
      accounts:[]
    }
  },
  created (){
    this.fetchAccounts()

  },
  methods: {
    async fetchAccounts(){
      let response = await this.$api.get('items/accounts')
      this.accounts = response.data.data
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

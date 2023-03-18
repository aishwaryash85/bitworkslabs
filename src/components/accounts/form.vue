<template>
  <q-card class="q-pa-md q-ma-md">
    {{ formData }}
    <div class="column">
      <q-input v-model="formData.id" label="ID" />
      <q-input v-model="formData.account_name" mask="S" reverse-fill-mask label="Account Name*" :rules="[val => !!val || 'Name is required']" />
      <q-input v-model="formData.account_address" label="Account Address*" type="text" :rules="[val => !!val || 'Address is required']" />
      <q-input v-model="formData.contact_number" label="Contact Number" />
      <q-input v-model="formData.email" type="email" value="@gmail.com" pattern="[a-z]{0,}" label="Email" :rules="[val => !!val || 'email is missing']" />
      <q-input v-model="formData.city" mask="S" reverse-fill-mask label="City" />
      <q-input v-model="formData.state" mask="S" reverse-fill-mask label="State" />
      <q-input v-model="formData.pin_code" mask="######" label="Pin Code" />
      <q-input v-model="formData.country" mask="N" reverse-fill-mask label="Country" />
      <q-input v-model="formData.accounting_receipts" label="Accounting Receipts" />
      <q-select v-model="formData.status" label="Status" :options="['Published','Draft','Archived']"
       option-label="Standard"  />
      <q-input v-model="formData.user_created" stack-label label="User Created" type="date" />
      <q-input v-model="formData.invoices" label="Invoices" />
      <q-input v-model="formData.contacts" mask="#" reverse-fill-mask label="Contacts" />
      <q-input v-model="formData.log_book" label="Log Book" />
      <q-input v-model="formData.contracts" label="Contracts" />
      <q-input  v-model="formData.gst" mask="## AAAAA####A # A #" label="GST" />
      <q-input v-model="formData.date_created" label="Date Created" >
      <template v-slot:prepend>
      <q-icon name="schedule" class="cursor-pointer">
      <q-popup-proxy cover transition-show="scale" transition-hide="scale">
      <q-time v-model="formData.date_created" mask="YYYY-MM-DD HH:mm">
      <div class="row items-center justify-end">
      <q-btn v-close-popup label="close" color="red" flat />
      </div>
      </q-time>
      </q-popup-proxy> </q-icon>
      </template>
      <template v-slot:append>
      <q-icon name="event" class="cursor-pointer">
      <q-popup-proxy cover transition-show="scale" transition-hide="scale">
      <q-date v-model="formData.date_created" mask="YYYY-MM-DD HH:mm">
      <div class="row items-center  justify-end">
      <q-btn v-close-popup label="close" color="teal" flat/>
      </div>
      </q-date>
      </q-popup-proxy>
      </q-icon>
      </template>
      </q-input>
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

<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Accounting Settlement',
    caption: '',
    icon: '',
    link: '/modules/accounting_settlements/'
  },
  {
    title: 'Accounting Receipts ',
    caption: '',
    icon: 'heart',
    link: '/modules/accounting_receipts/'
  },
  {
    title: 'accounting taxes',
    caption: '',
    icon: 'directions',
    link: '/modules/accounting_taxes/'
  },
  {
    title: 'Accounts',
    caption: '',
    icon: 'school',
    link: '/modules/accounts/'
  },
  {
    title: 'Banks',
    caption: '',
    icon: 'house',
    link: '/modules/banks/'
  },
  {
    title: 'Contracts',
    caption: '',
    icon: 'directions',
    link: '/modules/contracts/'
  },
  {
    title: 'contacts',
    caption: '',
    icon: 'directions',
    link: '/modules/contacts/'
  },
  {
    title: 'Driver',
    caption: '',
    icon: 'vehicle',
    link: '/modules/driver/'
  },
  {
    title: 'Document Sequence',
    caption: '',
    icon: ' ',
    link: '/modules/document_sequence/'
  },
  {
    title: 'Items',
    caption: '',
    icon: 'book',
    link: '/modules/items/'
  },
  {
    title: 'Invoices',
    caption: '',
    icon: 'coffee',
    link: '/modules/invoices/'
  },
  {
    title: 'Invoice Details',
    caption: '',
    icon: 'Account Circle',
    link: '/modules/invoice_details/'
  },
  {
    title: 'Log Book',
    caption: '',
    icon: 'money',
    link: '/modules/log_book/'
  },
  {
    title: 'organisation',
    caption: '',
    icon: 'Building',
    link: '/modules/organisation/'
  },
  {
    title: 'vehicles',
    caption: '',
    icon: ' ',
    link: '/modules/vehicles/'
  },
  {
    title: 'Vehicle Types',
    caption: '',
    icon: ' ',
    link: '/modules/vehicle_type/'
  },


]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

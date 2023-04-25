<template>
  <div class="q-pa-md" style="max-width: 400px">

    <q-form @submit="onSubmit()" class="q-gutter-md">
      <q-input filled v-model="email" label="Email *" hint="Gmail only for now" lazy-rules
        :rules="[val => val && val.length > 0 || 'Please type your email']" />

      <q-input filled v-model="password" label="Password *" lazy-rules :rules="[
          val => val !== null && val !== '' || 'Please type your password',
        ]" />

      <q-input filled v-model="host" label="Host *" hint="default for gmail is imap.gmail.com" lazy-rules
        :rules="[val => val && val.length > 0 || 'Please type imap host']" />

      <q-input filled v-model="port" label="Port *" hint="port for gmail is 993" lazy-rules
        :rules="[val => val && val.length > 0 || 'Please type imap port']" />

      <div>
        <q-btn label="Submit" type="submit" color="primary" />
      </div>
    </q-form>

  </div>
</template>
<script>
import axios from 'axios';
import { defineComponent } from 'vue'

export default defineComponent({
  data: () => ({
    email: '',
    password: '',
    host: '',
    port: ''
  }),

  //   "email": tgemailbot@gmail.com
  //   "password": kwmknsckbqimhnrw
  //   "host": imap.gmail.com
  //   "port": 993

  methods: {
    onSubmit() {
      axios.post(`http://localhost:3000/listen`, {
        'email': this.email,
        'password': this.password,
        'host': this.host,
        'port': this.port
      })
    }
  },

  name: 'IndexPage'
})
</script>

<template>
  <form ref="root" @submit.prevent="submit">
    <input class="honeypot" v-model="honeypot"/>
    <label>Name:<input type="text" v-model="form.name" required/></label>
    <label>Email:<input type="email" v-model="form.email" required/></label>
    <label>Message:<textarea v-model="form.message" required/></label>
    <button type="submit">Send</button>
  </form>
</template>

<script>
import axios from 'axios'
import qs from 'qs'

export default {
  data () {
    return {
      honeypot: '',
      form: {
        'form-name': 'contact',
        name: '',
        email: '',
        message: ''
      }
    }
  },
  methods: {
    submit () {
      if (this.honeypot !== '') return
      axios.post(this.$refs.root.action, qs.stringify(this.form))
        .then(() => {
          alert('Thank you!')
        })
    }
  }
}
</script>

<style>
.honeypot {
  border: 0;
  padding: 0;
  display: block;
  width: 0;
  height: 0;
  appearance: none;
}
label {
  display: block;
}
button {
  display: block;
}
</style>

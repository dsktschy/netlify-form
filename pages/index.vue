<template>
  <form ref="root" @submit.prevent="submit">
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
      axios.post(this.$refs.root.action, qs.stringify(this.form))
        .then(() => {
          alert('Thank you!')
        })
    }
  }
}
</script>

<style>
label {
  display: block;
}
button {
  display: block;
}
</style>

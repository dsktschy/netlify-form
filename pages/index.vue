<template>
  <form ref="root" @submit.prevent="submit" netlify netlify-honeypot="honeypot" name="contact">
    <input class="honeypot" name="honeypot"/>
    <label>Name:<input type="text" name="name" required/></label>
    <label>Email:<input type="email" name="email" required/></label>
    <label>Message:<textarea name="message" required/></label>
    <button type="submit">Send</button>
  </form>
</template>

<script>
import axios from 'axios'
import qs from 'qs'

export default {
  methods: {
    submit ({ target }) {
      if (target.honeypot.value !== '') return
      axios.post(target.action, qs.stringify({
        'form-name': target.getAttribute('name'),
        name: target.name.value,
        email: target.email.value,
        message: target.message.value
      }))
        .then(() => { alert('Thank you!') })
        .catch((err) => { throw err })
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

<template>
  <form name="contact" method="post" netlify>
    <input type="hidden" name="form-name" value="contact"/>
    <label>Name <input type="text" name="name"/></label>
    <label>Email <input type="email" name="email"/></label>
    <button type="submit">Send</button>
  </form>
</template>

<style>
label {
  display: block;
}
button {
  display: block;
}
</style>

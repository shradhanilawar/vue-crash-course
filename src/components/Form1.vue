<template>
    <div class="px-5">
      <form @submit.prevent="handleSubmit">
        <div class="mb-3">
          <label for="email" class="form-label">Email address</label>
          <input type="email" class="form-control" id="email" aria-describedby="emailHelp" v-model="form.email">
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input type="password" class="form-control" id="password" v-model="form.password">
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
        <button type="reset" class="btn btn-primary mx-5">Reset</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        form: {
          email: '',
          password: '',
        },
      };
    },
    methods: {
      async handleSubmit() {
        const payload = {
          username: this.form.email,
          password: this.form.password,
        };
  
        try {
          const response = await axios.post('http://localhost:3000/login', payload);
  
          if (response.status === 200) {
            alert('Form submitted successfully!');
          }
        } catch (error) {
          console.error('Error submitting form:', error);
          alert('There was an error submitting the form. Please try again.');
        }
      },
    },

  };
  </script>
  
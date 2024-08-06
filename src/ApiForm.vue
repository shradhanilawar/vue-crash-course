<template>
  <div class="container-fluid">
    <div class="header">
      <h4>Create An API</h4>
      <h6>Create an API by providing the following details.</h6>
    </div>
    <form @submit.prevent="handleSubmit">
      <section class="section">
        <h5 class="divider">API Details</h5>
        <div class="form-check form-check-inline">
          <input class="form-check-input" type="radio" name="inlineRadioOptions" value="Two" v-model="form.apiType">
          <label class="form-check-label">Create New API</label>
        </div>
        <div class="form-check form-check-inline">
          <input class="form-check-input" type="radio" name="inlineRadioOptions" value="Two" v-model="form.apiType">
          <label class="form-check-label"> Existing API</label>
        </div>
        <div class="row">
          <div class="col-3">
            <FormInput label="API Name" v-model="form.apiName" placeholder="Enter API Name" />
          </div>
          <div class="col-3">
            <FormSelect label="Version" v-model="form.version" :options="versions" placeholder="Select Version" />
          </div>
          <div class="col-3">
            <FormSelect label="API Exposure" v-model="form.apiExposure" :options="apiExposures"
              placeholder="Select API Exposure" />
          </div>
          <div class="col-3">
            <FormInput label="API Owner" v-model="form.apiOwner" placeholder="Enter API Owner" />
          </div>
          <div class="col-3">
            <FormInput label="Domain" v-model="form.domain" placeholder="Enter Domain" />
          </div>
        </div>
      </section>
      <section class="section mt-4">
        <h5 class="divider">Provider Details</h5>
        <div class="row">
          <div class="col-3">
            <FormInput label="Provider Name" v-model="form.providerName" placeholder="Enter Provider Name" />
          </div>
          <div class="col-3">
            <FormInput label="Platform Reviewer" v-model="form.platformReviewer"
              placeholder="Enter Platform Reviewer" />
          </div>
        </div>
      </section>
      <section class="section mt-4">
        <h5 class="divider">Consumer Details</h5>
        <div class="row">
          <div class="col-3">
            <FormInput label="Consumer Name" v-model="form.consumerName" placeholder="Enter Consumer Name" />
          </div>
          <div class="col-3">
            <FormInput label="Platform Reviewer" v-model="form.platformReviewer1"
              placeholder="Enter Platform Reviewer" />
          </div>
          <div class="col-3">
            <FormInput label="Tags" v-model="form.tags" placeholder="Enter Tags" />
          </div>
          <div class="col-3">
            <FormTextarea label="Description" v-model="form.description" placeholder="Enter Description" />
          </div>
        </div>
      </section>
      <div class="buttons">
        <button type="submit" class="btn btn-primary">Submit</button>
        <button type="reset" class="btn btn-secondary mx-5">Reset</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
import FormInput from './components/FormInput.vue';
import FormSelect from './components/FormSelect.vue';
import FormTextarea from './components/FormTextArea.vue'

export default {
  components: {
    FormInput,
    FormSelect,
    FormTextarea,
  },
  data() {
    return {
      form: {
        apiType: '',
        apiName: '',
        version: '',
        apiExposure: '',
        apiOwner: '',
        domain: '',
        providerName: '',
        platformReviewer: '',
        consumerName: '',
        platformReviewer1: '',
        tags: '',
        description: '',
      },
      versions: [
        { value: '1', text: '1.0' },
        { value: '2', text: '2.0' },
        { value: '3', text: '3.0' },
      ],
      apiExposures: [
        { value: '1', text: 'One' },
        { value: '2', text: 'Two' },
        { value: '3', text: 'Three' },
      ],
    };
  },
  methods: {
    async handleSubmit() {
      console.log(this.form);

      try {
        const response = await axios.post('http://localhost:3000/login', this.form);

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

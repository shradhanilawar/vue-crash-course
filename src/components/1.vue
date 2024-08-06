<style scoped>
h6 {
    font-weight: lighter;
}

.divider {
    display: flex;
    align-items: center;
}

.divider::after {
    flex: 1;
    content: '';
    padding: 1px;
    background-color: black;
    opacity: 0.1;
    margin: 5px;
}
</style>
<template>
    <div class="px-5 ">
        <div class="mt-3">
            <h4>Create An API</h4>
            <h6>Create an API by providing the following details.</h6>
        </div class="mt-6">

        <div class="mt-3">
            <form @submit.prevent="handleSubmit">
                <div>
                    <h5 class="divider">API Details</h5>
                    <div></div>

                    <input type="radio" id="one" value="One" name="flexRadioDefault" />
                    <label for="one"> Create New API</label>
                    &nbsp;&nbsp;&nbsp;
                    <input type="radio" id="two" value="Two" name="flexRadioDefault" />
                    <label for="two"> Existing API</label>
                    <div class="col-3 "> </div>
                    <div class="row mt-2">

                        <div class="col-3 ">
                            <label class="form-label">API Name</label>
                            <input type="text" class="form-control" placeholder="Enter API Name" v-model="form.apiName">
                        </div>
                        <div class="col-3"><label class="form-label">Version</label>
                            <select class="form-select" aria-label="Small select example" v-model="form.version">
                                <option value="undefined" disabled>Select Version</option>
                                <option value="1">1.0</option>
                                <option value="2">2.0</option>
                                <option value="3">3.0</option>
                            </select>
                        </div>
                        <div class="col-3"><label class="form-label">API Exposure</label>
                            <select class="form-select" aria-label="Small select example" v-model="form.apiExposure">
                                <option value="undefined" disabled>Select API Exposure</option>
                                <option value="1">One</option>
                                <option value="2">Two</option>
                                <option value="3">Three</option>
                            </select>
                        </div>
                        <div class="col-3"><label class="form-label">API Owner</label>
                            <input type="text" class="form-control" placeholder="Enter API Owner"
                                v-model="form.apiOwner">
                        </div>
                    </div>
                    <div class="row">
                        <div class="col-3">
                            <label class="form-label">Domain</label>
                            <input type="text" class="form-control" placeholder="Enter Domain" v-model="form.domain">
                        </div>
                    </div>
                </div>
                <div class="mt-3">
                    <h5 class="divider">Provider Details</h5>
                    <div class="row mt-2">
                        <div class="col-3">
                            <label class="form-label">Provider Name</label>
                            <input type="text" class="form-control" placeholder="Enter Provider Name"
                                v-model="form.providerName">
                        </div>
                        <div class="col-3">
                            <label class="form-label">Platform Reviewer</label>
                            <input type="text" class="form-control" placeholder="Enter Platform Reviewer"
                                v-model="form.platformReviewer">
                        </div>
                    </div>
                </div>
                <div class="mt-3">
                    <h5 class="divider">Consumer Details</h5>
                    <div class="row mt-2">
                        <div class="col-3">
                            <label class="form-label">Consumer Name</label>
                            <input type="text" class="form-control" placeholder="Enter Consumer Name"
                                v-model="form.consumerName">
                        </div>
                        <div class="col-3">
                            <label class="form-label">Platform Reviewer</label>
                            <input type="text" class="form-control" placeholder="Enter Platform Reviewer"
                                v-model="form.platformReviewer1">
                        </div>
                        <div class="col-3">
                            <label class="form-label">Tags</label>
                            <input type="text" class="form-control" placeholder="Enter Tags" v-model="form.tags">
                        </div>
                        <div class="col-3">
                            <label class="form-label">Description</label>
                            <textarea class="form-control" rows="3" placeholder="Enter Description"
                                v-model="form.description"></textarea>
                        </div>
                    </div>
                </div>
                <button type="submit" class="btn btn-primary">Submit</button>
        <button type="reset" class="btn btn-primary mx-5">Reset</button>
            </form>
        </div>
        
    </div>
    
</template>


<script>
import axios from 'axios';
export default {
    data() {
        return {
            form: {
                // apiName: '',
                // version: '',
                // apiExposure: '',
                // apiOwner:'',
                // domain: '',
                // providerName: '',
                // platformReviewer: '',
                // consumerName: '',
                // platformReviewer1: '',
                // tags: '',
                // description: '',
                apiName: 'aa',
                version: 'bb',
                apiExposure: 'cc',
                apiOwner:'d',
                domain: 'e',
                providerName: 'f',
                platformReviewer: 'gg',
                consumerName: 'h',
                platformReviewer1: 'i',
                tags: 'y',
                description: 'z'
            },
        };
    },
    methods: {
        async handleSubmit() {
            const payload = {
                apiName: this.form.apiName,
                version: this.form.version,
                apiExposure: this.form.apiExposure,
                apiOwner: this.form.apiOwner,
                domain: this.form.domain,
                providerName: this.form.providerName,
                platformReviewer: this.form.platformReviewer,
                consumerName: this.form.consumerName,
                platformReviewer1: this.form.platformReviewer1,
                tags: this.form.tags,
                description: this.form.description

            };
            console.log(payload);
            

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

}

</script>

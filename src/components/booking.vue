<template>
    <div>
        	                <h4>Book a ticket</h4>
	                <section>
                    	<div class="form-row">
							<div class="form-holder">
								<input type="text" v-model="bvn" class="form-control" placeholder="BVN :" maxlength="11">
							<div class="form-holder" v-show="showLoading">
								<p style="display: block">Please wait... </p>
							</div>
							</div>
						</div>
						<div v-if="data.firstName">
              <div class="form-row">
							<div class="form-holder">
								<input type="text" class="form-control" v-model="data.firstName" disabled="disabled" placeholder="First Name :">
							</div>
							<div class="form-holder">
								<input type="text" class="form-control" v-model="data.lastName" disabled="disabled" placeholder="Last Name :">
							</div>
						</div>
						<div class="form-row">
							<div class="form-holder">
								<input type="text" class="form-control" v-model="data.phoneNumber" disabled="disabled" placeholder="Phone :">
							</div>
							<div class="form-holder">
								<input type="email" v-model="data.email" class="form-control" placeholder="Mail :" required>
							</div>
						</div>
						</div>
						<div class="form-row">
							<div class="form-holder w-100">
								<input type="text" v-model="data.address" class="form-control" placeholder="Address :" required>
							</div>
						</div>
						<div class="form-row mb-21">
							<div class="form-holder w-100">
								<textarea v-model="data.requests" class="form-control" style="height: 79px;" placeholder="Special Requirements :"></textarea>
							</div>
						</div>
	                    <div class="checkbox">
							<label>
								<input type="checkbox" checked> I have read and accept the <a href="https://flutterwave.com/terms-of-service/">terms and conditions.</a>
								<span class="checkmark"></span>
							</label>
						</div>
	                    <button @click="$emit('next', {...secondPageData, ...data})" class="forward" style="width: 195px; margin-top: 44px;">Proceed to Pay
							<i class="zmdi zmdi-long-arrow-right"></i>
						</button>
	                </section>

    </div>
</template>

<script>
import axios from 'axios'
window.ax = axios
export default {
	props: ['secondPageData'],
  data() {
    return {
			error: "",
			showLoading: false,
			data: {
        firstName: "",
        lastName: "",
				phoneNumber: ""
			},
      bvn: "",
      page: 1
    };
  },
  methods: {
    getBVNDetails: function(param) {
			this.showLoading = true
      axios.get(
        "https://ravesandboxapi.flutterwave.com/v2/kyc/bvn/"+param+"?seckey=FLWSECK-5dac71a1067333bafcaabb070ad63d04-X"
      )
        .then((res) => {
          this.data.firstName = res.data.data.first_name;
          this.data.lastName = res.data.data.last_name;
					this.data.phoneNumber = res.data.data.phone_number;
					this.showLoading = false;
        })
        .catch(err => {
					this.error = err;
					this.showLoading =false;
        });
    }
	},
	watch: {
		bvn (val) {
			if(val.length>10) {
				this.getBVNDetails(this.bvn)
			} 
		}
	}   
}
</script>

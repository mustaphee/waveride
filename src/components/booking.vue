<template>
    <div>
        	                <h4>Book a ticket</h4>
	                <section>
                    	<div class="form-row">
							<div class="form-holder">
								<input type="text" v-model="bvn" class="form-control" placeholder="BVN :" ref="HHH">
							</div>
						</div>
						<div v-if="data">
              <div class="form-row">
							<div class="form-holder">
								<input type="text" class="form-control" v-model="data.firstName" placeholder="First Name :">
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
								<input type="text" class="form-control" placeholder="Mail :">
							</div>
						</div>
						</div>
						<div class="form-row">
							<div class="form-holder w-100">
								<input type="text" class="form-control" placeholder="Address :">
							</div>
						</div>
						<div class="form-row mb-21">
							<div class="form-holder w-100">
								<textarea name="" id="" class="form-control" style="height: 79px;" placeholder="Special Requirements :"></textarea>
							</div>
						</div>
	                    <div class="checkbox">
							<label>
								<input type="checkbox"> I have read and accept the <a href="#">terms and conditions.</a>
								<span class="checkmark"></span>
							</label>
						</div>
	                    <button @click="$emit('next')" class="forward" style="width: 195px; margin-top: 44px;">{{bvn}}
							<i class="zmdi zmdi-long-arrow-right"></i>
						</button>
	                </section>

    </div>
</template>

<script>
export default {
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
			error: "",
			data: {
        firstName: "",
        lastName: "",
        phoneNumber: "",
			},
      bvn: "fdg",
      date: new Date().toLocaleString(),
      page: 1
    };
  },
  methods: {
    getBVNDetails: function(param) {
      fetch(
        "https://ravesandboxapi.flutterwave.com/v2/kyc/bvn/{param}?seckey=FLWSECK-5dac71a1067333bafcaabb070ad63d04-X"
      )
        .then(res => {
          this.data.firstName = res.data.first_name;
          this.data.lastName = res.data.last_name;
          this.data.phoneNumber = res.data.phone;
        })
        .catch(err => {
          this.error = err;
        });
    }
  },    
}
</script>

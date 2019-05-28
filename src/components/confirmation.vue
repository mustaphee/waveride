<template>
    <div>
        	                <h4>Confirmation</h4>
	                <section class="section-style">
						<div class="board-wrapper">
                			<div class="board-inner">
                				<div class="board-item">
                					Date :
                					<span>{{dateAndTime}}</span>
                				</div>
                				<div class="board-item">
                					Take-off Time :
                					<span>{{thirdPageData.time}}</span>
                				</div>
                				<div class="board-item">
                					Trip :
                					<span>{{thirdPageData.source + ' to '+ thirdPageData.destination}}</span>
                				</div>
                			</div>
                		</div>
                		<div class="pay-wrapper">
                			<div class="bill">
	                			<div class="bill-cell">
	                				<div class="bill-item">
		            					<div class="bill-unit">
		            						Ride charges:  <span>{{thirdPageData.type}}</span>
		            					</div>
		            					<span class="price">N{{typeVAT}}</span>
		            				</div>
	                				<div class="bill-item">
		            					<div class="bill-unit">
		            						Base Fee:
		            					</div>
		            					<span class="price">N{{thirdPageData.price}}</span>
		            				</div>
	                			</div>
	            				
	                			<div class="bill-cell">
	                				<div class="bill-item vat">
		            					<div class="bill-unit">
		            						App commision 20% :
		            					</div>
		            					<span class="price">{{(thirdPageData.price + typeVAT)*0.2}}</span>
		            				</div>
		            				<div class="bill-item total-price">
		            					<div class="bill-unit">
		            						Total Price :
		            					</div>
		            					<span class="price">{{thirdPageData.price+typeVAT+(thirdPageData.price + typeVAT)*0.2}}</span>
		            				</div>
		            				<div class="checkbox-circle">
										<label>
											<input type="radio" name="payment" value="Remember card" checked> Remember Card<br>
											<span class="checkmark"></span>
										</label>
									</div>
	                			</div>
	            			</div>
							<form>
								<button @click="payWithRave" style="width: 195px; margin-top: 45px;">Pay Now
								<i class="zmdi zmdi-long-arrow-right"></i>
							</button>
							</form>
	            			
                		</div>
	                </section>
    </div>
</template>
<script>
const API_publicKey = 'FLWPUBK-c55c9ebf551cd425db012c52b5913be1-X';
export default {
	props: ['thirdPageData'],
	data() {
	  return {
		typeVAT: '',
		dateAndTime: (new Date()).toLocaleString()
	  }
	},
	methods: {
	  getType(){
		  let carType = this.thirdPageData.type
		  if (carType === 'Salon Car'){
			  this.typeVAT = 200
		  }
		  else if (carType === 'Jeep'){
			  this.typeVAT = 350
		  }
		  else if (carType === 'Minivan'){
			  this.typeVAT = 250
		  }
		  else {
			  this.typeVAT = 100
		  }
	  },
	  payWithRave(event) {
			  event.preventDefault();
        let x = getpaidSetup({
            PBFPubKey: API_publicKey,
            customer_email: this.thirdPageData.email,
            amount: this.thirdPageData.price+this.typeVAT+(this.thirdPageData.price + this.typeVAT)*0.2,
            currency: "NGN",
            txref: "rave-123456",
            subaccounts: [
              {
                id: "RS_04129E2A7B928AE4A0CFB4E1AD3DCBD2"
              }
            ],
            meta: [{
                metaname: "flightID",
                metavalue: "AP1234"
            }],
            onclose: function() {},
            callback: function(response) {
                var txref = response.tx.txRef; // collect flwRef returned and pass to a 					server page to complete status check.
                console.log("This is the response returned after a charge", response);
                if (
                    response.tx.chargeResponseCode == "00" ||
                    response.tx.chargeResponseCode == "0"
                ) {
					// redirect to a success page
					console.log('Success')
                } else {
					// redirect to a failure page.
					console.log('error here oo')
                }

                x.close(); // use this to close the modal immediately after payment.
            }
        });
    }
	},
	mounted() {
		this.getType()
	}
}
</script>


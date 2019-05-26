<template>
    <div>
        	                <h4>Confirmation</h4>
	                <section class="section-style">
						<div class="board-wrapper">
                			<div class="board-inner">
                				<div class="board-item">
                					Date :
                					<span> 25-12-2019</span>
                				</div>
                				<div class="board-item">
                					Take-off Time :
                					<span>7:00am to 8:00am</span>
                				</div>
                			</div>
                		</div>
                		<div class="pay-wrapper">
                			<div class="bill">
	                			<div class="bill-cell">
	                				<div class="bill-item">
		            					<div class="bill-unit">
		            						Ride Type :  <span>Car</span>
		            					</div>
		            					<span class="price">N800</span>
		            				</div>
		            				<div class="bill-item people">
		            					<div class="bill-unit">
		            						Comfort : <span>Luxury</span>
		            					</div>
		            					<div class="bill-unit">
		            						Children : <span>0</span>
		            					</div>
		            				</div>
	                			</div>
	            				<!-- <div class="bill-cell" style="margin-bottom: 13px">
	                				<div class="bill-item">
		            					<div class="bill-unit">
		            						Room 2 :  <span>Luxury Room</span>
		            					</div>
		            					<span class="price">$23</span>
		            				</div>
		            				<div class="bill-item people">
		            					<div class="bill-unit">
		            						Adult : <span>4</span>
		            					</div>
		            					<div class="bill-unit">
		            						Children : <span>1</span>
		            					</div>
		            				</div>
		            				<div class="bill-item service">
		            					<div class="bill-unit">
		            						Rooms & Services :
		            					</div>
		            					<span class="price">$80</span>
		            				</div>
	                			</div> -->
	                			<div class="bill-cell">
	                				<div class="bill-item vat">
		            					<div class="bill-unit">
		            						App commision 10% :
		            					</div>
		            					<span class="price">N800</span>
		            				</div>
		            				<div class="bill-item total-price">
		            					<div class="bill-unit">
		            						Total Price :
		            					</div>
		            					<span class="price">N1200</span>
		            				</div>
		            				<div class="checkbox-circle">
										<label>
											<input type="radio" name="payment" value="Remember card" checked> Remember Card<br>
											<span class="checkmark"></span>
										</label>
									</div>
	                			</div>
	            			</div>
	            			<button @click="$emit('next')" style="width: 195px; margin-top: 45px;">Confirmation
								<i class="zmdi zmdi-long-arrow-right"></i>
							</button>
                		</div>
	                </section>
    </div>
</template>

<script>
export default {
    
}
</script>


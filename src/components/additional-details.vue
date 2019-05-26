<template>
<div>
    <h4>Additional details</h4>
	                <section class="section-style">
                		<div class="board-wrapper">
                			<div class="board-inner">
                				<div class="board-item">
                					Ride Location :
                					<span>Lekki to Ikeja</span>
                				</div>
                				<div class="board-item">
                					Take off time :
                					<span>7:00am to 8:00am</span>
                				</div>
                				<div class="board-item">
                						Ride Type :
                						<span>Salon Car</span>
                					</div>
                				<div class="board-item" id="bol">
                						Estimated cost :
                						<span>N1200</span>
                					</div>
                					
                			</div>
                		</div>
                		<div class="form-wrapper">
                			<div class="form-group">
                				<label for="">Room 1 :</label>
	                			<div class="form-row">
									<div class="select mr-20">
										<div class="form-holder">
											<div class="select-control">1 Adult</div>
											<span class="lnr lnr-chevron-down"></span>
										</div>
										<ul class="dropdown">
											<li rel="1 Adult">1 Adult</li>
											<li rel="2 Adults">2 Adults</li>
											<li rel="3 Adults">3 Adults</li>
										</ul>
									</div>

									<div class="select">
										<div class="form-holder">
											<div class="select-control">No Child</div>
											<span class="lnr lnr-chevron-down"></span>
										</div>
										<ul class="dropdown">
											<li rel="1 Room">No Child</li>
											<li rel="1 Child">1 Child</li>
											<li rel="2 Children">2 Children</li>
											<li rel="3 Children">3 Children</li>
										</ul>
									</div>
	                			</div>
                			</div>
	                		<button class="forward" @click="$emit('next')">Proceed to Pay
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

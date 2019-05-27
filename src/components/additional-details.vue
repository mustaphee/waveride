<template>
  <div>
    <h4>Additional details</h4>
    <section class="section-style">
      <div class="board-wrapper">
        <div class="board-inner">
          <div class="board-item">
            Ride Location :
            <span>{{data.source}} to {{data.destination}}</span>
          </div>
          <div class="board-item">
            Take off time :
            <span>{{firstPageData.time}}</span>
          </div>
          <div class="board-item">
            Ride Type :
            <span> {{firstPageData.type}} </span>
          </div>
          <div class="board-item" id="bol">
            Estimated cost :
            <span>N{{data.price}}</span>
          </div>
        </div>
      </div>
      <div class="form-wrapper">
        <div class="form-group">
          <label for>
			  <span>Room 1 :</span>
			  
			</label>
          <div class="form-row">
            <div class="select mr-20"">
              <div class="form-holder"  @click="showSourceList=true">
                <div class="select-control"  v-if="data.source"> {{data.source}}</div>
				<span class="select-control" v-else>From :</span>
                <span class="lnr lnr-chevron-down"></span>
              </div>
              <ul class="dropdown" v-show="showSourceList" :class="{show: showSourceList}">
				<li :key="index" v-for="(location, index) in sourceList" :rel="location.name" @click="selectSource(location.name)">{{location.name}}</li>
                <!-- <li rel="Victoria Island">Victoria Island</li>
                <li rel="Ajah">Ajah</li>
                <li rel="Obalende">Obalende</li> -->
              </ul>
            </div>

            <div class="select">
              <div class="form-holder" @click="showDestinationList=true">
                <div class="select-control" v-if="data.destination">{{data.destination}}</div>
				<div class="select-control" v-else>To :</div>
                <span class="lnr lnr-chevron-down"></span>
              </div>
              <ul class="dropdown" v-show="showDestinationList"  :class="{show: showDestinationList}">
				  <li :key="index" v-for="(location, index) in destinationList" :rel="location.name" @click="selectDestination(location)">{{location.name}}</li>
              </ul>
            </div>
          </div>
        </div>
        <button class="forward" @click="$emit('next', {...firstPageData, ...data})">
          Continue
          <i class="zmdi zmdi-long-arrow-right"></i>
        </button>
      </div>
    </section>
  </div>
</template>

<script>
let Islandlocation =  [
	 {'name': 'Lekki', 
	  'destinations': [
		{'name': 'Ikeja',
		 'price': 800
		},
		{'name': 'Egbeda',
		 'price': 900},
		 {'name': 'Yaba',
		  'price': 1000}
	  ]
	 }, 
	 {'name': 'Ikoyi', 
	  'destinations': [
		{'name': 'Ikeja',
		 'price': 850
		},
		{'name': 'Egbeda',
		 'price': 950},
		 {'name': 'Yaba',
		  'price': 1050}
	  ]
	 }, 
	 {'name': 'VI', 
	  'destinations': [
		{'name': 'Ikeja',
		 'price': 900
		},
		{'name': 'Egbeda',
		 'price': 1000},
		 {'name': 'Yaba',
		  'price': 1100}
	  ]
	 }, 
	 
	 
  ]	
  let Mainlandlocation =  [
	 {'name': 'Ikeja', 
	  'destinations': [
		{'name': 'VI',
		 'price': 800
		},
		{'name': 'Lekki',
		 'price': 900},
		 {'name': 'Ikoyi',
		  'price': 1000}
	  ]
	 }, 
	 {'name': 'Egbeda', 
	  'destinations': [
		{'name': 'VI',
		 'price': 850
		},
		{'name': 'Lekki',
		 'price': 950},
		 {'name': 'Ikoyi',
		  'price': 1050}
	  ]
	 }, 
	 {'name': 'Yaba', 
	  'destinations': [
		{'name': 'VI',
		 'price': 900
		},
		{'name': 'Lekki',
		 'price': 1000},
		 {'name': 'Ikoyi',
		  'price': 1100}
	  ]
	 }	 
  ]
export default {
  props: ["firstPageData"], 
  data () {
	  return {
		  sourceList: [],
		  destinationList: [],
		  data: {},
		  showSourceList: false,
		  showDestinationList: false,
		  price: ''
	  }
  },
  methods: {
	  selectSource(source) {
		  console.log(source)
		this.data.source = source
		this.showSourceList = false
		let selectedSource = {}
			selectedSource = Islandlocation.find(member=>{return member.name == source})
			if(!selectedSource)
				selectedSource = Mainlandlocation.find(member=>{return member.name == source})
		this.destinationList = selectedSource.destinations 
	  },
	  selectDestination(destination){
		this.data.destination = destination.name
		this.showDestinationList = false
		this.data.price = destination.price
	  }
  },
  mounted() {
		if(this.firstPageData.from == 'Island')
			this.sourceList = Islandlocation
		else
		this.sourceList = Mainlandlocation
  },
  watch:{
	  firstPageData(val){
		  if(val.from == 'Island')
			  this.sourceList = Islandlocation
		  else
		  	this.sourceList = Mainlandlocation
	  }
  }
};
</script>
<style scoped>
.show{
	display: block !important
}
</style>

<template>
  <div>
    <h4>Pickup Details</h4>
    <section>
      <div class="form-row">
        <div class="select">
          <div class="form-holder">
            <div class="select-control">From :</div>
            <span class="lnr lnr-chevron-down"></span>
          </div>
          <ul class="dropdown">
            <li rel="Island" @click="saveFrom('Island')">Island</li>
            <li rel="Mainland" @click="saveFrom('Mainland')">Mainland</li>
            <!-- <li rel="Lekki" @click="saveFrom('Lekki')">Island</li> -->
            <!-- <li rel="Ikoyi" @click="saveFrom('Ikoyi')">Ikoyi</li>
            <li rel="Victoria Island" @click="saveFrom('VI')">Victoria Island</li>
            <li rel="Egbeda" @click="saveFrom('Egbeda')">Egbeda</li>
            <li rel="Yaba" @click="saveFrom('Yaba')">Yaba</li>
            <li rel="Ikeja" @click="saveFrom('Ikeja')">Ikeja</li> -->
          </ul>
        </div>
        <div class="select">
          <div class="form-holder">
            <div class="select-control">To :</div>
            <span class="lnr lnr-chevron-down"></span>
          </div>
          <ul class="dropdown">
            <li rel="Island" @click="saveTo('Island')">Island</li>
            <li rel="Mainland" @click="saveTo('Mainland')">Mainland</li>
            <!-- <li rel="Lekki" @click="saveTo('Lekki')">Lekki</li>
            <li rel="Ikoyi" @click="saveTo('Ikoyi')">Ikoyi</li>
            <li rel="Yaba" @click="saveTo('Yaba')">Yaba</li>
            <li rel="Egbeda" @click="saveTo('Egbeda')">Egbeda</li>
            <li rel="Ikeja" @click="saveTo('Ikeja')">Ikeja</li>
            <li rel="Victoria Island" @click="saveTo('VI')">Victoria Island</li> -->
          </ul>
        </div>
      </div>
      <div class="form-row">
        <div class="select">
          <div class="form-holder">
            <div class="select-control">Take off Time :</div>
            <span class="lnr lnr-chevron-down"></span>
          </div>
          <ul class="dropdown">
            <li rel="6:00am to 7:00am" @click="saveTime('6:00am to 7:00am')">6:00am to 7:00am</li>
            <li rel="7:00am to 8:00am" @click="saveTime('7:00am to 8:00am')">7:00am to 8:00am</li>
            <li rel="4:00pm to 5:00pm" @click="saveTime('6:00pm to 7:00pm')">4:00pm to 5:00pm</li>
            <li rel="5:00pm to 6:00pm" @click="saveTime('6:00pm to 7:00pm')">5:00pm to 6:00pm</li>
            <li rel="6:00pm to 7:00pm" @click="saveTime('6:00pm to 7:00pm')">6:00pm to 7:00pm</li>
          </ul>
        </div>
        <div class="select">
          <div class="form-holder">
            <div class="select-control">Ride Type :</div>
            <span class="lnr lnr-chevron-down"></span>
          </div>
          <ul class="dropdown">
            <li rel="Salon car" @click="saveType('Salon Car')">Salon Car</li>
            <li rel="Jeep" @click="saveType('Jeep')">Jeep</li>
            <li rel="Minivan" @click="saveType('Minivan')">Minivan</li>
            <li rel="Bus" @click="saveType('Bus')">Bus</li>
          </ul>
        </div>
      </div>

      <button @click="$emit('next', data)" class="forward">
        Continue
        <i class="zmdi zmdi-long-arrow-right"></i>
      </button>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data : {
        from: '',
        to: '',
        time: '',
        type: '',
      }
      // choice: ''
    }
  },
  methods: {
    saveFrom(params) {
      this.data.from = params
    },
    saveTo(params) {
      this.data.to = params
    },
    saveTime(params) {
      this.data.time = params
    },
    saveType(params) {
      this.data.type = params
    }
  }
};
</script>

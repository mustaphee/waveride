<template>
  <div class="wrapper">
    <div class="inner">
      <div class="image-holder">
        <img src="static/images/waveride.jpg" alt height="300" width="1024">
        <h3>BOOK A RIDE</h3>
      </div>

      <div class="wizard clearfix" id="wizard">
        <div class="steps clearfix">
          <ul role="tablist" @click="page=1">
            <li role="tab" aria-disabled="false" class="first done" :class="{current: page==1}" aria-selected="false">
              <a id="wizard-t-0" aria-controls="wizard-p-0">
                <span class="number">1.</span> Pickup Details
              </a>
            </li>
            <li role="tab" aria-disabled="false" :class="{current: page==2}" aria-selected="true" @click="page=2">
              <a id="wizard-t-1" aria-controls="wizard-p-1">
                <span class="current-info audible"></span>
                <span class="number">2.</span> Additional details
              </a>
            </li>
            <li role="tab" aria-disabled="false" :class="{current: page==3}" @click="page=3">
              <a id="wizard-t-2" aria-controls="wizard-p-2">
                <span class="number">3.</span> Book a ticket
              </a>
            </li>
            <li role="tab" aria-disabled="false" class="last" :class="{current: page==4}" @click="page=4">
              <a id="wizard-t-3" aria-controls="wizard-p-3">
                <span class="number">4.</span> Confirmation
              </a>
            </li>
          </ul>
        </div>
        <!-- SECTION 1 -->
        <div class="content clearfix">
          <my-details v-if="page==1" transition="expand" @next="onOpenDetails"></my-details>
          <additional-details v-if="page==2" transition="expand" @next="onOpenSecondDetails" :firstPageData="firstPageData"/>
          <booking v-show="page==3" transition="expand" @next="onOpenThirdDetails" :secondPageData="secondPageData"/>
          <confirmation v-show="page==4" transition="expand" :thirdPageData="thirdPageData"/>
        </div>
        <!-- SECTION 2 -->

        <!-- SECTION 3 -->

        <!-- SECTION 4 -->
      </div>
    </div>
  </div>
</template>

<script>
import MyDetails from "@/components/details";
import additionalDetails from "./additional-details.vue";
import confirmation from "@/components/confirmation";
import booking from "@/components/booking";
export default {
  name: "HelloWorld",
  components: { MyDetails, additionalDetails, booking, confirmation },
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      error: "",
      firstName: "",
      lastName: "",
      phoneNumber: "",
      bvn: "fdg",
      date: new Date().toLocaleString(),
      page: 1,
      firstPageData: {},
      secondPageData: {},
      thirdPageData: {}
    };
  },
  methods: {
    onOpenDetails(data){
      this.firstPageData = data;
      this.page = 2
    },
    onOpenSecondDetails(data){
      this.secondPageData = data;
      this.page = 3
    },
    onOpenThirdDetails(data){
      this.thirdPageData = data;
      this.page = 4
    },
   
  }
};
</script>
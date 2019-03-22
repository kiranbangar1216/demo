<template>
<div><h3>{{header}}</h3>

<div >
   
     <b-alert show variant="primary">
    Player name <input v-model="name">
    and I can hit <input v-model="age" > Clicks!!!
    </b-alert>
  
   <p>
     
    <b-button @click="persist" variant="success">Save</b-button>
  </p>
 

 
<!-- <input class="input" type="text" v-model="message" > -->
    </div>
    <p>

</p>

 <b-button @click="showAlert" variant="info" class="m-1">
     start
    </b-button>
   
    <b-alert
      :show="dismissCountDown"
      dismissible
      variant="warning"
      @dismissed="dismissCountDown=0"
      @dismiss-count-down="countDownChanged"
    >
      <p>You have {{ dismissCountDown }} seconds...</p>
      <b-progress variant="warning" :max="dismissSecs" :value="dismissCountDown" height="4px"  />
    </b-alert>
    
     <div >
  <b-button class="play" v-if="dismissCountDown!=0" v-on:click="counter += 1" variant="danger">Play</b-button>
 
  <b-alert show variant="primary">Your score is {{ counter }} </b-alert>
  <b-alert v-if="(counter>age && (dismissCountDown==0))" show variant="success">Yo!!Your Man of your words..You scored!! </b-alert>
  <!-- <b-alert v-if="(counter<age  && (dismissCountDown==0) && counter!=0)" show variant="danger">Better luck next time :(</b-alert>
   <b-alert v-if="(counter<age  && (dismissCountDown==0) && counter!=0)" show variant="danger">Better luck next time :(</b-alert> -->
</div>
<div >
  <b-button @click="show = !show" variant="success" class="m-1">Developed by-</b-button>
  <transition name="bounce">
    <!-- <p v-if="show">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris facilisis enim libero, at lacinia diam fermentum id. Pellentesque habitant morbi tristique senectus et netus.</p> -->
    <User  v-if="!show" v-for="person in team" v-bind:detail="person">
</User>
  </transition>
</div>

</div>
</template>

<script>
// import to access User
// note:Element name,Component name is name of model imported.
import User from "@/components/User.vue";

// import moment
import moment from "moment";

export default {
  name: "contactus",

  // model imported is written in components
  components: {
    User
  },

  // call on page load use created()
  created() {
    // this.initialcall();
  },

  // data
  data() {
    return {
      dismissSecs: 5,
      dismissCountDown: 0,
      show: true,
      counter: 0,
      name: "",
      age: 0,
      message: "",
      header: "",
      team: [
        {
          name: "kiran Bangar",
          about: "Backend Developer,Wohlig Transformation",
          dob: moment("20-10-1995", "DD-MM-YYYY")
        },
        {
          name: "vicky",
          about: "meanstack",
          dob: moment("27-1-1995", "DD-MM-YYYY")
        },
        {
          name: "nayan",
          about: "ui/ux developer",
          dob: moment("29-10-1991", "DD-MM-YYYY")
        },
        {
          name: "Karan",
          about: "Project Manager",
          dob: moment("31-12-1995", "DD-MM-YYYY")
        },
        {
          name: "manish",
          about: "Backend Developer",
          dob: moment("31-12-1995", "DD-MM-YYYY")
        }
      ]
    };
  },
  // mounted() {
  //   if (localStorage.name) {
  //     this.name = localStorage.name;
  //   }
  //   if (localStorage.age) {
  //     this.age = localStorage.age;
  //   }
  // },
  // acts like controller in angular js.
  methods: {
    // persist() {
    //   localStorage.name = this.name;
    //   localStorage.age = this.age;
    //   console.log("now pretend I did more stuff...");
    // },
    myFunction() {
      // this.message = "Bye Vue!!";
      this.message = this.message
        .split("")
        .reverse()
        .join("");
    },
    countDownChanged(dismissCountDown) {
      this.dismissCountDown = dismissCountDown;
    },
    showAlert() {
      this.counter = 0;
      this.dismissCountDown = this.dismissSecs;
    }
  }
};
</script>

<style scoped>
.body {
  background-color: darkgoldenrod;
}
.play {
  margin-bottom: 10px;
}
.message {
  color: black;

  border-radius: 50px;
  opacity: 0.9;
}
.input {
  background-color: navajowhite;
  border-radius: 5px;
}
.button {
  background-color: royalblue;
  border: snow;
  border-radius: 5px;
}
.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}
</style>

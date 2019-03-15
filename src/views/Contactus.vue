<template>
<div><h3>{{header}}</h3>
<p class="message">{{message}}</p>
<div>
<input class="input" type="text" v-model="message" >
    </div>
    <p>
<button class="button" @click="myFunction()">Click Me!</button>
</p>
<User v-for="person in team" v-bind:detail="person">
</User>
</div>
</template>

<script>
// import to access User
// note:Element name,Component name is name of model imported.
import User from '@/components/User.vue';

// import moment
import moment from 'moment';

export default {
  name: 'contactus',

  // model imported is written in components
  components: {
    User,
  },

  // call on page load use created()
  created() {
    // this.initialcall();
  },

  // data
  data() {
    return {
      message: 'Hello User!',
      header: 'Check this Stuff !!',
      team: [
        {
          name: 'roshan',
          about: 'uideveloper',
          dob: moment('20-10-1995', 'DD-MM-YYYY'),
        },
        {
          name: 'vicky',
          about: 'meanstack',
          dob: moment('27-1-1995', 'DD-MM-YYYY'),
        },

        {
          name: 'nayan',
          about: 'ui/ux developer',
          dob: moment('29-10-1991', 'DD-MM-YYYY'),
        },
      ],
    };
  },

  // acts like controller in angular js.
  methods: {
    myFunction() {
      // this.message = "Bye Vue!!";
      this.message = this.message
        .split('')
        .reverse()
        .join('');
    },
  },
};
</script>

<style scoped>
.message {
  color: aquamarine;
  background-color: orangered;
  border-radius: 50px;
  opacity: 0.9;
}
.input {
  background-color: olivedrab;
  border-radius: 5px;
}
.button {
  background-color: royalblue;
  border: snow;
  border-radius: 5px;
}
</style>

<template>
<div><h3>{{header}}</h3>
<p>{{message}}</p>
<div>
<input  type="text" v-model="message">
    </div>
    <p>
<button @click="myFunction()">Click Me!</button>
</p>
<User v-for="person in team" v-bind:detail="person">
</User>
</div>
</template>

<script>
import User from "@/components/User.vue";
import moment from "moment";

export default {
  name: "contactus",
  components: {
    User
  },
  created() {
    this.initialcall();
  },
  data() {
    return {
      message: "Hello Vue!",
      header: "Love apis!",
      team: [
        {
          name: "roshan",
          about: "uideveloper",
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
        }
      ]
    };
  },
  methods: {
    // initialcall() {
    //   this.header = "vue";
    // },
    myFunction() {
      this.message = "Bye Vue!!";
    }
  }
};
</script>

<style scoped>
</style>

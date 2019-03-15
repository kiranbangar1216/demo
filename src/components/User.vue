<template>
    <div>
        <div class="user">
<p>Name:{{detail.name}}</p>
<p>About:{{detail.about}}</p>
<p>Dob:{{detail.dob | formatDob}}</p>
</div>
    </div>
</template>

<script>
// import to use .
import moment from 'moment';

export default {
  name: 'User',
  // props use to store or act as model
  props: ['detail'],

  // filter
  filters: {
    formatDob(value) {
      if (value) {
        return moment(value).format('Do MMMM YYYY,dddd');
      }
      return 'No date found';
    },
  },
};
</script>

<style scoped>
.user {
  color: darkturquoise;
  background-color: white;
  opacity: 0.9;
  border: 5px;
  border-radius: 30px;
  padding: 20px;
}
</style>

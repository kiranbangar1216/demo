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
import moment from 'moment';

export default {
  name: 'User',
  props: ['detail'],
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
  border: 5px;
  padding: 10px;
}
</style>

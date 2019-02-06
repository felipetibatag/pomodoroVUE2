<template>
  <div class="display-3">{{minutos}}:{{segundos}}</div>
</template>

<script>
export default {
  props: ["minutos", "segundos"],
  data() {
    return {};
  }
};
</script>

<style>
</style>

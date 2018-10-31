<template>
  <div class="card">
    <h5 class="card-header">String Char Codes</h5>
    <div class="card-body">
      <ul class="list-group">
        <li class="list-group-item" v-for="(char, i) in charCodeArr" :key="i">
          <h4>{{ char }} = {{ actionText.charAt(i) }}</h4>
        </li>
      </ul>
    </div>
    </div>
</template>

<script>
export default {
  props: ["charCodeArr", "actionText"]
};
</script>

<style>
</style>

<template>

<div>
    <div class="card"  >
<div class="card-header">
  Quote
</div>
<div class="card-body" >
<blockquote class="blockquote mb-0">
    <p>สภาพอากาศ :{{items.list[0].dt_txt}}</p>
  <div>
    {{index+1}}

</div>
  <footer class="blockquote-footer">Someone famous in <cite title="Source Title">Source Title</cite></footer>
</blockquote>
</div>
</div>
</div>





</template>
<script setup>
import axios from "axios";
import { ref,onMounted } from "vue";

const items = ref({});
const lat = ref("13.568492813819963");
const lon = ref("100.82745158450724");
const apikey = ref("b658e1850340af07649e496a52c67a5f");

const url = ref('https://api.openweathermap.org/data/2.5/forecast?lat='+lat.value+'&lon='+lon.value+'&appid='+apikey.value+'&units=metric');
function fetchPosts() {
axios
.get(url.value)
.then((response) => {
items.value = response.data;
console.log(items.value);
})
.catch((err) => {
console.log(err);
});
}
onMounted(fetchPosts);

</script>
<style scoped>

</style>
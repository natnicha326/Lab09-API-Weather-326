
<script setup>
import axios from "axios";
import { ref,onMounted  } from "vue";
import { useRoute, } from "vue-router";
const route = useRoute()
const id = ref(route.params.id)
console.log("ID"+id.value);
const items = ref({});
const url = ref(`https://jsonplaceholder.typicode.com/posts/`+route.params.id);
function fetchPosts() {
 axios
 .get(url.value)
 .then((response) => {
 items.value = response.data;
 })
 .catch((err) => {
 console.log(err);
 });
}
onMounted(fetchPosts);
 </script>
<template>
    <div>
<h1>A-Post page{{ route.params.id }}</h1>


<div>
     <ui>
        <li>userId= {{ items.userId }}</li>
        <li>id={{items.id }} </li>
        <li>Title:{{items.title}}</li>
        <li>Body:{{items.body}}</li> 
    
</ui> 


</div>
    </div>
</template>

<style scoped></style>
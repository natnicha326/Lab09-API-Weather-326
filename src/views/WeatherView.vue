<template>
  <body>
    
<div class="container">
    <div class="row">
     <h1 class="subject"> มาเช็คสภาพอากาศกันเถอะ</h1>
   
      <div class="input-group">
  <span class="input-group-text border-purple">ละติจูดและลองติดจูดสถานที่</span>
  <input type="text" aria-label="Latitude" class="form-control text " v-model="lati">
  <input type="text" aria-label="Longitude" class="form-control text" v-model="long">
  <button @click="fetchPosts()" class="btn form "><img src="https://png.pngtree.com/png-vector/20190130/ourmid/pngtree-mbe-weather-cartoon-icon-rain-element-weathercartooniconrain-png-image_627462.jpg" class="iconbutton"></button> 
  </div>
    </div>
    <div class="row ">
        <div class="col-4 " >
            <div class="col-10  " v-for="(i,index) in items.list" :key="index">
    <div id="list-example">
      <a  class="card borderpurple " :href="`#`+index"><img :src="`https://openweathermap.org/img/wn/`+ i.weather[0].icon +`@2x.png`" class="card-img" style="max-width: 60px; ">{{items.list[index].dt_txt}}</a>
      
        </div>
    </div>
    </div>
        <div class="col-8 ">
            <div class="card h-80 container borderblue" v-for="(i,index) in items.list" :key="index">
            <div data-bs-spy="scroll" data-bs-target="#list-example" data-bs-smooth-scroll="true" class="scrollspy-example" tabindex="0" :id="index">
                <div class="row">
                  <div class="col-md-4">
                    <b class="date">สภาพอากาศ</b><br><p class="text">{{items.list[index].dt_txt}}</p> 
                    <img :src="`https://openweathermap.org/img/wn/`+ i.weather[0].icon +`@2x.png`" class="card-img" alt="..." style="max-width: 140px; ">
                     
                  </div>
                  <div class="col">
                    <h4 class="text"><strong>{{ items.city.name}} , {{ items.city.country }}</strong></h4>
                    <h5 class="text"> สภาพอากาศโดยรวม {{i.main.temp}}° C</h5>
                <div class="row justify-content-end text">
                  <div class="col-sm-6 col-md-6"><p><img  class="icontemp" src="https://cdn.icon-icons.com/icons2/788/PNG/512/temperature-1_icon-icons.com_65085.png" alt="temp_mim">   {{ i.main.temp_min }} ° C</p></div>
                  <div class="col-sm-6 col-md-6"><p><img  class="icontemp" src="https://cdn.icon-icons.com/icons2/788/PNG/512/temperature_icon-icons.com_65084.png" alt="temp_max">  {{ i.main.temp_max }} ° C</p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="icontemp" src="https://media.istockphoto.com/id/1083322658/th/%E0%B9%80%E0%B8%A7%E0%B8%84%E0%B9%80%E0%B8%95%E0%B8%AD%E0%B8%A3%E0%B9%8C/%E0%B8%A5%E0%B8%B9%E0%B8%81%E0%B8%84%E0%B8%A3%E0%B8%B4%E0%B8%AA%E0%B8%95%E0%B8%B1%E0%B8%A5%E0%B8%A1%E0%B8%B2%E0%B8%A2%E0%B8%B2%E0%B8%81%E0%B8%A5.webp?s=2048x2048&w=is&k=20&c=JMm_G7f9N_YsX8mga1UbBXUs9_5zLq44LMsRcatKyyI=" alt="description"> : {{i.weather[0].description}}</p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="icontemp" src="https://media.istockphoto.com/id/1392278078/th/%E0%B9%80%E0%B8%A7%E0%B8%84%E0%B9%80%E0%B8%95%E0%B8%AD%E0%B8%A3%E0%B9%8C/%E0%B8%94%E0%B8%A7%E0%B8%87%E0%B8%AD%E0%B8%B2%E0%B8%97%E0%B8%B4%E0%B8%95%E0%B8%A2%E0%B9%8C%E0%B9%81%E0%B8%A5%E0%B8%B0%E0%B9%80%E0%B8%A1%E0%B8%86%E0%B8%97%E0%B8%B5%E0%B9%88%E0%B8%A1%E0%B8%B5%E0%B8%AB%E0%B8%A2%E0%B8%94%E0%B8%99%E0%B9%89%E0%B9%8D%E0%B8%B2%E0%B8%9D%E0%B8%99-%E0%B9%81%E0%B8%99%E0%B8%A7%E0%B8%84%E0%B8%B4%E0%B8%94%E0%B8%AA%E0%B8%A0%E0%B8%B2%E0%B8%9E%E0%B8%AD%E0%B8%B2%E0%B8%81%E0%B8%B2%E0%B8%A8-%E0%B9%84%E0%B8%AD%E0%B8%84%E0%B8%AD%E0%B8%99%E0%B9%80%E0%B8%A7%E0%B8%81%E0%B9%80%E0%B8%95%E0%B8%AD%E0%B8%A3%E0%B9%8C-3-%E0%B8%A1%E0%B8%B4%E0%B8%95%E0%B8%B4-%E0%B8%AA%E0%B9%84%E0%B8%95%E0%B8%A5%E0%B9%8C%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%8C%E0%B8%95%E0%B8%B9%E0%B8%99%E0%B8%A1%E0%B8%B4%E0%B8%99%E0%B8%B4%E0%B8%A1%E0%B8%AD%E0%B8%A5.jpg?s=2048x2048&w=is&k=20&c=cpupCKSGRwOMfhMYcT3JAeGHBw4rBCWBxrWSpByUauo=" alt="humidity"> : {{ i.main.humidity }} %</p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="iconhpa" src="https://e7.pngegg.com/pngimages/513/728/png-clipart-humidity-indicator-card-computer-icons-relative-humidity-barometer-miscellaneous-text-thumbnail.png" alt="pressure"> : {{ i.main.pressure}} hPa </p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="iconhpa" src="https://cdn.icon-icons.com/icons2/3035/PNG/512/weather_snow_snowflake_winter_freeze_icon_189094.png" alt="pressure"> : {{i.clouds.all}} % </p></div>
                  <div class="col-sm-6 col-md-6"><p><img class="iconhpa" src="https://cdn.icon-icons.com/icons2/1338/PNG/512/hardwindandcloud_87409.png" alt="pressure"> : {{ i.wind.speed }} Km/hr</p></div>
                </div>
                  </div>
                </div>

        </div>
        </div>
  </div>
</div>  
</div>


</body>
</template>
<script setup>
import axios from "axios";
import { ref } from "vue";

const lati = ref( );
const long = ref( );

const items = ref({});

const apikey = ref("b658e1850340af07649e496a52c67a5f");


function fetchPosts() {
const url = ref('https://api.openweathermap.org/data/2.5/forecast?lat='+lati.value+'&lon='+long.value+'&appid='+apikey.value+'&units=metric');
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


</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Itim&family=Mali&family=Mooli&family=Nunito:wght@500&family=Roboto+Slab&family=Sriracha&display=swap');
.iconbutton{
max-width: 50px;
}
.subject{
  font-family: 'Itim', cursive;
  margin-top: 30px;
  padding: 10px;
  text-align: center;
  font-weight: 500;
  color: #ff2197;
  
}
.date{font-family: 'Itim', cursive;}
.input-group{
  font-family: 'Itim', cursive;
}
.fixed-top{
    padding: 100px;
    margin-right: 75%;
  }
h5{ font-family: 'Itim', cursive;}
.card{
padding: 20px;
margin: 20px;

  }
  .card-img{
  padding: 10px;
  margin: 10px;
}
.icontemp{
max-width: 40px;
}
.iconhpa{
max-width: 20px;
}
.list-group{
  margin: 5px;
  padding: 0px;
}
.date{
  color: #e93ca7;
}
.text{
  color: #c21e57;
}
.borderpurple{
border-color: #ff57eb;
border-width: 2px;
background-color: #ffa6f0;
}
.borderblue{
  border-color: #ff2ea5;
border-width: 2px;
background-color: #ffd6e6;
}
body{
  background-color: #ffd6e6;
}
</style>
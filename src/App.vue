<template>
  <div>
      <main>
        <div class="search-box">
          <input 
                     name="" 
                     id="" 
                     type="text" 
                     class="search-bar"
                     v-model="query"
            />
          
        </div>
    
        <div class="weather-wrap" >
          <div class="location-box">
            <div class="location">k</div>
            <div class="date">a</div>
          </div>
          <div class="weather-box">
            <div class="temp">s</div>
            <div class="weather-image">
            </div>
             <div class="weather">s</div>
             <div class="weather-description">s</div>
          </div>
        </div>
      </main>
  </div>
</template>
<script>

  export default {
    name: 'App',
    data() {
      return {
        api_key: 'a9af0ea17c5c72c362971c959e8c0b03' ,
        url_base: 'https://api.openweathermap.org/data/2.5/' , 
        query: '' , 
        weather: {}

      }
    },

    methods: {

      fetch_weather(e) {
        if (e.key === "Enter") {
          fetch(`${this.url_base}weather?q=${this.query}&units=metric&appid=${this.api_key}`)
          .then(res => {
            return res.json();
          }).then(this.setResults);
        }
      },
      setResults(results) {
        this.weather = results;
      },
      dateBuilder() {
        let d = new Date();
        let months = ["January","February","March","April","May","June","July","August","September","October","November","December"];
        let days = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"];
        let day = days[d.getDay()];
        let date = d.getDate();
        let month = months[d.getMonth()];
        let year = d.getFullYear(); 
        return `${day} ${date} ${month} ${year}`; 
      },

    }
  }

</script>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'montserrat', sans-serif;
  }

  #app {
    background-image: url("assets/25501.jpg");
    background-size: cover;
    background-position: bottom;
    transition: 0.4s;
  }
  main {
    min-height: 100vh;
    padding: 25px;
    background-image: linear-gradient(to bottom, (0, 0, 0, 0.25), tgba(0, 0, 0, 0.75));
  }
  
  .search-box {
    width: 100%;
    margin-bottom: 30px;
  }
  
  
  .search-box .search-bar {
    display: block;
    width: 100%;
    padding: 15px;
    color: #313131;
    font-size: 20px;
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);

    appearance: none;
    border: none;
    background: none;
    outline: none;

    background-color: rgba(255, 255, 255, 0.5);
    border-radius: 10px 10px 10px 10px;
    transition: 0.4s;
  }


  .search-box .search-bar:focus {
    background-color: rgba(255, 255, 255, 0.75);
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
    border-radius: 16px 5px 16px 5px;
  }
  .location-box .location {
    color: #ffffff;
    font-size: 32px;
    font-weight: 500;
    text-align: center;
    text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
  }
  .location-box .date {
    color: #ffffff;
    font-size: 20px;
    font-weight: 300;
    font-style: italic;
    text-align: center;
  }
  .weather-box {
    text-align: center;
  }
  .weather-box .temp {
    display: inline-block;
    padding: 10px 25px;
    color: #ffffff;
    font-size: 102px;
    font-weight: 900;
    
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
    background-color: rgba(255, 255, 255, 0.25);
    border-radius: 16px;
    margin: 30px 0px;

    box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  }
  .weather-box .weather{
    color: #ffffff;
    font-size: 35px;
    font-weight: 300;
    font-style: italic;
    text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  }
  .weather-box .weather-description {
    color: #ffffff;
    font-size: 10px;
    font-weight: 300;
    font-style: italic;
  }
    .weather-box .weather-image {
      position: center;
    }

  



</style>

# current_weather_wu_vue

Current weather conditions data is requested from [Weather Underground API](https://www.wunderground.com/weather/api/) through the [axios](https://www.npmjs.com/package/axios) http requests client. The browser gets the weather data in JSON format which `axios` also transforms. The Web interface is then rendered by [vue.js](https://vuejs.org/). See example image below.

## Example Image

![example]

## Vue Script

The JSON data for current weather conditions is collected in `results: []`.

```node
const url = 'http://api.wunderground.com/api/ad8ef392afe1e78f/conditions/q/IL/pws:KILMORRI2.json'
const vm = new Vue({
  el: '#app',
  data: {
    results: []
  },
  mounted() {
    axios.get(url).then(response => {
      this.results = response.data
    })
  }
});
```

## Template System

Vue.js uses a [mustache-style](https://en.wikipedia.org/wiki/Mustache_(template_system)) template system. See syntax example below:

```html
<p><span>UV:</span> {{ results.current_observation.UV }}</p>
```

In the line example above, `UV` data is rendered to the display thru the path `results.current_observation.UV` since `response.data` was stored in `results` (all of the current weather conditions data). WU API's own current weather data is stored in the object `current_observation`. So `current_observation.UV` contains the numerical value for the current UV level.

## API Key with Sub

A personal API key comes with a free subscription to [Weather Underground](https://www.wunderground.com/). Usage limits apply.

[example]: example.png "Weather App Example"

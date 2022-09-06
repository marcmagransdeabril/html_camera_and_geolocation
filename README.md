# HTML Camera and Geolocation

_"Why do you use mobile native applications instead of simple HTML?"_ I asked [oriol](https://github.com/orioli) while chatting about his new project, [qualnotes project](https://qualnotes.com/).

I'm prety ignorant on all the involved subjects (i.e. mobile apps and frameworkds, camera and video APIs, geolocation API to name a few). A month after this conversation I read in hackernews the solution: https://news.ycombinator.com/item?id=32738501

It turns out that it is actually possible and simple, too. Check out the [index.html](https://github.com/marcmagransdeabril/html_camera_and_geolocation/blob/main/index.html).

# Can I reduce the latency of the first capture?

Just store the old coordinates in local storage:

```html
const oldCoords = localStorage.getItem('coords');

if (oldCoords) {
  showWeather(JSON.parse(oldCoords));
}

navigator.geolocation.getCurrentPosition(position => {
  const newCoords = JSON.stringify(position.coords);
  localStorage.setItem('coords', newCoords);
  showWeather(newCoords);
});
```

# Browser Support

camera support per browser: https://caniuse.com/html-media-capture

geolocation support per browser: https://caniuse.com/?search=geolocation


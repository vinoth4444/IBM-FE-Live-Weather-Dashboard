const apiKey = "YOUR_WEATHER_API_KEY"; // Replace with IBM Weather API Key or OpenWeatherMap key

document.getElementById("city-input-btn").onclick = function () {
  let city = document.getElementById("city-input").value;
  if (city) {
    getWeather(city);
  }
};

async function getWeather(city) {
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${encodeURIComponent(city)}&appid=${apiKey}&units=metric`;
  try {
    let res = await fetch(url);
    let data = await res.json();
    if (res.ok) {
      showWeather(data);
      document.getElementById("error-message").textContent = "";
    } else {
      document.getElementById("error-message").textContent = "City not found!";
      document.getElementById("weather-info").style.display = "none";
    }
  } catch (e) {
    document.getElementById("error-message").textContent = "Network error.";
    document.getElementById("weather-info").style.display = "none";
  }
}

function showWeather(data) {
  document.getElementById("weather-info").style.display = "block";
  document.getElementById("city-name").textContent = data.name;
  document.getElementById("date").textContent = moment().format('MMMM Do YYYY, h:mm:ss a');
  document.getElementById("temperature").textContent = `${data.main.temp}°C`;
  document.getElementById("description").textContent = data.weather[0].description;
  document.getElementById("wind-speed").textContent = `Wind Speed: ${data.wind.speed} m/s`;
  document.getElementById("weather-icon").src = `https://openweathermap.org/img/wn/${data.weather[0].icon}.png`;
}

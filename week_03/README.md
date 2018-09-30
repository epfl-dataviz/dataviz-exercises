
# Weather forecasts with DOM API, fetch and JS classes

In this exercise we display weather forecasts.
We use JavaScript to make the presentation interactive: download the data from the internet and display it dynamically.


## DOM API

The DOM API allows JavaScript to completely control (edit, add, remove) the HTML objects constituting the web page.
Please look at the example in [documentation](https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Using_the_W3C_DOM_Level_1_Core), we will be using similar operations.

We start, as usual, with the page in [`exercise/index.html`](exercise/index.html). Please edit the files `exercise/exercise_weather.js` and `exercise/style_weather.css` to complete the exercise.

* **On Click** - The page contains a button with the id `btn-part1`. [Find it](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
and [register a JS function to be executed](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener) when the button is clicked. For now, the function should write "The button was clicked" to the console, so we can check if it executes properly upon click.

	**Note - Ensure the DOM has been loaded:** we should make sure that the HTML has been loaded (and therefore, the button and other elements already exist) before we execute our script. Use the provided function `whenDocumentLoaded` to achieve that [(about DOMContentLoaded event)](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded).

* **Show the temperatures** - Given an array of forecast temperatures (such as the array `TEST_TEMPERATURES`), we want to display them in order. Create a function `showTemperatures(container_element, temperature_array)` such that:

	* Clears the `container_element`'s content, for example by setting the [`innerHTML`](https://developer.mozilla.org/en-US/docs/Web/API/Element/innerHTML) to "".
	* For each temperature value in `temperature_array`, it [creates](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) a `<p>` element with the temperature value inside (for example `<p>13</p>`).
	Please practoce a functional iteration method instead of an explicit `for`/`while` loop.
	* Places the `<p>`s in `container_element`.

	Use that function to display the temperatures from `TEST_TEMPERATURES` in the div with id `weather-part1`.

* **Colors with CSS classes** - Change the background color of the `<p>` depending on the temperature value.
	Create the classes `warm` and `cold` in `exercise/style_weather.css` with appropriate background colors.
	In your `showTemperatures` function, apply the appropriate CSS class to the created elements:

	* `warm` for temperature 23 C or higher,
	* `cold` for temperature 17 C and lower.

	<img src="task_images/temperatures_with_color.png" width="640" />

## JS Classes

[Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) allow us to organize our program around objects ("object-oriented programming") and makes code easier to reuse - do the same actions with many objects.
An object contains data (called properties) and functions (called methods).

First, we convert the code from the previous part into a class.

* Create a `Forecast` class, which has the following properties:

	* `container` - the element in which the temperatures will be written, the initial value should be given as an argument to the constructor,
	* `temperatures` - current value of the temperature forecast, should be initialized to `[1,2,3,4,5,6,7]`.

	Thus we create the object as `new Forecast(container_div)`.
	Instantiate the class, giving it the div with id `weather-part2` as the container.

* Add a `toString` method which writes its attributes to a string.

* Add a `print` method which prints that string to the console.

* Adapt `showTemperatures` to create a `show` method which takes no arguments and instead displays the object's `temperatures` in its `container`.

* Add a `reload` method which will be loading and displaying our data:

	* sets the `temperatures` property to `TEST_TEMPERATURES` (we will change it to real data later),
	* calls `show`.

* Upon the click of the button, call the `reload` method. Check if the temperatures are properly displayed.

Inheritance ([`extends`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends))
allows us to create a sub-type with different behaviour (for example `class Dog extends Animal`).
In our case, we will extend the `Forecast` class to change its data source:
the child class `ForecastOnline` will download its data from the internet to provide a real forecast.

* Create the class `ForecastOnline` which overrides the `reload` method
	and sets the temperature to `[2, 3, 4, 5, 6, 7, 8]` (we will get the real data in the next section).
	Instantiate `ForecastOnline` with div with id `weather-part3` and test if it shows the temperatures.

	<img src="task_images/result_from_inheritance.png" width="640" />

## `fetch`ing JSON data from the internet

The data displayed in a visualization is most often not part of the code.
Instead it is stored in data files and downloaded separately from our server or an external service.

This data can be downloaded using the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch).
Fetching is an asynchronous operation (we have to wait some time for the response), therefore it uses [JS Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise).
Please read the linked documentation to see the examples.

We can get a forecast in the JSON format using Yahoo Weather, for example the query for Lausanne is:
```
http://query.yahooapis.com/v1/public/yql?format=json&q=select * from weather.forecast where woeid in (select woeid from geo.places(1) where text="Lausanne") and u="c"
```

* Use `fetch` to download the JSON from this URL, convert the JSON to a JS object and store the result to a global variable.
	Experiment with that value in the developer console to find out how to get the temperatures.

* Create a function `yahooToTemperatures` which will extract the temperatures from the data.
	Since the API provides `low` and `high` temperature bounds, please calculate the mean of those values and return it as the result.

* In `ForecastOnline`'s `reload` method, download the forecast from the specified URL and store it in the `temperatures` property, then call `show`. Please remember that `show` has to be executed after the data is downloaded (when the promise fires).

## Optional: Interactive choice of the city

If you feel confident with DOM, fetch and classes, let's combine them all into a more advanced system.

* Create a class `ForecastOnlineCity` which allows fetching the forecast for any city:

	* Add some mechanism of inputting the city name, for example a method `setCity`.

	* Override `reload` to fetch the URL for the chosen city.

	* Override `show` to also display the name of the city.
		You can use `super.show()` to call the method in the parent class.
		[`insertBefore`](https://developer.mozilla.org/en-US/docs/Web/API/Node/insertBefore) can be useful to insert the city name before the temperature.

* Upon the click of the button with id `btn-city`, read the `.value` of the input with id `query-city`,
	then use your `ForecastOnlineCity` object to perform the query.

	<img src="task_images/interactive.png" width="640" />


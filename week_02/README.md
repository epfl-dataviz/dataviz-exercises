
# JavaScript basics

In this exercise we will practice programming with (JavaScript)[https://developer.mozilla.org/en-US/docs/Web/JavaScript],
which we will need to create interactive visualizations in the browser.
Today we will focus on processing data in JS, the functions used to plot the data are provided.

We would like to practice the functional style of programming, because it fits well with the d3.js library which we are going to use for the visualizations.
This means that instead of `for` or `while` loops to iterate over arrays, we would use
[`forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach),
[`map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map),
[`reduce`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce) and
[`filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
- if you haven't seen them before, please take a look at the linked documentation which contains intuitive examples.

Please write your solutions in `exercise/exercise.js` and open the site [`exercise/index.html`](exercise/index.html) to execute them. Reload the page to re-run your script after applying changes.
Remember that you can use the developer tools to interactively call your functions or see the values of variables.

## Functions and iteration

### isEven
Let's try a basic function `isEven` that will check if an integer is divisible by 2.

Then apply it over an array of integers to see the results:

* Apply `isEven` to each element of `[1, 2, 3, 4, 5]` using [`map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).

* Choose even numbers from `1...5` by using [`filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter).

### multiply
Now, imagine, you do not know how many numbers in your array. In JS, there is a way to create functions with arbitrary number of parameters. This is also called [Spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax). Let's implement a function `multiply` that computes a product of all numbers specified as parameters. For example, `multiply(1,2,3,4,5)` should return `120`.

## Closures

In JS, functions are treated as objects.
When a function is created, it has access to all currently visible variables -
the newly created function and these variables form a closure.
The details are in the [documentation about closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures).



### divisibleBy
Let's generalize the above example, and create the function `divisibleBy` which:

* takes an argument `divisor`
* returns a function `f` such that `f(x)` returns `true` when `x` is divisible by `divisor`

The [arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) syntax is a convenient way to construct functions.

Now we have an alternative solution to the previous task `const isEvenNew = divisibleBy(2)`.
Try filtering `[0, 1, 2, 3, 4, 5, 6]` by `divisibleBy(3)`.


### increment

Sometimes, in JS, you will have to deal with nested functions. Implement a function `increment` such that it can be called as `increment(100)(2)` with the first parameter as an initial value (`0` as a default parameter) and second params as a step size (`1` as a default parameter).

### colorCycle

In plots, we often want to apply different colors, for example to distinguish between lines illustrating different quantities.
When making a general mechanism, we can't predict how many colored objects there are going to be, so we will
make the colors repeat in a cycle.

Create a function `colorCycle` such that

* it takes one argument: an array of colors,
* the default value of the the color array is `COLOR_CYCLE_DEFAULT`
* it returns a function which repeats the colors in the cycle, for example

	```
	cc = colorCycle(['red', 'green']);
	console.log([cc(), cc(), cc(), cc()]); // ['red', 'green', 'red', 'green']
	```

Now create a cycle `my_cc` with your chosen colors and run `showColorCycle(my_cc)` to apply the colors to a demo plot on the website [`index.html`](exercise/index.html).

<img src="task_images/color_cycle.png" width="640" />


## Range

In the above task, we were writing the sequences `[1, 2, ..., N]` explicitly, now let's automate it.

* Create a function `range(N)` which constructs a range of integers [0, 1, ..., N-1].

	For an additional challenge, you can try using a functional approach, that is without a `for` or `while` loop.

	We could try creating an empty array of size `N`: `Array(N)`. However, the elements of the array are not created and `forEach` or `map` does nothing.
	Try it yourself: `Array(10).forEach(console.log)`

	[Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) allows us to create an array from another sequence -
	for example convert a string to an array like we did with letter counting.
	`Array.from(Array(10))` actually creates the elements and we could iterate over them (the elements are `undefined`).

	Additionally, we can pass a function as the second argument - this function will be applied on every element of the newly created array.
	`Array.from(seq, f)` is equivalent to `Array.from(seq).map(f)` but more efficient because it does not create the intermediate array.
	Remember that the mapping function receives as arguments both the current element and the current index.

* Let's find the integers from 0 to 100 which are divisible by 13.
	Create a range `[0, ..., 99]` and filter it by divisibility by 13


* Implement a function `randomInRange(min_val=0, max_val=100)` which returns a random float value between `min_val` and `max_val`.

* Implement a function `randomArray(N, min_val=0, max_val=100)` which generates an array of `N` random values between `min_val` and `max_val`.

## Counting

* Create a function `countOccurences(string)` which counts the number of occurences of each letter in a string.
	For example `countOccurences("hello")` yields `{'h': 1, 'e': 1, 'l': 2, 'o': 1 }`.
	A string is not an array and it does not have the `forEach` or `map` methods, so to use them, convert a string to an array with [Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from), for example `let a = Array.from('a string!');`.

	To store the counts, use an [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
	which is key-value container with strings as keys (in our case, the key will be the letter).

	To perform functional-style iteration over Objects, use
	[`Object.keys`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys),
	[`Object.values`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values) and
	[`Object.entries`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries).
	Please remember that they have to be called `Object.entries(obj)` instead of `obj.entries()`.

* Create the function `normalizeCounts` which takes the character counts outputted by `countOccurences`,
	and calculates normalized counts - that is divided by the total sum.
	Please calculate the sum using [`reduce`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce).
	For example:
	`normalizeCounts({'h': 1, 'e': 1, 'l': 2, 'o': 1})` yields `{'h': 0.2, 'e': 0.2, 'l': 0.4, 'o': 0.2}`

* Create `countOccurencesNormalized` - a function which given a string, first applies `countOccurences` and then normalizes the counts using `normalizeCounts`.

* Visualize the results by calling `setCharacterCountingFunction(countOccurencesNormalized);` - look at `index.html`, now you should be able to count the distribution
of characters in any text you input. You can pass a `colorCycle` with your colors as the second argument to color the bars.

<img src="task_images/character_counting.png" width="640" />

## Advanced exercise. Throwing balls (optional)

We will simulate a ball thrown at angle $b$ with velocity $v_0$. The initial velocity $(v_x, v_y)$ is:

$$v_x = v_0 cos(b)$$
$$v_y = v_0 sin(b)$$

The position of the ball at time $t$ is given by:

$$x(t) = v_x * t$$
$$y(t) = v_y * t + (a * t^2 * 0.5)$$

where $a$ is the acceleration caused by gravity, usually -9.81 $m/s^2$.

Implement a function `simulateBall(v0, angle, num_steps, dt, g)` such that:

* `v0` is the magnitude of the initial velocity

* 'angle' is the inclination angle in degrees, multiply by `DEG_TO_RAD = Math.PI / 180.` to get radians for the trigonometric functions,

* `num_steps` is the number of steps of the simulation, the default value should be 256,

* `dt` is the time that advances between steps, default value 0.05,

* `g` is the acceleration, default value -9.81,

* it returns an array of ball positions at each time step,

* each position is given as a array `[x, y]`,

Use the `range` function to create the array of time points, then `map` them to the `[x, y]` values given by the equations above.

* We want to finish the plot when the ball hits the ground (y=0), so please filter the point array to remove points with y below 0.

* Visualize the ball trajectories using `plotBall` (the 2nd optional argument is the line color):

```
const ball_cc = colorCycle(['hsl(160, 100%, 64%)', 'hsl(200, 100%, 64%)', 'hsl(240, 100%, 64%)', 'hsl(120, 100%, 64%)', 'hsl(80, 100%, 64%)']);
plotBall(simulateBall(40, 60), ball_cc());
plotBall(simulateBall(40, 30), ball_cc());
plotBall(simulateBall(40, 45), ball_cc());
```

* Use `randomArray` to create 20 random angles between 0 deg and 90 deg, then plot the ball trajectories for each angle.

<img src="task_images/plot_ball_one.png" width="640" />


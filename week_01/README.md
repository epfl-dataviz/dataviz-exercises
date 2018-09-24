# Getting started


## Create a Slack account

Your pseudo should be in the format: firstname\_lastname\_SCIPER.
Example : kirell\_benzi\_20417X

[Now join the team!](https://join.slack.com/t/epfl-com480/shared_invite/enQtNDM0NTQ2NDM2MTUxLWEwNzQxNTYwZTFjZjk0YjZjZjc0ZTdlMWE0MGE2MzlhYTE0NDM2MTVhNDgzOWExNTNiNzA0MjhlOGI4MjFmODM)

**All communications will happen via Slack, it is mandatory that you
create an account.**

## Tools
For this exercise we will be using a web browser and a text editor with syntax highlighting,
for example [Chrome](https://www.google.com/chrome/) and [Atom](https://atom.io/).
Here you can find some [help with the installation](InstallationHelp.md).

You might also find the SVG editor [Inkscape](https://inkscape.org/en/) useful for inspecting and experimenting with SVG.

# Website

The goal of this course is to create an interactive visulization.
But in order to show it, we need to put it on a website - today we will practice building and styling the website.

We will use [`exercise/index.html`](./exercise/index.html) as our starting point. Open it in your browser to see the site.

The site source consists of the HTML `index.html` which is our content and of the stylesheet `style.css` which controls the appearance of the site. Please look at the comments in `style.css` for more details.

Now practice CSS by customizing the website according to your preferred style.

* First let's inspect the site content and style with the browser's developer tools.
	Read [Dev Tools overview](https://developer.chrome.com/devtools) and
	[Inspect styles](https://developers.google.com/web/tools/chrome-devtools/inspect-styles) for more info about dev-tools.
	Try changing the background of the first paragraph using the dev-tools:

	<img src="task_images/paragraph_green.png" width="640" />

* Edit the stylesheet `style.css` to adapt the site to your preferred visual style:

	* Change the background color of the title area, or use an image as background
	* Change the text colors
	* Add a shadow to the title
	* Add a box around the "How to use" section
	* Change the width of the content
	* Optional: use [css variables](https://developer.mozilla.org/en-US/docs/Web/CSS/--*) to avoid repetition.

Alternatively, you may decide to use a framework like [Bootstrap](https://getbootstrap.com) to build your site.

Below you can see the result of my edits. Your result can look similar or completely different based on your tastes.

<img src="task_images/site_customized.png" width="960" />

# SVG plot

[SVG](https://developer.mozilla.org/en-US/docs/Web/SVG) is a vector-graphics format, which means that instead of storing pixel values, it consists of objects to draw, such as circles, lines, other shapes and text.

In this course we will use SVG to draw our visualization.
To start, let's consider the plot placed on the example site, which is also an SVG image.

* Read the source of [`exercise/viz_plot.svg`](./exercise/viz_plot.svg) to see how it is constructed.
* Inspect the plot on the website using dev-tools. Like with HTML, you can edit them in the browser.
	Try to move the red dot up and change the color of the plot, to achieve the result shown below.
	(To change colors, read about [stroke and fill](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Fills_and_Strokes) - these properties control the contour of a shape and its interior.

	<img src="task_images/plot_devtooled.png" width="640" />

	[Inkscape](https://inkscape.org/en/) can also be useful for inspecting SVGs.

* The main plot is a *path* - a versative element that can describe a variety of shapes.
	Please read the [tutorial on paths](https://developer.mozilla.org/en-US/docs/Web/SVG/Tutorial/Paths) and edit the path's points to match the plot's shape (approximately) in the image below.


* 	Edit the colors of the elements (or in the stylesheet)
* 	Add the text label with a line pointing at the graph

This is the reference end result of the edits, but like with the website, you can choose the style that fits your preference.

<img src="task_images/plot_customized.png" width="960" />

# Extending the site

Create the sub-pages `description.html`, `data.html` (about your dataset) and `team.html` (about your team) by copying `index.html`. Later we will have more to put there but right now you can fill it with [placeholder text](http://www.blindtextgenerator.com/snippets).

# Practice CSS and HTML in an interactive game

CSS selectors determine which elements the style is applied to.
They help separating content from style and prevent repetition.

* Practice CSS selectors in a game - [CSS Diner](https://flukeout.github.io/)

* Practice the [quiz about HTML elements](http://www.landofcode.com/html-quiz/)

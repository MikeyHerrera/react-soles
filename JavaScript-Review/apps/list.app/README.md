# List App

## Setting Up a Web Server
We will be using live-server to set up a web server for local development. Download it with the following command

`npm install -g live-server`

You can then create a local web page with the following command:

`live-server <path-to-folder>`

You can also specify a browser you want to use like so:

`live-server <path-to-folder> --browser='Google Chrome'`

I will be using Google Chrome for the rest of the lesson, so feel free to download it if you aren't using it.

Live-server is extremely useful, as you can make changes and have your local web page update automatically.

## Using Chrome Developer Tools
You can use the console in Chrome Developer Tools to inspect elements of HTML pages and look at the console that can be used to debug your JavaScript file. You can access it by clicking on the three dots in the upper right corner -> More Tools -> Developer Tools. The Elements tab shows the HTML page while the Console tab shows the output from console from the JavaScript file. 

## Practice HTML
Put the following code into index.html.
```
<!DOCTYPE <!DOCTYPE html>
<html>
    <head>
    </head>
    <body>
        <h1>List App</h1>
        <h2>Create your list!</h2>
<<<<<<< HEAD
        <p>Created by <Your Name Here></p>
=======
        <p id="first"> Let's get started</p>
        <p id="second"> I love SOLES</p>
        <input>
        <button> Create List Item </button>
>>>>>>> e191de61267948ce5d69aac27e147fb1d2768fc9
        <script src="list-app.js"></script>
    </body>
</html>
```

## Document Object Model (DOM)
The DOM allows you to change elements in HTML in JavaScript. You use the global variable `document` in the JavaScript file to access the DOM. 

### Document Methods/Properties Review

#### querySelector
You can access an element from its tag by using the `querySelector` method. This method grabs the first element with the `<p>` tag. If you put this code in the list-app.js file, you will get `<p> Let's get started! </p>`.

```
const pElement = document.querySelector('p');
console.log(pElement);
```

You can also select an element by its id. The syntax is shown below.
```
const pElement = document.querySelector('#second');
console.log(pElement);
```

#### querySelectorAll
You can grab all elements with `<p>` tags by using the `querySelectorAll` method.

```
const pElements = document.querySelectorAll('p');
console.log(pElements);
```

#### remove
You can use the `remove` method to remove an element via the DOM. You can see how you can use integrate forEach to loop through each element in pElements. Now all elements with `<p>` will be removed from the web page.

```
const pElements = document.querySelectorAll('p');
pElements.forEach(function(pElement) {
    pElement.remove()
})
```

#### textContent
You can also access the text content of an element by using the `textContent` property. The following example adds an exclamation point to each of the `<p>` elements.

```
const pElements = document.querySelectorAll('p');
pElements.forEach(function(pElement) {
    pElement.textContent += '!';
})
```

### Adding Elements via the DOM

To create a new element at the end of body element, follow these steps.

#### Create Element and Add Content
You will first need to create a DOM element with the `createElement` method. You can specify what element tag you want. The following line will create a paragraph element. You can then add content by setting the textContent that we used previously.
```
const paragraphElement = document.createElement('p');
paragraphElement.textContent = 'I am a new paragraph!';
```
#### Appending to Body Tag
Now that the paragraph element is created, use the `appendChild` method to append the paragraph element. To append it to the end of the body tag, you first must use `querySelector` to get that element. Try the code above and below in the list-app.js to see your new paragraph element!

```
document.querySelector('body').appendChild(paragraphElement);
```

### Handle User Interaction
You probably have noticed the `Create List Item` button on the web page. As of now, the button is pretty useless, so let's change that. 

First, grab the button element by using `querySelector`.
```
const listButton = document.querySelector('button')
```

Next, use the `addEventListener` object to have something happen whenever the button is clicked. The first parameter is the type of event (in this scenario, it is `"click"`. The second argument is a callback function. Use the parameter e to get information regarding the event that occured. Use this code in this section to have the button change to `I'm different` when the button is clicked.
```
listButton.addEventListener('click', function(e) {
e.target.textContent = "I'm different"
})
```
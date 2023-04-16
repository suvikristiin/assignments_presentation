# Presenting the Trainee Academy Assignments
Welcome to my GitHub repository! Here I will present in more detail some of the assignments I completed during the Buutti Trainee Academy. These tasks have allowed me to utilize various front-end programming concepts I learned during my training, such as HTML, CSS, and JavaScript. As the training progresses, I plan to update this repository with my new React programming skills.

I carefully select every task I add to this repository. These tasks have been particularly interesting and educational for me, and completing them has deepened my understanding of web development and strengthened my programming skills.

Note that this repository only contains presentations and reflections on the assignments, as well as the essentials parts of the solutions. The complete versions of the solutions can be found in [this repository](https://github.com/suvikristiin/trainee_academy_assignments.git).

## Assignment 1: Fake Store API
In this assignment, I will create a simple web page using JavaScript, HTML, and CSS and retrieve the information presented on the page from an external API using Axios.

I have chosen this assignment to demonstrate my ability to build websites using these techniques. I have implemented many similar projects and now I am confident that I know how to use these technologies well and effectively. Additionally, I aim to demonstrate my ability to work with external APIs, which is an important skill in modern web development. 

In summary, the purpose of this assignment is to showcase my ability to utilize APIs in my projects and build dynamic and visually appealing web pages using JavaScript, CSS, and HTML.
### Instructions for the assignment
Create an HTML page with JavaScript that makes a request to the Fake Store API (https://fakestoreapi.com/docs/) and retrieves the products. The products to be returned should be displayed on the page as a list with their name and price, as in the following example:

- Fjallraven - Foldsack No. 1 Backpack, Fits 15 Laptops $109.95
- Mens Casual Premium Slim Fit T-Shirts  $22.3

For each product, add a delete button that sends a DELETE request to the API with the product ID. When the API responds, the corresponding product should be removed from the page.
### Solution and thoughts during the assignment
The first thing I need to do is choose a technology to request data from the API. For this task, I chose the open-source library Axios because of its user-friendliness and built-in error handling support. In addition, Axios works with both browser-based JavaScript and server-side JavaScript environments.

We can quickly add Axios to our web project via CDN, or we can add it to our project using npm. However, Npm Axios is a package for Node.js, a JavaScript runtime environment that allows us to run JavaScript outside of a web browser. If we want to use Axios with vanilla JavaScript in the browser, we need to include the Axios library in the HTML file. However, this approach has some drawbacks. Managing large amounts of dependencies can be challenging and can slow down web page load times. Since we don't have any problems with load times or large dependencies in this case, we added the Axios library to our project using npm. I added the axios library to the project as follows:
1. Let's initialize the npm project. This command creates a default package.json file in the directory.
```sh
npm init -y
```
2. Let's then install the Axios library using npm:
```sh
npm install axios
```
3. Let's add the axios library to the html file. The node_modules directory must be located in the same directory as the html file.
```html
<script src="./node_modules/axios/dist/axios.min.js"></script>
```
Now that we can use the Axios library to make a GET request, let's create the CSS and JavaScript files and add code to the JavaScript file that uses Axios to make a GET request to the API endpoint 'https://fakestoreapi.com/products', retrieve the products from the FakeStore API, and extract the products from the response data into a table:
```js
axios.get("https://fakestoreapi.com/products").then((response) => {
    const products = response.data;
```
After searching for products, I created an unordered list using the document.createElement() method and added it to the body element. I also realized, which I think is a useful feature, that I can use the forEach() method to iterate through each product and create a div element for each one. Within the div element, I added a list item element that lists the desired information and a delete button.
```js
const body = document.getElementById("body");
const productList = document.createElement("ul");
body.appendChild(productList);
// Loop through each product and create a list item for each one
products.forEach((product) => {
    const productDiv = document.createElement("div");
    const listItem = document.createElement("li");
    listItem.innerHTML = `${product.title} $${product.price}`;
    const deleteButton = document.createElement("button");
    deleteButton.innerHTML = "DELETE";
```
I also added an event listener to the delete button that sends a delete request to the FakeStore API endpoint of a specific product using the axios library. If the request succeeds, it removes the product div element from the page. If an error occurs, it logs the error to the console. Finally, the created elements are combined so that they appear as a list on the page.
```js
deleteButton.addEventListener("click", () => {
    axios.delete("https://fakestoreapi.com/products/" + product.id)
    .then(() => {
        productDiv.remove();
    })
    .catch((error) => {
        console.log(error);
    });
});

productList.appendChild(productDiv);
productDiv.appendChild(listItem);
productDiv.appendChild(deleteButton);
```
Of course, I also wanted to make the web page look nice even though it was not asked for in the assignment, so I added some css styles to it. In the end, the web page looks like this:
![](/fakestore.png)

## Assignment 2: Count letters
I chose this task because it is simple, yet it effectively tests and teaches various programming concepts with JavaScript, including looping constructs and manipulating objects and strings. Initially, I found the task challenging, particularly due to the use of objects. However, I persevered and am now satisfied with my final solution. Throughout the entire trainee academy, I have made significant progress in working with objects and other programming fundamentals through trial and error and helpful code examples.
### Instructions for the assignment
Create a function getCountOfLetters that counts the number of each letter in a string and returns the data in an object.

For example:
```js
const result = getCountOfLetters("a black cat");
console.log(result);
/* prints 
{
	a: 3,
	b: 1,
	c: 2,
	k: 1,
	l: 1,
	t: 1
}
*/
```
### Solution and thoughts during the assignment
First, I decide to use a for loop to iterate through each character of the input string. I also decide to initialize an empty object at the beginning. If the iterated character is not already in the object, I would add it to the object with a value of 1. Otherwise, I would simply increase its value by one. I should also skip spaces in the for loop using a conditional statement. 
```js
for (let i in str) {
    if (str[i] === " ") { 
        continue;
    } else if (str[i] in count) {
        count[str[i]]++;
    } else {
        count[str[i]] = 1;
    }
}
```
At the end of the assignment, I realized that I should sort the object in alphabetical order based on the keys. Initially, this was a bit challenging because I wanted to sort the object keys using the ```Object.keys(obj).sort()``` command. This sorts the object keys but returns them as an array. However, I need to return a sorted object that displays the count of each letter in the input string. 

After many attempts, I realized that I could initialize an empty return object and use the forEach method to iterate through the sorted object keys. At the same time, I could add each key-value pair to the return object.
```js
const sortedCount = Object.keys(count).sort();
const returnObject = {};
sortedCount.forEach(key => returnObject[key] = count[key]);
```

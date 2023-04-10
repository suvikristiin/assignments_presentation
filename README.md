# Presenting the Trainee Academy Assignments
Welcome to my GitHub repository! Here I will present in more detail some of the assignments I completed during the Buutti Trainee Academy. These tasks have allowed me to utilize various front-end programming concepts I learned during my training, such as HTML, CSS, and JavaScript. As the training progresses, I plan to update this repository with my new React programming skills.

I carefully select every task I add to this repository. These tasks have been particularly interesting and educational for me, and completing them has deepened my understanding of web development and strengthened my programming skills.

Note that this repository only contains presentations and reflections on the assignments, as well as the essentials parts of the solutions. The complete versions of the solutions can be found in [this repository](https://github.com/suvikristiin/trainee_academy_assignments.git).

## Assignment 1: Count letters
I chose this task because it is simple, yet it effectively tests and teaches various programming concepts, including looping constructs and manipulating objects and strings. Initially, I found the task challenging, particularly due to the use of objects. However, I persevered and am now satisfied with my final solution. Throughout the entire trainee academy, I have made significant progress in working with objects and other programming fundamentals through trial and error and helpful code examples.
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

At the end of the assignment, I realized that I should sort the object in alphabetical order based on the keys. Initially, this was a bit challenging because I wanted to sort the object keys using the ```Object.keys(obj).sort()``` command. This sorts the object keys but returns them as an array. However, I need to return a sorted object that displays the count of each letter in the input string. 

After many attempts, I realized that I could initialize an empty return object and use the forEach method to iterate through the sorted object keys. At the same time, I could add each key-value pair to the return object.
```js
function getCountOfLetters(str) {
    const count = {};

    for (let i in str) {
        // Ignore whitespace characters
        if (str[i] === " ") { 
            continue;
        // If the character is already in the count object, increment its count
        } else if (str[i] in count) {
            count[str[i]]++;
        // If the character is not in the count object, add it with a count of 1
        } else {
            count[str[i]] = 1;
        }
    }
    
    // Sort the keys of the count object alphabetically
    const sortedCount = Object.keys(count).sort();
    const returnObject = {};
    // Loop through the sorted keys and add them to the return object
    sortedCount.forEach(key => returnObject[key] = count[key]);
    
    return returnObject;
}
```

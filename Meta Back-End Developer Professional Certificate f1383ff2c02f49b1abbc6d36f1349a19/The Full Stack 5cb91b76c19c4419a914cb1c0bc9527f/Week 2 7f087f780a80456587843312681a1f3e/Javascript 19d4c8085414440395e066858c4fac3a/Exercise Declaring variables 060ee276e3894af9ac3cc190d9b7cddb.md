# Exercise: Declaring variables

In this exercise, you will practice declaring variables.

To check the output of your code, please enter it into the text box provided and click the "Run" button. This will execute the code and display the resulting output.

# Tasks

1. Declare a new variable named **petDog** and give it the name **Rex**.
2. Declare a new variable named **petCat** and give it the name **Pepper**.
3. Console.log the **petDog** variable.
4. Console.log the **petCat** variable.
5. Console.log the text **"My pet dog's name is: "** and the **petDog** variable.
6. Console.log the text **"My pet cat's name is: "** and the **petCat** variable.
7. Declare another variable and name it **catSound**. Assign the string of **"purr"** to it.
8. Declare another variable and name it **dogSound**. Assign the string of **"woof"** to it.
9. Console.log the variable **petDog**, then the string **"says"**, then the variable **dogSound**.
10. Console.log the variable **petCat**, then the string **"says"**, then the variable **catSound**.
11. Reassign the value stored in **catSound** to the string **"meow"**.
12. Console.log the variable **petCat**, then the string **"now says"**, then the variable **catSound**.

Make sure to output all your variables. Feel free to play.

```css
var petDog = "Rex"
var petCat = "Pepper"
console.log(petDog)
console.log(petCat)
console.log("My pet dog's name is: ", petDog)
console.log("my pet cat's name is: ", petCat)
var catSound = "purr";
var dogSound = "woof";
console.log(petDog, "says ", dogSound)
console.log(petCat, "says ", catSound)
catSound = "meow"
console.log(petCat, "says " , catSound)
```

```css
Rex
Pepper
My pet dog's name is:  Rex
my pet cat's name is:  Pepper
Rex says  woof
Pepper says  meow
```
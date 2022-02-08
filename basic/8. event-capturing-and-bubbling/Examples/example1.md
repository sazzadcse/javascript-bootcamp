
We already know the basics of event capturing and bubbling. 
In this example, we will dive a little deeper. 
The third argument of 'addEventListener' function tell 
whether the event will be in the capture phase or in the bubbling phase. 
By default it is in bubbling phase (if we provide no parameter) 

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Bubbling and Capturing</title>
    <!-- Some css to identify the divs easily -->
    <style>
        div {
            border: 1px solid black;
        }
        #grandparent {
            background-color: green;
            width: 300px;
            height: 300px;
        }
        #parent {
            background-color: blue;
            width: 200px;
            height: 200px;
        }
        #child {
            background-color: red;
            width: 100px;
            height: 100px;
        }
    </style>
</head>
<body>
    <div id="grandparent">
        Grandparent
        <div id="parent">
            Parent
            <div id="child">
                Child
            </div>
        </div>
    </div>
    <script>
        const grandparent = document.getElementById("grandparent")
        const parent = document.getElementById("parent")
        const child = document.getElementById("child")
        // bubbling
        grandparent.addEventListener("click", ()=> {
            console.log("Grandparent clicked");
        }, false)
        // capturing or trickling
        parent.addEventListener("click", ()=> {
            console.log("Parent clicked");
        }, true)
        // bubbling
        child.addEventListener("click", ()=> {
            console.log("Child clicked");
        }, false)
    </script>
</body>
</html>

```

Run the code. now click on the child div. We can see that the output will be.

Output: 
Parent clicked
Child clicked
Grandparent clicked

We can see that the event capturing of event listeners happened first 
and then the event bubbling happened.
This means the propagation of event listeners first goes from 
outside to inside and then from inside to outside in the DOM. 
As 'parent' div is propagated, it prints to the console first,
then by follwing event capturing rules, 'child' div is clicked
and 'grandparent' div is clicked.

I hope things are clear now. We can play with this code as we want
and see different output.

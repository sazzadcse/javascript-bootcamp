We can stop event capturing and bubbling if we want.
We can use a parameter "e" in the callback function of 
addEventListener function. It is an event object
which has a function called stopPropagation() which helps
to stop event capturing and bubbling.

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>How to stop Event Capturing and Bubbling</title>
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
        grandparent.addEventListener("click", (e)=> {
            console.log("Grandparent clicked");
        })
        // bubbling
        parent.addEventListener("click", (e)=> {
            console.log("Parent clicked");
            e.stopPropagation()
        })
        // bubbling
        child.addEventListener("click", (e)=> {
            console.log("Child clicked");
        })
    </script>
</body>
</html>

```

Output:
Child clicked
Parent clicked

If we clicked on child div, the propagation is stopped 
on parent div and does not move to grandparent div. 
Hence, the event bubbling is prevented. 
We can also stop capturing the same way.
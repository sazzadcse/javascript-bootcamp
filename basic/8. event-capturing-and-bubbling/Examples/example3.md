
ইফেক্ট বুঝতে হলে প্রথমে এই HTML ফাইলটি আপনার ব্রাউজারে ওপেন করে মাউসের রাইট বাটন ক্লিক করে Inspect এ ক্লিক করুন।
অতঃপর Console ট্যাবে ক্লিক করুন। এখন Event Bubbling ও Event Capturing কিভাবে হচ্ছে সেটা বুঝতে বক্সগুলোতে
ক্লিক করে দেখুন। 

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Event Bubbling and Capturing</title>

    <!-- CSS Style for Better Visualization -->
    <style>
        body {
            height: 100vh;
        }
        h2 { text-align: center; }
        .mid {
            display: flex;
            justify-content: space-around;
            align-items: center;
            cursor: pointer;
        }
        .hw300 {
            height: 300px;
            width: 300px;
        }
        .hw200 {
            height: 200px;
            width: 200px;
        }
        .hw100 {
            height: 100px;
            width: 100px;
        }
        #red { background-color: red; }
        #green { background-color: green; }
        #skyblue { background-color: skyblue; }
        #blue { background-color: blue; }
        #purple { background-color: purple; }
        #gold { background-color: goldenrod; }
    </style>
</head>
<body class="mid" style="cursor: auto;">
    <!-- Event Bubbling Section  -->
    <h2>
        Event Bubbling
        <div id="red" class="mid hw300">
            <div id="green" class="mid hw200">
                <div id="skyblue" class="mid hw100">
                    Click Me
                </div>
            </div>
        </div>
    </h2>

    <!-- Event Capturing Section -->
    <h2>
        Event Capturing
        <div id="blue" class="mid hw300">
            <div id="purple" class="mid hw200">
                <div id="gold" class="mid hw100">
                    Click Me
                </div>
            </div>
        </div>
    </h2>


    <!-- JavaScript Code for Functionality -->
    <script>
        const redDiv = document.querySelector('#red');
        const greenDiv = document.querySelector('#green');
        const skyblueDiv = document.querySelector('#skyblue');
        const blueDiv = document.querySelector('#blue');
        const purpleDiv = document.querySelector('#purple');
        const goldDiv = document.querySelector('#gold');

        // Event Bubbling Phase
        redDiv.addEventListener('click', () => {
            console.log('Red box clicked.');
        }, false)
        greenDiv.addEventListener('click', () => {
            console.log('Green box clicked');
        }, false)
        skyblueDiv.addEventListener('click', () => {
            console.log('Skyblue box clicked');
        }, false)
        
        // Event Capturing Phase
        blueDiv.addEventListener('click', () => {
            console.log('Blue box clicked.');
        }, true)
        purpleDiv.addEventListener('click', () => {
            console.log('Purple box clicked');
        }, true)
        goldDiv.addEventListener('click', () => {
            console.log('Golden box clicked');
        }, true)

        

    </script>

</body>
</html>

```

addEventListener() ফাংশনের তৃতীয় argument হিসেবে আমরা যে true/false ভ্যালু দিয়েছি সেটা বাই ডিফল্ট false থাকে অর্থাৎ nested element ক্লিক করার ক্ষেত্রে সেটা বাই ডিফল্ট event bubbling করে থাকে। বিষয়টি যদি অন্যভাবে বলি তাহলে বলা যায় যে তৃতীয় আর্গুমেন্টে জিজ্ঞাসা করা থাকে এই event টি প্রথমে capture করা হবে নাকি হবে না।
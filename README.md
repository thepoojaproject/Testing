
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Styled Clickable Image Link</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: #f0f0f0; /* Keeping the light background */
        }
        /* Styling for the clickable container, like the button you provided */
        .image-button-container {
            background-color: white; /* White background */
            padding: 15px 30px; /* Adjust padding to give space around the image */
            border-radius: 12px; /* More rounded corners, similar to the button image */
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1); /* Stronger, but still subtle shadow */
            display: inline-flex; /* Use inline-flex to shrink-wrap content and center it */
            justify-content: center;
            align-items: center;
            cursor: pointer; /* Indicate it's clickable */
            text-decoration: none; /* Remove underline from the link */
            transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out; /* Smooth hover effects */
        }

        .image-button-container:hover {
            transform: translateY(-2px); /* Lift effect on hover */
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15); /* Slightly stronger shadow on hover */
        }

        img {
            width: 250px; /* Keep the image width */
            height: auto; /* Maintain aspect ratio */
            display: block; /* Ensure no extra space */
            /* No need for cursor: pointer here, as it's on the container now */
        }
    </style>
</head>
<body>

<a href="http://hack.chat/?(Hello)" class="image-button-container">
    <img src="https://i.ibb.co/20jcjKbs/image.png" alt="image">
</a>

</body>
</html>

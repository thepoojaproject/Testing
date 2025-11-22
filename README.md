
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Styled Clickable Image Link (Black Background with Footer)</title>
    <style>
        body {
            /* Changed body to use position: relative to act as a reference for the footer */
            position: relative; 
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: #000000;
            /* Added padding-bottom to ensure the centered content doesn't overlap the footer */
            padding-bottom: 50px; 
        }

        /* Styling for the clickable container (the white box) */
        .image-button-container {
            background-color: white;
            padding: 15px 30px;
            border-radius: 12px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            display: inline-flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            text-decoration: none;
            transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
        }

        .image-button-container:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }

        img {
            width: 250px;
            height: auto;
            display: block;
        }
        
        /* NEW FOOTER STYLES */
        footer {
            position: absolute; /* Allows positioning relative to the body */
            bottom: 20px; /* 20 pixels from the bottom */
            width: 100%;
            text-align: center;
            color: #888888; /* A light grey color to contrast with the black background */
            font-family: sans-serif;
            font-size: 14px;
        }
    </style>
</head>
<body>

<a href="http://hack.chat/?(Hello)" class="image-button-container">
    <img src="https://i.ibb.co/20jcjKbs/image.png" alt="image">
</a>

<footer>
    Made in ❤️ By Armeen
</footer>

</body>
</html>

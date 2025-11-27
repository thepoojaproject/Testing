
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Background Remover</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f8f9fa;
            text-align: center;
            padding: 40px;
        }
        .container {
            background: white;
            padding: 25px;
            border-radius: 12px;
            max-width: 450px;
            margin: auto;
            box-shadow: 0 0 15px rgba(0,0,0,0.1);
        }
        img {
            width: 100%;
            margin-top: 20px;
            border-radius: 10px;
        }
        #upload {
            margin: 20px 0;
        }
        button {
            padding: 10px 15px;
            font-size: 16px;
            border: none;
            background: #4caf50;
            color: white;
            border-radius: 8px;
            cursor: pointer;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Remove Image Background</h2>

    <input type="file" id="upload" accept="image/*">
    <button onclick="removeBG()">Remove Background</button>

    <div id="result"></div>
</div>

<script>
async function removeBG() {
    const fileInput = document.getElementById("upload");
    if (!fileInput.files.length) {
        alert("Please upload an image!");
        return;
    }

    const formData = new FormData();
    formData.append("image_file", fileInput.files[0]);
    formData.append("size", "auto");

    const res = await fetch("https://api.remove.bg/v1.0/removebg", {
        method: "POST",
        headers: {
            "X-Api-Key": "fPq6PiUgdfrcE3HLLTckqsCA"
        },
        body: formData
    });

    const blob = await res.blob();
    const url = URL.createObjectURL(blob);

    document.getElementById("result").innerHTML =
        `<img src="${url}" alt="Removed Background Image">`;
}
</script>

</body>
</html>

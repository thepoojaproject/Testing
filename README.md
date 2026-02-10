<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Advanced Video to GIF</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #eaeaea;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.app {
  background: #fff;
  padding: 20px;
  width: 380px;
  border-radius: 10px;
  box-shadow: 0 10px 25px rgba(0,0,0,.15);
}

h2 {
  text-align: center;
  margin-bottom: 15px;
}

input, button {
  width: 100%;
  margin: 6px 0;
  padding: 8px;
  font-size: 14px;
}

label {
  font-size: 13px;
  color: #444;
}

button {
  background: #111;
  color: #fff;
  border: none;
  cursor: pointer;
}

button:disabled {
  background: #999;
}

#status {
  font-size: 13px;
  margin-top: 8px;
  text-align: center;
}

img {
  max-width: 100%;
  margin-top: 10px;
  border-radius: 6px;
}
</style>
</head>
<body>

<div class="app">
  <h2>Video → GIF</h2>

  <input type="file" id="videoFile" accept="video/*">

  <label>Start Time (sec)</label>
  <input type="number" id="start" value="0">

  <label>End Time (sec)</label>
  <input type="number" id="end" value="3">

  <label>Width (px)</label>
  <input type="number" id="width" value="320">

  <label>FPS</label>
  <input type="number" id="fps" value="10">

  <button id="convertBtn">Convert to GIF</button>

  <div id="status"></div>
  <img id="result">
</div>

<script src="https://unpkg.com/@ffmpeg/ffmpeg@0.12.6/dist/ffmpeg.min.js"></script>
<script>
const { createFFmpeg, fetchFile } = FFmpeg;
const ffmpeg = createFFmpeg({ log: true });

const btn = document.getElementById("convertBtn");
const status = document.getElementById("status");

btn.onclick = async () => {
  const file = document.getElementById("videoFile").files[0];
  if (!file) return alert("Please upload a video");

  btn.disabled = true;
  status.innerText = "Loading FFmpeg...";

  if (!ffmpeg.isLoaded()) await ffmpeg.load();

  status.innerText = "Processing video...";

  const start = document.getElementById("start").value;
  const end = document.getElementById("end").value;
  const width = document.getElementById("width").value;
  const fps = document.getElementById("fps").value;

  ffmpeg.FS("writeFile", "input.mp4", await fetchFile(file));

  await ffmpeg.run(
    "-ss", start,
    "-to", end,
    "-i", "input.mp4",
    "-vf", `fps=${fps},scale=${width}:-1:flags=lanczos`,
    "-gifflags", "+transdiff",
    "output.gif"
  );

  const data = ffmpeg.FS("readFile", "output.gif");
  const gifURL = URL.createObjectURL(
    new Blob([data.buffer], { type: "image/gif" })
  );

  document.getElementById("result").src = gifURL;
  status.innerText = "Done ✅ GIF Ready";
  btn.disabled = false;
};
</script>

</body>
</html>

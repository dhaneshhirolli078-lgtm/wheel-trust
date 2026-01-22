<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Advanced Video Editor</title>
<style>
  body { font-family: Arial; background:#0f172a; color:#fff; margin:0; padding:20px; }
  h1 { text-align:center; }
  .editor { display:grid; grid-template-columns: 2fr 1fr; gap:20px; }
  video { width:100%; background:#000; }
  .panel { background:#111827; padding:15px; border-radius:10px; }
  label { display:block; margin-top:10px; }
  input, button {
    width:100%; padding:8px; margin-top:5px;
    border:none; border-radius:6px;
  }
  button { background:#22c55e; color:#000; font-weight:bold; cursor:pointer; }
  button:hover { background:#16a34a; }
</style>
</head>

<body>
<h1>🎬 Advanced Video Editor (Web)</h1>

<div class="editor">
  <!-- Video Preview -->
  <div>
    <video id="video" controls></video>
  </div>

  <!-- Controls -->
  <div class="panel">
    <label>Upload Video</label>
    <input type="file" accept="video/*" id="upload">

    <label>Trim Start (seconds)</label>
    <input type="number" id="start" value="0">

    <label>Trim End (seconds)</label>
    <input type="number" id="end" value="10">

    <label>Overlay Text</label>
    <input type="text" id="text" placeholder="Enter text">

    <button onclick="applyEdit()">Apply Preview</button>
  </div>
</div>

<script>
const video = document.getElementById("video");
const upload = document.getElementById("upload");

upload.onchange = e => {
  const file = e.target.files[0];
  if(file){
    video.src = URL.createObjectURL(file);
  }
};

function applyEdit(){
  const start = parseFloat(document.getElementById("start").value);
  const end = parseFloat(document.getElementById("end").value);
  const text = document.getElementById("text").value;

  video.currentTime = start;
  video.play();

  // Stop at end time
  const stopVideo = () => {
    if(video.currentTime >= end){
      video.pause();
      video.removeEventListener("timeupdate", stopVideo);
    }
  };
  video.addEventListener("timeupdate", stopVideo);

  // Simple text overlay (preview)
  if(text){
    video.setAttribute("title", text);
    alert("Text overlay preview added (export step next).");
  }
}
</script>
</body>
</html>

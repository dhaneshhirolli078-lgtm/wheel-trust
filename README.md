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

  <!DOCTYPE html>
<html lang="kn">
<head>
    <meta charset="UTF-8">
    <title>ProEdit Studio - Kannada</title>
    <link rel="stylesheet" href="style.css">
    <script src="https://unpkg.com/@ffmpeg/ffmpeg@0.11.0/dist/ffmpeg.min.js"></script>
</head>
<body>
    <div class="editor-wrapper">
        <header class="main-header">
            <div class="logo">PRO EDIT 🎥</div>
            <div class="actions">
                <button onclick="document.getElementById('video-input').click()">+ Video</button>
                <button onclick="addTextOverlay()">+ Text</button>
                <button id="render-btn" class="render-btn">Export Video</button>
            </div>
            <input type="file" id="video-input" hidden accept="video/*">
        </header>

        <div class="workspace">
            <aside class="side-panel">
                <div class="panel-tab">Effects</div>
                <div class="effect-item" onclick="applyEffect('none')">Normal</div>
                <div class="effect-item" onclick="applyEffect('grayscale(100%)')">B&W</div>
                <div class="effect-item" onclick="applyEffect('invert(100%)')">Invert</div>
            </aside>

            <main class="viewer-section">
                <div class="canvas-container">
                    <video id="preview-video"></video>
                    <div id="text-overlay" class="draggable-text" contenteditable="true">ನಿಮ್ಮ ಶೀರ್ಷಿಕೆ ಇಲ್ಲಿ ಟೈಪ್ ಮಾಡಿ</div>
                </div>
                <div class="transport-controls">
                    <button onclick="playPause()">Play/Pause</button>
                </div>
            </main>
        </div>

        <footer class="timeline-v2">
            <div class="track-labels">
                <div>Video 1</div>
                <div>Audio 1</div>
            </div>
            <div class="timeline-scroll" id="timeline">
                <div class="playhead" id="playhead"></div>
                <div class="track video-t" id="video-track"></div>
                <div class="track audio-t" id="audio-track"></div>
            </div>
        </footer>
    </div>
    <script src="script.js"></script>
</body>
</html>
:root { --dark: #111; --panel: #1e1e1e; --accent: #f39c12; --blue: #2980b9; }

body { margin: 0; background: var(--dark); color: white; font-family: 'Segoe UI', sans-serif; }

.editor-wrapper { display: flex; flex-direction: column; height: 100vh; }

.main-header { background: #2c2c2c; padding: 10px 20px; display: flex; justify-content: space-between; border-bottom: 1px solid #333; }

.workspace { display: flex; flex: 1; overflow: hidden; }

.side-panel { width: 200px; background: var(--panel); padding: 10px; border-right: 1px solid #333; }

.effect-item { padding: 10px; margin-bottom: 5px; background: #333; cursor: pointer; border-radius: 4px; text-align: center; }

.viewer-section { flex: 1; display: flex; flex-direction: column; align-items: center; justify-content: center; position: relative; }

.canvas-container { position: relative; width: 80%; background: #000; }

video { width: 100%; height: auto; }

.draggable-text { position: absolute; top: 20%; left: 30%; color: white; font-size: 24px; cursor: move; border: 1px dashed transparent; }
.draggable-text:hover { border: 1px dashed #ccc; }

.timeline-v2 { height: 180px; background: #151515; display: flex; border-top: 2px solid #333; }

.track-labels { width: 80px; padding: 10px; font-size: 12px; display: flex; flex-direction: column; justify-content: space-around; background: #1a1a1a; }

.timeline-scroll { flex: 1; position: relative; overflow-x: auto; padding: 10px 0; }

.track { height: 40px; margin-bottom: 10px; background: #222; border: 1px solid #333; position: relative; width: 2000px; }

.video-clip { background: var(--blue); height: 100%; position: absolute; border-radius: 3px; }

.playhead { width: 2px; height: 100%; background: red; position: absolute; z-index: 10; pointer-events: none; }
const video = document.getElementById('preview-video');
const videoTrack = document.getElementById('video-track');
const playhead = document.getElementById('playhead');
const textOverlay = document.getElementById('text-overlay');

// 1. ವಿಡಿಯೋ ಇಂಪೋರ್ಟ್ ಮತ್ತು ಟೈಮ್‌ಲೈನ್ ಸೆಟಪ್
document.getElementById('video-input').addEventListener('change', function(e) {
    const file = e.target.files[0];
    video.src = URL.createObjectURL(file);
    
    video.onloadedmetadata = () => {
        const clip = document.createElement('div');
        clip.className = 'video-clip';
        clip.style.width = (video.duration * 20) + "px"; // 1s = 20px
        clip.innerText = "Video Layer";
        videoTrack.appendChild(clip);
    };
});

// 2. ಪ್ಲೇ/ಪಾಸ್ ಮತ್ತು ಟೈಮ್‌ಲೈನ್ ಸಿಂಕ್
function playPause() {
    video.paused ? video.play() : video.pause();
}

video.addEventListener('timeupdate', () => {
    playhead.style.left = (video.currentTime * 20) + "px";
});

// 3. ಟೆಕ್ಸ್ಟ್ ಓವರ್‌ಲೇ ಸೇರಿಸುವುದು
function addTextOverlay() {
    textOverlay.style.display = 'block';
}

// 4. ಎಫೆಕ್ಟ್‌ಗಳನ್ನು ಅನ್ವಯಿಸುವುದು (Color Grading)
function applyEffect(filterValue) {
    video.style.filter = filterValue;
}

// 5. ಎಕ್ಸ್‌ಪೋರ್ಟ್ (Export) ಲಾಜಿಕ್ - FFmpeg ಅಡಿಪಾಯ
document.getElementById('render-btn').onclick = async () => {
    alert("Rendering ಪ್ರಕ್ರಿಯೆ ಆರಂಭವಾಗಿದೆ... ದಯವಿಟ್ಟು ಕಾಯಿರಿ.");
    // FFmpeg.wasm ಬಳಸಿ ಇಲ್ಲಿ ಕಮಾಂಡ್ ರನ್ ಮಾಡಲಾಗುತ್ತದೆ
    // ಉದಾ: await ffmpeg.run('-i', 'input.mp4', '-vf', 'format=gray', 'output.mp4');
};

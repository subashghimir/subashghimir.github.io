<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Embed Video Generator</title>
  <style>
    body { font-family: Arial; margin: 2rem; }
    input { width: 100%; padding: 0.5rem; }
    button { padding: 0.5rem 1rem; margin-top: 1rem; }
    iframe { width: 100%; height: 360px; margin-top: 1rem; border: none; }
    pre { background: #eee; padding: 1rem; }
  </style>
</head>
<body>
  <h1>Video Embed Generator</h1>
  <input type="text" id="videoURL" placeholder="Paste video URL here" />
  <button onclick="generateEmbed()">Generate Embed</button>
  <div id="embedContainer"></div>
  <pre id="embedCode"></pre>

  <script>
    function generateEmbed() {
      const url = document.getElementById('videoURL').value;
      let embedHTML = '';
      let embedCode = '';

      if (url.includes('youtube.com') || url.includes('youtu.be')) {
        const videoId = url.split('v=')[1]?.split('&')[0] || url.split('/').pop();
        embedCode = `<iframe src="https://www.youtube.com/embed/${videoId}" frameborder="0" allowfullscreen></iframe>`;
      } else if (url.includes('vimeo.com')) {
        const videoId = url.split('/').pop();
        embedCode = `<iframe src="https://player.vimeo.com/video/${videoId}" frameborder="0" allowfullscreen></iframe>`;
      } else if (url.includes('dailymotion.com')) {
        const videoId = url.split('/video/')[1]?.split('_')[0];
        embedCode = `<iframe src="https://www.dailymotion.com/embed/video/${videoId}" frameborder="0" allowfullscreen></iframe>`;
      } else {
        document.getElementById('embedContainer').innerHTML = '<p style="color:red;">Unsupported video URL.</p>';
        document.getElementById('embedCode').textContent = '';
        return;
      }

      document.getElementById('embedContainer').innerHTML = embedCode;
      document.getElementById('embedCode').textContent = embedCode;
    }
  </script>
</body>
</html>

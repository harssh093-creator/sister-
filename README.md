# sister-
!doctype html>

<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>For My Sis — Deepu</title>
  <style>
    :root{--bg1:#ff9a9e;--bg2:#fad0c4;--accent:#fff;--card:#ffffffaa}
    *{box-sizing:border-box}
    body{margin:0;min-height:100vh;display:flex;align-items:center;justify-content:center;font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;background:linear-gradient(135deg,var(--bg1),var(--bg2));color:#222}
    .card{width:92vw;max-width:720px;background:var(--card);backdrop-filter:blur(6px);border-radius:20px;padding:28px;box-shadow:0 10px 30px rgba(0,0,0,0.12);text-align:center}
    h1{margin:0;font-size:28px;letter-spacing:1px}
    .heart{margin:18px auto 8px;width:110px;height:110px;border-radius:50%;display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg,#fff0,#fff);box-shadow:inset 0 -10px 30px rgba(255,255,255,0.15);}
    .heart svg{width:66px;height:66px}
    .name{font-size:44px;margin:8px 0 2px;font-weight:700}
    .sub{color:rgba(0,0,0,0.45);margin:0 0 16px}
    .btns{display:flex;gap:10px;justify-content:center}
    button{padding:10px 14px;border-radius:10px;border:0;background:#222;color:#fff;font-weight:600;cursor:pointer}
    button.ghost{background:transparent;color:#222;border:1px solid rgba(0,0,0,0.08)}
    footer{margin-top:14px;font-size:13px;color:rgba(0,0,0,0.5)}
    @media (max-width:420px){.name{font-size:32px}.heart{width:90px;height:90px}.card{padding:18px}}
  </style>
</head>
<body>
  <main class="card" id="card-root">
    <h1>For My Sis</h1>
    <div class="heart" aria-hidden>
      <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 20s-7.5-4.35-9.5-7.25C-0.25 7.5 5 4 7.5 6.5 9.5 8.5 12 11 12 11s2.5-2.5 4.5-4.5C19 4 24.25 7.5 21.5 12.75 19.5 15.65 12 20 12 20z" fill="#ff6b81"/>
      </svg>
    </div><div class="name" id="sister-name">Deepu</div>
<p class="sub">Tumhare liye special message — humesha khush raho ❤️</p>

<div class="btns">
  <button id="downloadBtn">Download as image</button>
  <button class="ghost" id="editBtn">Edit name</button>
</div>

<footer>Open this file locally or host it to share the exact page.</footer>

  </main>  <script>
    // Edit name button
    document.getElementById('editBtn').addEventListener('click', ()=>{
      const cur = document.getElementById('sister-name').textContent;
      const v = prompt('Enter name to show on card:', cur);
      if(v!==null) document.getElementById('sister-name').textContent = v.trim() || cur;
    });

    // Download as PNG using HTML2Canvas-like approach using canvas
    document.getElementById('downloadBtn').addEventListener('click', async ()=>{
      const el = document.getElementById('card-root');
      // create an offscreen canvas and draw a snapshot using foreignObject
      const w = el.offsetWidth * 2;
      const h = el.offsetHeight * 2;
      const svg = <?xml version='1.0' encoding='UTF-8'?><svg xmlns='http://www.w3.org/2000/svg' width='${w}' height='${h}'><foreignObject width='100%' height='100%'>${new XMLSerializer().serializeToString(el)}</foreignObject></svg>;
      const DOMURL = self.URL || self.webkitURL || self;
      const img = new Image();
      const svgBlob = new Blob([svg], {type: 'image/svg+xml;charset=utf-8'});
      const url = DOMURL.createObjectURL(svgBlob);
      img.onload = function(){
        const canvas = document.createElement('canvas');
        canvas.width = w; canvas.height = h;
        const ctx = canvas.getContext('2d');
        ctx.drawImage(img, 0, 0, w, h);
        DOMURL.revokeObjectURL(url);
        const png = canvas.toDataURL('image/png');
        const a = document.createElement('a');
        a.href = png; a.download = (document.getElementById('sister-name').textContent || 'card') + '.png';
        a.click();
      };
      img.onerror = ()=>alert('Download failed in this browser. Try opening this file in Chrome or Firefox.');
      img.src = url;
    });
  </script></body>
</html>

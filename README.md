# which-position-do-you-like-<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Which One Do You Like?</title>
  <style>
    body{font-family:system-ui,Segoe UI,Arial; margin:0; padding:0; background:#f6f7fb; color:#111}
    .container{max-width:1000px;margin:28px auto;padding:0 16px}
    .grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(160px,1fr));gap:12px}
    .card{background:#fff;border-radius:10px;overflow:hidden;cursor:pointer;box-shadow:0 6px 18px rgba(15,20,30,.06);display:flex;flex-direction:column}
    .card img{width:100%;height:140px;object-fit:cover;display:block}
    .card .meta{padding:8px;font-size:14px;text-align:center}
    .preview{position:fixed;right:20px;top:90px;width:320px;background:#fff;border-radius:12px;padding:12px;box-shadow:0 8px 30px rgba(0,0,0,.12)}
    .preview img{width:100%;height:260px;object-fit:cover;border-radius:8px}
    .btn{display:inline-block;padding:8px 12px;border-radius:8px;background:#0b78ff;color:#fff;text-decoration:none;margin-top:8px;cursor:pointer;border:none;}
    .btn-secondary{background:#888;}
    .agegate, #confirmModal, #cameraUploadModal{position:fixed;inset:0;background:rgba(0,0,0,0.6);display:flex;align-items:center;justify-content:center;z-index:999;}
    .agebox, .modal-content{background:#fff;padding:22px;border-radius:10px;text-align:center;max-width:420px;}
    footer{padding:12px;text-align:center;color:#666;font-size:13px;margin-top:32px}
    @media(max-width:900px){ .preview{position:static;margin:20px auto;width:calc(100% - 32px)} }
  </style>
</head>
<body>

<header style="position:relative; background:#fff; text-align:center; padding:40px 16px; box-shadow:0 1px 6px rgba(0,0,0,.06);">
  <div style="position:absolute; top:50%; left:50%; transform:translate(-50%,-50%); font-size:80px; color:rgba(255,0,102,0.1); pointer-events:none;">👄</div>
  <h1 style="position:relative; z-index:1; font-size:32px; margin:0; color:#111;">Which one do you like?</h1>
  <p style="position:relative; z-index:1; margin:6px 0 0; color:#666; font-size:16px;">
    Click a thumbnail to preview it. Click “Choose” to confirm.
  </p>
</header>

<div class="container">

  <div id="poseSection" style="display:none;">
    <a id="open-poses" href="#poses" class="btn" style="margin-bottom:14px;display:inline-block">Open Pose Gallery</a>

    <div id="poses" class="grid">
      <div class="card" data-title="Pose 1" data-src="https://i.postimg.cc/MMwrGR7P/pearly-gates-2-1650381834.jpg">
        <img src="https://i.postimg.cc/MMwrGR7P/pearly-gates-2-1650381834.jpg" alt="Pose 1">
        <div class="meta">Pose 1</div>
      </div>
      <div class="card" data-title="Pose 2" data-src="https://i.postimg.cc/svxH13hH/men-shealth-thesocket-1581101518.jpg">
        <img src="https://i.postimg.cc/svxH13hH/men-shealth-thesocket-1581101518.jpg" alt="Pose 2">
        <div class="meta">Pose 2</div>
      </div>
      <div class="card" data-title="Pose 3" data-src="https://i.postimg.cc/fJyqkM9F/menshealth-faceoff-v3-1581102194.jpg">
        <img src="https://i.postimg.cc/fJyqkM9F/menshealth-faceoff-v3-1581102194.jpg" alt="Pose 3">
        <div class="meta">Pose 3</div>
      </div>
      <div class="card" data-title="Pose 4" data-src="https://i.postimg.cc/WhzYtskX/menshealth-standingo-1581101725.jpg">
        <img src="https://i.postimg.cc/WhzYtskX/menshealth-standingo-1581101725.jpg" alt="Pose 4">
        <div class="meta">Pose 4</div>
      </div>
      <div class="card" data-title="Pose 5" data-src="https://i.postimg.cc/BtMwqjXM/mh-captain-1650390659.jpg">
        <img src="https://i.postimg.cc/BtMwqjXM/mh-captain-1650390659.jpg" alt="Pose 5">
        <div class="meta">Pose 5</div>
      </div>
      <div class="card" data-title="Pose 6" data-src="https://i.postimg.cc/w7M439mX/mh-happybaby-1650382591.jpg">
        <img src="https://i.postimg.cc/w7M439mX/mh-happybaby-1650382591.jpg" alt="Pose 6">
        <div class="meta">Pose 6</div>
      </div>
    </div>

    <div id="preview" class="preview" style="display:none">
      <div style="font-weight:600;margin-bottom:8px" id="preview-title">Preview</div>
      <img id="preview-img" src="" alt="Preview">
      <div style="text-align:center">
        <button id="choose-btn" class="btn">Choose this pose</button>
      </div>
    </div>

    <footer>Make sure any images you use are legal and that visitors are adults.</footer>
  </div>

</div>

<!-- Age gate -->
<div id="agegate" class="agegate" aria-hidden="false">
  <div class="agebox">
    <h2>Age verification</h2>
    <p>By continuing you confirm you are 18 years or older. Content may be intended for adults only.</p>
    <div style="margin-top:12px">
      <button id="i-am-18" class="btn">I am 18 or older</button>
      <button id="not-18" class="btn btn-secondary" style="margin-left:10px;">I am under 18</button>
    </div>
  </div>
</div>

<!-- Confirmation Modal -->
<div id="confirmModal" style="display:none;">
  <div class="modal-content">
    <h3>Do you want to take a photo in this pose?</h3>
    <div style="margin-top:12px;">
      <button id="yesPose" class="btn">Yes</button>
      <button id="noPose" class="btn btn-secondary" style="margin-left:10px;">No</button>
    </div>
  </div>
</div>

<!-- Camera / Upload Modal -->
<div id="cameraUploadModal" style="display:none;">
  <div class="modal-content">
    <h3>Choose an option</h3>
    <div style="margin-top:12px;">
      <button id="takeCamera" class="btn">Take Photo</button>
      <button id="uploadFile" class="btn btn-secondary" style="margin-left:10px;">Upload Photo</button>
    </div>
  </div>
</div>

<script>
  // Age gate
  const poseSection = document.getElementById('poseSection');
  const ageGate = document.getElementById('agegate');
  if(localStorage.getItem('is18')==='true'){ ageGate.style.display='none'; poseSection.style.display='block'; }

  document.getElementById('i-am-18').addEventListener('click', ()=>{
    localStorage.setItem('is18','true');
    ageGate.style.display='none';
    poseSection.style.display='block';
  });

  document.getElementById('not-18').addEventListener('click', ()=>{
    alert('You must be 18 or older to view this content.');
    window.location.href='https://example.com';
  });

  // Gallery
  const cards = document.querySelectorAll('.card');
  const preview = document.getElementById('preview');
  const previewImg = document.getElementById('preview-img');
  const previewTitle = document.getElementById('preview-title');
  const chooseBtn = document.getElementById('choose-btn');
  let selectedPoseTitle='', selectedPoseSrc='';

  cards.forEach(c=>{
    c.addEventListener('click', ()=>{
      selectedPoseSrc = c.dataset.src;
      selectedPoseTitle = c.dataset.title;
      previewImg.src = selectedPoseSrc;
      previewTitle.textContent = selectedPoseTitle;
      preview.style.display='block';
    });
  });

  // Smooth scroll
  document.getElementById('open-poses').addEventListener('click', function(e){
    e.preventDefault();
    document.getElementById('poses').scrollIntoView({behavior:'smooth'});
  });

  // Confirmation modal
  const confirmModal = document.getElementById('confirmModal');
  const cameraUploadModal = document.getElementById('cameraUploadModal');

  chooseBtn.onclick = e=>{
    e.preventDefault();
    confirmModal.style.display='flex';
  };

  document.getElementById('noPose').onclick = ()=>{
    confirmModal.style.display='none';
  };

  document.getElementById('yesPose').onclick = ()=>{
    confirmModal.style.display='none';
    cameraUploadModal.style.display='flex';
  };

  // Camera
  document.getElementById('takeCamera').onclick = async ()=>{
    cameraUploadModal.style.display='none';
    if(navigator.mediaDevices && navigator.mediaDevices.getUserMedia){
      try{
        const stream = await navigator.mediaDevices.getUserMedia({video:true});
        const video = document.createElement('video');
        video.srcObject = stream;
        video.autoplay=true;
        video.style.width='320px';
        video.style.height='240px';
        video.style.display='block';
        video.style.margin='20px auto';
        document.body.appendChild(video);
        alert('Camera started! You can see yourself in the video above.');
      }catch(err){
        alert('Camera access denied or not available.');
      }
    }else{
      alert('Camera not supported on this device.');
    }
  };

  // Upload
  document.getElementById('uploadFile').onclick = ()=>{
    cameraUploadModal.style.display='none';
    const input = document.createElement('input');
    input.type='file';
    input.accept='image/*';
    input.onchange = e=>{
      const file = e.target.files[0];
      if(file){
        const imgURL = URL.createObjectURL(file);
        const img = document.createElement('img');
        img.src = imgURL;
        img.style.width='320px';
        img.style.margin='20px auto';
        document.body.appendChild(img);
        alert('Photo uploaded successfully!');
      }
    };
    input.click();
  };
</script>

</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>For My Jaan</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.11.4/gsap.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
  <style>
    body { margin:0; overflow:hidden; font-family:'Inter',sans-serif; height:100vh; touch-action:manipulation; background: linear-gradient(135deg,#f9a8d4,#f3e8ff); }
    #app{position:relative;width:100%;height:100%;overflow:hidden;}
    #content{position:relative;z-index:10;width:100%;height:100%;display:flex;flex-direction:column;justify-content:center;align-items:center;padding:20px;box-sizing:border-box;}
    .step{position:absolute;width:100%;max-width:800px;padding:40px;background:rgba(255,255,255,0.509);backdrop-filter:blur(10px);border-radius:20px;box-shadow:0 10px 30px rgba(0,0,0,0.1);text-align:center;opacity:0;transform:translateY(20px);transition:all 0.8s cubic-bezier(0.16,1,0.3,1);pointer-events:none;}
    .step.active{opacity:1;transform:translateY(0);pointer-events:all;}
    .btn{background:linear-gradient(135deg,#ec4899,#f43f5e);color:white;border:none;padding:12px 24px;border-radius:50px;font-weight:600;cursor:pointer;margin-top:20px;box-shadow:0 4px 15px rgba(236,72,153,0.3);transition:all 0.3s ease;}
    .btn:hover{transform:translateY(-2px);box-shadow:0 6px 20px rgba(236,72,153,0.4);}
    .btn:active{transform:translateY(0);}
    .text-gradient{background:linear-gradient(135deg,#ec4899,#f43f5e,#f59e0b);-webkit-background-clip:text;background-clip:text;color:transparent;}
    .heart-beat{animation:heartbeat 1.5s ease-in-out infinite;}
    @keyframes heartbeat{0%{transform:scale(1)}25%{transform:scale(1.1)}50%{transform:scale(1)}75%{transform:scale(1.1)}100%{transform:scale(1)}}
    .emoji{font-size:3rem;margin-bottom:20px;display:inline-block;}
    .reason-card{background:white;border-radius:15px;padding:20px;margin:10px;box-shadow:0 5px 15px rgba(0,0,0,0.05);transition:all 0.3s ease;}
    .reason-card:hover{transform:translateY(-5px);box-shadow:0 8px 25px rgba(0,0,0,0.1);}
    #progress-container{position:fixed;top:20px;left:50%;transform:translateX(-50%);width:80%;max-width:400px;height:6px;background:rgba(255,255,255,0.3);border-radius:3px;z-index:100;}
    #progress-bar{height:100%;width:0%;background:linear-gradient(90deg,#ec4899,#f43f5e);border-radius:3px;transition:width 0.5s ease;}
    #canvas-container{position:fixed;top:0;left:0;width:100%;height:100%;z-index:1;}
    @media (max-width:640px){ .step{padding:20px} .text-4xl{font-size:1.8rem} }
  </style>
</head>
<body>
  <div id="app">
    <div id="canvas-container"></div>

    <div id="progress-container"><div id="progress-bar"></div></div>

    <div id="content">
      <!-- Step 1 -->
      <div class="step active" id="step1">
        <div class="emoji heart-beat">❤️</div>
        <h1 class="text-4xl md:text-5xl font-bold mb-6 text-gradient">Hello mera bacha</h1>
        <p class="text-xl text-gray-700 mb-8">I made something special for you...</p>
        <button class="btn" id="start-btn">Let's Begin</button>
      </div>

      <!-- Step 2 -->
      <div class="step" id="step2">
        <div class="emoji">🎉</div>
        <h2 class="text-3xl md:text-4xl font-bold mb-6 text-gradient">Happy Birthday!</h2>
        <p class="text-lg text-gray-700 mb-6">
          On your special Birthday,i want You to Know How preety are you. your smile And laughter made me feels 
          like heaven. I swear God has made you in their best time and mood as you are the example of perfection.
        </p>
        <button class="btn" id="next-btn-2">What makes you special?</button>
      </div>

      <!-- Step 3 -->
      <div class="step" id="step3">
        <h2 class="text-3xl md:text-4xl font-bold mb-8 text-gradient">Here's why you're incredible</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-8">
          <div class="reason-card">
            <div class="emoji text-3xl">✨</div>
            <h3 class="text-xl font-bold mb-2 text-pink-600">Your Kindness</h3>
            <p class="text-gray-700">The way you care and think about everyone whether they are Good or bad to you is absolutely Unconditional and inspiring.</p>
          </div>
          <div class="reason-card">
            <div class="emoji text-3xl">😊</div>
            <h3 class="text-xl font-bold mb-2 text-pink-600">Your Smile</h3>
            <p class="text-gray-700">Praising Your smile is like Guiding sun with Torch.</p>
          </div>
          <div class="reason-card">
            <div class="emoji text-3xl">🌟</div>
            <h3 class="text-xl font-bold mb-2 text-pink-600">Your Dedication</h3>
            <p class="text-gray-700">Your passion and Dedication Towards Your study, work, family and friends is Absolutely Unbelievable!</p>
          </div>
        </div>
        <button class="btn" id="next-btn-3">A Little Surprise</button>
      </div>

      <!-- Step 4 -->
      <div class="step" id="step4">
        <div class="emoji">📸</div>
        <h2 class="text-3xl md:text-4xl font-bold mb-6 text-gradient">Remember When...</h2>
        <div class="bg-gradient-to-r from-pink-200 to-rose-200 rounded-xl p-8 mb-8 flex flex-col justify-center items-center">
          <img src="https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcSrjpTIDiQyb-gVAiW1gE8brKzzAhqhOlUmOCFgyJbmI41zteJ2" height="200" width="200" alt="">
          <p class="text-lg text-gray-700 italic mt-2">(Imagine our favorite memory together here)</p>
        </div>
        <p class="text-lg text-gray-700 mb-6">Every moment with you becomes an unforgettable memory. Talking to you is like medicine that releases all my stress and makes me the happiest person in the world.</p>
        <button class="btn" id="next-btn-4">One Last Thing</button>
      </div>

      <!-- Step 5 -->
      <div class="step" id="step5">
        <div class="emoji">🎂</div>
        <h2 class="text-3xl md:text-4xl font-bold mb-6 text-gradient">My Birthday Wish For The Best Person</h2>
        <p class="text-lg text-gray-700 mb-8">Happiest Birthday Meri Pari. May Maa Radha fulfill all your wishes and grant you success and happiness throughout your life. Always stay joyful and never let your inner child die.</p>
        <p class="text-xl font-semibold text-pink-600 mb-8">Happy Birthday Meri Jaan ❤️</p>
        <button class="btn" id="confetti-btn">Celebrate!</button>
        <p class="mt-8 text-gray-500">Made with ❤️ just for you</p>
      </div>
    </div>
  </div>

  <!-- Background Music (replace with your audio file) -->
  <audio id="bg-music" src="https://files.catbox.moe/4zkss2.mp3"preload="auto">
</audio>

  <script>
    /* ----------------------------
       Three.js Heart Background
       (kept similar to your original)
       ---------------------------- */
    const container = document.getElementById('canvas-container');
    const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
    renderer.setSize(window.innerWidth, window.innerHeight);
    container.appendChild(renderer.domElement);

    const scene = new THREE.Scene();
    const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
    camera.position.z = 30;

    const x = 0, y = 0;
    const heartShape = new THREE.Shape();
    heartShape.moveTo(x + 0.5, y + 0.5);
    heartShape.bezierCurveTo(x + 0.5, y + 0.5, x + 1, y, x, y);
    heartShape.bezierCurveTo(x - 1, y, x - 1, y + 1.5, x - 1, y + 1.5);
    heartShape.bezierCurveTo(x - 1, y + 2.5, x + 0.5, y + 3.5, x + 0.5, y + 3.5);
    heartShape.bezierCurveTo(x + 0.5, y + 3.5, x + 2, y + 2.5, x + 2, y + 1.5);
    heartShape.bezierCurveTo(x + 2, y + 1.5, x + 2, y, x + 1, y);
    heartShape.bezierCurveTo(x + 0.5, y, x + 0.5, y + 0.5, x + 0.5, y + 0.5);

    const extrudeSettings = { depth: 0.5, bevelEnabled: true, bevelSegments: 3, bevelSize: 0.2, bevelThickness: 0.3 };
    const heartGeometry = new THREE.ExtrudeGeometry(heartShape, extrudeSettings);

    const hearts = [];
    const colors = [0xff6b6b, 0xff8e8e, 0xffb3b3, 0xffd8d8, 0xff9e9e, 0xffc1c1, 0xff6b8e, 0xff8eb3];

    for (let i = 0; i < 25; i++) {
      const material = new THREE.MeshPhongMaterial({ color: colors[Math.floor(Math.random() * colors.length)], emissive: 0xff0000, emissiveIntensity: 0.1, shininess: 100, transparent: true, opacity: 0.9 });
      const heart = new THREE.Mesh(heartGeometry, material);
      heart.position.x = (Math.random() - 0.5) * 50;
      heart.position.y = (Math.random() - 0.5) * 50;
      heart.position.z = (Math.random() - 0.5) * 50;
      const scale = Math.random() * 0.8 + 0.5;
      heart.scale.set(scale, scale, scale);
      heart.rotation.x = Math.random() * Math.PI;
      heart.rotation.y = Math.random() * Math.PI;
      heart.userData = {
        speedX: Math.random() * 0.02 - 0.01,
        speedY: Math.random() * 0.02 - 0.01,
        speedZ: Math.random() * 0.02 - 0.01,
        rotationSpeedX: Math.random() * 0.01,
        rotationSpeedY: Math.random() * 0.01,
        originalX: heart.position.x,
        originalY: heart.position.y,
        originalZ: heart.position.z,
        floatDistance: 2 + Math.random() * 3
      };
      scene.add(heart);
      hearts.push(heart);
    }

    const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
    scene.add(ambientLight);
    const directionalLight = new THREE.DirectionalLight(0xffffff, 0.8);
    directionalLight.position.set(1,1,1);
    scene.add(directionalLight);

    function animate() {
      requestAnimationFrame(animate);
      const time = Date.now() * 0.001;
      hearts.forEach(heart => {
        heart.position.x = heart.userData.originalX + Math.sin(time * heart.userData.speedX * 10) * heart.userData.floatDistance;
        heart.position.y = heart.userData.originalY + Math.sin(time * heart.userData.speedY * 10) * heart.userData.floatDistance;
        heart.position.z = heart.userData.originalZ + Math.sin(time * heart.userData.speedZ * 10) * heart.userData.floatDistance;
        heart.rotation.x += heart.userData.rotationSpeedX;
        heart.rotation.y += heart.userData.rotationSpeedY;
      });
      renderer.render(scene, camera);
    }
    animate();

    window.addEventListener('resize', () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    });

    /* ----------------------------
       Step navigation
       ---------------------------- */
    let currentStep = 1;
    const totalSteps = 5;

    function updateProgressBar() {
      const progress = ((currentStep - 1) / (totalSteps - 1)) * 100;
      document.getElementById('progress-bar').style.width = `${progress}%`;
    }

    function showStep(stepNumber) {
      document.querySelectorAll('.step').forEach(step => step.classList.remove('active'));
      const el = document.getElementById(`step${stepNumber}`);
      if (el) el.classList.add('active');
      updateProgressBar();
      if (stepNumber === totalSteps) {
        document.getElementById('confetti-btn').classList.add('animate-pulse');
      } else {
        document.getElementById('confetti-btn').classList.remove('animate-pulse');
      }
    }

    // buttons
    document.getElementById('start-btn').addEventListener('click', () => {
      currentStep = 2;
      showStep(currentStep);
    });
    document.getElementById('next-btn-2').addEventListener('click', () => {
      currentStep = 3; showStep(currentStep);
    });
    document.getElementById('next-btn-3').addEventListener('click', () => {
      currentStep = 4; showStep(currentStep);
    });
    document.getElementById('next-btn-4').addEventListener('click', () => {
      currentStep = 5; showStep(currentStep);
    });

    updateProgressBar();

    /* ----------------------------
       Audio fade helpers & confetti handler
       ---------------------------- */
    function fadeAudio(audio, from, to, duration) {
      // clamp
      from = Math.max(0, Math.min(1, from));
      to = Math.max(0, Math.min(1, to));
      const steps = Math.max(1, Math.floor(duration / 100));
      const step = (to - from) / steps;
      let currentVolume = from;
      audio.volume = currentVolume;
      const interval = setInterval(() => {
        currentVolume += step;
        // clamp and assign
        currentVolume = Math.max(0, Math.min(1, currentVolume));
        audio.volume = currentVolume;
        if ((step > 0 && currentVolume >= to - 0.0001) || (step < 0 && currentVolume <= to + 0.0001)) {
          clearInterval(interval);
          audio.volume = to;
          if (to === 0) {
            audio.pause();
            audio.currentTime = 0;
          }
        }
      }, 100);
    }

    document.getElementById('confetti-btn').addEventListener('click', () => {
      const music = document.getElementById('bg-music');
      // reset and play with initial volume 0 so we can fade in
      try {
        music.currentTime = 0;
        music.volume = 0;
        const p = music.play();
        if (p && typeof p.then === 'function') {
          p.catch(e => console.warn('Playback prevented by browser until user gesture:', e));
        }
      } catch (e) {
        console.warn('play() failed:', e);
      }

      fadeAudio(music, 0, 0.65, 3000); // fade in to 0.65 over 3s
      // fade out after 30s
      setTimeout(() => fadeAudio(music, 0.65, 0, 3000), 30000);

      // confetti bursts
      confetti({ particleCount:150, spread:70, origin:{ y:0.6 }, colors:['#ff0000','#ff69b4','#ff1493','#ffc0cb'] });
      setTimeout(()=>{ confetti({ particleCount:30, spread:60, origin:{ y:0.5 }, shapes:['heart'], colors:['#ff0000','#ff69b4'] }); }, 300);
      setTimeout(()=> {
        confetti({ particleCount:20, angle:60, spread:55, origin:{ x:0 }, shapes:['heart'], colors:['#ff0000','#ff69b4'] });
        confetti({ particleCount:20, angle:120, spread:55, origin:{ x:1 }, shapes:['heart'], colors:['#ff0000','#ff69b4'] });
      }, 600);

      // make Three.js hearts float up and fade
      hearts.forEach(heart => {
        gsap.to(heart.position, { y: heart.position.y - 30, duration: 3, ease: "power1.out" });
        gsap.to(heart.material, { opacity: 0, duration: 3, ease: "power1.out" });
      });
    });
  </script>
</body>
</html>

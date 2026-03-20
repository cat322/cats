<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>عيدكم مبارك</title>
  <style>
    :root{
      --gold:#f6d27a;
      --gold2:#ffefb0;
      --night1:#07111f;
      --night2:#0f2242;
      --night3:#1e3d73;
      --white:rgba(255,255,255,.95);
    }

    *{box-sizing:border-box}
    html,body{
      margin:0;
      height:100%;
      font-family:"Tahoma","Arial",sans-serif;
      background:#06101e;
      color:white;
      overflow:hidden;
    }

    body{
      background:
        radial-gradient(circle at 15% 20%, rgba(255,230,150,.10), transparent 18%),
        radial-gradient(circle at 85% 10%, rgba(255,255,255,.06), transparent 14%),
        linear-gradient(180deg,var(--night1),var(--night2) 52%,var(--night3));
    }

    #sky, #fireworks {
      position: fixed;
      inset: 0;
      width:100%;
      height:100%;
      display:block;
    }

    .moon{
      position:fixed;
      top:58px;
      left:65px;
      width:132px;
      height:132px;
      border-radius:50%;
      background: radial-gradient(circle at 35% 35%, #fff9d3, #ffe08a 60%, #f0ba4f 100%);
      box-shadow: 0 0 35px rgba(255,226,130,.75), 0 0 120px rgba(255,226,130,.18);
      z-index:1;
    }
    .moon:after{
      content:"";
      position:absolute;
      width:126px;height:126px;
      left:30px;top:6px;
      border-radius:50%;
      background: linear-gradient(180deg,var(--night1),var(--night2));
    }

    .lantern{
      position:fixed;
      top:-10px;
      width:34px;height:94px;
      border-radius:14px;
      background: linear-gradient(180deg,#fff0ae,#ffcc66 42%,#f39a33);
      box-shadow: 0 0 25px rgba(255,198,90,.75);
      animation: swing 4.4s ease-in-out infinite;
      transform-origin: top center;
      z-index:2;
    }
    .lantern:before{
      content:"";
      position:absolute;
      top:-80px;left:16px;
      width:2px;height:80px;background:rgba(255,255,255,.5);
    }
    .lantern:after{
      content:"";
      position:absolute;
      bottom:-12px;left:11px;
      width:12px;height:12px;border-radius:0 0 50% 50%;
      background:#ffd36b; box-shadow:0 0 12px rgba(255,211,107,.9);
    }
    @keyframes swing{
      0%,100%{transform:rotate(6deg)}
      50%{transform:rotate(-6deg)}
    }

    .wrap{
      position:relative;
      z-index:5;
      min-height:100%;
      display:grid;
      place-items:center;
      padding:24px;
    }

    .card{
      width:min(930px,94vw);
      border-radius:34px;
      padding:32px 24px 24px;
      background:linear-gradient(180deg, rgba(255,255,255,.12), rgba(255,255,255,.07));
      border:1px solid rgba(255,255,255,.18);
      backdrop-filter: blur(14px);
      box-shadow:
        0 18px 60px rgba(0,0,0,.35),
        inset 0 1px 0 rgba(255,255,255,.20);
      position:relative;
      overflow:hidden;
      text-align:center;
    }

    .card:before{
      content:"";
      position:absolute; inset:-2px;
      border-radius:34px;
      padding:1px;
      background:linear-gradient(135deg, rgba(255,244,187,.75), rgba(255,255,255,.08), rgba(255,214,107,.55));
      -webkit-mask:
        linear-gradient(#fff 0 0) content-box,
        linear-gradient(#fff 0 0);
      -webkit-mask-composite:xor;
              mask-composite:exclude;
      pointer-events:none;
    }

    .badge{
      display:inline-block;
      padding:11px 18px;
      border-radius:999px;
      background:rgba(246,210,122,.14);
      border:1px solid rgba(246,210,122,.28);
      color:#ffe7a1;
      font-size:15px;
      box-shadow:0 0 18px rgba(246,210,122,.12);
      margin-bottom:16px;
    }

    h1{
      margin:10px 0 14px;
      font-size:clamp(34px,5.2vw,66px);
      line-height:1.3;
      color:var(--white);
      text-shadow:0 0 18px rgba(255,255,255,.10);
    }
    h1 .name{
      color:var(--gold2);
      text-shadow:0 0 20px rgba(255,225,140,.55), 0 0 40px rgba(255,225,140,.18);
      display:inline-block;
      animation: glow 2.3s ease-in-out infinite alternate;
    }
    @keyframes glow{
      from{transform:scale(1)}
      to{transform:scale(1.03)}
    }

    .sub{
      font-size:clamp(18px,2.2vw,24px);
      line-height:2;
      margin:0 auto 10px;
      max-width:760px;
      color:rgba(255,255,255,.92);
    }

    .divider{
      width:170px;
      height:2px;
      margin:20px auto 18px;
      background:linear-gradient(90deg, transparent, rgba(255,223,140,.95), transparent);
      box-shadow:0 0 18px rgba(255,223,140,.4);
    }

    .dua{
      font-size:clamp(16px,2vw,21px);
      line-height:2.1;
      max-width:800px;
      margin:0 auto;
      color:rgba(240,245,255,.92);
    }

    .actions{
      display:flex;
      gap:14px;
      flex-wrap:wrap;
      justify-content:center;
      margin-top:26px;
    }

    button{
      border:none;
      cursor:pointer;
      border-radius:18px;
      padding:14px 22px;
      font-size:16px;
      font-weight:700;
      transition:.25s ease;
      text-decoration:none;
    }
    .gold-btn{
      color:#102240;
      background:linear-gradient(180deg,#ffe8a7,#f7c859);
      box-shadow:0 10px 24px rgba(247,200,89,.23);
    }
    button:hover{transform:translateY(-3px) scale(1.02)}

    .footer{
      margin-top:18px;
      color:rgba(255,255,255,.72);
      font-size:14px;
    }

    .corner{
      position:absolute;
      width:180px;height:180px;
      border:1px solid rgba(255,231,161,.18);
      border-radius:24px;
      transform:rotate(45deg);
      opacity:.3;
      pointer-events:none;
    }
    .corner.one{top:-90px;right:-90px}
    .corner.two{bottom:-90px;left:-90px}

    @media (max-width:700px){
      .moon{left:18px;top:30px;transform:scale(.8)}
      .card{padding:24px 16px 20px}
    }

    /* نافذة العيدية */
    .overlay{
      position:fixed;
      inset:0;
      background:rgba(2,8,20,.72);
      backdrop-filter: blur(8px);
      display:none;
      align-items:center;
      justify-content:center;
      z-index:20;
      padding:20px;
    }
    .overlay.show{display:flex}

    .gift-modal{
      width:min(980px,96vw);
      border-radius:30px;
      padding:28px 20px 24px;
      background:linear-gradient(180deg, rgba(255,255,255,.14), rgba(255,255,255,.08));
      border:1px solid rgba(255,255,255,.2);
      box-shadow:0 20px 70px rgba(0,0,0,.45);
      text-align:center;
      position:relative;
    }

    .gift-title{
      font-size:clamp(26px,4vw,42px);
      margin:0 0 10px;
      color:#fff4c4;
    }

    .gift-sub{
      color:rgba(255,255,255,.86);
      margin:0 0 22px;
      font-size:18px;
    }

    .gift-grid{
      display:grid;
      grid-template-columns:repeat(3, minmax(170px, 1fr));
      gap:18px;
    }

    .gift-box{
      position:relative;
      min-height:220px;
      border-radius:24px;
      background:linear-gradient(180deg, rgba(255,255,255,.13), rgba(255,255,255,.07));
      border:1px solid rgba(255,255,255,.16);
      cursor:pointer;
      transition:.25s ease;
      overflow:hidden;
      display:flex;
      align-items:center;
      justify-content:center;
      padding:18px;
    }
    .gift-box:hover{
      transform:translateY(-6px) scale(1.02);
      box-shadow:0 16px 30px rgba(0,0,0,.22);
    }

    .gift-closed,.gift-opened{
      width:100%;
    }

    .gift-icon{
      font-size:64px;
      margin-bottom:10px;
      display:block;
      filter:drop-shadow(0 8px 14px rgba(0,0,0,.25));
    }

    .gift-label{
      font-size:20px;
      color:#fff;
      font-weight:bold;
    }

    .gift-opened{
      display:none;
      animation:fadeIn .5s ease;
    }

    .gift-box.revealed .gift-closed{display:none}
    .gift-box.revealed .gift-opened{display:block}

    .gift-opened .prize{
      font-size:34px;
      margin-bottom:10px;
    }

    .gift-opened .prize-title{
      font-size:24px;
      color:#ffe7a1;
      margin-bottom:10px;
      font-weight:bold;
    }

    .gift-opened .prize-text{
      color:rgba(255,255,255,.92);
      line-height:1.9;
      font-size:17px;
      white-space:pre-line;
    }

    .selected{
      outline:2px solid rgba(255,232,167,.85);
      box-shadow:0 0 25px rgba(255,220,120,.28);
    }

    .close-btn{
      margin-top:22px;
      background:linear-gradient(180deg,#ffe8a7,#f7c859);
      color:#102240;
    }

    @keyframes fadeIn{
      from{opacity:0;transform:scale(.96)}
      to{opacity:1;transform:scale(1)}
    }

    @media (max-width:850px){
      .gift-grid{
        grid-template-columns:1fr;
      }
      .gift-box{
        min-height:180px;
      }
    }
  </style>
</head>
<body>
  <canvas id="sky"></canvas>
  <canvas id="fireworks"></canvas>

  <div class="moon"></div>
  <div class="lantern" style="left:10%;animation-delay:.2s"></div>
  <div class="lantern" style="left:23%;animation-delay:1s"></div>
  <div class="lantern" style="right:12%;animation-delay:.6s"></div>
  <div class="lantern" style="right:26%;animation-delay:1.3s"></div>

  <div class="wrap">
    <section class="card">
      <div class="corner one"></div>
      <div class="corner two"></div>

      <div class="badge">🌙 تهنئة خاصة بمناسبة عيد الفطر المبارك</div>
      <h1>عيدكم <span class="name">مبارك</span> ✨</h1>

      <p class="sub">
        بمناسبة قدوم عيد الفطر المبارك،
        أهديكم أطيب التهاني وأجمل الأمنيات،
        وأسأل الله أن يجعل أيامكم مليئة بالفرح والسكينة والبركة.
      </p>

      <div class="divider"></div>

      <p class="dua">
        كل عام وأنتم بخير،
        تقبل الله طاعتكم وصيامكم وقيامكم،
        وجعل هذا العيد عيد سعادة ومحبة وطمأنينة لكم ولمن تحبون. 🤍
      </p>

      <div class="actions">
        <button class="gold-btn" id="giftBtn">اخذ عيديتك</button>
      </div>

      <div class="footer">معايدة مقدمة من عبدالله</div>
    </section>
  </div>

  <div class="overlay" id="giftOverlay">
    <div class="gift-modal">
      <h2 class="gift-title">اختر هديتك 🎁</h2>
      <p class="gift-sub">اختر واحدة من الهدايا الثلاث</p>

      <div class="gift-grid">
        <div class="gift-box" data-index="0">
          <div class="gift-closed">
            <span class="gift-icon">🎁</span>
            <div class="gift-label">هدية 1</div>
          </div>
          <div class="gift-opened">
            <div class="prize">💌</div>
            <div class="prize-title">عيدية خاصة</div>
            <div class="prize-text">قد لا تكون هذه سيارة ولا 100 دولار،
لكنّها دعوة صادقة بالسعادة والتوفيق والبركة،
وكل عام وأنتم بألف خير.</div>
          </div>
        </div>

        <div class="gift-box" data-index="1">
          <div class="gift-closed">
            <span class="gift-icon">🎁</span>
            <div class="gift-label">هدية 2</div>
          </div>
          <div class="gift-opened">
            <div class="prize">💵</div>
            <div class="prize-title">$100</div>
            <div class="prize-text"></div>
          </div>
        </div>

        <div class="gift-box" data-index="2">
          <div class="gift-closed">
            <span class="gift-icon">🎁</span>
            <div class="gift-label">هدية 3</div>
          </div>
          <div class="gift-opened">
            <div class="prize">🚗</div>
            <div class="prize-title">سيارة</div>
            <div class="prize-text"></div>
          </div>
        </div>
      </div>

      <button class="close-btn" id="closeOverlay">إغلاق</button>
    </div>
  </div>

  <script>
    const sky = document.getElementById('sky');
    const sctx = sky.getContext('2d');
    let w = sky.width = innerWidth;
    let h = sky.height = innerHeight;

    const stars = Array.from({length: 120}, () => ({
      x: Math.random()*w,
      y: Math.random()*h*0.75,
      r: Math.random()*1.8 + 0.3,
      a: Math.random(),
      v: Math.random()*0.02 + 0.003
    }));

    function drawSky(){
      sctx.clearRect(0,0,w,h);
      for(const st of stars){
        st.a += st.v;
        const alpha = 0.4 + Math.abs(Math.sin(st.a))*0.6;
        sctx.beginPath();
        sctx.fillStyle = `rgba(255,255,255,${alpha})`;
        sctx.arc(st.x, st.y, st.r, 0, Math.PI*2);
        sctx.fill();
      }
      requestAnimationFrame(drawSky);
    }
    drawSky();

    const canvas = document.getElementById('fireworks');
    const ctx = canvas.getContext('2d');
    let cw = canvas.width = innerWidth;
    let ch = canvas.height = innerHeight;

    let fireworks = [];
    let particles = [];

    class Firework{
      constructor(sx, sy, tx, ty){
        this.x = sx; this.y = sy; this.sx = sx; this.sy = sy;
        this.tx = tx; this.ty = ty;
        this.distanceToTarget = Math.hypot(tx-sx, ty-sy);
        this.distanceTraveled = 0;
        this.angle = Math.atan2(ty-sy, tx-sx);
        this.speed = 3;
        this.acceleration = 1.04;
        this.brightness = 50 + Math.random()*30;
        this.hue = Math.random()*60 + 20;
      }
      update(i){
        this.speed *= this.acceleration;
        const vx = Math.cos(this.angle) * this.speed;
        const vy = Math.sin(this.angle) * this.speed;
        this.distanceTraveled = Math.hypot(this.x + vx - this.sx, this.y + vy - this.sy);

        if(this.distanceTraveled >= this.distanceToTarget){
          createParticles(this.tx, this.ty, this.hue);
          fireworks.splice(i,1);
        }else{
          this.x += vx; this.y += vy;
        }
      }
      draw(){
        ctx.beginPath();
        ctx.moveTo(this.x, this.y);
        ctx.lineTo(this.x - Math.cos(this.angle)*12, this.y - Math.sin(this.angle)*12);
        ctx.strokeStyle = `hsl(${this.hue},100%,${this.brightness}%)`;
        ctx.stroke();
      }
    }

    class Particle{
      constructor(x,y,hue){
        this.x = x; this.y = y;
        this.angle = Math.random()*Math.PI*2;
        this.speed = Math.random()*8 + 1;
        this.friction = 0.96;
        this.gravity = 0.9;
        this.hue = hue + (Math.random()*20 - 10);
        this.brightness = Math.random()*25 + 50;
        this.alpha = 1;
        this.decay = Math.random()*0.02 + 0.012;
      }
      update(i){
        this.speed *= this.friction;
        this.x += Math.cos(this.angle)*this.speed;
        this.y += Math.sin(this.angle)*this.speed + this.gravity;
        this.alpha -= this.decay;
        if(this.alpha <= this.decay){
          particles.splice(i,1);
        }
      }
      draw(){
        ctx.beginPath();
        ctx.arc(this.x,this.y,2,0,Math.PI*2);
        ctx.fillStyle = `hsla(${this.hue},100%,${this.brightness}%,${this.alpha})`;
        ctx.fill();
      }
    }

    function createParticles(x,y,hue){
      const count = 90;
      for(let i=0;i<count;i++) particles.push(new Particle(x,y,hue));
    }

    function launchFirework(x = Math.random()*cw*0.8 + cw*0.1, y = Math.random()*ch*0.45 + 60){
      fireworks.push(new Firework(Math.random()*cw, ch + 10, x, y));
    }

    function burstFireworks(times = 6){
      for(let i=0;i<times;i++){
        setTimeout(() => {
          launchFirework(
            Math.random()*cw*0.8 + cw*0.1,
            Math.random()*ch*0.45 + 60
          );
        }, i * 180);
      }
    }

    function animateFireworks(){
      requestAnimationFrame(animateFireworks);
      ctx.globalCompositeOperation = 'destination-out';
      ctx.fillStyle = 'rgba(0,0,0,0.18)';
      ctx.fillRect(0,0,cw,ch);
      ctx.globalCompositeOperation = 'lighter';

      for(let i=fireworks.length-1;i>=0;i--){
        fireworks[i].draw();
        fireworks[i].update(i);
      }
      for(let i=particles.length-1;i>=0;i--){
        particles[i].draw();
        particles[i].update(i);
      }
    }
    animateFireworks();

    setInterval(() => {
      const amount = Math.random() > 0.65 ? 2 : 1;
      for(let i=0;i<amount;i++){
        setTimeout(() => launchFirework(), i*260);
      }
    }, 1400);

    setTimeout(() => {
      launchFirework(cw*0.22, ch*0.28);
      launchFirework(cw*0.50, ch*0.22);
      launchFirework(cw*0.78, ch*0.30);
    }, 700);

    const giftBtn = document.getElementById('giftBtn');
    const overlay = document.getElementById('giftOverlay');
    const closeOverlay = document.getElementById('closeOverlay');
    const giftBoxes = document.querySelectorAll('.gift-box');

    giftBtn.addEventListener('click', () => {
      overlay.classList.add('show');
      giftBoxes.forEach(box => {
        box.classList.remove('revealed', 'selected');
      });
      burstFireworks(5);
    });

    closeOverlay.addEventListener('click', () => {
      overlay.classList.remove('show');
    });

    overlay.addEventListener('click', (e) => {
      if(e.target === overlay){
        overlay.classList.remove('show');
      }
    });

    giftBoxes.forEach((box, clickedIndex) => {
      box.addEventListener('click', () => {
        giftBoxes.forEach(b => {
          b.classList.remove('revealed', 'selected');
          b.querySelector('.gift-opened .prize').textContent = '';
          b.querySelector('.gift-opened .prize-title').textContent = '';
          b.querySelector('.gift-opened .prize-text').textContent = '';
        });

        const rewards = [
          {
            icon:'💌',
            title:'عيدية خاصة',
            text:`قد لا تكون هذه سيارة ولا 100 دولار،
لكنّها دعوة صادقة بالسعادة والتوفيق والبركة،
وكل عام وأنتم بألف خير.`
          },
          {
            icon:'💵',
            title:'100 دولار',
            text:''
          },
          {
            icon:'🚗',
            title:'سيارة',
            text:''
          }
        ];

        const order = [0,1,2];
        order.splice(clickedIndex, 1);
        const visualRewards = [];
        visualRewards[clickedIndex] = rewards[0];
        visualRewards[order[0]] = rewards[1];
        visualRewards[order[1]] = rewards[2];

        giftBoxes.forEach((b, i) => {
          const reward = visualRewards[i];
          b.querySelector('.gift-opened .prize').textContent = reward.icon;
          b.querySelector('.gift-opened .prize-title').textContent = reward.title;
          b.querySelector('.gift-opened .prize-text').textContent = reward.text;
          b.classList.add('revealed');
        });

        box.classList.add('selected');
        burstFireworks(8);
      });
    });

    addEventListener('resize', () => {
      w = sky.width = innerWidth;
      h = sky.height = innerHeight;
      cw = canvas.width = innerWidth;
      ch = canvas.height = innerHeight;
    });
  </script>
</body>
</html>

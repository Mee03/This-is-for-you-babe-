   <!DOCTYPE html>
<html>
<head>
   <title>Inwepo Heart</title>
   <style>
      * {
         margin: 0;
         padding: 0;
      }

      body {
         background: linear-gradient(white, lightblue); /* Gradasi dari putih ke biru muda */
         font-family: 'Segoe UI', sans-serif;
         color: white;
         text-align: center;
      }

      h1 {
         margin-top: 5%;
         font-size: 60px;
         color: black; /* Warna teks bisa diubah agar lebih terlihat */
      }

      .marquee {
         font-size: 18px;
         color: black; /* Warna teks agar sesuai dengan background */
         margin-top: 20px;
      }

      canvas {
         position: absolute;
         top: 0;
         left: 0;
         z-index: -1; /* Pindahkan canvas di belakang teks */
      }
   </style>
</head>
<body>
   <h1>Selamat Ulang Tahun💗💗💗</h1>
   <div class="marquee">
      <marquee scrollamount="5" width="630" height="20" behavior="alternate">
         Selamat ulang tahun sayangku 🎉💗💗. Semoga panjang umur, sehat selalu, dan selalu dilindungi oleh Tuhan. Ingat selalu pesan yang selalu aku bilangin ke kamu! Jaga diri dan kesehatan kamu, dan maaf aku nggak bisa ngasih hadiah, cuma bisa ngasih ini 💗💗
      </marquee>
   </div>

   <script>
      var rnd = Math.random, flr = Math.floor;
      let canvas = document.createElement('canvas');
      document.body.appendChild(canvas);
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;

      let ctx = canvas.getContext('2d');
      let gravity = 0.2;
      let hearts = [];
      let snapTime = 0, flash = false;

      function rndNum(num) {
         return rnd() * num + 1;
      }

      function vector(x, y) {
         this.x = x;
         this.y = y;

         this.add = function(vec2) {
            this.x += vec2.x;
            this.y += vec2.y;
         }
      }

      function particle(pos, vel) {
         this.pos = new vector(pos.x, pos.y);
         this.vel = vel;
         this.finish = false;
         this.start = 0;

         this.update = function(time) {
            if (time - this.start > 500) {
               this.finish = true;
            }
            if (!this.finish) {
               this.pos.add(this.vel);
               this.vel.y += gravity;
            }
         }

         this.draw = function() {
            if (!this.finish) {
               drawDot(this.pos.x, this.pos.y, 1);
            }
         }
      }

      function heart(x, y) {
         this.pos = new vector(x, y);
         this.vel = new vector(0, -rndNum(10) - 3);
         this.color = 'hsl(' + rndNum(360) + ', 100%, 50%)';
         this.size = 4;
         this.finish = false;
         this.start = 0;
         let exParticles = [], exPLen = 100;
         let rootShow = true;

         this.update = function(time) {
            if (this.finish) return;

            rootShow = this.vel.y < 0;

            if (rootShow) {
               this.pos.add(this.vel);
               this.vel.y += gravity;
            } else {
               if (exParticles.length === 0) {
                  flash = true;
                  for (let i = 0; i < exPLen; i++) {
                     exParticles.push(new particle(this.pos, new vector(-rndNum(10) + 5, -rndNum(10) + 5)));
                     exParticles[i].start = time;
                  }
               }
               let countFinish = 0;
               for (let i = 0; i < exPLen; i++) {
                  exParticles[i].update(time);
                  if (exParti
	   
   
   

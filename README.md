<!doctype html>




AI Hub – Interactive Assistants
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@3.4.1/dist/tailwind.min.css" rel="stylesheet" />

<style>
/* ================================
   AI HUB FLOATING BUTTON
================================ */
.ai-hub-btn {
  position: fixed;
  left: 14px;
  top: 50%;
  transform: translateY(-50%);
  background: linear-gradient(135deg,#16a34a,#22c55e);
  color: #fff;
  padding: 12px 16px;
  border-radius: 999px;
  font-size: 13px;
  font-weight: 700;
  cursor: pointer;
  box-shadow: 0 10px 30px rgba(0,0,0,.3);
  z-index: 9999;
  display: flex;
  align-items: center;
  gap: 8px;
  transition: transform .25s ease, opacity .25s ease;
}

.ai-hub-btn:hover {
  transform: translateY(-50%) scale(1.05);
  opacity: .95;
}

/* NEW AI BADGE */
.new-badge {
  background: #ef4444;
  color: #fff;
  font-size: 10px;
  padding: 2px 6px;
  border-radius: 999px;
  animation: pulse 1.5s infinite;
}

@keyframes pulse {
  0% { transform: scale(1); opacity: 1; }
  50% { transform: scale(1.15); opacity: .7; }
  100% { transform: scale(1); opacity: 1; }
}

/* ================================
   OVERLAY
================================ */
#ai-hub-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,.75);
  z-index: 99999;
}

.ai-hub-box {
  width: 96%;
  height: 92%;
  margin: 3% auto;
  background: #f5f7fb;
  border-radius: 20px;
  overflow: hidden;
  position: relative;
}

.ai-hub-close {
  position: absolute;
  top: 12px;
  right: 18px;
  font-size: 28px;
  cursor: pointer;
  z-index: 10;
}

/* ================================
   CAROUSEL
================================ */
.carousel {
  display: flex;
  gap: 20px;
  padding: 40px;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
}

.card {
  min-width: 320px;
  background: white;
  border-radius: 18px;
  box-shadow: 0 10px 25px rgba(0,0,0,.15);
  scroll-snap-align: center;
  overflow: hidden;
  transition: transform .3s;
}

.card:hover {
  transform: translateY(-6px);
}

.card img {
  width: 100%;
  height: 180px;
  object-fit: cover;
}

.card-body {
  padding: 20px;
}

/* ================================
   IFRAME MODAL
================================ */
#iframe-modal {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,.7);
  z-index: 100000;
}

#iframe-box {
  width: 95%;
  height: 92%;
  margin: 3% auto;
  background: #fff;
  border-radius: 18px;
  overflow: hidden;
  position: relative;
}

#iframe-box iframe {
  width: 100%;
  height: 100%;
  border: none;
}

#iframe-close {
  position: absolute;
  top: 10px;
  right: 16px;
  font-size: 26px;
  cursor: pointer;
  z-index: 10;
}
</style>




<!-- FLOATING AI HUB BUTTON -->
<div class="ai-hub-btn" onclick="openAIHub()">
  🤖 AI Hub
  <span class="new-badge">NEW AI</span>
</div>

<!-- AI HUB OVERLAY -->
<div id="ai-hub-overlay">
  <div class="ai-hub-box">
    <span class="ai-hub-close" onclick="closeAIHub()">✖</span>

    <div class="text-center pt-8">
      <h1 class="text-3xl font-bold text-gray-800">AI Assistant Hub</h1>
      <p class="text-gray-600 mt-2">Chat with purpose-built AI assistants in real time</p>
    </div>

    <!-- CAROUSEL -->
    <div class="carousel">

      <!-- CARD 1 -->
      <div class="card">
        <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createavibranteye-catchingyoutubeblogthumbnailfeaturingafloatingquizpop-upicononadigitalblogpage5084708667809205788.jpg" />
        <div class="card-body">
          <h3 class="text-xl font-bold mb-2">AI Companion</h3>
          <p class="text-sm text-gray-600 mb-4">
            Your everyday smart companion for guidance, ideas, and productivity.
          </p>
          <button onclick="openChat('https://agent.jotform.com/0195482a4e8d72b894a09678ddb9b513d564')" 
            class="bg-green-600 text-white px-4 py-2 rounded-lg w-full">
            Chat Now
          </button>
        </div>
      </div>

      <!-- CARD 2 -->
      <div class="card">
        <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/createamodernandcleanthumbnailforawebdevelopmentproducttitledmodernhomepagestylingtemplatewithtailwindcss3420170625469385526.jpg" />
        <div class="card-body">
          <h3 class="text-xl font-bold mb-2">Debeatzgh AI Assistant</h3>
          <p class="text-sm text-gray-600 mb-4">
            Expert assistant for blogging, tools, automation, and digital growth.
          </p>
          <button onclick="openChat('https://agent.jotform.com/0195424fb5d47897a72080768094791e9c32')" 
            class="bg-blue-600 text-white px-4 py-2 rounded-lg w-full">
            Chat Now
          </button>
        </div>
      </div>

      <!-- CARD 3 -->
      <div class="card">
        <img src="https://debeatzgh.wordpress.com/wp-content/uploads/2025/08/designadigitalproductse-commerceonlinedeals3545265155247625100.jpg" />
        <div class="card-body">
          <h3 class="text-xl font-bold mb-2">Side Hustle Assistant</h3>
          <p class="text-sm text-gray-600 mb-4">
            Discover side hustles, monetization ideas, and online income strategies.
          </p>
          <button onclick="openChat('https://agent.jotform.com/0195479af1b879f3a82ea15cbaf3859eaa44')" 
            class="bg-purple-600 text-white px-4 py-2 rounded-lg w-full">
            Chat Now
          </button>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- IFRAME CHAT MODAL -->
<div id="iframe-modal">
  <div id="iframe-box">
    <span id="iframe-close" onclick="closeChat()">✖</span>
    <iframe id="chat-frame"></iframe>
  </div>
</div>

<script>
function openAIHub() {
  document.getElementById("ai-hub-overlay").style.display = "block";
}

function closeAIHub() {
  document.getElementById("ai-hub-overlay").style.display = "none";
}

function openChat(url) {
  document.getElementById("chat-frame").src = url;
  document.getElementById("iframe-modal").style.display = "block";
}

function closeChat() {
  document.getElementById("iframe-modal").style.display = "none";
  document.getElementById("chat-frame").src = "";
}
</script>


</!doctype>

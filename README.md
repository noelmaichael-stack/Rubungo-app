# Rubungo-app
index.html
Urekebishaji wa Makosa ya Msimbo
216,904 tokens

Model 7:45 AM
ThinkingThoughts
Expand to view model thoughts

Inaonekana umetuma kodi ya faili lako la HTML (imejirudia mara 3 mfululizo) bila kuandika swali au maelekezo ya kile unachotaka nifanye.
Nimeipitia kodi yako kwa makini, na nimegundua makosa (bugs) muhimu ambayo yatazuia app kufanya kazi vizuri ukijaribu kuitumia sasa hivi. Haya hapa ni mambo makuu yanayohitaji kurekebishwa:
1. Kosa Kubwa Kwenye bootApp() (App Inakwama Baada ya Kuingia)
Kwenye JavaScript ndani ya bootApp(), umeandika:
Js
document.getElementById('topUserName').textContent = currentUser.name;
document.getElementById('topUserBadge').textContent = currentUser.title.toUpperCase();
Lakini kwenye <header> ya HTML, hakuna id="topUserName" wala id="topUserBadge" (kuna id="topUserRoleSubtitle" pekee). Kwa hiyo mtu akijaribu kuingia (Login), mfumo unatoa kosa (Cannot set properties of null) na hauwezi kufungua Chat, Video, wala Wanachama.
Suluhisho:
Badilisha sehemu hiyo kwenye bootApp() itumie topUserRoleSubtitle au ongeza span za jina na cheo kwenye <header>:
Js
const subtitleEl = document.getElementById('topUserRoleSubtitle');
if (subtitleEl) {
  subtitleEl.textContent = `${currentUser.name} • ${currentUser.title.toUpperCase()}`;
}
2. Kitufe cha dismissToast() Hakipo Kwenye JavaScript
Kwenye #liveLeaderNotification, kuna kitufe cha onclick="dismissToast()", lakini kazi (function) ya dismissToast() haijatengenezwa kwenye <script>.
Js
function dismissToast() {
  document.getElementById('liveLeaderNotification').classList.add('hidden');
}
3. Mapungufu Kwenye WhatsApp Chat (#view-whatsapp)
Tatizo la isMe: Kwenye renderWhatsAppChat(), umeweka msg.author === currentUser.name || msg.isMe. Kwa kuwa ujumbe mpya unahifadhiwa na isMe: true, mtu mwingine akiingia kwenye simu/kifaa hicho hicho ataona meseji za wenzake zikiwa upande wa kulia kama zake. Tumia msg.author === currentUser.name pekee.
Kubonyeza Enter: #waMessageInput haina uwezo wa kutuma ujumbe kwa kubonyeza kitufe cha Enter kwenye keyboard—inabidi uongeze onkeydown="if(event.key==='Enter') handleSendWaMessage()".
4. Mapungufu ya VICOBA (Hisa, Mikopo, Ripoti na Ruhusa)
Ruhusa za Viongozi vs Wanachama: Fomu za kusajili mwanachama (handleRegisterMember), kuweka akiba (handleDepositSavings), na kuidhinisha mikopo (handleApplyLoan) hazikagui kama aliyeingia ni ADMIN (kiongozi). Mwanachama wa kawaida anaweza kujiongezea akiba au mkopo.
Ripoti (#view-reports): Sehemu ya #printableReport ina kichwa cha habari na saini za viongozi tu, haina jedwali la wanachama wala jumla ya fedha za mfuko zinazojazwa na JavaScript.
Hisa & Mikopo: Hakuna orodha ya miamala iliyofanyika wala sehemu ya kurejesha mkopo au kulipa faini, na handleApplyLoan haikagui kama mfuko una pesa za kutosha (data.cashOnHand).
Namba ya Simu ya RL-024 (Eliya Ananias): Imeandikwa '071639256' (tarakimu 9 badala ya 10).
5. Michezo 10 (#view-games) & PWA (Sakinisha App)
Michezo: Kichwa kinasema Michezo 10, kadi zilizopo ni 5 (snake, tictactoe, math, memory, quiz), lakini memory na quiz zikibonyezwa zinafungua mchezo wa math, na Tic-Tac-Toe haina ukaguzi wa mshindi.
PWA Install: Kwenye Chrome ya Android, kitufe cha beforeinstallprompt hakitafanya kazi hadi uwepo wa faili la manifest.json na Service Worker.
Niambie ungependa nikufanyie nini sasa?
Kwa mfano, unaweza kuniambia:
"Nirekebishie makosa yote haya na unipe kodi kamili iliyokamilika."
"Niongezee michezo yote 10 kamili pamoja na mfumo wa marejesho ya mikopo na ripoti ya kuchapa."
"Nataka sehemu fulani tu ibadilishwe..." (taja sehemu hiyo).
Model 7:46 AM
ThinkingThoughts
Expand to view model thoughts

Model 7:51 AM
ThinkingThoughts
Expand to view model thoughts

Nimeboresha mfumo wote wa **RUBUNGO LEGENDS** na kuweka vipengele vyote ulivyoomba ndani ya faili moja kamili.

### Vipengele Vipya Vilivyoongezwa:
1. **Mtandao wa Moja kwa Moja (Online Cloud Sync - Firebase):** Ukijiunga na Firebase (maelekezo rahisi yapo ndani ya app kwenye kitufe cha **Mtandao / Cloud**), kila mwanachama akiwasha data ataona michango, mikopo, matangazo, kalenda na chat zote zikijisasisha moja kwa moja kwenye simu yake.
2. **Matangazo ya Kiotomatiki (`Automatic Announcements`):** Mfumo unapotambua mtu amewasha data (`online`) au amefungua app, unamkumbusha kiotomatiki:
   - Kulipia **Hisa za mwezi husika** (na unamwambia kama tayari amechangia au bado).
   - **Kikao cha kila baada ya miezi 3** (Machi, Juni, Septemba, Desemba) **Jumapili ya wiki ya mwisho saa 2:00 kamili jioni** (mfumo unapiga hesabu tarehe kamili ya Jumapili hiyo) pamoja na onyo la **Faini TZS 1,000/= ukichelewa**.
   - **TZS 1,000/= ya malipo ya viongozi** kila baada ya miezi 3.
3. **Kikokotoo cha Michango ya Mwezi (`Nani Kachanga vs Hajachangia`):** Kuna jedwali la mwezi husika linalohesabu wanachama wote 26—linaonyesha nani amenunua hisa mwezi huo, nani bado, nani amelipa `1,000/=` ya viongozi, na jumla ya fedha zilizokusanywa.
4. **Mikopo (`TZS 50,000/= mpaka 500,000/=`) & Uthibitisho wa Kumaliza Deni:**
   - Kuna **Kikokotoo cha Mkopo** (`50,000`–`500,000`), riba yake (5%), na faini ya ucheleweshaji ambayo ikilipwa inarudi kwenye **mfuko wa kundi**.
   - Mkopaji akilipa deni, mfumo unatangaza kwenye chat na bodi ya mikopo kama **BADO ANADAIWA** au **AMEMALIZA DENI LAKE PAMOJA NA RIBA (HANA DENI ✅)** ili kila mwanachama aone na kuthibitisha.
5. **Sherehe ya Umoja (Miaka ya Kundi), Kuaga Mwaka & Kalenda (Januari – Desemba):**
   - Mfumo unaonyesha **2026 ni Mwaka wa 4** tangu kuanzishwa kwa kikundi, na tunapomaliza mwaka unawatangazia wanachama tunaingia **Mwaka wa 5 (2027)**, **Happy New Year**, na ujumbe wa **Kuaga Mwaka & Kukaribisha Mwaka Mpya** pamoja na sherehe ya umoja.
   - **Kalenda Kamili ya Rubungo Legends (Januari – Desemba)** yenye tarehe zote za vikao vya robo mwaka, hisa, malipo ya viongozi, na uwezo wa viongozi kuongeza matukio mengine.

---

Nakili kodi hii yote na uihifadhi kama faili la `index.html`:

```html
<!DOCTYPE html>
<html lang="sw">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>RUBUNGO LEGENDS - VICOBA, WhatsApp, Kalenda & Media App</title>
  
  <!-- PWA & Mobile App Meta Tags (Android & iOS) -->
  <meta name="theme-color" content="#0A192F" />
  <meta name="mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-capable" content="yes" />
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
  <meta name="apple-mobile-web-app-title" content="Rubungo App" />
  <link id="dynamicManifest" rel="manifest" />
  
  <!-- Tailwind CSS & FontAwesome Icons -->
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" />
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            brandDark: '#020C1B',
            brandNavy: '#0A192F',
            brandGold: '#D4AF37',
            brandGoldLight: '#F59E0B',
            waGreen: '#25D366',
            waDarkGreen: '#075E54',
            waTeal: '#128C7E',
            waChatBg: '#0B141A'
          }
        }
      }
    }
  </script>
  <style>
    @media print {
      body * { visibility: hidden; }
      #printableReport, #printableReport * { visibility: visible; }
      #printableReport { position: absolute; left: 0; top: 0; width: 100%; color: #000; background: #fff; padding: 20px; }
      .no-print { display: none !important; }
    }
    .gold-border { border: 1px solid rgba(212, 175, 55, 0.35); }
    .wa-bubble-in { background-color: #202C33; border-radius: 12px 12px 12px 0px; }
    .wa-bubble-out { background-color: #005C4B; border-radius: 12px 12px 0px 12px; }
    @keyframes slideDown {
      from { transform: translate(-50%, -100%); opacity: 0; }
      to { transform: translate(-50%, 0); opacity: 1; }
    }
    .animate-slide-down { animation: slideDown 0.35s ease-out forwards; }
  </style>
</head>
<body class="bg-brandDark text-slate-100 min-h-screen flex flex-col font-sans select-none">

  <!-- ========================================== -->
  <!-- TOAST NOTIFICATION POPUP                   -->
  <!-- ========================================== -->
  <div id="liveLeaderNotification" class="fixed top-4 left-1/2 -translate-x-1/2 z-[220] hidden max-w-md w-full px-4 animate-slide-down">
    <div class="bg-gradient-to-r from-amber-600 via-amber-500 to-amber-700 text-slate-950 p-4 rounded-2xl shadow-2xl border border-white/40 flex items-start gap-3">
      <div class="w-10 h-10 rounded-xl bg-slate-950 text-brandGold flex items-center justify-center flex-shrink-0 text-lg font-bold">
        <i class="fa-solid fa-bell"></i>
      </div>
      <div class="flex-1">
        <h4 class="font-black text-xs uppercase tracking-wider" id="toastLeaderTitle">Taarifa ya Mfumo</h4>
        <p class="text-xs font-bold text-slate-900 mt-0.5 leading-snug" id="toastLeaderBody">Ujumbe umewasili.</p>
      </div>
      <button onclick="dismissToast()" class="text-slate-950 hover:text-white p-1">
        <i class="fa-solid fa-xmark"></i>
      </button>
    </div>
  </div>

  <!-- BANGO LA KUSAKINISHA APP YA IPHONE & ANDROID -->
  <div id="pwaInstallBanner" class="bg-gradient-to-r from-emerald-900 via-slate-900 to-emerald-950 border-b border-emerald-500/40 px-4 py-2 text-xs flex justify-between items-center gap-2 no-print">
    <div class="flex items-center space-x-2">
      <span class="w-7 h-7 rounded-lg bg-emerald-500 text-slate-950 flex items-center justify-center font-bold text-sm">
        <i class="fa-solid fa-mobile-screen"></i>
      </span>
      <span class="text-slate-200" id="installBannerText">
        Tumia kama App kwenye <strong>Android au iPhone</strong> yako bila Play Store!
      </span>
    </div>
    <div class="flex items-center space-x-2">
      <button onclick="triggerAppInstallation()" class="bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-black px-3 py-1 rounded-xl text-[11px] shadow">
        Sakinisha App 📲
      </button>
      <button onclick="document.getElementById('pwaInstallBanner').style.display='none'" class="text-slate-400 hover:text-white text-xs">
        <i class="fa-solid fa-xmark"></i>
      </button>
    </div>
  </div>

  <!-- ========================================== -->
  <!-- 1. UKURASA WA KUINGIA (LOGIN SCREEN)       -->
  <!-- ========================================== -->
  <div id="loginScreen" class="min-h-screen flex items-center justify-center p-4">
    <div class="w-full max-w-md bg-brandNavy rounded-3xl p-6 sm:p-8 gold-border shadow-2xl relative overflow-hidden">
      
      <div class="text-center mb-6">
        <div class="w-20 h-20 mx-auto rounded-3xl bg-gradient-to-tr from-amber-600 via-amber-300 to-amber-700 p-0.5 shadow-xl mb-3 flex items-center justify-center">
          <div class="w-full h-full bg-brandNavy rounded-3xl flex items-center justify-center text-brandGold font-black text-3xl">RL</div>
        </div>
        <h1 class="text-xl font-black text-white tracking-wide">RUBUNGO LEGENDS</h1>
        <p class="text-xs text-amber-300 font-semibold uppercase tracking-widest mt-0.5">VICOBA, KALENDA, WHATSAPP & MEDIA</p>
        <p class="text-[11px] text-slate-300 mt-2">Weka Nambari ya Simu na PIN: <strong>1234</strong> kuingia</p>
      </div>

      <form id="loginForm" onsubmit="handleLogin(event)" class="space-y-4">
        <div>
          <label class="block text-xs font-bold text-slate-300 mb-1">Nambari ya Simu ya Kuingilia *</label>
          <div class="relative">
            <i class="fa-solid fa-phone absolute left-3 top-3 text-slate-500 text-sm"></i>
            <input type="text" id="loginIdentifier" required placeholder="mf. 0758277600 au namba yako" class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl pl-9 pr-3 py-2.5 text-xs focus:ring-2 focus:ring-brandGold outline-none font-medium select-text" />
          </div>
        </div>

        <div>
          <label class="block text-xs font-bold text-slate-300 mb-1">Nenosiri Rasmi la Mfumo (Wote: 1234) *</label>
          <div class="relative">
            <i class="fa-solid fa-lock absolute left-3 top-3 text-slate-500 text-sm"></i>
            <input type="password" id="loginPassword" required placeholder="1234" value="1234" class="w-full bg-slate-900 border border-slate-700 text-amber-400 font-bold tracking-widest rounded-xl pl-9 pr-3 py-2.5 text-xs focus:ring-2 focus:ring-brandGold outline-none select-text" />
          </div>
        </div>

        <button type="submit" class="w-full bg-brandGold hover:bg-amber-400 text-slate-950 font-black py-2.5 rounded-xl text-xs uppercase tracking-wider transition shadow-lg active:scale-95">
          Ingia Kwenye Mfumo
        </button>
      </form>

      <div class="mt-6 p-3.5 bg-slate-900/95 rounded-2xl border border-slate-800 text-[11px] space-y-1.5 text-slate-300">
        <p class="font-bold text-amber-400 flex items-center justify-between">
          <span><i class="fa-solid fa-user-shield mr-1"></i> Baraza Kuu la Uongozi:</span>
          <span class="bg-amber-500/20 text-brandGold px-2 py-0.5 rounded font-mono font-bold">PIN: 1234</span>
        </p>
        <p>• Mwenyekiti: Noel Michael (0758277600)</p>
        <p>• Mhazini Mkuu: Justus Joel (0758145105)</p>
        <p>• Katibu Mkuu: Antia Kaujra (0767179054)</p>
      </div>

    </div>
  </div>

  <!-- ========================================== -->
  <!-- 2. UKURASA WA MFUMO (MAIN DASHBOARD/APP)    -->
  <!-- ========================================== -->
  <div id="appScreen" class="hidden flex-1 flex flex-col">
    
    <!-- Top Bar -->
    <header class="bg-brandNavy gold-border sticky top-0 z-50 px-4 py-3 flex justify-between items-center shadow-xl no-print">
      <div class="flex items-center space-x-3">
        <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-amber-600 to-amber-300 p-0.5 flex items-center justify-center flex-shrink-0">
          <div class="w-full h-full bg-brandNavy rounded-xl flex items-center justify-center text-brandGold font-black text-sm">RL</div>
        </div>
        <div>
          <h1 class="font-extrabold text-sm sm:text-base text-white tracking-wide flex items-center gap-2">
            RUBUNGO LEGENDS
            <span id="onlineStatusBadge" class="text-[9px] px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-500/40 font-bold">ONLINE</span>
          </h1>
          <p class="text-[10px] text-amber-300 font-semibold" id="topUserRoleSubtitle">VICOBA & WHATSAPP HUB</p>
        </div>
      </div>

      <!-- Quick Actions -->
      <div class="flex items-center space-x-1.5 sm:space-x-2">
        <button onclick="openAutoRemindersModal()" title="Matangazo ya Kiotomatiki" class="relative bg-amber-500/20 hover:bg-amber-500/30 text-amber-300 px-2.5 py-1.5 rounded-xl text-xs border border-amber-500/40 transition">
          <i class="fa-solid fa-bullhorn"></i>
          <span class="absolute -top-1 -right-1 w-2.5 h-2.5 rounded-full bg-rose-500 animate-ping"></span>
        </button>

        <button onclick="openCloudSyncModal()" title="Mipangilio ya Mtandao (Firebase)" class="bg-slate-800 hover:bg-slate-700 text-cyan-300 px-2.5 py-1.5 rounded-xl text-xs border border-slate-700 transition flex items-center gap-1">
          <i class="fa-solid fa-cloud"></i>
          <span class="hidden md:inline text-[11px]" id="cloudBtnLabel">Mtandao</span>
        </button>

        <button onclick="openWhatsAppGroupDirect()" title="Fungua WhatsApp Group" class="bg-emerald-600 hover:bg-emerald-500 text-white px-2.5 sm:px-3 py-1.5 rounded-xl text-xs font-bold transition flex items-center gap-1.5 shadow">
          <i class="fa-brands fa-whatsapp text-sm"></i>
          <span class="hidden sm:inline">WhatsApp</span>
        </button>

        <button onclick="handleLogout()" title="Ondoka (Logout)" class="bg-rose-900/60 hover:bg-rose-800 text-rose-200 px-2.5 sm:px-3 py-1.5 rounded-xl text-xs border border-rose-700/50 transition">
          <i class="fa-solid fa-power-off"></i>
        </button>
      </div>
    </header>

    <!-- Navigation Tabs -->
    <nav id="navTabsContainer" class="bg-brandNavy/95 backdrop-blur border-b border-slate-800 px-4 py-2 flex space-x-2 overflow-x-auto text-xs sm:text-sm font-semibold whitespace-nowrap no-print">
      <button onclick="switchTab('whatsapp')" id="tabBtn-whatsapp" class="tab-btn px-4 py-2 rounded-xl bg-brandGold text-slate-950 font-bold flex items-center gap-2">
        <i class="fa-brands fa-whatsapp text-emerald-700 text-base"></i> WhatsApp & Matangazo
      </button>
      <button onclick="switchTab('calendar')" id="tabBtn-calendar" class="tab-btn px-4 py-2 rounded-xl text-slate-300 hover:bg-slate-800 flex items-center gap-2">
        <i class="fa-solid fa-calendar-days text-amber-400"></i> Kalenda & Sherehe
      </button>
      <button onclick="switchTab('savings')" id="tabBtn-savings" class="tab-btn px-4 py-2 rounded-xl text-slate-300 hover:bg-slate-800 flex items-center gap-2">
        <i class="fa-solid fa-vault text-emerald-400"></i> Hisa, Michango & Faini
      </button>
      <button onclick="switchTab('loans')" id="tabBtn-loans" class="tab-btn px-4 py-2 rounded-xl text-slate-300 hover:bg-slate-800 flex items-center gap-2">
        <i class="fa-solid fa-hand-holding-dollar text-purple-400"></i> Mikopo (50k-500k)
      </button>
      <button onclick="switchTab('members')" id="tabBtn-members" class="tab-btn px-4 py-2 rounded-xl text-slate-300 hover:bg-slate-800 flex items-center gap-2">
        <i class="fa-solid fa-users text-blue-400"></i> Wanachama (<span id="navMemberCount">26</span>)
      </button>
      <button onclick="switchTab('tube')" id="tabBtn-tube" class="tab-btn px-4 py-2 rounded-xl text-slate-300 hover:bg-slate-800 flex items-center gap-2">
        <i class="fa-brands fa-youtube text-rose-500"></i> Rubungo Tube
      </button>
      <button onclick="switchTab('games')" id="tabBtn-games" class="tab-btn px-4 py-2 rounded-xl text-slate-300 hover:bg-slate-800 flex items-center gap-2">
        <i class="fa-solid fa-gamepad text-amber-400"></i> Michezo 10
      </button>
      <button onclick="switchTab('reports')" id="tabBtn-reports" class="tab-btn px-4 py-2 rounded-xl text-slate-300 hover:bg-slate-800 flex items-center gap-2">
        <i class="fa-solid fa-file-invoice-dollar text-yellow-400"></i> Ripoti
      </button>
    </nav>

    <!-- Main Content Body -->
    <main class="flex-1 p-4 sm:p-6 max-w-7xl w-full mx-auto space-y-6">

      <!-- ======================================================== -->
      <!-- BANGO LA MATANGAZO YA KIOTOMATIKI (AUTO REMINDERS)       -->
      <!-- ======================================================== -->
      <div id="autoAnnouncementBar" class="bg-gradient-to-r from-brandNavy via-[#132c50] to-brandNavy p-4 rounded-3xl gold-border shadow-xl space-y-3 no-print">
        <div class="flex flex-wrap justify-between items-center gap-2">
          <div class="flex items-center gap-2">
            <span class="w-8 h-8 rounded-xl bg-brandGold text-slate-950 flex items-center justify-center font-black">
              <i class="fa-solid fa-bullhorn"></i>
            </span>
            <div>
              <h3 class="font-black text-xs sm:text-sm text-white uppercase tracking-wide">Matangazo ya Kiotomatiki ya Kikundi</h3>
              <p class="text-[10px] text-amber-300" id="groupAnniversaryTag">Mwaka wa 4 tangu kuanzishwa (2026)</p>
            </div>
          </div>
          <button onclick="openAutoRemindersModal()" class="bg-slate-800 hover:bg-slate-700 text-amber-300 text-[11px] font-bold px-3 py-1.5 rounded-xl border border-slate-700">
            Angalia Yote <i class="fa-solid fa-arrow-right ml-1"></i>
          </button>
        </div>

        <div id="autoAnnouncementCards" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-2.5 text-xs">
          <!-- Inajazwa kiotomatiki na JS -->
        </div>
      </div>

      <!-- ======================================================== -->
      <!-- A. SEHEMU YA WHATSAPP GROUP & CHAT                       -->
      <!-- ======================================================== -->
      <section id="view-whatsapp" class="space-y-6">
        
        <div class="bg-gradient-to-r from-emerald-950 via-slate-900 to-emerald-950 p-5 sm:p-6 rounded-3xl border border-emerald-500/40 shadow-2xl flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
          <div class="flex items-center space-x-4">
            <div class="w-14 h-14 rounded-2xl bg-emerald-500 text-slate-950 flex items-center justify-center text-3xl font-black shadow-lg flex-shrink-0">
              <i class="fa-brands fa-whatsapp"></i>
            </div>
            <div>
              <span class="text-xs uppercase tracking-wider text-emerald-400 font-bold flex items-center gap-1.5">
                <span class="w-2.5 h-2.5 rounded-full bg-emerald-400 animate-ping"></span> KIKUNDI RASMI CHA WHATSAPP
              </span>
              <h2 class="text-xl sm:text-2xl font-black text-white mt-1">RUBUNGO LEGENDS VICOBA GROUP</h2>
              <p class="text-xs text-slate-300">Pokea uthibitisho wa mikopo, vikao, hisa na ujumbe wa wanachama wote.</p>
            </div>
          </div>

          <div class="flex flex-wrap items-center gap-2.5 w-full md:w-auto">
            <button onclick="openWhatsAppGroupDirect()" class="bg-emerald-500 hover:bg-emerald-400 text-slate-950 font-black px-5 py-2.5 rounded-2xl text-xs transition shadow-lg flex items-center gap-2">
              <i class="fa-brands fa-whatsapp text-base"></i> Fungua Group la WhatsApp
            </button>
            <button onclick="promptEditWhatsAppLink()" id="btnEditWaLink" class="bg-slate-800 hover:bg-slate-700 text-emerald-300 px-3.5 py-2.5 rounded-2xl text-xs border border-slate-700 transition font-bold">
              <i class="fa-solid fa-gear mr-1"></i> Weka Link ya Group
            </button>
          </div>
        </div>

        <!-- WHATSAPP WEB-STYLE CHAT INTERFACE -->
        <div class="bg-[#0B141A] rounded-3xl border border-slate-800 shadow-2xl overflow-hidden flex flex-col h-[500px]">
          <div class="bg-[#202C33] px-4 py-3 border-b border-slate-700 flex justify-between items-center">
            <div class="flex items-center space-x-3">
              <div class="w-10 h-10 rounded-full bg-emerald-600 flex items-center justify-center text-white text-lg font-bold">
                <i class="fa-solid fa-users"></i>
              </div>
              <div>
                <h3 class="font-bold text-sm text-white flex items-center gap-1.5">
                  RUBUNGO LEGENDS (VICOBA CHAT)
                  <i class="fa-solid fa-circle-check text-emerald-400 text-xs"></i>
                </h3>
                <p class="text-[10px] text-slate-400" id="chatMemberStatus">Wanachama 26 wapo hewani</p>
              </div>
            </div>

            <div class="flex items-center space-x-2">
              <button onclick="shareDirectToWhatsApp()" title="Tuma kwenda WhatsApp halisi" class="bg-[#005C4B] hover:bg-emerald-600 text-white px-3 py-1.5 rounded-xl text-xs font-bold transition flex items-center gap-1.5">
                <i class="fa-solid fa-share-nodes"></i> Tuma WhatsApp
              </button>
            </div>
          </div>

          <div id="waChatBox" class="flex-1 overflow-y-auto p-4 space-y-3 text-xs bg-[radial-gradient(#1f2c34_1px,transparent_1px)] [background-size:16px_16px]"></div>

          <div id="leaderQuickChatBar" class="hidden bg-[#182229] px-3 py-1.5 border-t border-slate-800 flex items-center gap-2 overflow-x-auto text-[11px]">
            <span class="text-amber-400 font-bold whitespace-nowrap">Matangazo:</span>
            <button onclick="sendAutoAnnouncementToChat('SHARES')" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-2.5 py-1 rounded-lg whitespace-nowrap">💰 Tangaza Hisa za Mwezi</button>
            <button onclick="sendAutoAnnouncementToChat('MEETING')" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-2.5 py-1 rounded-lg whitespace-nowrap">🗓️ Tangaza Kikao (Saa 2 Jioni)</button>
            <button onclick="sendAutoAnnouncementToChat('LEADER_FEE')" class="bg-slate-800 hover:bg-slate-700 text-slate-200 px-2.5 py-1 rounded-lg whitespace-nowrap">👑 Tangaza 1,000/= ya Viongozi</button>
            <button onclick="sendAutoAnnouncementToChat('CELEBRATION')" class="bg-slate-800 hover:bg-slate-700 text-amber-300 px-2.5 py-1 rounded-lg whitespace-nowrap">🎉 Sherehe ya Umoja & Mwaka Mpya</button>
          </div>

          <div class="bg-[#202C33] p-3 border-t border-slate-700 flex items-center space-x-2">
            <input type="text" id="waMessageInput" onkeydown="if(event.key==='Enter') handleSendWaMessage()" placeholder="Andika ujumbe hapa kisha bonyeza Enter..." 
              class="flex-1 bg-[#2A3942] border-0 text-white rounded-xl px-4 py-2.5 text-xs outline-none focus:ring-1 focus:ring-emerald-400 select-text" />
            
            <button onclick="handleSendWaMessage()" class="w-10 h-10 rounded-full bg-[#00A884] hover:bg-emerald-500 text-slate-950 flex items-center justify-center shadow-lg transition active:scale-95">
              <i class="fa-solid fa-paper-plane text-xs"></i>
            </button>
          </div>
        </div>
      </section>

      <!-- ======================================================== -->
      <!-- B. KALENDA YA RUBUNGO (JAN - DEC) & SHEREHE YA UMOJA     -->
      <!-- ======================================================== -->
      <section id="view-calendar" class="hidden space-y-6">
        
        <!-- Kadi ya Sherehe ya Umoja, Kuaga Mwaka & Happy New Year -->
        <div id="celebrationBanner" class="bg-gradient-to-r from-amber-900/80 via-brandNavy to-emerald-900/80 p-6 rounded-3xl gold-border shadow-2xl space-y-4">
          <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
            <div>
              <span class="text-xs font-black uppercase tracking-widest text-amber-300" id="anniversaryBadge">🎉 UMOJA NA MAFANIKIO YA RUBUNGO LEGENDS</span>
              <h2 class="text-xl sm:text-2xl font-black text-white mt-1" id="anniversaryHeadline">Tunamaliza Mwaka wa 4 (2026) — Tunaingia Mwaka wa 5 (2027)!</h2>
              <p class="text-xs text-slate-200 mt-1" id="anniversaryMessage">
                Hongereni wanachama wote kwa umoja wetu! Tuungane kwa furaha na kushangilia tunapoadhimisha miaka 4 ya kikundi chetu.
              </p>
            </div>
            <div class="flex flex-wrap gap-2">
              <button onclick="previewNewYearCelebration()" class="bg-brandGold hover:bg-amber-400 text-slate-950 font-black px-4 py-2 rounded-xl text-xs shadow">
                🎊 Sherehekea Mwaka Mpya / Umoja
              </button>
              <select id="calendarYearSelect" onchange="renderCalendarView()" class="bg-slate-900 border border-brandGold/50 text-amber-300 font-bold px-3 py-2 rounded-xl text-xs outline-none">
                <option value="2026">Mwaka 2026 (Mwaka wa 4)</option>
                <option value="2027">Mwaka 2027 (Mwaka wa 5)</option>
                <option value="2028">Mwaka 2028 (Mwaka wa 6)</option>
              </select>
            </div>
          </div>

          <!-- Ujumbe wa Kuaga Mwaka / Happy New Year -->
          <div id="newYearBannerBox" class="bg-slate-950/70 border border-amber-500/40 rounded-2xl p-4 text-xs text-slate-100 space-y-1">
            <!-- Inajazwa na JS -->
          </div>
        </div>

        <!-- Fomu ya Viongozi Kuongeza Tukio Kwenye Kalenda -->
        <div id="leaderAddEventCard" class="hidden bg-brandNavy p-5 rounded-2xl gold-border shadow-lg">
          <h3 class="font-bold text-sm text-white mb-2"><i class="fa-solid fa-calendar-plus text-brandGold mr-1"></i> Ongeza Tukio Maalum Kwenye Kalenda (Viongozi)</h3>
          <form onsubmit="handleAddCalendarEvent(event)" class="grid grid-cols-1 sm:grid-cols-4 gap-3">
            <select id="calEventMonth" class="bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none">
              <option value="0">Januari</option><option value="1">Februari</option><option value="2">Machi</option>
              <option value="3">Aprili</option><option value="4">Mei</option><option value="5">Juni</option>
              <option value="6">Julai</option><option value="7">Agosti</option><option value="8">Septemba</option>
              <option value="9">Oktoba</option><option value="10">Novemba</option><option value="11">Desemba</option>
            </select>
            <input type="text" id="calEventDay" required placeholder="Tarehe / Siku (mf. Tarehe 15)" class="bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
            <input type="text" id="calEventTitle" required placeholder="Tukio (mf. Sherehe ya Kikundi)" class="bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
            <button type="submit" class="bg-brandGold hover:bg-amber-400 text-slate-950 font-black py-2 rounded-xl text-xs">Hifadhi Tukio</button>
          </form>
        </div>

        <!-- Kalenda ya Miezi 12 (Januari - Desemba) -->
        <div id="fullYearCalendarGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4">
          <!-- Inajazwa na JS -->
        </div>
      </section>

      <!-- ======================================================== -->
      <!-- C. HISA, MICHANGO YA MWEZI & FAINI                       -->
      <!-- ======================================================== -->
      <section id="view-savings" class="hidden space-y-6">
        
        <!-- Muhtasari wa Mfuko -->
        <div class="grid grid-cols-2 lg:grid-cols-4 gap-3">
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800">
            <p class="text-[11px] text-slate-400">Jumla ya Hisa / Akiba</p>
            <h4 class="text-lg font-black text-brandGold mt-1" id="statTotalSavings">TZS 0</h4>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800">
            <p class="text-[11px] text-slate-400">Salio la Mfuko (Pesa Iliyopo)</p>
            <h4 class="text-lg font-black text-emerald-400 mt-1" id="statCashOnHand">TZS 0</h4>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800">
            <p class="text-[11px] text-slate-400">Mikopo Inayodaiwa</p>
            <h4 class="text-lg font-black text-rose-400 mt-1" id="statTotalLoans">TZS 0</h4>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800">
            <p class="text-[11px] text-slate-400">Riba & Faini Kwenye Mfuko</p>
            <h4 class="text-lg font-black text-amber-400 mt-1" id="statTotalIncome">TZS 0</h4>
          </div>
        </div>

        <!-- Fomu za Viongozi: Hisa, 1000 ya Viongozi & Faini -->
        <div id="leaderSavingsCard" class="hidden bg-brandNavy p-5 rounded-2xl gold-border shadow-lg space-y-5">
          <div>
            <h3 class="font-bold text-base text-white mb-2"><i class="fa-solid fa-coins text-brandGold mr-1"></i> Weka Hisa / Akiba ya Mwezi (Min TZS 15,000)</h3>
            <form id="savingDepositForm" onsubmit="handleDepositSavings(event)" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-3">
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Mwanachama *</label>
                <select id="savingMemberSelect" required class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none"></select>
              </div>
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Kiasi (TZS) *</label>
                <input type="number" id="savingAmount" min="15000" step="500" required placeholder="Min 15000" class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
              </div>
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Mwezi wa Hisa *</label>
                <input type="month" id="savingMonthInput" required class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none" />
              </div>
              <div class="flex items-end">
                <button type="submit" class="w-full bg-emerald-600 hover:bg-emerald-500 text-white font-bold py-2 rounded-xl text-xs transition">Hifadhi Hisa</button>
              </div>
            </form>
          </div>

          <!-- Malipo ya Viongozi 1,000/= kila baada ya miezi 3 -->
          <div class="border-t border-slate-800 pt-4">
            <h4 class="font-bold text-xs text-cyan-300 mb-2"><i class="fa-solid fa-crown mr-1"></i> Rekodi Malipo ya Viongozi (TZS 1,000/= Kila Baada ya Miezi 3)</h4>
            <form onsubmit="handleLeaderFeePayment(event)" class="grid grid-cols-1 sm:grid-cols-3 gap-3">
              <select id="leaderFeeMemberSelect" required class="bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none"></select>
              <select id="leaderFeeQuarterSelect" class="bg-slate-900 border border-slate-700 text-cyan-300 rounded-xl px-3 py-2 text-xs outline-none font-bold"></select>
              <button type="submit" class="bg-cyan-600 hover:bg-cyan-500 text-white font-bold py-2 rounded-xl text-xs transition">Thibitisha TZS 1,000/=</button>
            </form>
          </div>

          <!-- Faini (Kikao / Kuchelewa / Zingine) -->
          <div class="border-t border-slate-800 pt-4">
            <h4 class="font-bold text-xs text-amber-300 mb-2"><i class="fa-solid fa-gavel mr-1"></i> Faini ya Kikao (1,000/=) & Faini Nyinginezo</h4>
            <form id="penaltyForm" onsubmit="handlePenaltyAction(event)" class="grid grid-cols-1 sm:grid-cols-4 gap-3">
              <select id="penaltyMemberSelect" required class="bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none"></select>
              <input type="number" id="penaltyAmount" min="500" step="500" value="1000" required placeholder="Kiasi (mf. 1000)" class="bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
              <select id="penaltyType" class="bg-slate-900 border border-slate-700 text-amber-300 rounded-xl px-3 py-2 text-xs outline-none font-bold">
                <option value="ADD">Toza Faini (Kuchelewa Kikao 1,000/=)</option>
                <option value="PAY">Lipa Faini (Inaingia Kwenye Mfuko)</option>
              </select>
              <button type="submit" class="bg-amber-600 hover:bg-amber-500 text-white font-bold py-2 rounded-xl text-xs transition">Tekeleza</button>
            </form>
          </div>
        </div>

        <!-- KIKOKOTOO CHA MWEZI: NANI KACHANGA VS HAJACHANGIA -->
        <div class="bg-brandNavy p-5 rounded-2xl border border-slate-800 shadow-lg space-y-4">
          <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3">
            <div>
              <h3 class="font-bold text-base text-white"><i class="fa-solid fa-calculator text-brandGold mr-1"></i> Ukaguzi wa Michango ya Wanachama Wote</h3>
              <p class="text-[11px] text-slate-400">Angalia nani kachanga hisa mwezi husika na nani hajachangia, pamoja na 1,000/= ya viongozi.</p>
            </div>
            <div class="flex items-center gap-2">
              <input type="month" id="trackerMonthPicker" onchange="renderMonthlyTracker()" class="bg-slate-900 border border-brandGold/50 text-amber-300 text-xs font-bold px-3 py-1.5 rounded-xl outline-none" />
              <select id="trackerStatusFilter" onchange="renderMonthlyTracker()" class="bg-slate-900 border border-slate-700 text-white text-xs px-3 py-1.5 rounded-xl outline-none">
                <option value="ALL">Wote</option>
                <option value="PAID">Waliolipa Hisa</option>
                <option value="UNPAID">Hawajalipa Hisa</option>
              </select>
            </div>
          </div>

          <!-- Hesabu za Haraka za Mwezi Husika -->
          <div class="grid grid-cols-1 sm:grid-cols-3 gap-3 text-xs">
            <div class="bg-emerald-950/50 border border-emerald-500/30 p-3 rounded-xl flex justify-between items-center">
              <span class="text-emerald-300 font-bold">✅ Waliolipa Hisa Mwezi Huu:</span>
              <strong class="text-base text-white" id="trackerPaidCount">0 / 26</strong>
            </div>
            <div class="bg-rose-950/50 border border-rose-500/30 p-3 rounded-xl flex justify-between items-center">
              <span class="text-rose-300 font-bold">❌ Hawajalipa Hisa Mwezi Huu:</span>
              <strong class="text-base text-white" id="trackerUnpaidCount">26</strong>
            </div>
            <div class="bg-amber-950/50 border border-amber-500/30 p-3 rounded-xl flex justify-between items-center">
              <span class="text-amber-300 font-bold">💰 Jumla Iliyochangwa Mwezi Huu:</span>
              <strong class="text-base text-brandGold" id="trackerMonthTotal">TZS 0</strong>
            </div>
          </div>

          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs">
              <thead>
                <tr class="border-b border-slate-800 text-slate-400 uppercase text-[10px]">
                  <th class="py-2 px-2">ID</th>
                  <th class="py-2 px-2">Mwanachama</th>
                  <th class="py-2 px-2">Mchango Mwezi Huu</th>
                  <th class="py-2 px-2">Hali ya Hisa</th>
                  <th class="py-2 px-2">1,000/= ya Viongozi (Robo Hii)</th>
                </tr>
              </thead>
              <tbody id="monthlyTrackerBody" class="divide-y divide-slate-800/60"></tbody>
            </table>
          </div>
        </div>

        <!-- Historia ya Akiba -->
        <div class="bg-brandNavy p-5 rounded-2xl border border-slate-800 shadow-lg space-y-3">
          <h3 class="font-bold text-sm text-white"><i class="fa-solid fa-clock-rotate-left text-emerald-400 mr-1"></i> Historia ya Miamala ya Akiba</h3>
          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs">
              <thead>
                <tr class="border-b border-slate-800 text-slate-400 uppercase text-[10px]">
                  <th class="py-2 px-2">Mwezi / Tarehe</th>
                  <th class="py-2 px-2">Mwanachama</th>
                  <th class="py-2 px-2">Kiasi</th>
                  <th class="py-2 px-2">Aliyeidhinisha</th>
                </tr>
              </thead>
              <tbody id="savingsHistoryBody" class="divide-y divide-slate-800/60"></tbody>
            </table>
          </div>
        </div>

      </section>

      <!-- ======================================================== -->
      <!-- D. MIKOPO (50,000 - 500,000), RIBA, FAINI & UTHIBITISHO  -->
      <!-- ======================================================== -->
      <section id="view-loans" class="hidden space-y-6">

        <!-- KIKOKOTOO CHA MKOPO (50,000/= MPAKA 500,000/=) -->
        <div class="bg-gradient-to-r from-brandNavy via-[#162748] to-brandNavy p-5 rounded-3xl gold-border shadow-xl space-y-4">
          <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-2">
            <div>
              <h3 class="font-black text-base text-white"><i class="fa-solid fa-calculator text-brandGold mr-1"></i> Kikokotoo cha Mikopo (TZS 50,000/= mpaka 500,000/=)</h3>
              <p class="text-[11px] text-slate-300">Piga hesabu ya Mkopo, Riba (5%), na Faini endapo marejesho yatachelewa (vyote vinarudi kwenye Mfuko wa Kundi).</p>
            </div>
            <span class="bg-brandGold/20 text-brandGold border border-brandGold/40 px-3 py-1 rounded-xl text-xs font-bold">50k - 500k</span>
          </div>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 items-center">
            <div class="space-y-3">
              <div>
                <div class="flex justify-between text-xs font-bold mb-1">
                  <span class="text-slate-300">Kiasi cha Mkopo:</span>
                  <span class="text-brandGold" id="calcLoanDisplay">TZS 100,000</span>
                </div>
                <input type="range" id="calcLoanSlider" min="50000" max="500000" step="10000" value="100000" oninput="updateLoanCalculator()" class="w-full accent-brandGold cursor-pointer" />
                <div class="flex justify-between text-[10px] text-slate-400">
                  <span>50,000/=</span><span>250,000/=</span><span>500,000/=</span>
                </div>
              </div>
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Faini ya Kuchelewa Mkopo (ikizidishwa muda, mf. 5% au TZS):</label>
                <input type="number" id="calcPenaltyInput" value="0" min="0" step="1000" oninput="updateLoanCalculator()" class="w-full bg-slate-900 border border-slate-700 text-amber-300 rounded-xl px-3 py-2 text-xs outline-none select-text" />
              </div>
            </div>

            <div class="bg-slate-950/80 border border-slate-800 rounded-2xl p-4 grid grid-cols-2 gap-3 text-xs">
              <div><span class="text-slate-400 block">Mkopo Halisi:</span><strong class="text-white text-sm" id="calcResPrincipal">TZS 100,000</strong></div>
              <div><span class="text-slate-400 block">Riba (5%):</span><strong class="text-amber-400 text-sm" id="calcResInterest">TZS 5,000</strong></div>
              <div><span class="text-slate-400 block">Faini (Ikichelewa):</span><strong class="text-rose-400 text-sm" id="calcResPenalty">TZS 0</strong></div>
              <div><span class="text-emerald-300 block font-bold">Jumla Inayorudi Mfukoni:</span><strong class="text-emerald-400 text-base font-black" id="calcResTotal">TZS 105,000</strong></div>
            </div>
          </div>
        </div>

        <!-- Fomu za Viongozi: Toa Mkopo, Rejesha Mkopo, Faini ya Mkopo -->
        <div id="leaderLoansCard" class="hidden grid grid-cols-1 lg:grid-cols-3 gap-4">
          <!-- Toa Mkopo -->
          <div class="bg-brandNavy p-5 rounded-2xl gold-border shadow-lg">
            <h3 class="font-bold text-sm text-white mb-2"><i class="fa-solid fa-file-signature text-brandGold mr-1"></i> Idhinisha Mkopo (50k - 500k)</h3>
            <form id="loanApplyForm" onsubmit="handleApplyLoan(event)" class="space-y-3">
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Mkopaji *</label>
                <select id="loanMemberSelect" onchange="updateMaxLoanHint()" required class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none"></select>
                <span id="maxLoanHint" class="text-[10px] text-amber-400 block mt-1">Kikomo: TZS 50,000 - 500,000</span>
              </div>
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Kiasi (50,000 - 500,000) *</label>
                <input type="number" id="loanAmount" step="5000" min="50000" max="500000" required placeholder="50000 - 500000" class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
              </div>
              <button type="submit" class="w-full bg-brandGold hover:bg-amber-400 text-slate-950 font-bold py-2.5 px-4 rounded-xl text-xs transition">Idhinisha Mkopo (+5% Riba)</button>
            </form>
          </div>

          <!-- Rejesha Mkopo -->
          <div class="bg-brandNavy p-5 rounded-2xl border border-emerald-500/40 shadow-lg">
            <h3 class="font-bold text-sm text-white mb-2"><i class="fa-solid fa-money-bill-wave text-emerald-400 mr-1"></i> Pokea Rejesho la Mkopo</h3>
            <form id="loanRepayForm" onsubmit="handleRepayLoan(event)" class="space-y-3">
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Mkopaji Anayerejesha *</label>
                <select id="repayMemberSelect" required class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none"></select>
              </div>
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Kiasi Anacholipa (TZS) *</label>
                <input type="number" id="repayAmount" step="500" min="500" required placeholder="Kiasi cha Rejesho" class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
              </div>
              <button type="submit" class="w-full bg-emerald-600 hover:bg-emerald-500 text-white font-bold py-2.5 px-4 rounded-xl text-xs transition">Pokea & Tangaza Kwenye Kundi</button>
            </form>
          </div>

          <!-- Faini ya Kuchelewa Mkopo -->
          <div class="bg-brandNavy p-5 rounded-2xl border border-rose-500/40 shadow-lg">
            <h3 class="font-bold text-sm text-white mb-2"><i class="fa-solid fa-triangle-exclamation text-rose-400 mr-1"></i> Ongeza Faini ya Kuchelewa Mkopo</h3>
            <form onsubmit="handleLoanPenalty(event)" class="space-y-3">
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Mkopaji Aliyechelewa *</label>
                <select id="loanPenaltyMemberSelect" required class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none"></select>
              </div>
              <div>
                <label class="block text-[11px] font-bold text-slate-300 mb-1">Kiasi cha Faini ya Mkopo (TZS) *</label>
                <input type="number" id="loanPenaltyAmount" step="500" min="500" required placeholder="mf. 5000" class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
              </div>
              <button type="submit" class="w-full bg-rose-600 hover:bg-rose-500 text-white font-bold py-2.5 px-4 rounded-xl text-xs transition">Ongeza Kwenye Deni (Rudi Mfukoni)</button>
            </form>
          </div>
        </div>

        <!-- HALI YA MADENI YA WANACHAMA (WANAODAIWA VS WALIOMALIZA DENI) -->
        <div class="bg-brandNavy p-5 rounded-2xl border border-slate-800 shadow-lg space-y-3">
          <h3 class="font-bold text-sm text-white"><i class="fa-solid fa-shield-check text-emerald-400 mr-1"></i> Uthibitisho wa Hali ya Mikopo (Waliomaliza vs Wanaodaiwa)</h3>
          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs">
              <thead>
                <tr class="border-b border-slate-800 text-slate-400 uppercase text-[10px]">
                  <th class="py-2 px-2">Mwanachama</th>
                  <th class="py-2 px-2">Salio la Deni (+Riba & Faini)</th>
                  <th class="py-2 px-2">Hali ya Uthibitisho</th>
                </tr>
              </thead>
              <tbody id="loanStatusBoardBody" class="divide-y divide-slate-800/60"></tbody>
            </table>
          </div>
        </div>

        <!-- Historia ya Mikopo & Marejesho -->
        <div class="bg-brandNavy p-5 rounded-2xl border border-slate-800 shadow-lg space-y-3">
          <h3 class="font-bold text-sm text-white"><i class="fa-solid fa-list-check text-purple-400 mr-1"></i> Historia ya Mikopo, Riba, Faini & Marejesho</h3>
          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs">
              <thead>
                <tr class="border-b border-slate-800 text-slate-400 uppercase text-[10px]">
                  <th class="py-2 px-2">Tarehe</th>
                  <th class="py-2 px-2">Mwanachama</th>
                  <th class="py-2 px-2">Aina</th>
                  <th class="py-2 px-2">Kiasi</th>
                  <th class="py-2 px-2">Riba / Maelezo</th>
                </tr>
              </thead>
              <tbody id="loansHistoryBody" class="divide-y divide-slate-800/60"></tbody>
            </table>
          </div>
        </div>
      </section>

      <!-- ======================================================== -->
      <!-- E. DAFTARI LA WANACHAMA WOTE                             -->
      <!-- ======================================================== -->
      <section id="view-members" class="hidden space-y-6">
        
        <div id="leaderAddMemberCard" class="hidden bg-brandNavy p-5 rounded-2xl gold-border shadow-lg">
          <h3 class="font-bold text-base text-white mb-2"><i class="fa-solid fa-user-plus text-brandGold mr-1"></i> Sajili Mwanachama Mpya (Viongozi Pekee)</h3>
          <form id="addMemberForm" onsubmit="handleRegisterMember(event)" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 gap-3">
            <div>
              <label class="block text-[11px] font-bold text-slate-300 mb-1">Jina Kamili *</label>
              <input type="text" id="newMemName" required placeholder="Jina Kamili" class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
            </div>
            <div>
              <label class="block text-[11px] font-bold text-slate-300 mb-1">Nambari ya Simu *</label>
              <input type="tel" id="newMemPhone" required placeholder="07XXXXXXXX" class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
            </div>
            <div>
              <label class="block text-[11px] font-bold text-amber-300 mb-1">Cheo / Wadhifa *</label>
              <select id="newMemRole" class="w-full bg-slate-950 border border-brandGold/50 text-amber-300 rounded-xl px-3 py-2 text-xs font-bold outline-none">
                <option value="MEMBER">Mwanachama wa Kawaida</option>
                <option value="TREASURER">Mhazini Mkuu</option>
                <option value="SECRETARY">Katibu Mkuu</option>
                <option value="VICE_CHAIRPERSON">Naibu Mwenyekiti</option>
                <option value="COMMITTEE">Mjumbe wa Kamati</option>
              </select>
            </div>
            <div class="flex items-end">
              <button type="submit" class="w-full bg-brandGold hover:bg-amber-400 text-slate-950 font-black py-2 rounded-xl text-xs transition">Sajili Mwanachama</button>
            </div>
          </form>
        </div>

        <div class="bg-brandNavy p-5 rounded-2xl border border-slate-800 shadow-lg space-y-4">
          <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3">
            <div>
              <h3 class="font-bold text-base text-white"><i class="fa-solid fa-address-book text-brandGold mr-1"></i> Daftari la Wanachama Hai (<span id="membersTotalCount">26</span>)</h3>
              <p class="text-[11px] text-slate-400">Wanachama wote wanaingia kwa simu na PIN: 1234</p>
            </div>
            <input type="text" id="memberSearchInput" onkeyup="filterMembersTable()" placeholder="Tafuta jina au simu..." class="bg-slate-900 border border-slate-700 text-xs text-white px-3 py-2 rounded-xl outline-none w-full sm:w-64 select-text" />
          </div>

          <div class="overflow-x-auto">
            <table class="w-full text-left text-xs" id="membersTable">
              <thead>
                <tr class="border-b border-slate-800 text-slate-400 uppercase text-[11px]">
                  <th class="py-2.5 px-2">Namba</th>
                  <th class="py-2.5 px-2">Jina Kamili</th>
                  <th class="py-2.5 px-2">Simu</th>
                  <th class="py-2.5 px-2 text-amber-300 font-bold">Cheo</th>
                  <th class="py-2.5 px-2">Akiba Yote</th>
                  <th class="py-2.5 px-2">Mkopo</th>
                  <th class="py-2.5 px-2">Faini</th>
                  <th class="py-2.5 px-2 text-center">PIN</th>
                  <th class="py-2.5 px-2 text-center">Kitendo</th>
                </tr>
              </thead>
              <tbody id="membersTableBody" class="divide-y divide-slate-800/60"></tbody>
            </table>
          </div>
        </div>
      </section>

      <!-- ======================================================== -->
      <!-- F. RUBUNGO TUBE (TV, MPIRA & MOVIES)                     -->
      <!-- ======================================================== -->
      <section id="view-tube" class="hidden space-y-6">
        <div class="bg-brandNavy p-5 rounded-3xl gold-border shadow-2xl space-y-4">
          <div class="flex flex-col md:flex-row justify-between items-start md:items-center gap-4">
            <div>
              <h2 class="text-xl sm:text-2xl font-black text-white flex items-center gap-2">
                <i class="fa-brands fa-youtube text-rose-500 text-2xl"></i> Rubungo Tube & Sinema
              </h2>
              <p class="text-xs text-slate-300">Azam TV, Ligi na UEFA, Katuni, Filamu za Kiswahili (DJ) na English Movies!</p>
            </div>

            <div class="w-full md:w-96 relative">
              <i class="fa-solid fa-magnifying-glass absolute left-3 top-3 text-slate-500 text-sm"></i>
              <input type="text" id="videoSearchInput" onkeyup="filterVideosCatalog()" placeholder="Tafuta mpira, tamthilia, katuni, movie..." class="w-full bg-slate-900 border border-slate-700 text-white rounded-2xl pl-9 pr-3 py-2 text-xs focus:ring-2 focus:ring-rose-500 outline-none select-text" />
            </div>
          </div>

          <div class="flex flex-wrap gap-2 text-xs border-t border-slate-800 pt-3">
            <button onclick="setVideoCategory('ALL')" id="vcat-ALL" class="px-3 py-1.5 rounded-xl font-bold bg-rose-600 text-white transition">🔥 Zote</button>
            <button onclick="setVideoCategory('SPORTS')" id="vcat-SPORTS" class="px-3 py-1.5 rounded-xl font-bold bg-slate-900 text-slate-300 border border-slate-700 hover:border-emerald-500 transition">⚽ Mpira & UEFA</button>
            <button onclick="setVideoCategory('AZAM')" id="vcat-AZAM" class="px-3 py-1.5 rounded-xl font-bold bg-slate-900 text-slate-300 border border-slate-700 hover:border-blue-500 transition">📺 Azam TV Tanzania</button>
            <button onclick="setVideoCategory('CARTOON')" id="vcat-CARTOON" class="px-3 py-1.5 rounded-xl font-bold bg-slate-900 text-slate-300 border border-slate-700 hover:border-amber-500 transition">🦁 Katuni</button>
            <button onclick="setVideoCategory('SWAHILI_DJ')" id="vcat-SWAHILI_DJ" class="px-3 py-1.5 rounded-xl font-bold bg-slate-900 text-slate-300 border border-slate-700 hover:border-brandGold transition">🗣️ Movie za Kiswahili (DJ)</button>
            <button onclick="setVideoCategory('ENGLISH')" id="vcat-ENGLISH" class="px-3 py-1.5 rounded-xl font-bold bg-slate-900 text-slate-300 border border-slate-700 hover:border-purple-500 transition">🎬 English Movies</button>
            <button onclick="setVideoCategory('KOREAN')" id="vcat-KOREAN" class="px-3 py-1.5 rounded-xl font-bold bg-slate-900 text-slate-300 border border-slate-700 hover:border-rose-500 transition">🇰🇷 K-Drama</button>
          </div>

          <div class="relative w-full h-[240px] sm:h-[420px] rounded-2xl overflow-hidden bg-black border border-slate-800 mt-2">
            <iframe id="cinemaIframe" class="w-full h-full" src="https://www.youtube.com/embed/fJ9rUzIMcZQ?autoplay=0" title="Rubungo Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
          </div>
          <h3 class="font-bold text-white text-sm" id="cinemaActiveTitle">Inacheza: Azam Sports HD - NBC Premier League</h3>
        </div>

        <div id="videoCardsGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4"></div>
      </section>

      <!-- ======================================================== -->
      <!-- G. MICHEZO 10 YA GAME (ARCADE)                           -->
      <!-- ======================================================== -->
      <section id="view-games" class="hidden space-y-6">
        <div class="bg-gradient-to-r from-brandNavy via-[#0f2847] to-brandNavy p-6 rounded-3xl gold-border shadow-2xl flex justify-between items-center">
          <div>
            <h2 class="text-xl sm:text-2xl font-black text-white">Rubungo Game Arcade (Michezo 10) 🎮</h2>
            <p class="text-xs text-slate-300">Michezo 10 ya kuburudisha na kuchangamsha akili moja kwa moja!</p>
          </div>
          <span class="text-xs bg-amber-500/20 text-brandGold font-bold px-3 py-1.5 rounded-xl border border-brandGold/40 font-mono">10 GAMES</span>
        </div>

        <div id="activeGameArena" class="hidden bg-slate-950 p-6 rounded-3xl border border-brandGold/40 shadow-2xl space-y-4">
          <div class="flex justify-between items-center pb-3 border-b border-slate-800">
            <h3 class="font-black text-base text-white" id="arenaGameTitle">Mchezo</h3>
            <button onclick="closeGameArena()" class="bg-slate-800 hover:bg-rose-900 text-slate-300 hover:text-white px-3 py-1 rounded-xl text-xs font-bold transition">Funga Mchezo</button>
          </div>
          <div id="gamePlayContainer" class="flex flex-col items-center justify-center min-h-[280px]"></div>
        </div>

        <div class="grid grid-cols-2 sm:grid-cols-3 lg:grid-cols-5 gap-3.5">
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">1. Mchezo wa Nyoka 🐍</h4><p class="text-[10px] text-slate-400 mt-1">Kula dhahabu bila kugonga</p></div>
            <button onclick="launchGame('snake')" class="mt-3 bg-emerald-600 hover:bg-emerald-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">2. X na O (Tic-Tac-Toe) ❌⭕</h4><p class="text-[10px] text-slate-400 mt-1">Shindana na kompyuta</p></div>
            <button onclick="launchGame('tictactoe')" class="mt-3 bg-brandGold hover:bg-amber-400 text-slate-950 font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">3. Hesabu za Haraka 🧮</h4><p class="text-[10px] text-slate-400 mt-1">Pima hisabati yako</p></div>
            <button onclick="launchGame('math')" class="mt-3 bg-purple-600 hover:bg-purple-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">4. Kumbukumbu ya Kadi 🃏</h4><p class="text-[10px] text-slate-400 mt-1">Oanisha kadi zinazofanana</p></div>
            <button onclick="launchGame('memory')" class="mt-3 bg-blue-600 hover:bg-blue-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">5. Maswali ya VICOBA 💡</h4><p class="text-[10px] text-slate-400 mt-1">Elimu ya fedha</p></div>
            <button onclick="launchGame('quiz')" class="mt-3 bg-amber-600 hover:bg-amber-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">6. Kasi ya Kubofya ⚡</h4><p class="text-[10px] text-slate-400 mt-1">Sekunde 10 za kasi</p></div>
            <button onclick="launchGame('tap')" class="mt-3 bg-rose-600 hover:bg-rose-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">7. Buni Namba 🎯</h4><p class="text-[10px] text-slate-400 mt-1">Namba ya siri (1-100)</p></div>
            <button onclick="launchGame('guess')" class="mt-3 bg-cyan-600 hover:bg-cyan-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">8. Mwamba, Karatasi, Mikasi ✊</h4><p class="text-[10px] text-slate-400 mt-1">Pambana na kompyuta</p></div>
            <button onclick="launchGame('rps')" class="mt-3 bg-indigo-600 hover:bg-indigo-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">9. Sanduku la Bahati 🎁</h4><p class="text-[10px] text-slate-400 mt-1">Chagua zawadi yako</p></div>
            <button onclick="launchGame('lucky')" class="mt-3 bg-teal-600 hover:bg-teal-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
          <div class="bg-brandNavy p-4 rounded-2xl border border-slate-800 flex flex-col justify-between">
            <div><h4 class="font-bold text-xs text-white">10. Mfuatano wa Rangi 🎨</h4><p class="text-[10px] text-slate-400 mt-1">Kumbuka mpangilio</p></div>
            <button onclick="launchGame('simon')" class="mt-3 bg-pink-600 hover:bg-pink-500 text-white font-bold py-1.5 rounded-xl text-xs">Cheza</button>
          </div>
        </div>
      </section>

      <!-- ======================================================== -->
      <!-- H. RIPOTI RASMI YA FEDHA                                 -->
      <!-- ======================================================== -->
      <section id="view-reports" class="hidden space-y-6">
        <div class="flex justify-between items-center bg-brandNavy p-4 rounded-2xl border border-slate-800 no-print">
          <div>
            <h3 class="font-bold text-base text-white">Ripoti Rasmi ya Fedha na Leja</h3>
            <p class="text-xs text-slate-400">Chapa taarifa kamili yenye hesabu zote na saini za viongozi</p>
          </div>
          <button onclick="window.print()" class="bg-brandGold hover:bg-amber-400 text-slate-950 px-4 py-2 rounded-xl text-xs font-bold transition shadow">
            <i class="fa-solid fa-print mr-1"></i> Chapa Ripoti
          </button>
        </div>

        <div id="printableReport" class="bg-white text-slate-900 p-6 sm:p-8 rounded-2xl shadow-xl space-y-6">
          <div class="text-center border-b-2 border-slate-900 pb-4">
            <h2 class="text-2xl font-black text-slate-950 uppercase">RUBUNGO LEGENDS VICOBA</h2>
            <p class="text-xs font-semibold text-slate-600">TAARIFA RASMI YA FEDHA NA WANACHAMA (<span id="reportYearLabel">Mwaka wa 4</span>)</p>
            <p class="text-[11px] text-slate-500 mt-1">Tarehe ya Ripoti: <span id="reportGeneratedDate">-</span></p>
          </div>

          <div class="grid grid-cols-2 sm:grid-cols-4 gap-3 text-xs">
            <div class="border border-slate-300 p-3 rounded-xl">
              <span class="text-slate-500 block">Jumla ya Akiba (Hisa)</span>
              <strong class="text-sm text-slate-950" id="repTotalSavings">TZS 0</strong>
            </div>
            <div class="border border-slate-300 p-3 rounded-xl">
              <span class="text-slate-500 block">Salio la Mfuko Mkononi</span>
              <strong class="text-sm text-emerald-700" id="repCashOnHand">TZS 0</strong>
            </div>
            <div class="border border-slate-300 p-3 rounded-xl">
              <span class="text-slate-500 block">Mikopo Inayodaiwa</span>
              <strong class="text-sm text-rose-700" id="repTotalLoans">TZS 0</strong>
            </div>
            <div class="border border-slate-300 p-3 rounded-xl">
              <span class="text-slate-500 block">Riba & Faini Kwenye Mfuko</span>
              <strong class="text-sm text-amber-700" id="repTotalIncome">TZS 0</strong>
            </div>
          </div>

          <div class="overflow-x-auto">
            <table class="w-full text-left text-[11px] border-collapse border border-slate-300">
              <thead>
                <tr class="bg-slate-100 border-b border-slate-300">
                  <th class="p-2 border border-slate-300">ID</th>
                  <th class="p-2 border border-slate-300">Jina Kamili</th>
                  <th class="p-2 border border-slate-300">Cheo</th>
                  <th class="p-2 border border-slate-300 text-right">Akiba</th>
                  <th class="p-2 border border-slate-300 text-right">Deni la Mkopo</th>
                  <th class="p-2 border border-slate-300 text-right">Hali ya Deni</th>
                  <th class="p-2 border border-slate-300 text-right">Faini</th>
                </tr>
              </thead>
              <tbody id="reportTableBody"></tbody>
            </table>
          </div>

          <div class="pt-8 flex justify-between text-xs text-center border-t border-slate-300">
            <div class="w-1/3"><div class="border-b border-slate-400 mx-4 mb-1 h-6"></div><p class="font-bold">Noel Michael</p><p class="text-[10px]">Mwenyekiti</p></div>
            <div class="w-1/3"><div class="border-b border-slate-400 mx-4 mb-1 h-6"></div><p class="font-bold">Antia Kaujra</p><p class="text-[10px]">Katibu Mkuu</p></div>
            <div class="w-1/3"><div class="border-b border-slate-400 mx-4 mb-1 h-6"></div><p class="font-bold">Justus Joel</p><p class="text-[10px]">Mhazini Mkuu</p></div>
          </div>
        </div>
      </section>

    </main>
  </div>

  <!-- ========================================== -->
  <!-- MODAL: MATANGAZO YOTE YA KIOTOMATIKI       -->
  <!-- ========================================== -->
  <div id="autoRemindersModal" class="fixed inset-0 bg-black/85 z-[180] hidden items-center justify-center p-4">
    <div class="bg-brandNavy gold-border rounded-3xl max-w-lg w-full p-6 shadow-2xl space-y-4 max-h-[85vh] overflow-y-auto">
      <div class="flex justify-between items-center border-b border-slate-800 pb-3">
        <h3 class="font-black text-white text-base flex items-center gap-2">
          <i class="fa-solid fa-bullhorn text-brandGold"></i> Matangazo & Vikumbusho vya Kikundi
        </h3>
        <button onclick="closeAutoRemindersModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark text-lg"></i></button>
      </div>
      <div id="autoRemindersModalBody" class="space-y-3 text-xs"></div>
      <button onclick="closeAutoRemindersModal()" class="w-full bg-brandGold text-slate-950 font-black py-2.5 rounded-xl text-xs">Nimepata Taarifa!</button>
    </div>
  </div>

  <!-- ========================================== -->
  <!-- MODAL: MTANDAO (FIREBASE REALTIME SYNC)    -->
  <!-- ========================================== -->
  <div id="cloudSyncModal" class="fixed inset-0 bg-black/85 z-[180] hidden items-center justify-center p-4">
    <div class="bg-brandNavy gold-border rounded-3xl max-w-md w-full p-6 shadow-2xl space-y-4 max-h-[90vh] overflow-y-auto">
      <div class="flex justify-between items-center border-b border-slate-800 pb-2">
        <h3 class="font-black text-white text-base"><i class="fa-solid fa-cloud text-cyan-400 mr-1"></i> Unganisha Mtandao (Online Sync)</h3>
        <button onclick="closeCloudSyncModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
      </div>
      <p class="text-xs text-slate-300 leading-relaxed">
        Ili wanachama wote 26 waone data mpya moja kwa moja kutoka kwenye simu zao wanapowasha data, weka kiungo cha <strong>Firebase Realtime Database URL</strong> hapa chini:
      </p>
      <div class="bg-slate-900 p-3 rounded-xl border border-slate-800 text-[11px] text-slate-300 space-y-1">
        <p class="font-bold text-amber-300">Jinsi ya Kupata Link Bure (Dakika 2):</p>
        <p>1. Nenda <strong>console.firebase.google.com</strong> &rarr; Create Project.</p>
        <p>2. Chagua <strong>Realtime Database</strong> &rarr; Create Database &rarr; Start in <strong>Test Mode</strong>.</p>
        <p>3. Nakili URL (mf. <code>https://rubungo-default-rtdb.firebaseio.com</code>) na uiweke hapa.</p>
      </div>
      <form onsubmit="saveCloudSyncUrl(event)" class="space-y-3">
        <input type="url" id="cloudDbUrlInput" placeholder="https://mradi-wako-default-rtdb.firebaseio.com" class="w-full bg-slate-900 border border-slate-700 text-cyan-300 rounded-xl px-3 py-2.5 text-xs outline-none select-text" />
        <div class="flex gap-2">
          <button type="submit" class="flex-1 bg-cyan-600 hover:bg-cyan-500 text-white font-black py-2 rounded-xl text-xs">Hifadhi & Unganisha</button>
          <button type="button" onclick="syncNowManual()" class="bg-emerald-600 hover:bg-emerald-500 text-white font-bold px-3 py-2 rounded-xl text-xs">Sync Sasa</button>
        </div>
      </form>
      <div class="border-t border-slate-800 pt-3 flex justify-between items-center text-[11px]">
        <button onclick="exportJsonBackup()" class="text-amber-300 hover:underline font-bold"><i class="fa-solid fa-download mr-1"></i> Pakua Nakala (Backup)</button>
        <label class="text-emerald-300 hover:underline font-bold cursor-pointer">
          <i class="fa-solid fa-upload mr-1"></i> Pakia Nakala
          <input type="file" accept=".json" onchange="importJsonBackup(event)" class="hidden" />
        </label>
      </div>
    </div>
  </div>

  <!-- MODAL YA KUHARIRI MWANACHAMA -->
  <div id="editMemberModal" class="fixed inset-0 bg-black/85 z-[170] hidden items-center justify-center p-4">
    <div class="bg-brandNavy gold-border rounded-3xl max-w-sm w-full p-6 shadow-2xl space-y-4">
      <div class="flex justify-between items-center">
        <h3 class="font-black text-white text-base">Hariri Mwanachama</h3>
        <button onclick="closeEditMemberModal()" class="text-slate-400 hover:text-white"><i class="fa-solid fa-xmark"></i></button>
      </div>
      <form onsubmit="saveEditedMember(event)" class="space-y-3">
        <input type="hidden" id="editMemId" />
        <div>
          <label class="block text-[11px] font-bold text-slate-300 mb-1">Jina Kamili</label>
          <input type="text" id="editMemName" required class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
        </div>
        <div>
          <label class="block text-[11px] font-bold text-slate-300 mb-1">Nambari ya Simu</label>
          <input type="tel" id="editMemPhone" required class="w-full bg-slate-900 border border-slate-700 text-white rounded-xl px-3 py-2 text-xs outline-none select-text" />
        </div>
        <button type="submit" class="w-full bg-brandGold text-slate-950 font-black py-2 rounded-xl text-xs">Hifadhi Mabadiliko</button>
      </form>
    </div>
  </div>

  <!-- MODAL YA MAELEKEZO YA KUSAKINISHA APP -->
  <div id="installGuideModal" class="fixed inset-0 bg-black/85 z-[160] hidden items-center justify-center p-4">
    <div class="bg-brandNavy gold-border rounded-3xl max-w-md w-full p-6 shadow-2xl relative text-left space-y-4">
      <button onclick="closeInstallGuide()" class="absolute top-4 right-4 bg-slate-800 text-slate-300 w-8 h-8 rounded-full flex items-center justify-center"><i class="fa-solid fa-xmark"></i></button>
      <div class="flex items-center space-x-3">
        <div class="w-12 h-12 rounded-2xl bg-brandGold text-slate-950 flex items-center justify-center text-2xl font-bold">
          <i class="fa-solid fa-mobile-screen"></i>
        </div>
        <div>
          <h3 class="font-black text-white text-base">Sakinisha App ya Rubungo</h3>
          <p class="text-[11px] text-amber-300">Inafanya kazi kama App ya Android na iPhone!</p>
        </div>
      </div>
      <div class="bg-slate-900 p-3.5 rounded-2xl border border-slate-800 space-y-2.5 text-xs text-slate-300">
        <div class="border-b border-slate-800 pb-2">
          <strong class="text-white block mb-1">🤖 Kwenye Simu ya Android (Chrome):</strong>
          <p>Bofya <strong>nukta tatu (...)</strong> za juu kulia kwenye browser yako kisha chagua <strong>"Install app"</strong> au <strong>"Add to Home screen"</strong>.</p>
        </div>
        <div>
          <strong class="text-white block mb-1">🍏 Kwenye Simu ya iPhone (Safari):</strong>
          <p>Bofya kitufe cha <strong>Share (Kishale kinachoangalia juu)</strong> chini ya kioo kisha chagua <strong>"Add to Home Screen"</strong>.</p>
        </div>
      </div>
      <button onclick="closeInstallGuide()" class="w-full bg-brandGold text-slate-950 font-black py-2.5 rounded-xl text-xs">Nimeelewa!</button>
    </div>
  </div>

  <!-- ==================== JAVASCRIPT ENGINE ==================== -->
  <script>
    const UNIVERSAL_PASSWORD = "1234";
    const SWAHILI_MONTHS = ["Januari","Februari","Machi","Aprili","Mei","Juni","Julai","Agosti","Septemba","Oktoba","Novemba","Desemba"];
    const FOUNDING_BASE_YEAR = 2022; // 2026 - 2022 = Mwaka wa 4!
    let toastTimer = null;

    // ==================== PWA MANIFEST ====================
    (function setupManifest() {
      const iconSvg = `<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><rect width='100' height='100' rx='22' fill='#0A192F'/><text x='50' y='63' font-size='44' font-family='Arial, sans-serif' font-weight='900' fill='#D4AF37' text-anchor='middle'>RL</text></svg>`;
      const manifest = {
        name: "RUBUNGO LEGENDS VICOBA",
        short_name: "Rubungo App",
        start_url: ".",
        display: "standalone",
        background_color: "#020C1B",
        theme_color: "#0A192F",
        icons: [{ src: "data:image/svg+xml," + encodeURIComponent(iconSvg), sizes: "192x192", type: "image/svg+xml" }]
      };
      const blob = new Blob([JSON.stringify(manifest)], { type: 'application/json' });
      const manifestEl = document.getElementById('dynamicManifest');
      if (manifestEl) manifestEl.setAttribute('href', URL.createObjectURL(blob));
    })();

    // ==================== TOAST ====================
    function showToast(title, body) {
      const el = document.getElementById('liveLeaderNotification');
      document.getElementById('toastLeaderTitle').textContent = title;
      document.getElementById('toastLeaderBody').textContent = body;
      el.classList.remove('hidden');
      clearTimeout(toastTimer);
      toastTimer = setTimeout(dismissToast, 5500);
    }
    function dismissToast() { document.getElementById('liveLeaderNotification').classList.add('hidden'); }

    function cleanPhone(phone) {
      if (!phone) return "";
      let cleaned = phone.toString().replace(/[\s\+\-\(\)]/g, '');
      if (cleaned.startsWith('255')) cleaned = '0' + cleaned.substring(3);
      return cleaned;
    }

    function escapeHtml(text) {
      if (text === null || text === undefined) return '';
      const div = document.createElement('div');
      div.innerText = String(text);
      return div.innerHTML;
    }

    function formatTZS(val) { return 'TZS ' + Number(val || 0).toLocaleString('en-US'); }

    // ==================== DATE, QUARTER & LAST SUNDAY HELPERS ====================
    function getGroupYearNumber(year) {
      return Math.max(1, year - FOUNDING_BASE_YEAR); // 2026 => 4, 2027 => 5
    }

    function getLastSundayOfMonth(year, monthIndex0) {
      const lastDay = new Date(year, monthIndex0 + 1, 0);
      lastDay.setDate(lastDay.getDate() - lastDay.getDay());
      return lastDay;
    }

    function getQuarterKey(dateObj) {
      const y = dateObj.getFullYear();
      const q = Math.floor(dateObj.getMonth() / 3) + 1;
      return `${y}-Q${q}`;
    }

    function getNextQuarterlyMeetingInfo(refDate = new Date()) {
      const y = refDate.getFullYear();
      const qMonths = [2, 5, 8, 11]; // Machi, Juni, Septemba, Desemba
      for (let m of qMonths) {
        const sun = getLastSundayOfMonth(y, m);
        const meetingDateTime = new Date(sun.getFullYear(), sun.getMonth(), sun.getDate(), 20, 0, 0);
        if (meetingDateTime >= new Date(refDate.getFullYear(), refDate.getMonth(), refDate.getDate())) {
          return {
            dateObj: sun,
            monthName: SWAHILI_MONTHS[m],
            formatted: `Jumapili, ${sun.getDate()} ${SWAHILI_MONTHS[m]} ${sun.getFullYear()} • Saa 2:00 Jioni`
          };
        }
      }
      const nextSun = getLastSundayOfMonth(y + 1, 2);
      return {
        dateObj: nextSun,
        monthName: SWAHILI_MONTHS[2],
        formatted: `Jumapili, ${nextSun.getDate()} ${SWAHILI_MONTHS[2]} ${nextSun.getFullYear()} • Saa 2:00 Jioni`
      };
    }

    // ==================== DATA STORE & CLOUD SYNC ====================
    const DEFAULT_DATA = {
      cashOnHand: 0,
      totalInterestEarned: 0,
      totalPenaltiesCollected: 0,
      whatsappGroupUrl: 'https://chat.whatsapp.com/invite/rubungolegends',
      members: [
        { id: 'RL-001', name: 'Noel Michael', phone: '0758277600', role: 'CHAIRPERSON', title: 'Mwenyekiti', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-002', name: 'Justus Joel', phone: '0758145105', role: 'TREASURER', title: 'Mhazini Mkuu', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-003', name: 'Antia Kaujra', phone: '0767179054', role: 'SECRETARY', title: 'Katibu Mkuu', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-004', name: 'Aman Mpaka', phone: '0767961676', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-005', name: 'Agnetha Ananiasi', phone: '0657886568', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-006', name: 'Irene Gustava', phone: '0687802876', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-007', name: 'Jioram Jonas', phone: '0763753584', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-008', name: 'Aly Mohamed', phone: '0672297383', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-009', name: 'Harison Ignatus', phone: '0756994334', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-010', name: 'Sofia Hamza', phone: '0677445343', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-011', name: 'Plautila Pius', phone: '0746837973', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-012', name: 'Avna Revocaatus', phone: '0755350294', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-013', name: 'Eddy Burchard', phone: '0698155068', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-014', name: 'Raphael Obadia', phone: '0743616153', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-015', name: 'Beckham Muhamba', phone: '0763124558', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-016', name: 'Justine Charles', phone: '0712039638', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-017', name: 'Julieth K. Weyamba', phone: '0769074119', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-018', name: 'Justa Kweyamba', phone: '0765789268', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-019', name: 'Delphinus Deocles', phone: '0733544946', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-020', name: 'Kevina Thobias', phone: '0755529168', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-021', name: 'Doreen Emmanuel', phone: '0614157277', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-022', name: 'Irene Rwiza', phone: '0747391606', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-023', name: 'Joseph Bing\'are', phone: '0659592301', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-024', name: 'Eliya Ananias', phone: '071639256', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-025', name: 'Avitha Jasson', phone: '0758792595', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 },
        { id: 'RL-026', name: 'Adelaida Jovin', phone: '0760490710', role: 'MEMBER', title: 'Mwanachama wa Kawaida', savings: 0, loanBalance: 0, penalties: 0 }
      ],
      whatsappMessages: [
        { id: 'w1', author: 'Noel Michael', role: 'Mwenyekiti', text: 'Habari wanachama wa Rubungo Legends! Karibuni kwenye mfumo wetu wa mtandaoni. Mwaka 2026 ni mwaka wa 4 wa umoja wetu!', time: '17:30' },
        { id: 'w2', author: 'Justus Joel', role: 'Mhazini Mkuu', text: 'Kumbukeni hisa za mwezi (Min TZS 15,000) na TZS 1,000/= ya viongozi kila baada ya miezi 3.', time: '17:32' }
      ],
      savings: [],
      loans: [],
      penalties: [],
      leaderFees: [],
      customEvents: []
    };

    function loadData() {
      const stored = localStorage.getItem('RUBUNGO_DATA_STORE_V21');
      if (!stored) {
        const clone = JSON.parse(JSON.stringify(DEFAULT_DATA));
        localStorage.setItem('RUBUNGO_DATA_STORE_V21', JSON.stringify(clone));
        return clone;
      }
      try {
        const parsed = JSON.parse(stored);
        if (!parsed.members || parsed.members.length === 0) return JSON.parse(JSON.stringify(DEFAULT_DATA));
        parsed.savings = parsed.savings || [];
        parsed.loans = parsed.loans || [];
        parsed.penalties = parsed.penalties || [];
        parsed.leaderFees = parsed.leaderFees || [];
        parsed.customEvents = parsed.customEvents || [];
        parsed.whatsappMessages = parsed.whatsappMessages || [];
        parsed.totalInterestEarned = parsed.totalInterestEarned || 0;
        parsed.totalPenaltiesCollected = parsed.totalPenaltiesCollected || 0;
        return parsed;
      } catch (e) {
        return JSON.parse(JSON.stringify(DEFAULT_DATA));
      }
    }

    function getCloudDbUrl() {
      return (localStorage.getItem('RUBUNGO_FIREBASE_URL') || '').trim().replace(/\/+$/, '');
    }

    function saveData(data) {
      localStorage.setItem('RUBUNGO_DATA_STORE_V21', JSON.stringify(data));
      pushToCloud(data);
    }

    async function pushToCloud(data) {
      const dbUrl = getCloudDbUrl();
      if (!dbUrl || !navigator.onLine) return;
      try {
        await fetch(`${dbUrl}/rubungoData.json`, {
          method: 'PUT',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify(data)
        });
      } catch (err) {
        console.warn('Cloud push failed:', err);
      }
    }

    async function pullFromCloud(silent = true) {
      const dbUrl = getCloudDbUrl();
      if (!dbUrl || !navigator.onLine) return;
      try {
        const res = await fetch(`${dbUrl}/rubungoData.json`);
        if (!res.ok) return;
        const remote = await res.json();
        if (remote && remote.members && remote.members.length > 0) {
          localStorage.setItem('RUBUNGO_DATA_STORE_V21', JSON.stringify(remote));
          refreshAllUI();
          renderWhatsAppChat();
          renderAutoAnnouncements();
          if (!silent) showToast('Mtandao Umesawazishwa', 'Taarifa mpya kutoka mtandaoni zimepakuliwa!');
        } else if (remote === null) {
          await pushToCloud(loadData());
        }
      } catch (err) {
        if (!silent) showToast('Hitilafu ya Mtandao', 'Imeshindwa kuwasiliana na Firebase.');
      }
    }

    function openCloudSyncModal() {
      document.getElementById('cloudDbUrlInput').value = getCloudDbUrl();
      const m = document.getElementById('cloudSyncModal');
      m.classList.remove('hidden'); m.classList.add('flex');
    }
    function closeCloudSyncModal() {
      const m = document.getElementById('cloudSyncModal');
      m.classList.add('hidden'); m.classList.remove('flex');
    }
    function saveCloudSyncUrl(e) {
      e.preventDefault();
      const url = document.getElementById('cloudDbUrlInput').value.trim().replace(/\/+$/, '');
      localStorage.setItem('RUBUNGO_FIREBASE_URL', url);
      updateOnlineBadge();
      closeCloudSyncModal();
      if (url) {
        pullFromCloud(false);
      } else {
        showToast('Hali ya Ndani (Local)', 'Mtandao umeondolewa; data zinahifadhiwa kwenye simu hii.');
      }
    }
    function syncNowManual() { pullFromCloud(false); }

    function exportJsonBackup() {
      const blob = new Blob([JSON.stringify(loadData(), null, 2)], { type: 'application/json' });
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = `rubungo-legends-backup-${new Date().toISOString().split('T')[0]}.json`;
      a.click();
    }

    function importJsonBackup(e) {
      const file = e.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = (ev) => {
        try {
          const parsed = JSON.parse(ev.target.result);
          if (parsed.members) {
            saveData(parsed);
            refreshAllUI();
            renderWhatsAppChat();
            showToast('Imefanikiwa', 'Nakala ya data imepakiwa kikamilifu!');
          }
        } catch { showToast('Kosa', 'Faili hili si sahihi.'); }
      };
      reader.readAsText(file);
    }

    let currentUser = JSON.parse(localStorage.getItem('RUBUNGO_ACTIVE_USER_V21')) || null;

    // ==================== ONLINE / DATA DETECTION & AUTO ANNOUNCEMENTS ====================
    function updateOnlineBadge() {
      const badge = document.getElementById('onlineStatusBadge');
      const cloudLabel = document.getElementById('cloudBtnLabel');
      const hasCloud = !!getCloudDbUrl();
      if (cloudLabel) cloudLabel.textContent = hasCloud ? 'Cloud Live' : 'Mtandao';

      if (!badge) return;
      if (navigator.onLine) {
        badge.textContent = hasCloud ? 'CLOUD LIVE' : 'ONLINE';
        badge.className = 'text-[9px] px-2 py-0.5 rounded-full bg-emerald-500/20 text-emerald-300 border border-emerald-500/40 font-bold';
      } else {
        badge.textContent = 'OFFLINE';
        badge.className = 'text-[9px] px-2 py-0.5 rounded-full bg-rose-500/20 text-rose-300 border border-rose-500/40 font-bold';
      }
    }

    window.addEventListener('online', () => {
      updateOnlineBadge();
      if (currentUser) {
        pullFromCloud(true);
        triggerOnlineReminders(true);
      }
    });
    window.addEventListener('offline', updateOnlineBadge);

    function getAutoAnnouncementItems() {
      const data = loadData();
      const now = new Date();
      const year = now.getFullYear();
      const monthIdx = now.getMonth();
      const monthName = SWAHILI_MONTHS[monthIdx];
      const monthKey = `${year}-${String(monthIdx + 1).padStart(2, '0')}`;
      const qKey = getQuarterKey(now);
      const groupYr = getGroupYearNumber(year);
      const nextMeeting = getNextQuarterlyMeetingInfo(now);

      const mySharePaid = currentUser && data.savings.some(s => s.memberId === currentUser.id && s.monthKey === monthKey);
      const myFeePaid = currentUser && data.leaderFees.some(f => f.memberId === currentUser.id && f.quarterKey === qKey);
      const myLoan = currentUser ? (data.members.find(m => m.id === currentUser.id)?.loanBalance || 0) : 0;

      const items = [
        {
          icon: 'fa-coins',
          color: mySharePaid ? 'border-emerald-500/40 bg-emerald-950/40 text-emerald-300' : 'border-amber-500/50 bg-amber-950/40 text-amber-200',
          title: `Hisa za ${monthName} ${year}`,
          body: mySharePaid
            ? `Hongera! Tayari umeshalipia hisa zako za ${monthName} ${year}.`
            : `Kikumbusho: Tafadhali lipia hisa zako za ${monthName} ${year} (Kuanzia TZS 15,000/=).`
        },
        {
          icon: 'fa-calendar-check',
          color: 'border-rose-500/40 bg-rose-950/40 text-rose-200',
          title: `Kikao cha Miezi 3 (Saa 2:00 Jioni)`,
          body: `Kikao kijacho: ${nextMeeting.formatted}. Ukichelewa kuingia faini ni TZS 1,000/=!`
        },
        {
          icon: 'fa-crown',
          color: myFeePaid ? 'border-emerald-500/40 bg-emerald-950/40 text-emerald-300' : 'border-cyan-500/40 bg-cyan-950/40 text-cyan-200',
          title: `Malipo ya Viongozi (${qKey})`,
          body: myFeePaid
            ? `Tayari umeshalipa TZS 1,000/= ya viongozi kwa robo hii (${qKey}).`
            : `Kila mwanachama aweke TZS 1,000/= ya malipo ya viongozi kila baada ya miezi 3.`
        },
        {
          icon: 'fa-champagne-glasses',
          color: 'border-brandGold/50 bg-slate-900/80 text-amber-200',
          title: monthIdx === 0 ? `HAPPY NEW YEAR ${year}! 🎉` : `Mwaka wa ${groupYr} (${year}) • Umoja`,
          body: monthIdx === 11
            ? `Tunamaliza Mwaka wa ${groupYr} (${year}) na tunaingia Mwaka wa ${groupYr + 1} (${year + 1})! Tuungane kusherehekea umoja wetu!`
            : monthIdx === 0
            ? `Happy New Year ${year}! Karibuni katika Mwaka wa ${groupYr} wa Rubungo Legends!`
            : `Tunapoendelea na Mwaka wa ${groupYr} (${year}), tuimarishe umoja wetu! ${myLoan > 0 ? `Deni lako: ${formatTZS(myLoan)}.` : 'Huna deni la mkopo ✅'}`
        }
      ];
      return items;
    }

    function renderAutoAnnouncements() {
      const now = new Date();
      const year = now.getFullYear();
      const groupYr = getGroupYearNumber(year);
      const tagEl = document.getElementById('groupAnniversaryTag');
      if (tagEl) tagEl.textContent = `Mwaka wa ${groupYr} tangu kuanzishwa (${year}) • Tunaelekea Mwaka wa ${groupYr + 1} (${year + 1})`;

      const cardsEl = document.getElementById('autoAnnouncementCards');
      const modalBody = document.getElementById('autoRemindersModalBody');
      const items = getAutoAnnouncementItems();

      if (cardsEl) {
        cardsEl.innerHTML = items.map(it => `
          <div class="p-3 rounded-2xl border ${it.color} flex items-start gap-2.5">
            <i class="fa-solid ${it.icon} text-sm mt-0.5"></i>
            <div>
              <h4 class="font-black text-[11px]">${escapeHtml(it.title)}</h4>
              <p class="text-[11px] opacity-90 mt-0.5 leading-snug">${escapeHtml(it.body)}</p>
            </div>
          </div>
        `).join('');
      }

      if (modalBody) {
        modalBody.innerHTML = items.map(it => `
          <div class="p-3.5 rounded-2xl border ${it.color} flex items-start gap-3">
            <i class="fa-solid ${it.icon} text-base mt-0.5"></i>
            <div>
              <h4 class="font-black text-xs">${escapeHtml(it.title)}</h4>
              <p class="text-xs opacity-90 mt-1">${escapeHtml(it.body)}</p>
            </div>
          </div>
        `).join('');
      }
    }

    function triggerOnlineReminders(fromReconnect = false) {
      renderAutoAnnouncements();
      const items = getAutoAnnouncementItems();
      if (fromReconnect) {
        showToast('Data Imewashwa! 📶', `${items[0].body} | ${items[1].body}`);
      } else {
        const lastShown = sessionStorage.getItem('RUBUNGO_REMINDER_SHOWN');
        if (!lastShown) {
          sessionStorage.setItem('RUBUNGO_REMINDER_SHOWN', '1');
          showToast('Matangazo ya Kikundi 📢', `${items[0].title}: ${items[0].body}`);
        }
      }
    }

    function openAutoRemindersModal() {
      renderAutoAnnouncements();
      const m = document.getElementById('autoRemindersModal');
      m.classList.remove('hidden'); m.classList.add('flex');
    }
    function closeAutoRemindersModal() {
      const m = document.getElementById('autoRemindersModal');
      m.classList.add('hidden'); m.classList.remove('flex');
    }

    // ==================== PWA INSTALLATION ====================
    let deferredPrompt = null;
    window.addEventListener('beforeinstallprompt', (e) => {
      e.preventDefault();
      deferredPrompt = e;
      document.getElementById('pwaInstallBanner').style.display = 'flex';
    });

    function triggerAppInstallation() {
      if (deferredPrompt) {
        deferredPrompt.prompt();
        deferredPrompt.userChoice.then((choiceResult) => {
          if (choiceResult.outcome === 'accepted') showToast('Hongera!', 'App ya Rubungo imesakinishwa!');
          deferredPrompt = null;
        });
      } else {
        const m = document.getElementById('installGuideModal');
        m.classList.remove('hidden'); m.classList.add('flex');
      }
    }
    function closeInstallGuide() {
      const m = document.getElementById('installGuideModal');
      m.classList.add('hidden'); m.classList.remove('flex');
    }

    // ==================== WHATSAPP GROUP & CHAT ====================
    function openWhatsAppGroupDirect() {
      const data = loadData();
      window.open(data.whatsappGroupUrl || 'https://chat.whatsapp.com', '_blank');
    }

    function promptEditWhatsAppLink() {
      if (!currentUser || currentUser.role !== 'ADMIN') {
        showToast('Ruhusa Imezuiwa', 'Ni viongozi pekee wanaoweza kubadilisha link ya WhatsApp group!');
        return;
      }
      const data = loadData();
      const newLink = prompt('Weka kiungo cha mwaliko cha WhatsApp Group lenu:', data.whatsappGroupUrl);
      if (newLink && newLink.trim()) {
        data.whatsappGroupUrl = newLink.trim();
        saveData(data);
        showToast('Imefanikiwa', 'Kiungo cha WhatsApp Group kimesasishwa!');
      }
    }

    function postSystemChatMessage(text) {
      const data = loadData();
      const now = new Date();
      const timeStr = `${String(now.getHours()).padStart(2, '0')}:${String(now.getMinutes()).padStart(2, '0')}`;
      data.whatsappMessages.push({
        id: 'sys-' + Date.now(),
        author: 'MFUMO WA RUBUNGO',
        role: 'Taarifa Rasmi',
        text,
        time: timeStr
      });
      saveData(data);
      renderWhatsAppChat();
    }

    function sendAutoAnnouncementToChat(kind) {
      const now = new Date();
      const year = now.getFullYear();
      const monthName = SWAHILI_MONTHS[now.getMonth()];
      const groupYr = getGroupYearNumber(year);
      const nextMeet = getNextQuarterlyMeetingInfo(now);
      let msg = '';

      if (kind === 'SHARES') {
        msg = `📢 KIKUMBUSHO CHA HISA: Wanachama wote mnakumbushwa kulipia Hisa za mwezi ${monthName} ${year} (Kuanzia TZS 15,000/=).`;
      } else if (kind === 'MEETING') {
        msg = `🗓️ KIKAO CHA MIEZI 3: Kikao chetu kitafanyika ${nextMeet.formatted}. Kumbuka: Ukichelewa kuingia faini ni TZS 1,000/=`;
      } else if (kind === 'LEADER_FEE') {
        msg = `👑 MALIPO YA VIONGOZI: Kila mwanachama anakumbushwa kuweka TZS 1,000/= kwa ajili ya malipo ya viongozi kwa robo hii (${getQuarterKey(now)}).`;
      } else if (kind === 'CELEBRATION') {
        msg = `🎉 SHEREHE YA UMOJA & MWAKA MPYA: Mwaka huu ${year} ni Mwaka wa ${groupYr} wa Rubungo Legends! Tunapouaga mwaka ${year} na kuingia Mwaka wa ${groupYr + 1} (${year + 1}), tuungane kwa furaha na kushangilia! Happy New Year Mapema! 🎊`;
      }

      const input = document.getElementById('waMessageInput');
      input.value = msg;
      input.focus();
    }

    function handleSendWaMessage() {
      if (!currentUser) return;
      const input = document.getElementById('waMessageInput');
      const text = input.value.trim();
      if (!text) return;

      const data = loadData();
      const now = new Date();
      const timeStr = `${String(now.getHours()).padStart(2, '0')}:${String(now.getMinutes()).padStart(2, '0')}`;

      data.whatsappMessages.push({
        id: 'w-' + Date.now(),
        author: currentUser.name,
        role: currentUser.title,
        text,
        time: timeStr
      });

      saveData(data);
      input.value = '';
      renderWhatsAppChat();
    }

    function shareDirectToWhatsApp() {
      const input = document.getElementById('waMessageInput');
      const text = input.value.trim() || 'Habari za kazi wana-Rubungo Legends!';
      const waUrl = `https://api.whatsapp.com/send?text=${encodeURIComponent(text + '\n\n— Imetumwa kutoka RUBUNGO LEGENDS VICOBA APP')}`;
      window.open(waUrl, '_blank');
    }

    function renderWhatsAppChat() {
      const data = loadData();
      const chatBox = document.getElementById('waChatBox');
      if (!chatBox) return;

      const statusEl = document.getElementById('chatMemberStatus');
      if (statusEl) statusEl.textContent = `Wanachama ${data.members.length} wapo hewani`;

      chatBox.innerHTML = '';
      data.whatsappMessages.forEach(msg => {
        const isMyMsg = currentUser && msg.author === currentUser.name;
        const isSys = msg.author === 'MFUMO WA RUBUNGO';
        const div = document.createElement('div');
        div.className = `flex flex-col ${isSys ? 'items-center' : isMyMsg ? 'items-end' : 'items-start'}`;

        if (isSys) {
          div.innerHTML = `
            <div class="bg-amber-500/15 border border-brandGold/40 text-amber-200 p-2.5 rounded-2xl max-w-lg text-center shadow space-y-1">
              <div class="text-[10px] font-black text-brandGold uppercase"><i class="fa-solid fa-shield-halved mr-1"></i> ${escapeHtml(msg.author)} • ${escapeHtml(msg.time)}</div>
              <p class="text-xs leading-relaxed">${escapeHtml(msg.text)}</p>
            </div>
          `;
        } else {
          div.innerHTML = `
            <div class="${isMyMsg ? 'wa-bubble-out text-slate-100' : 'wa-bubble-in text-slate-200'} p-2.5 max-w-[85%] sm:max-w-md shadow space-y-1">
              <div class="text-[10px]">
                <span class="font-bold text-amber-300">${escapeHtml(msg.author)} <span class="opacity-75">(${escapeHtml(msg.role || 'Mwanachama')})</span></span>
              </div>
              <p class="text-xs leading-relaxed break-words">${escapeHtml(msg.text)}</p>
              <div class="text-[9px] text-right opacity-70 flex items-center justify-end gap-1">
                <span>${escapeHtml(msg.time)}</span>
                ${isMyMsg ? '<i class="fa-solid fa-check-double text-blue-400 text-[10px]"></i>' : ''}
              </div>
            </div>
          `;
        }
        chatBox.appendChild(div);
      });
      chatBox.scrollTop = chatBox.scrollHeight;
    }

    // ==================== KALENDA (JAN - DEC) & SHEREHE ====================
    function renderCalendarView() {
      const selYear = parseInt(document.getElementById('calendarYearSelect')?.value || new Date().getFullYear(), 10);
      const groupYr = getGroupYearNumber(selYear);
      const nextGroupYr = groupYr + 1;
      const now = new Date();
      const curMonth = now.getMonth();
      const curYear = now.getFullYear();

      document.getElementById('anniversaryHeadline').textContent =
        `Mwaka ${selYear} ni Mwaka wa ${groupYr} wa Rubungo Legends — Tunapomaliza Tunaingia Mwaka wa ${nextGroupYr} (${selYear + 1})!`;

      document.getElementById('anniversaryMessage').textContent =
        `Sherehe ya Umoja: Wanachama wote tuungane kwa furaha na kushangilia miaka ${groupYr} tangu kuanzishwa kwa kikundi chetu (2022–${selYear})!`;

      const nyBox = document.getElementById('newYearBannerBox');
      if (curMonth === 0) {
        nyBox.innerHTML = `<strong class="text-brandGold text-sm">🎆 HAPPY NEW YEAR ${curYear}!</strong> Karibuni wana-Rubungo Legends katika <strong>Mwaka wa ${getGroupYearNumber(curYear)}</strong>! Tumeuaga mwaka ${curYear - 1} kwa mafanikio na tunakaribisha mwaka mpya ${curYear} kwa umoja na mshikamano!`;
      } else {
        nyBox.innerHTML = `<strong class="text-amber-300 text-sm">🎊 KUAGA MWAKA ${selYear} & KUKARIBISHA ${selYear + 1}:</strong> Tunapomaliza Mwaka huu wa <strong>${groupYr} (${selYear})</strong>, tunawaaga mwaka huu kwa shangwe na kuukaribisha <strong>Mwaka Mpya ${selYear + 1} (Mwaka wa ${nextGroupYr})</strong>! <em>Happy New Year Mapema Wana-Rubungo Legends!</em>`;
      }

      const data = loadData();
      const grid = document.getElementById('fullYearCalendarGrid');
      if (!grid) return;
      grid.innerHTML = '';

      SWAHILI_MONTHS.forEach((mName, mIdx) => {
        const isCurrentMonth = selYear === curYear && mIdx === curMonth;
        const isQuarterMonth = [2, 5, 8, 11].includes(mIdx); // Machi, Juni, Septemba, Desemba
        const events = [];

        events.push({ icon: '💰', text: `Tarehe 1–5: Kulipia Hisa za ${mName} (Min TZS 15,000)` });

        if (mIdx === 0) {
          events.push({ icon: '🎆', text: `1 Januari: HAPPY NEW YEAR ${selYear}! Kukaribisha Mwaka wa ${groupYr}` });
        }

        if (isQuarterMonth) {
          const sun = getLastSundayOfMonth(selYear, mIdx);
          const qNum = Math.floor(mIdx / 3) + 1;
          events.push({ icon: '👑', text: `Malipo ya Viongozi (Robo ${qNum}): TZS 1,000/= kila mwanachama` });
          events.push({ icon: '🗓️', text: `Jumapili ${sun.getDate()} ${mName}: Kikao Kikuu saa 2:00 Jioni (Kuchelewa Faini 1,000/=)` });
        }

        if (mIdx === 11) {
          events.push({ icon: '🎉', text: `Sherehe ya Umoja (Mwaka wa ${groupYr}) • Kuaga ${selYear} na Kukaribisha ${selYear + 1} (Mwaka wa ${nextGroupYr})!` });
        }

        (data.customEvents || []).filter(ev => ev.year === selYear && ev.month === mIdx).forEach(ev => {
          events.push({ icon: '📌', text: `${ev.day}: ${ev.title}` });
        });

        const card = document.createElement('div');
        card.className = `rounded-2xl p-4 border shadow-lg space-y-2.5 ${isCurrentMonth ? 'bg-[#13294B] border-brandGold ring-1 ring-brandGold/50' : 'bg-brandNavy border-slate-800'}`;
        card.innerHTML = `
          <div class="flex justify-between items-center border-b border-slate-800 pb-2">
            <h4 class="font-black text-sm text-white">${mName} ${selYear}</h4>
            <div class="flex gap-1">
              ${isCurrentMonth ? '<span class="text-[9px] bg-brandGold text-slate-950 font-black px-2 py-0.5 rounded-full">MWEZI HUU</span>' : ''}
              ${isQuarterMonth ? '<span class="text-[9px] bg-rose-500/20 text-rose-300 border border-rose-500/40 font-bold px-2 py-0.5 rounded-full">KIKAO</span>' : ''}
            </div>
          </div>
          <ul class="space-y-1.5 text-[11px] text-slate-200">
            ${events.map(ev => `<li class="flex items-start gap-1.5"><span>${ev.icon}</span><span>${escapeHtml(ev.text)}</span></li>`).join('')}
          </ul>
        `;
        grid.appendChild(card);
      });
    }

    function handleAddCalendarEvent(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const year = parseInt(document.getElementById('calendarYearSelect').value, 10);
      const month = parseInt(document.getElementById('calEventMonth').value, 10);
      const day = document.getElementById('calEventDay').value.trim();
      const title = document.getElementById('calEventTitle').value.trim();
      if (!day || !title) return;

      const data = loadData();
      data.customEvents.push({ id: 'ev-' + Date.now(), year, month, day, title });
      saveData(data);
      document.getElementById('calEventDay').value = '';
      document.getElementById('calEventTitle').value = '';
      renderCalendarView();
      showToast('Kalenda Imesasishwa', `Tukio "${title}" limeongezwa kwenye ${SWAHILI_MONTHS[month]} ${year}.`);
    }

    function previewNewYearCelebration() {
      const selYear = parseInt(document.getElementById('calendarYearSelect').value, 10);
      const yrNum = getGroupYearNumber(selYear);
      const msg = `🎉 HAPPY NEW YEAR & SHEREHE YA UMOJA! Tunasherehekea Mwaka wa ${yrNum} (${selYear}) na kuingia Mwaka wa ${yrNum + 1} (${selYear + 1}) kwa furaha na mshikamano! 🥂`;
      showToast(`Sherehe ya Umoja (${selYear})`, msg);
      postSystemChatMessage(msg);
    }

    // ==================== HISA, MICHANGO YA MWEZI & VIONGOZI 1,000 ====================
    function renderMonthlyTracker() {
      const data = loadData();
      const picker = document.getElementById('trackerMonthPicker');
      const filter = document.getElementById('trackerStatusFilter')?.value || 'ALL';
      const now = new Date();
      const defaultMonth = `${now.getFullYear()}-${String(now.getMonth() + 1).padStart(2, '0')}`;
      if (picker && !picker.value) picker.value = defaultMonth;

      const monthKey = picker ? picker.value : defaultMonth;
      const [yStr, mStr] = monthKey.split('-');
      const qKey = `${yStr}-Q${Math.floor((parseInt(mStr, 10) - 1) / 3) + 1}`;

      let paidMembersCount = 0;
      let monthTotalTzs = 0;

      const tbody = document.getElementById('monthlyTrackerBody');
      if (!tbody) return;
      tbody.innerHTML = '';

      data.members.forEach(m => {
        const memMonthSavings = data.savings
          .filter(s => s.memberId === m.id && s.monthKey === monthKey)
          .reduce((sum, s) => sum + (s.amount || 0), 0);

        const hasPaidShare = memMonthSavings > 0;
        if (hasPaidShare) paidMembersCount++;
        monthTotalTzs += memMonthSavings;

        const hasPaidFee = data.leaderFees.some(f => f.memberId === m.id && f.quarterKey === qKey);

        if (filter === 'PAID' && !hasPaidShare) return;
        if (filter === 'UNPAID' && hasPaidShare) return;

        tbody.innerHTML += `
          <tr class="hover:bg-slate-800/40">
            <td class="py-2 px-2 font-mono text-amber-400">${escapeHtml(m.id)}</td>
            <td class="py-2 px-2 font-bold text-white">${escapeHtml(m.name)}</td>
            <td class="py-2 px-2 font-bold ${hasPaidShare ? 'text-emerald-400' : 'text-slate-500'}">${formatTZS(memMonthSavings)}</td>
            <td class="py-2 px-2">
              ${hasPaidShare
                ? '<span class="px-2 py-0.5 rounded bg-emerald-500/20 text-emerald-300 font-bold text-[10px]">✅ Amelipa Hisa</span>'
                : '<span class="px-2 py-0.5 rounded bg-rose-500/20 text-rose-300 font-bold text-[10px]">❌ Hajachanga</span>'}
            </td>
            <td class="py-2 px-2">
              ${hasPaidFee
                ? `<span class="px-2 py-0.5 rounded bg-cyan-500/20 text-cyan-300 font-bold text-[10px]">✅ Amelipa 1,000/= (${qKey})</span>`
                : `<span class="px-2 py-0.5 rounded bg-slate-800 text-slate-400 text-[10px]">⏳ Bado (${qKey})</span>`}
            </td>
          </tr>
        `;
      });

      document.getElementById('trackerPaidCount').textContent = `${paidMembersCount} / ${data.members.length}`;
      document.getElementById('trackerUnpaidCount').textContent = `${data.members.length - paidMembersCount}`;
      document.getElementById('trackerMonthTotal').textContent = formatTZS(monthTotalTzs);
    }

    function handleDepositSavings(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;

      const memberId = document.getElementById('savingMemberSelect').value;
      const amount = parseFloat(document.getElementById('savingAmount').value);
      const monthKey = document.getElementById('savingMonthInput').value;

      const data = loadData();
      const member = data.members.find(m => m.id === memberId);
      if (!member || isNaN(amount) || amount < 15000 || !monthKey) {
        showToast('Tahadhari', 'Chagua mwanachama, mwezi na weka kiasi kisichopungua TZS 15,000!');
        return;
      }

      member.savings = (member.savings || 0) + amount;
      data.cashOnHand += amount;
      data.savings.push({
        id: 'sav-' + Date.now(),
        memberId: member.id,
        memberName: member.name,
        amount,
        monthKey,
        date: new Date().toISOString().split('T')[0],
        recordedBy: currentUser.name
      });

      saveData(data);
      document.getElementById('savingAmount').value = '';
      showToast('Hisa Imehifadhiwa', `${member.name} ameweka ${formatTZS(amount)} kwa mwezi ${monthKey}.`);
      refreshAllUI();
    }

    function handleLeaderFeePayment(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const memberId = document.getElementById('leaderFeeMemberSelect').value;
      const quarterKey = document.getElementById('leaderFeeQuarterSelect').value;
      const data = loadData();
      const member = data.members.find(m => m.id === memberId);
      if (!member || !quarterKey) return;

      if (data.leaderFees.some(f => f.memberId === member.id && f.quarterKey === quarterKey)) {
        showToast('Taarifa', `${member.name} tayari alishalipa 1,000/= ya viongozi kwa ${quarterKey}.`);
        return;
      }

      data.leaderFees.push({
        id: 'lf-' + Date.now(),
        memberId: member.id,
        memberName: member.name,
        amount: 1000,
        quarterKey,
        date: new Date().toISOString().split('T')[0],
        recordedBy: currentUser.name
      });
      data.cashOnHand += 1000;
      saveData(data);
      showToast('Malipo ya Viongozi', `${member.name} amelipa TZS 1,000/= (${quarterKey}).`);
      refreshAllUI();
    }

    function handlePenaltyAction(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const memberId = document.getElementById('penaltyMemberSelect').value;
      const amount = parseFloat(document.getElementById('penaltyAmount').value);
      const type = document.getElementById('penaltyType').value;

      const data = loadData();
      const member = data.members.find(m => m.id === memberId);
      if (!member || isNaN(amount) || amount <= 0) return;

      if (type === 'ADD') {
        member.penalties = (member.penalties || 0) + amount;
        showToast('Faini Imeongezwa', `${member.name} ametozwa faini ya ${formatTZS(amount)}.`);
      } else {
        const paid = Math.min(amount, member.penalties || 0);
        if (paid <= 0) {
          showToast('Taarifa', `${member.name} hana deni la faini.`);
          return;
        }
        member.penalties -= paid;
        data.cashOnHand += paid;
        data.totalPenaltiesCollected = (data.totalPenaltiesCollected || 0) + paid;
        showToast('Faini Imelipwa', `${member.name} amelipa faini ya ${formatTZS(paid)} (imerudi kwenye mfuko).`);
      }

      saveData(data);
      refreshAllUI();
    }

    // ==================== MIKOPO (50,000 - 500,000), KIKOKOTOO & UTHIBITISHO ====================
    function updateLoanCalculator() {
      const principal = parseFloat(document.getElementById('calcLoanSlider')?.value || 100000);
      const penalty = parseFloat(document.getElementById('calcPenaltyInput')?.value || 0);
      const interest = Math.round(principal * 0.05);
      const total = principal + interest + (isNaN(penalty) ? 0 : penalty);

      document.getElementById('calcLoanDisplay').textContent = formatTZS(principal);
      document.getElementById('calcResPrincipal').textContent = formatTZS(principal);
      document.getElementById('calcResInterest').textContent = formatTZS(interest);
      document.getElementById('calcResPenalty').textContent = formatTZS(isNaN(penalty) ? 0 : penalty);
      document.getElementById('calcResTotal').textContent = formatTZS(total);
    }

    function handleApplyLoan(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;

      const memberId = document.getElementById('loanMemberSelect').value;
      const amount = parseFloat(document.getElementById('loanAmount').value);
      const data = loadData();
      const member = data.members.find(m => m.id === memberId);
      if (!member || isNaN(amount)) return;

      if (amount < 50000 || amount > 500000) {
        showToast('Kiasi Hakiruhusiwi', 'Mkopo ni kuanzia TZS 50,000/= mpaka TZS 500,000/= pekee!');
        return;
      }

      const maxBySavings = (member.savings || 0) * 2;
      if ((member.loanBalance || 0) + amount > maxBySavings) {
        showToast('Ukomo wa Akiba', `Jumla ya mkopo (${formatTZS((member.loanBalance || 0) + amount)}) inazidi 2x ya akiba ya ${member.name} (${formatTZS(maxBySavings)}).`);
        return;
      }

      if (amount > data.cashOnHand) {
        showToast('Salio Halitoshi', `Mfuko una ${formatTZS(data.cashOnHand)} pekee mkononi!`);
        return;
      }

      const interest = Math.round(amount * 0.05);
      member.loanBalance = (member.loanBalance || 0) + amount + interest;
      data.cashOnHand -= amount;

      data.loans.push({
        id: 'ln-' + Date.now(),
        memberId: member.id,
        memberName: member.name,
        type: 'DISBURSEMENT',
        amount,
        interest,
        note: `Mkopo + Riba 5% (${formatTZS(interest)})`,
        date: new Date().toISOString().split('T')[0]
      });

      saveData(data);
      document.getElementById('loanAmount').value = '';
      postSystemChatMessage(`💳 MKOPO MPYA: ${member.name} amekopeshwa ${formatTZS(amount)} + Riba 5% (${formatTZS(interest)}). Jumla ya deni: ${formatTZS(member.loanBalance)}.`);
      showToast('Mkopo Umetolewa', `${member.name} amekopeshwa ${formatTZS(amount)}.`);
      refreshAllUI();
    }

    function handleLoanPenalty(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const memberId = document.getElementById('loanPenaltyMemberSelect').value;
      const penAmount = parseFloat(document.getElementById('loanPenaltyAmount').value);
      const data = loadData();
      const member = data.members.find(m => m.id === memberId);

      if (!member || isNaN(penAmount) || penAmount <= 0 || member.loanBalance <= 0) return;

      member.loanBalance += penAmount;
      data.loans.push({
        id: 'lp-' + Date.now(),
        memberId: member.id,
        memberName: member.name,
        type: 'PENALTY',
        amount: penAmount,
        interest: 0,
        note: 'Faini ya Kuchelewa Marejesho (Itarudi Mfukoni)',
        date: new Date().toISOString().split('T')[0]
      });

      saveData(data);
      document.getElementById('loanPenaltyAmount').value = '';
      postSystemChatMessage(`⚠️ FAINI YA MKOPO: ${member.name} ameongezewa faini ya ${formatTZS(penAmount)} kwa kuchelewesha marejesho. Salio la deni sasa ni ${formatTZS(member.loanBalance)}.`);
      showToast('Faini ya Mkopo', `Faini ya ${formatTZS(penAmount)} imeongezwa kwenye deni la ${member.name}.`);
      refreshAllUI();
    }

    function handleRepayLoan(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const memberId = document.getElementById('repayMemberSelect').value;
      const amount = parseFloat(document.getElementById('repayAmount').value);
      const data = loadData();
      const member = data.members.find(m => m.id === memberId);

      if (!member || isNaN(amount) || amount <= 0 || member.loanBalance <= 0) return;

      const payment = Math.min(amount, member.loanBalance);
      member.loanBalance -= payment;
      data.cashOnHand += payment;

      const estInterest = Math.round(payment * (5 / 105));
      data.totalInterestEarned = (data.totalInterestEarned || 0) + estInterest;

      data.loans.push({
        id: 'rp-' + Date.now(),
        memberId: member.id,
        memberName: member.name,
        type: 'REPAYMENT',
        amount: payment,
        interest: estInterest,
        note: member.loanBalance === 0 ? 'AMEMALIZA DENI LOTE ✅' : `Bado anadaiwa ${formatTZS(member.loanBalance)}`,
        date: new Date().toISOString().split('T')[0]
      });

      saveData(data);
      document.getElementById('repayAmount').value = '';

      if (member.loanBalance === 0) {
        const clearMsg = `✅ UTHIBITISHO RASMI: ${member.name} amemaliza kulipa deni lake lote la mkopo pamoja na riba (${formatTZS(payment)} mwisho)! HANA DENI LOLOTE na mfuko wa Rubungo Legends!`;
        postSystemChatMessage(clearMsg);
        showToast('AMEMALIZA DENI! ✅', `${member.name} amemaliza deni lake pamoja na riba. Hana deni!`);
      } else {
        const remMsg = `⏳ REJESHO LA MKOPO: ${member.name} amelipa ${formatTZS(payment)}. BADO ANADAIWA salio la ${formatTZS(member.loanBalance)} (Mkopo + Riba).`;
        postSystemChatMessage(remMsg);
        showToast('Rejesho Limepokelewa', `${member.name} amelipa ${formatTZS(payment)}. Bado anadaiwa ${formatTZS(member.loanBalance)}.`);
      }

      refreshAllUI();
    }

    function updateMaxLoanHint() {
      const memberId = document.getElementById('loanMemberSelect').value;
      const data = loadData();
      const member = data.members.find(m => m.id === memberId);
      const hintEl = document.getElementById('maxLoanHint');
      if (member) {
        const bySavings = Math.max(0, (member.savings * 2) - (member.loanBalance || 0));
        const allowedMax = Math.min(500000, bySavings);
        hintEl.textContent = `Akiba 2x: ${formatTZS(member.savings * 2)} • Kikomo chake: ${formatTZS(allowedMax)} (Min 50,000)`;
      } else {
        hintEl.textContent = `Kikomo: TZS 50,000 - 500,000`;
      }
    }

    // ==================== RUBUNGO TUBE ====================
    const videoCatalog = [
      { id: "v1", title: "Azam Sports HD: NBC Premier League Tanzania", category: "AZAM", author: "Azam TV", embedId: "fJ9rUzIMcZQ" },
      { id: "v2", title: "UEFA Champions League: Magoli na Marudio", category: "SPORTS", author: "UEFA Official", embedId: "kJQP7kiw5Fk" },
      { id: "v3", title: "Tom & Jerry: Katuni za Watoto", category: "CARTOON", author: "Kids TV", embedId: "t0Q2otsqC4I" },
      { id: "v4", title: "Filamu ya Kiswahili: DJ Afro Action Movie", category: "SWAHILI_DJ", author: "DJ Afro Swahili", embedId: "1abgBwB3W_U" },
      { id: "v5", title: "Hollywood English Movie: Mission Action", category: "ENGLISH", author: "Paramount Pictures", embedId: "2m1drlOYSDw" },
      { id: "v6", title: "Boys Over Flowers (K-Drama Kikorea)", category: "KOREAN", author: "KBS World", embedId: "MdeR_zXhU-k" }
    ];
    let currentVideoCategory = 'ALL';

    function setVideoCategory(cat) {
      currentVideoCategory = cat;
      ['ALL', 'SPORTS', 'AZAM', 'CARTOON', 'SWAHILI_DJ', 'ENGLISH', 'KOREAN'].forEach(c => {
        const btn = document.getElementById('vcat-' + c);
        if (btn) {
          btn.className = (c === cat)
            ? 'px-3 py-1.5 rounded-xl font-bold bg-rose-600 text-white transition'
            : 'px-3 py-1.5 rounded-xl font-bold bg-slate-900 text-slate-300 border border-slate-700 hover:border-rose-500 transition';
        }
      });
      renderVideoCards();
    }

    function renderVideoCards() {
      const grid = document.getElementById('videoCardsGrid');
      if (!grid) return;
      const query = (document.getElementById('videoSearchInput')?.value || '').toLowerCase();
      grid.innerHTML = '';

      const filtered = videoCatalog.filter(v => {
        const matchesCategory = currentVideoCategory === 'ALL' || v.category === currentVideoCategory;
        const matchesQuery = v.title.toLowerCase().includes(query) || v.author.toLowerCase().includes(query);
        return matchesCategory && matchesQuery;
      });

      if (filtered.length === 0) {
        grid.innerHTML = `<div class="col-span-full text-center text-xs text-slate-400 py-8">Hakuna video iliyopatikana.</div>`;
        return;
      }

      filtered.forEach(video => {
        const div = document.createElement('div');
        div.className = 'bg-slate-900 rounded-2xl border border-slate-800 p-3 hover:border-rose-500 transition cursor-pointer shadow flex flex-col justify-between';
        div.onclick = () => playSelectedVideo(video.embedId, video.title);
        div.innerHTML = `
          <div>
            <div class="relative w-full h-32 bg-black rounded-xl overflow-hidden mb-2">
              <img src="https://img.youtube.com/vi/${video.embedId}/mqdefault.jpg" alt="${escapeHtml(video.title)}" class="w-full h-full object-cover" />
              <div class="absolute inset-0 bg-black/30 flex items-center justify-center">
                <div class="w-8 h-8 rounded-full bg-rose-600 text-white flex items-center justify-center text-xs"><i class="fa-solid fa-play"></i></div>
              </div>
            </div>
            <span class="text-[9px] px-2 py-0.5 rounded bg-rose-950 text-rose-300 font-bold border border-rose-800">${escapeHtml(video.category)}</span>
            <h4 class="font-bold text-white text-xs mt-1.5 line-clamp-2">${escapeHtml(video.title)}</h4>
          </div>
          <p class="text-[10px] text-slate-400 mt-2">${escapeHtml(video.author)}</p>
        `;
        grid.appendChild(div);
      });
    }
    function filterVideosCatalog() { renderVideoCards(); }
    function playSelectedVideo(embedId, title) {
      document.getElementById('cinemaIframe').src = `https://www.youtube.com/embed/${embedId}?autoplay=1`;
      document.getElementById('cinemaActiveTitle').textContent = `Inacheza: ${title}`;
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }

    // ==================== MICHEZO 10 YA GAME ====================
    let gameLoopInterval = null;
    let gameCountdownTimer = null;
    function clearAllGameTimers() {
      clearInterval(gameLoopInterval); clearInterval(gameCountdownTimer);
      gameLoopInterval = null; gameCountdownTimer = null;
    }

    function launchGame(gameType) {
      const arena = document.getElementById('activeGameArena');
      const title = document.getElementById('arenaGameTitle');
      const container = document.getElementById('gamePlayContainer');
      arena.classList.remove('hidden');
      clearAllGameTimers();
      window.scrollTo({ top: arena.offsetTop - 80, behavior: 'smooth' });

      const map = {
        snake: ["Mchezo wa Nyoka (Snake) 🐍", startSnakeGame],
        tictactoe: ["X na O (Tic-Tac-Toe vs AI) ❌⭕", startTicTacToeGame],
        math: ["Hesabu za Haraka 🧮", startMathChallenge],
        memory: ["Kumbukumbu ya Kadi 🃏", startMemoryGame],
        quiz: ["Maswali ya VICOBA 💡", startVicobaQuiz],
        tap: ["Kasi ya Kubofya ⚡", startSpeedTapGame],
        guess: ["Buni Namba (1 - 100) 🎯", startGuessNumberGame],
        rps: ["Mwamba, Karatasi, Mikasi ✊📄✂️", startRpsGame],
        lucky: ["Sanduku la Bahati 🎁", startLuckyBoxGame],
        simon: ["Mfuatano wa Rangi 🎨", startSimonGame]
      };
      const selected = map[gameType] || map.math;
      title.innerHTML = selected[0];
      selected[1](container);
    }
    function closeGameArena() {
      clearAllGameTimers();
      document.getElementById('activeGameArena').classList.add('hidden');
      document.getElementById('gamePlayContainer').innerHTML = '';
    }

    function startSnakeGame(container) {
      container.innerHTML = `
        <div class="flex flex-col items-center space-y-3">
          <div class="text-xs font-bold text-amber-400">Alama: <span id="snakeScore">0</span></div>
          <canvas id="snakeCanvas" width="240" height="240" class="border border-slate-700 rounded-2xl"></canvas>
          <div class="grid grid-cols-3 gap-2 w-40 pt-2">
            <div></div><button onclick="setSnakeDir('UP')" class="bg-slate-800 text-white p-2 rounded-xl font-bold"><i class="fa-solid fa-arrow-up"></i></button><div></div>
            <button onclick="setSnakeDir('LEFT')" class="bg-slate-800 text-white p-2 rounded-xl font-bold"><i class="fa-solid fa-arrow-left"></i></button>
            <button onclick="setSnakeDir('DOWN')" class="bg-slate-800 text-white p-2 rounded-xl font-bold"><i class="fa-solid fa-arrow-down"></i></button>
            <button onclick="setSnakeDir('RIGHT')" class="bg-slate-800 text-white p-2 rounded-xl font-bold"><i class="fa-solid fa-arrow-right"></i></button>
          </div>
        </div>
      `;
      const cvs = document.getElementById('snakeCanvas'), ctx = cvs.getContext('2d'), box = 12;
      let snake = [{ x: 10 * box, y: 10 * box }], food = { x: 5 * box, y: 5 * box }, d = 'RIGHT', score = 0;
      window.setSnakeDir = (dir) => {
        if (dir === 'LEFT' && d !== 'RIGHT') d = 'LEFT';
        if (dir === 'RIGHT' && d !== 'LEFT') d = 'RIGHT';
        if (dir === 'UP' && d !== 'DOWN') d = 'UP';
        if (dir === 'DOWN' && d !== 'UP') d = 'DOWN';
      };
      gameLoopInterval = setInterval(() => {
        ctx.fillStyle = '#020C1B'; ctx.fillRect(0, 0, cvs.width, cvs.height);
        ctx.fillStyle = '#D4AF37'; ctx.fillRect(food.x, food.y, box, box);
        for (let i = 0; i < snake.length; i++) { ctx.fillStyle = i === 0 ? '#10B981' : '#059669'; ctx.fillRect(snake[i].x, snake[i].y, box, box); }
        let sx = snake[0].x, sy = snake[0].y;
        if (d === 'LEFT') sx -= box; if (d === 'UP') sy -= box; if (d === 'RIGHT') sx += box; if (d === 'DOWN') sy += box;
        if (sx < 0 || sx >= cvs.width || sy < 0 || sy >= cvs.height || snake.some(p => p.x === sx && p.y === sy)) {
          clearAllGameTimers(); showToast('Mchezo Umekwisha!', `Alama zako: ${score}`); startSnakeGame(container); return;
        }
        if (sx === food.x && sy === food.y) { score += 10; document.getElementById('snakeScore').textContent = score; food = { x: Math.floor(Math.random() * 20) * box, y: Math.floor(Math.random() * 20) * box }; }
        else snake.pop();
        snake.unshift({ x: sx, y: sy });
      }, 150);
    }

    function startTicTacToeGame(container) {
      let board = Array(9).fill(''), over = false;
      const wins = [[0,1,2],[3,4,5],[6,7,8],[0,3,6],[1,4,7],[2,5,8],[0,4,8],[2,4,6]];
      container.innerHTML = `<div class="flex flex-col items-center space-y-3"><p id="tttStatus" class="text-xs font-bold text-amber-300">Zamu yako (X)</p><div class="grid grid-cols-3 gap-2 w-56 h-56">${[0,1,2,3,4,5,6,7,8].map(i => `<button onclick="handleTttClick(${i})" id="tttCell-${i}" class="bg-slate-900 border border-slate-700 text-2xl font-black text-amber-400 rounded-xl flex items-center justify-center"></button>`).join('')}</div><button onclick="launchGame('tictactoe')" class="bg-slate-800 text-xs text-white px-4 py-1.5 rounded-xl font-bold">Anza Upya</button></div>`;
      const checkWin = (p) => wins.some(c => c.every(i => board[i] === p));
      window.handleTttClick = (idx) => {
        if (over || board[idx] !== '') return;
        board[idx] = 'X'; document.getElementById(`tttCell-${idx}`).textContent = 'X';
        if (checkWin('X')) { over = true; document.getElementById('tttStatus').textContent = 'Hongera! Umeshinda 🎉'; return; }
        let emp = board.map((v, i) => v === '' ? i : null).filter(v => v !== null);
        if (!emp.length) { over = true; document.getElementById('tttStatus').textContent = 'Sare 🤝'; return; }
        let ai = emp[Math.floor(Math.random() * emp.length)];
        board[ai] = 'O'; const c = document.getElementById(`tttCell-${ai}`); c.textContent = 'O'; c.classList.remove('text-amber-400'); c.classList.add('text-rose-500');
        if (checkWin('O')) { over = true; document.getElementById('tttStatus').textContent = 'Kompyuta Imeshinda!'; }
      };
    }

    function startMathChallenge(container, score = 0) {
      let n1 = Math.floor(Math.random() * 25) + 5, n2 = Math.floor(Math.random() * 18) + 3, ans = n1 + n2;
      let choices = [ans, ans + 3, ans - 2, ans + 6].sort(() => Math.random() - 0.5);
      container.innerHTML = `<div class="bg-slate-900 p-5 rounded-2xl border border-slate-700 space-y-4 max-w-xs w-full text-center"><div class="text-xs text-emerald-400 font-bold">Alama: ${score}</div><h4 class="text-2xl font-black text-white">${n1} + ${n2} = ?</h4><div class="grid grid-cols-2 gap-2">${choices.map(c => `<button onclick="answerMath(${c === ans}, ${score})" class="bg-slate-800 hover:bg-slate-700 text-white font-bold p-2.5 rounded-xl">${c}</button>`).join('')}</div></div>`;
      window.answerMath = (ok, sc) => { if (ok) startMathChallenge(container, sc + 10); else { showToast('Jibu Si Sahihi', `Alama: ${sc}`); startMathChallenge(container, 0); } };
    }

    function startMemoryGame(container) {
      const icons = ['💰','🦁','⚽','🏆','📱','💎','🚀','🎯'];
      let deck = [...icons, ...icons].sort(() => Math.random() - 0.5), flipped = [], matched = 0, moves = 0;
      container.innerHTML = `<div class="space-y-3 text-center"><p class="text-xs text-amber-300 font-bold">Hatua: <span id="memMoves">0</span></p><div class="grid grid-cols-4 gap-2 w-64">${deck.map((_, i) => `<button id="mem-${i}" onclick="flipMem(${i})" class="h-14 bg-slate-800 border border-slate-700 rounded-xl text-xl font-bold flex items-center justify-center">❓</button>`).join('')}</div></div>`;
      window.flipMem = (i) => {
        const b = document.getElementById(`mem-${i}`);
        if (flipped.length >= 2 || b.dataset.done === '1' || flipped.includes(i)) return;
        b.textContent = deck[i]; b.classList.add('bg-slate-700'); flipped.push(i);
        if (flipped.length === 2) {
          moves++; document.getElementById('memMoves').textContent = moves;
          const [a, c] = flipped;
          if (deck[a] === deck[c]) { document.getElementById(`mem-${a}`).dataset.done = '1'; document.getElementById(`mem-${c}`).dataset.done = '1'; matched += 2; flipped = []; if (matched === deck.length) showToast('Umefaulu! 🎉', `Hatua ${moves}!`); }
          else setTimeout(() => { [a, c].forEach(x => { const el = document.getElementById(`mem-${x}`); if (el) { el.textContent = '❓'; el.classList.remove('bg-slate-700'); } }); flipped = []; }, 650);
        }
      };
    }

    function startVicobaQuiz(container) {
      const qs = [
        { q: "Kiwango cha chini cha hisa za mwezi kwenye Rubungo Legends ni kipi?", opts: ["TZS 5,000", "TZS 15,000", "TZS 50,000"], a: 1 },
        { q: "Kikao cha miezi 3 hufanyika lini na kuchelewa faini ni shilingi ngapi?", opts: ["Jumapili ya mwisho saa 2 jioni • Faini 1,000/=", "Jumatatu asubuhi • Faini 500/=", "Ijumaa • Hakuna faini"], a: 0 },
        { q: "Kila mwanachama hutoa shilingi ngapi za viongozi kila baada ya miezi 3?", opts: ["TZS 500/=", "TZS 1,000/=", "TZS 5,000/="], a: 1 },
        { q: "Kikomo cha mikopo ya kawaida hapa ni kuanzia shilingi ngapi mpaka ngapi?", opts: ["10,000 - 100,000", "50,000 - 500,000", "1,000,000+"], a: 1 }
      ];
      let idx = 0, score = 0;
      function renderQ() {
        if (idx >= qs.length) { container.innerHTML = `<div class="text-center space-y-3"><h4 class="text-xl font-black text-brandGold">Umepata ${score} / ${qs.length}! 🎉</h4><button onclick="launchGame('quiz')" class="bg-brandGold text-slate-950 font-bold px-4 py-2 rounded-xl text-xs">Cheza Tena</button></div>`; return; }
        const cur = qs[idx];
        container.innerHTML = `<div class="bg-slate-900 p-5 rounded-2xl border border-slate-700 max-w-md w-full space-y-3"><span class="text-[10px] text-amber-400 font-bold">Swali ${idx + 1} / ${qs.length}</span><h4 class="text-sm font-bold text-white">${cur.q}</h4><div class="space-y-2">${cur.opts.map((o, i) => `<button onclick="ansQuiz(${i})" class="w-full text-left bg-slate-800 hover:bg-slate-700 text-xs text-white p-2.5 rounded-xl font-semibold">${o}</button>`).join('')}</div></div>`;
      }
      window.ansQuiz = (c) => { if (c === qs[idx].a) score++; idx++; renderQ(); }; renderQ();
    }

    function startSpeedTapGame(container) {
      let count = 0, time = 10, started = false;
      container.innerHTML = `<div class="text-center space-y-4"><div class="flex justify-center gap-6 text-sm font-bold"><span class="text-amber-400">Muda: <span id="tapTime">10</span>s</span><span class="text-emerald-400">Mibofyo: <span id="tapCount">0</span></span></div><button onclick="doTap()" class="w-36 h-36 rounded-full bg-gradient-to-tr from-rose-600 to-amber-500 text-white font-black text-lg shadow-2xl active:scale-90 transition">BOFYA HAPA!</button></div>`;
      window.doTap = () => {
        if (time <= 0) return;
        if (!started) { started = true; gameCountdownTimer = setInterval(() => { time--; const el = document.getElementById('tapTime'); if (el) el.textContent = time; if (time <= 0) { clearAllGameTimers(); showToast('Muda Umekwisha!', `Mibofyo ${count}!`); } }, 1000); }
        count++; document.getElementById('tapCount').textContent = count;
      };
    }

    function startGuessNumberGame(container) {
      const secret = Math.floor(Math.random() * 100) + 1; let tries = 0;
      container.innerHTML = `<div class="bg-slate-900 p-5 rounded-2xl border border-slate-700 max-w-xs w-full space-y-3 text-center"><p class="text-xs text-slate-300" id="guessHint">Chagua namba kati ya 1 na 100!</p><input type="number" id="guessInput" min="1" max="100" class="w-full bg-slate-800 text-white text-center font-bold p-2 rounded-xl text-sm outline-none select-text" /><button onclick="checkGuess()" class="w-full bg-cyan-600 text-white font-bold py-2 rounded-xl text-xs">Angalia</button></div>`;
      window.checkGuess = () => {
        const v = parseInt(document.getElementById('guessInput').value, 10); if (isNaN(v)) return; tries++;
        const h = document.getElementById('guessHint');
        if (v === secret) h.innerHTML = `<span class="text-emerald-400 font-bold">HONGERA! Ni ${secret} (Majaribio ${tries}) 🎉</span>`;
        else if (v < secret) h.innerHTML = `<span class="text-amber-400">KUBWA zaidi ya ${v} ⬆️</span>`;
        else h.innerHTML = `<span class="text-rose-400">NDOGO zaidi ya ${v} ⬇️</span>`;
      };
    }

    function startRpsGame(container) {
      let uScore = 0, aiScore = 0; const items = [{ k: 'Mwamba', icon: '✊' }, { k: 'Karatasi', icon: '📄' }, { k: 'Mikasi', icon: '✂️' }];
      container.innerHTML = `<div class="text-center space-y-4"><div class="text-xs font-bold text-amber-300" id="rpsScore">Wewe: 0 | Kompyuta: 0</div><p class="text-xs text-slate-300" id="rpsResult">Chagua silaha yako:</p><div class="flex gap-3 justify-center">${items.map(it => `<button onclick="playRps('${it.k}')" class="bg-slate-800 hover:bg-slate-700 p-4 rounded-2xl text-2xl border border-slate-700">${it.icon}<span class="block text-[10px] mt-1">${it.k}</span></button>`).join('')}</div></div>`;
      window.playRps = (u) => {
        const ai = items[Math.floor(Math.random() * 3)].k; let msg = 'Sare!';
        if ((u === 'Mwamba' && ai === 'Mikasi') || (u === 'Karatasi' && ai === 'Mwamba') || (u === 'Mikasi' && ai === 'Karatasi')) { uScore++; msg = 'Umeshinda! 🎉'; }
        else if (u !== ai) { aiScore++; msg = 'Kompyuta Imeshinda!'; }
        document.getElementById('rpsScore').textContent = `Wewe: ${uScore} | Kompyuta: ${aiScore}`;
        document.getElementById('rpsResult').textContent = `Wewe (${u}) vs Kompyuta (${ai}) → ${msg}`;
      };
    }

    function startLuckyBoxGame(container) {
      const prizes = ['💎 Almas 1000', '🪙 Dhahabu 500', '💨 Hamna Kitu', '🏆 Kombe la Dhahabu'].sort(() => Math.random() - 0.5);
      container.innerHTML = `<div class="text-center space-y-3"><p class="text-xs text-slate-300" id="luckyMsg">Chagua sanduku 1 la bahati:</p><div class="grid grid-cols-2 gap-3 w-56">${prizes.map((_, i) => `<button id="box-${i}" onclick="openBox(${i})" class="bg-slate-800 hover:bg-amber-600/30 border border-brandGold/40 p-5 rounded-2xl text-2xl">🎁</button>`).join('')}</div><button onclick="launchGame('lucky')" class="bg-slate-800 text-xs text-white px-4 py-1.5 rounded-xl font-bold">Cheza Tena</button></div>`;
      let picked = false;
      window.openBox = (i) => { if (picked) return; picked = true; prizes.forEach((p, idx) => document.getElementById(`box-${idx}`).innerHTML = `<span class="text-xs font-bold text-white">${p}</span>`); document.getElementById('luckyMsg').textContent = `Umepata: ${prizes[i]}!`; };
    }

    function startSimonGame(container) {
      const colors = [{ id: 0, bg: 'bg-emerald-600' }, { id: 1, bg: 'bg-rose-600' }, { id: 2, bg: 'bg-amber-500' }, { id: 3, bg: 'bg-blue-600' }];
      let seq = [], userIdx = 0, locking = false;
      container.innerHTML = `<div class="text-center space-y-3"><p class="text-xs font-bold text-amber-300" id="simonStatus">Bonyeza "Anza" kisha fuatisha rangi!</p><div class="grid grid-cols-2 gap-3 w-48 mx-auto">${colors.map(c => `<button id="sim-${c.id}" onclick="tapSimon(${c.id})" class="${c.bg} h-20 rounded-2xl opacity-85 transition"></button>`).join('')}</div><button onclick="nextSimonRound(true)" class="bg-brandGold text-slate-950 font-bold px-4 py-1.5 rounded-xl text-xs">Anza / Rudia</button></div>`;
      function flash(id) { const el = document.getElementById(`sim-${id}`); if (!el) return; el.classList.add('ring-4', 'ring-white', 'scale-105'); setTimeout(() => el.classList.remove('ring-4', 'ring-white', 'scale-105'), 350); }
      window.nextSimonRound = (reset = false) => {
        if (reset) seq = []; seq.push(Math.floor(Math.random() * 4)); userIdx = 0; locking = true;
        document.getElementById('simonStatus').textContent = `Angalia... (Hatua ${seq.length})`;
        seq.forEach((cId, i) => setTimeout(() => { flash(cId); if (i === seq.length - 1) setTimeout(() => { locking = false; const st = document.getElementById('simonStatus'); if (st) st.textContent = 'Zamu yako!'; }, 400); }, (i + 1) * 600));
      };
      window.tapSimon = (id) => {
        if (locking || seq.length === 0) return; flash(id);
        if (id === seq[userIdx]) { userIdx++; if (userIdx === seq.length) { document.getElementById('simonStatus').textContent = 'Safi! Unapanda ngazi...'; setTimeout(() => nextSimonRound(false), 700); } }
        else { showToast('Umekosea!', `Ulifikia hatua ya ${seq.length}.`); seq = []; document.getElementById('simonStatus').textContent = 'Umekosea! Bonyeza Anza tena.'; }
      };
    }

    // ==================== LOGIN, BOOT & UI REFRESH ====================
    function handleLogin(e) {
      e.preventDefault();
      const rawIdentifier = document.getElementById('loginIdentifier').value.trim();
      const password = document.getElementById('loginPassword').value.trim();
      const data = loadData();

      if (password !== UNIVERSAL_PASSWORD) {
        showToast('KOSA', 'Nenosiri si sahihi! PIN ni 1234');
        return;
      }

      const cleanedInput = cleanPhone(rawIdentifier);
      let userFound = data.members.find(m => cleanPhone(m.phone) === cleanedInput || m.id.toLowerCase() === rawIdentifier.toLowerCase());
      if (!userFound && rawIdentifier.toLowerCase() === 'admin') userFound = data.members.find(m => m.role === 'CHAIRPERSON');

      if (userFound) {
        currentUser = {
          role: userFound.role && userFound.role !== 'MEMBER' ? 'ADMIN' : 'MEMBER',
          actualRole: userFound.role || 'MEMBER',
          title: userFound.title || 'Mwanachama wa Kawaida',
          id: userFound.id,
          name: userFound.name,
          phone: userFound.phone,
          isChairperson: userFound.role === 'CHAIRPERSON'
        };
        localStorage.setItem('RUBUNGO_ACTIVE_USER_V21', JSON.stringify(currentUser));
        bootApp();
        return;
      }

      showToast('KOSA', `Namba ya simu "${rawIdentifier}" haijasajiliwa!`);
    }

    function handleLogout() {
      clearAllGameTimers();
      currentUser = null;
      localStorage.removeItem('RUBUNGO_ACTIVE_USER_V21');
      document.getElementById('appScreen').classList.add('hidden');
      document.getElementById('loginScreen').classList.remove('hidden');
    }

    function bootApp() {
      updateOnlineBadge();
      if (!currentUser) {
        document.getElementById('loginScreen').classList.remove('hidden');
        document.getElementById('appScreen').classList.add('hidden');
        return;
      }

      document.getElementById('loginScreen').classList.add('hidden');
      document.getElementById('appScreen').classList.remove('hidden');

      const subtitleEl = document.getElementById('topUserRoleSubtitle');
      if (subtitleEl) subtitleEl.textContent = `${currentUser.name} • ${currentUser.title.toUpperCase()}`;

      const isAdmin = currentUser.role === 'ADMIN';
      const btnEdit = document.getElementById('btnEditWaLink');
      if (btnEdit) btnEdit.style.display = isAdmin ? 'inline-block' : 'none';

      const quickChat = document.getElementById('leaderQuickChatBar');
      if (quickChat) quickChat.classList.toggle('hidden', !isAdmin);

      ['leaderAddMemberCard', 'leaderSavingsCard', 'leaderLoansCard', 'leaderAddEventCard'].forEach(cardId => {
        const card = document.getElementById(cardId);
        if (card) card.classList.toggle('hidden', !isAdmin);
      });

      const now = new Date();
      const curMonthKey = `${now.getFullYear()}-${String(now.getMonth() + 1).padStart(2, '0')}`;
      const savMonthEl = document.getElementById('savingMonthInput');
      if (savMonthEl && !savMonthEl.value) savMonthEl.value = curMonthKey;
      const trackMonthEl = document.getElementById('trackerMonthPicker');
      if (trackMonthEl && !trackMonthEl.value) trackMonthEl.value = curMonthKey;

      const qSelect = document.getElementById('leaderFeeQuarterSelect');
      if (qSelect) {
        const y = now.getFullYear();
        const curQ = getQuarterKey(now);
        qSelect.innerHTML = [1,2,3,4].map(q => {
          const val = `${y}-Q${q}`;
          return `<option value="${val}" ${val === curQ ? 'selected' : ''}>Robo ${q} (${val}) - TZS 1,000/=</option>`;
        }).join('');
      }

      pullFromCloud(true);
      updateLoanCalculator();
      switchTab('whatsapp');
      renderWhatsAppChat();
      renderVideoCards();
      triggerOnlineReminders(false);
    }

    function switchTab(tabId) {
      if (tabId !== 'games') clearAllGameTimers();
      ['whatsapp', 'calendar', 'savings', 'loans', 'members', 'tube', 'games', 'reports'].forEach(id => {
        const el = document.getElementById('view-' + id);
        if (el) el.classList.add('hidden');
        const btn = document.getElementById('tabBtn-' + id);
        if (btn) {
          btn.classList.remove('bg-brandGold', 'text-slate-950', 'font-bold');
          btn.classList.add('text-slate-300');
        }
      });

      const activeEl = document.getElementById('view-' + tabId);
      if (activeEl) activeEl.classList.remove('hidden');
      const activeBtn = document.getElementById('tabBtn-' + tabId);
      if (activeBtn) {
        activeBtn.classList.add('bg-brandGold', 'text-slate-950', 'font-bold');
        activeBtn.classList.remove('text-slate-300');
      }

      refreshAllUI();
      if (tabId === 'calendar') renderCalendarView();
    }

    function refreshAllUI() {
      const data = loadData();
      renderAutoAnnouncements();
      renderMembersTable();
      renderMonthlyTracker();

      const totalSavings = data.members.reduce((sum, m) => sum + (m.savings || 0), 0);
      const totalLoans = data.members.reduce((sum, m) => sum + (m.loanBalance || 0), 0);
      const totalIncome = (data.totalInterestEarned || 0) + (data.totalPenaltiesCollected || 0);

      document.getElementById('statTotalSavings').textContent = formatTZS(totalSavings);
      document.getElementById('statCashOnHand').textContent = formatTZS(data.cashOnHand);
      document.getElementById('statTotalLoans').textContent = formatTZS(totalLoans);
      document.getElementById('statTotalIncome').textContent = formatTZS(totalIncome);

      const navCount = document.getElementById('navMemberCount');
      if (navCount) navCount.textContent = data.members.length;

      const savingSelect = document.getElementById('savingMemberSelect');
      const feeSelect = document.getElementById('leaderFeeMemberSelect');
      const penaltySelect = document.getElementById('penaltyMemberSelect');
      const loanSelect = document.getElementById('loanMemberSelect');
      const repaySelect = document.getElementById('repayMemberSelect');
      const loanPenSelect = document.getElementById('loanPenaltyMemberSelect');

      if (savingSelect) savingSelect.innerHTML = '<option value="">-- Chagua Mwanachama --</option>';
      if (feeSelect) feeSelect.innerHTML = '<option value="">-- Chagua Mwanachama --</option>';
      if (penaltySelect) penaltySelect.innerHTML = '<option value="">-- Chagua Mwanachama --</option>';
      if (loanSelect) loanSelect.innerHTML = '<option value="">-- Chagua Mkopaji --</option>';
      if (repaySelect) repaySelect.innerHTML = '<option value="">-- Chagua Anayerejesha --</option>';
      if (loanPenSelect) loanPenSelect.innerHTML = '<option value="">-- Chagua Aliyechelewa --</option>';

      data.members.forEach(m => {
        if (savingSelect) savingSelect.innerHTML += `<option value="${m.id}">${escapeHtml(m.name)} (${escapeHtml(m.phone)})</option>`;
        if (feeSelect) feeSelect.innerHTML += `<option value="${m.id}">${escapeHtml(m.name)}</option>`;
        if (penaltySelect) penaltySelect.innerHTML += `<option value="${m.id}">${escapeHtml(m.name)} (Faini: ${formatTZS(m.penalties)})</option>`;
        if (loanSelect) loanSelect.innerHTML += `<option value="${m.id}">${escapeHtml(m.name)} (Akiba: ${formatTZS(m.savings)})</option>`;
        if (repaySelect && m.loanBalance > 0) repaySelect.innerHTML += `<option value="${m.id}">${escapeHtml(m.name)} (Deni: ${formatTZS(m.loanBalance)})</option>`;
        if (loanPenSelect && m.loanBalance > 0) loanPenSelect.innerHTML += `<option value="${m.id}">${escapeHtml(m.name)} (Deni: ${formatTZS(m.loanBalance)})</option>`;
      });

      renderLoanStatusBoard(data);
      renderSavingsHistory(data);
      renderLoansHistory(data);
      renderPrintableReport(data, totalSavings, totalLoans, totalIncome);
    }

    function renderLoanStatusBoard(data) {
      const tbody = document.getElementById('loanStatusBoardBody');
      if (!tbody) return;
      tbody.innerHTML = '';

      data.members.forEach(m => {
        const hadLoanBefore = data.loans.some(l => l.memberId === m.id);
        if (m.loanBalance <= 0 && !hadLoanBefore) return;

        tbody.innerHTML += `
          <tr>
            <td class="py-2 px-2 font-bold text-white">${escapeHtml(m.name)}</td>
            <td class="py-2 px-2 font-bold ${m.loanBalance > 0 ? 'text-rose-400' : 'text-emerald-400'}">${formatTZS(m.loanBalance)}</td>
            <td class="py-2 px-2">
              ${m.loanBalance === 0
                ? '<span class="px-2.5 py-1 rounded-lg bg-emerald-500/20 text-emerald-300 border border-emerald-500/40 font-bold text-[10px]">✅ AMEMALIZA DENI & RIBA (HANA DENI)</span>'
                : '<span class="px-2.5 py-1 rounded-lg bg-rose-500/20 text-rose-300 border border-rose-500/40 font-bold text-[10px]">⏳ BADO ANADAIWA MKOPO + RIBA</span>'}
            </td>
          </tr>
        `;
      });

      if (!tbody.innerHTML) {
        tbody.innerHTML = `<tr><td colspan="3" class="py-4 text-center text-slate-500">Hakuna mwanachama mwenye rekodi ya mkopo kwa sasa.</td></tr>`;
      }
    }

    function renderMembersTable() {
      const data = loadData();
      const memTbody = document.getElementById('membersTableBody');
      const countEl = document.getElementById('membersTotalCount');
      if (!memTbody) return;
      memTbody.innerHTML = '';
      if (countEl) countEl.textContent = data.members.length;

      const isAdmin = currentUser && currentUser.role === 'ADMIN';
      data.members.forEach(m => {
        const tr = document.createElement('tr');
        tr.className = 'hover:bg-slate-800/40 transition';
        let badge = `<span class="px-2 py-0.5 rounded text-[10px] bg-slate-800 text-slate-300">Mwanachama</span>`;
        if (m.role === 'CHAIRPERSON') badge = `<span class="px-2 py-0.5 rounded text-[10px] bg-amber-500/20 text-brandGold font-bold border border-brandGold/40">Mwenyekiti</span>`;
        else if (m.role === 'TREASURER') badge = `<span class="px-2 py-0.5 rounded text-[10px] bg-emerald-500/20 text-emerald-300 font-bold border border-emerald-500/40">Mhazini</span>`;
        else if (m.role === 'SECRETARY') badge = `<span class="px-2 py-0.5 rounded text-[10px] bg-blue-500/20 text-blue-300 font-bold border border-blue-500/40">Katibu</span>`;
        else if (m.role !== 'MEMBER') badge = `<span class="px-2 py-0.5 rounded text-[10px] bg-purple-500/20 text-purple-300 font-bold border border-purple-500/40">${escapeHtml(m.title)}</span>`;

        const actionsHtml = isAdmin
          ? `<div class="flex justify-center gap-1">
               <button onclick="openEditMemberModal('${m.id}')" class="text-amber-300 hover:text-white px-2 py-1 rounded bg-slate-800"><i class="fa-solid fa-pen"></i></button>
               ${m.role !== 'CHAIRPERSON' ? `<button onclick="handleDeleteMember('${m.id}')" class="text-rose-400 hover:text-white px-2 py-1 rounded bg-rose-950/60"><i class="fa-solid fa-trash"></i></button>` : ''}
             </div>`
          : '-';

        tr.innerHTML = `
          <td class="py-2.5 px-2 font-mono text-amber-400 font-bold">${escapeHtml(m.id)}</td>
          <td class="py-2.5 px-2 font-bold text-white">${escapeHtml(m.name)}</td>
          <td class="py-2.5 px-2 font-mono text-amber-300">${escapeHtml(m.phone)}</td>
          <td class="py-2.5 px-2">${badge}</td>
          <td class="py-2.5 px-2 font-bold text-brandGold">${formatTZS(m.savings)}</td>
          <td class="py-2.5 px-2 font-bold text-rose-400">${formatTZS(m.loanBalance)}</td>
          <td class="py-2.5 px-2 font-bold text-amber-500">${formatTZS(m.penalties)}</td>
          <td class="py-2.5 px-2 text-center font-mono text-slate-400">1234</td>
          <td class="py-2.5 px-2 text-center">${actionsHtml}</td>
        `;
        memTbody.appendChild(tr);
      });
    }

    function renderSavingsHistory(data) {
      const tbody = document.getElementById('savingsHistoryBody');
      if (!tbody) return;
      tbody.innerHTML = '';
      if (data.savings.length === 0) {
        tbody.innerHTML = `<tr><td colspan="4" class="py-4 text-center text-slate-500">Bado hakuna miamala ya akiba iliyorekodiwa.</td></tr>`;
        return;
      }
      [...data.savings].reverse().forEach(s => {
        tbody.innerHTML += `
          <tr>
            <td class="py-2 px-2 text-slate-300">${escapeHtml(s.monthKey || s.date)}</td>
            <td class="py-2 px-2 font-bold text-white">${escapeHtml(s.memberName)}</td>
            <td class="py-2 px-2 font-bold text-emerald-400">${formatTZS(s.amount)}</td>
            <td class="py-2 px-2 text-slate-400">${escapeHtml(s.recordedBy || 'Uongozi')}</td>
          </tr>
        `;
      });
    }

    function renderLoansHistory(data) {
      const tbody = document.getElementById('loansHistoryBody');
      if (!tbody) return;
      tbody.innerHTML = '';
      if (data.loans.length === 0) {
        tbody.innerHTML = `<tr><td colspan="5" class="py-4 text-center text-slate-500">Bado hakuna historia ya mikopo.</td></tr>`;
        return;
      }
      [...data.loans].reverse().forEach(l => {
        const badgeCls = l.type === 'REPAYMENT' ? 'bg-emerald-900 text-emerald-300' : l.type === 'PENALTY' ? 'bg-amber-900 text-amber-300' : 'bg-rose-900 text-rose-300';
        const label = l.type === 'REPAYMENT' ? 'Rejesho' : l.type === 'PENALTY' ? 'Faini' : 'Mkopo';
        tbody.innerHTML += `
          <tr>
            <td class="py-2 px-2 text-slate-300">${escapeHtml(l.date)}</td>
            <td class="py-2 px-2 font-bold text-white">${escapeHtml(l.memberName)}</td>
            <td class="py-2 px-2"><span class="px-2 py-0.5 rounded text-[10px] font-bold ${badgeCls}">${label}</span></td>
            <td class="py-2 px-2 font-bold text-white">${formatTZS(l.amount)}</td>
            <td class="py-2 px-2 text-amber-300">${escapeHtml(l.note || formatTZS(l.interest || 0))}</td>
          </tr>
        `;
      });
    }

    function renderPrintableReport(data, totalSavings, totalLoans, totalIncome) {
      const now = new Date();
      document.getElementById('reportYearLabel').textContent = `Mwaka wa ${getGroupYearNumber(now.getFullYear())} (${now.getFullYear()})`;
      document.getElementById('reportGeneratedDate').textContent = now.toLocaleDateString('sw-TZ', { dateStyle: 'long' });
      document.getElementById('repTotalSavings').textContent = formatTZS(totalSavings);
      document.getElementById('repCashOnHand').textContent = formatTZS(data.cashOnHand);
      document.getElementById('repTotalLoans').textContent = formatTZS(totalLoans);
      document.getElementById('repTotalIncome').textContent = formatTZS(totalIncome);

      const repBody = document.getElementById('reportTableBody');
      if (!repBody) return;
      repBody.innerHTML = '';
      data.members.forEach(m => {
        repBody.innerHTML += `
          <tr class="border-b border-slate-200">
            <td class="p-2 border border-slate-300 font-mono">${escapeHtml(m.id)}</td>
            <td class="p-2 border border-slate-300 font-bold">${escapeHtml(m.name)}</td>
            <td class="p-2 border border-slate-300">${escapeHtml(m.title)}</td>
            <td class="p-2 border border-slate-300 text-right">${formatTZS(m.savings)}</td>
            <td class="p-2 border border-slate-300 text-right">${formatTZS(m.loanBalance)}</td>
            <td class="p-2 border border-slate-300 text-right">${m.loanBalance > 0 ? 'Bado Anadaiwa' : 'Hana Deni'}</td>
            <td class="p-2 border border-slate-300 text-right">${formatTZS(m.penalties)}</td>
          </tr>
        `;
      });
    }

    // ==================== MEMBER CRUD ====================
    function handleRegisterMember(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const name = document.getElementById('newMemName').value.trim();
      const phone = document.getElementById('newMemPhone').value.trim();
      const role = document.getElementById('newMemRole').value;
      if (!name || !phone) return;
      const data = loadData();
      if (data.members.some(m => cleanPhone(m.phone) === cleanPhone(phone))) {
        showToast('Tahadhari', 'Namba hii ya simu tayari imesajiliwa!');
        return;
      }
      let title = "Mwanachama wa Kawaida";
      if (role === 'TREASURER') title = "Mhazini Mkuu";
      else if (role === 'SECRETARY') title = "Katibu Mkuu";
      else if (role === 'VICE_CHAIRPERSON') title = "Naibu Mwenyekiti";
      else if (role === 'COMMITTEE') title = "Mjumbe wa Kamati";

      const maxNum = data.members.reduce((max, m) => {
        const n = parseInt((m.id || '').replace('RL-', ''), 10);
        return !isNaN(n) && n > max ? n : max;
      }, 0);
      const memId = 'RL-' + String(maxNum + 1).padStart(3, '0');
      data.members.push({ id: memId, name, phone, role, title, savings: 0, loanBalance: 0, penalties: 0 });
      saveData(data);
      document.getElementById('addMemberForm').reset();
      showToast('Imefanikiwa', `Mwanachama ${name} (${memId}) amesajiliwa!`);
      refreshAllUI();
    }

    function openEditMemberModal(memberId) {
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const m = loadData().members.find(x => x.id === memberId);
      if (!m) return;
      document.getElementById('editMemId').value = m.id;
      document.getElementById('editMemName').value = m.name;
      document.getElementById('editMemPhone').value = m.phone;
      const modal = document.getElementById('editMemberModal');
      modal.classList.remove('hidden'); modal.classList.add('flex');
    }
    function closeEditMemberModal() {
      const modal = document.getElementById('editMemberModal');
      modal.classList.add('hidden'); modal.classList.remove('flex');
    }
    function saveEditedMember(e) {
      e.preventDefault();
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const id = document.getElementById('editMemId').value;
      const name = document.getElementById('editMemName').value.trim();
      const phone = document.getElementById('editMemPhone').value.trim();
      const data = loadData();
      const member = data.members.find(m => m.id === id);
      if (!member) return;
      member.name = name; member.phone = phone;
      saveData(data);
      closeEditMemberModal();
      showToast('Imesasishwa', `Taarifa za ${name} zimebadilishwa.`);
      refreshAllUI();
    }
    function handleDeleteMember(memberId) {
      if (!currentUser || currentUser.role !== 'ADMIN') return;
      const data = loadData();
      const member = data.members.find(m => m.id === memberId);
      if (!member) return;
      if (confirm(`Je, una uhakika unataka kumfuta kabisa ${member.name}?`)) {
        data.members = data.members.filter(m => m.id !== memberId);
        saveData(data);
        showToast('Ameondolewa', `${member.name} amefutwa.`);
        refreshAllUI();
      }
    }
    function filterMembersTable() {
      const query = document.getElementById('memberSearchInput').value.toLowerCase();
      document.querySelectorAll('#membersTableBody tr').forEach(row => {
        row.style.display = row.innerText.toLowerCase().includes(query) ? '' : 'none';
      });
    }

    // ==================== SYNC PERIODICALLY IF ONLINE ====================
    setInterval(() => {
      if (currentUser && navigator.onLine && getCloudDbUrl()) {
        pullFromCloud(true);
      }
    }, 15000);

    window.addEventListener('DOMContentLoaded', () => { bootApp(); });
  </script>
</body>
</html>
```

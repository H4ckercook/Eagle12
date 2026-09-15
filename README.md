<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1" />
<title>DudeChat</title>
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' rx='22' fill='%236C5CE7'/%3E%3Ctext x='50' y='68' font-size='58' font-family='Arial' font-weight='bold' fill='white' text-anchor='middle'%3ED%3C/text%3E%3C/svg%3E" />
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@500;600;700&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet" />

<style>
/* ============================================================
   DUDECHAT — DESIGN TOKENS
   ============================================================ */
:root{
  --bg-deepest:#0E1015;
  --bg-app:#12151B;
  --bg-panel:#171B23;
  --bg-panel-raised:#1E232D;
  --bg-hover:#252B37;
  --bg-input:#1B2028;
  --border:#272D39;
  --border-soft:#1F2530;

  --text-primary:#EDEFF3;
  --text-secondary:#9299AC;
  --text-tertiary:#5D6479;

  --brand:#6C5CE7;
  --brand-hover:#7D6EF0;
  --brand-soft:rgba(108,92,231,.16);

  --mint:#35D5A0;
  --mint-soft:rgba(53,213,160,.14);

  --danger:#FF5470;
  --danger-soft:rgba(255,84,112,.14);
  --amber:#FFB020;

  --radius-sm:8px;
  --radius-md:12px;
  --radius-lg:18px;
  --radius-pill:999px;

  --font-display:'Space Grotesk',sans-serif;
  --font-body:'Inter',sans-serif;

  --shadow-panel:0 12px 32px rgba(0,0,0,.35);
  --sidebar-w:272px;
}

*{ box-sizing:border-box; }
html,body{ height:100%; }
body{
  margin:0;
  font-family:var(--font-body);
  background:var(--bg-deepest);
  color:var(--text-primary);
  -webkit-font-smoothing:antialiased;
  overflow:hidden;
}
button{ font-family:inherit; }
textarea, input{ font-family:inherit; }
::selection{ background:var(--brand-soft); color:var(--text-primary); }

::-webkit-scrollbar{ width:8px; height:8px; }
::-webkit-scrollbar-track{ background:transparent; }
::-webkit-scrollbar-thumb{ background:var(--border); border-radius:8px; }
::-webkit-scrollbar-thumb:hover{ background:var(--text-tertiary); }

:focus-visible{ outline:2px solid var(--brand); outline-offset:2px; border-radius:4px; }

.hidden{ display:none !important; }

/* ============================================================
   AUTH SCREEN
   ============================================================ */
#authScreen{
  height:100%;
  display:flex;
  align-items:center;
  justify-content:center;
  padding:24px;
  background:
    radial-gradient(ellipse 900px 500px at 15% 0%, rgba(108,92,231,.22), transparent 60%),
    radial-gradient(ellipse 700px 500px at 100% 100%, rgba(53,213,160,.10), transparent 60%),
    var(--bg-deepest);
}
.auth-wrap{
  width:100%;
  max-width:880px;
  display:grid;
  grid-template-columns:1.1fr 1fr;
  background:var(--bg-panel);
  border:1px solid var(--border);
  border-radius:var(--radius-lg);
  overflow:hidden;
  box-shadow:var(--shadow-panel);
  min-height:560px;
}
.auth-hero{
  padding:48px 40px;
  display:flex;
  flex-direction:column;
  justify-content:center;
  background:
    radial-gradient(ellipse 400px 300px at 20% 20%, rgba(108,92,231,.35), transparent 60%),
    linear-gradient(165deg, var(--bg-panel-raised), var(--bg-panel));
  border-right:1px solid var(--border);
  position:relative;
}
.auth-hero .mark{
  width:52px; height:52px; border-radius:14px;
  background:linear-gradient(135deg, var(--brand), #8B7CF6);
  display:flex; align-items:center; justify-content:center;
  font-family:var(--font-display); font-weight:700; font-size:24px;
  color:#fff; margin-bottom:28px;
  box-shadow:0 8px 20px rgba(108,92,231,.4);
}
.auth-hero h1{
  font-family:var(--font-display);
  font-weight:700;
  font-size:40px;
  line-height:1.08;
  margin:0 0 14px;
  letter-spacing:-0.01em;
}
.auth-hero p{
  color:var(--text-secondary);
  font-size:15px;
  line-height:1.6;
  margin:0 0 28px;
  max-width:34ch;
}
.hero-tags{ display:flex; flex-direction:column; gap:12px; }
.hero-tag{
  display:flex; align-items:center; gap:10px;
  color:var(--text-secondary); font-size:14px;
}
.hero-tag .dot{ width:7px; height:7px; border-radius:50%; background:var(--mint); flex:none; }

.auth-forms{
  padding:48px 40px;
  display:flex;
  flex-direction:column;
  justify-content:center;
}
.auth-toggle{
  display:flex;
  background:var(--bg-input);
  border:1px solid var(--border);
  border-radius:var(--radius-pill);
  padding:4px;
  margin-bottom:28px;
}
.auth-toggle button{
  flex:1;
  border:none;
  background:transparent;
  color:var(--text-secondary);
  padding:10px 0;
  border-radius:var(--radius-pill);
  font-weight:600;
  font-size:14px;
  cursor:pointer;
  transition:background .18s ease, color .18s ease;
}
.auth-toggle button.active{
  background:var(--brand);
  color:#fff;
}
.auth-form{ display:flex; flex-direction:column; gap:16px; }
.field{ display:flex; flex-direction:column; gap:6px; }
.field label{ font-size:13px; color:var(--text-secondary); font-weight:500; }
.field input{
  background:var(--bg-input);
  border:1px solid var(--border);
  color:var(--text-primary);
  padding:12px 14px;
  border-radius:var(--radius-md);
  font-size:15px;
  transition:border-color .15s ease, background .15s ease;
}
.field input:focus{ border-color:var(--brand); background:var(--bg-panel-raised); outline:none; }
.field-hint{ font-size:12px; color:var(--text-tertiary); }

.btn{
  border:none;
  border-radius:var(--radius-md);
  padding:13px 18px;
  font-weight:600;
  font-size:15px;
  cursor:pointer;
  transition:transform .08s ease, background .15s ease, opacity .15s ease;
}
.btn:active{ transform:scale(.98); }
.btn-primary{ background:var(--brand); color:#fff; }
.btn-primary:hover{ background:var(--brand-hover); }
.btn-primary:disabled{ opacity:.55; cursor:not-allowed; }
.btn-ghost{ background:transparent; color:var(--text-secondary); border:1px solid var(--border); }
.btn-ghost:hover{ background:var(--bg-hover); color:var(--text-primary); }
.btn-danger{ background:var(--danger-soft); color:var(--danger); }
.btn-danger:hover{ background:var(--danger); color:#fff; }

.auth-error{
  background:var(--danger-soft);
  color:var(--danger);
  padding:11px 14px;
  border-radius:var(--radius-md);
  font-size:13.5px;
  line-height:1.4;
}
.auth-note{
  margin-top:18px;
  font-size:12.5px;
  color:var(--text-tertiary);
  line-height:1.5;
}

/* ============================================================
   APP SHELL
   ============================================================ */
#appScreen{
  height:100%;
  display:flex;
}
.sidebar{
  width:var(--sidebar-w);
  flex:none;
  background:var(--bg-panel);
  border-right:1px solid var(--border);
  display:flex;
  flex-direction:column;
  height:100%;
}
.server-header{
  display:flex;
  align-items:center;
  gap:12px;
  padding:18px 18px 16px;
  border-bottom:1px solid var(--border);
  flex:none;
}
.server-header .mark{
  width:38px; height:38px; border-radius:11px;
  background:linear-gradient(135deg, var(--brand), #8B7CF6);
  display:flex; align-items:center; justify-content:center;
  font-family:var(--font-display); font-weight:700; font-size:17px;
  color:#fff; flex:none;
}
.server-header .server-name{
  font-family:var(--font-display);
  font-weight:700;
  font-size:16px;
  line-height:1.2;
}
.server-header .server-sub{
  font-size:11.5px;
  color:var(--text-tertiary);
  margin-top:1px;
}

.channel-list{
  padding:16px 12px;
  overflow-y:auto;
  flex:1 1 auto;
  min-height:0;
}
.section-label{
  font-size:11.5px;
  color:var(--text-tertiary);
  font-weight:600;
  padding:0 8px 8px;
  letter-spacing:.02em;
}
.channel-btn{
  width:100%;
  display:flex;
  align-items:center;
  gap:8px;
  background:transparent;
  border:none;
  color:var(--text-secondary);
  padding:9px 10px;
  border-radius:var(--radius-sm);
  font-size:14.5px;
  text-align:left;
  cursor:pointer;
  margin-bottom:2px;
  transition:background .12s ease, color .12s ease;
}
.channel-btn .hash{ color:var(--text-tertiary); font-weight:600; }
.channel-btn:hover{ background:var(--bg-hover); color:var(--text-primary); }
.channel-btn.active{ background:var(--brand-soft); color:#fff; }
.channel-btn.active .hash{ color:var(--brand-hover); }
.channel-btn .lock{ margin-left:auto; font-size:12px; color:var(--text-tertiary); }

.voice-section{
  border-top:1px solid var(--border-soft);
  padding:14px 12px;
  flex:none;
}
.voice-header{
  display:flex; align-items:center; justify-content:space-between;
  padding:0 8px 10px;
}
.voice-header .section-label{ padding:0; }
.voice-join-btn{
  background:var(--mint-soft);
  color:var(--mint);
  border:none;
  border-radius:var(--radius-pill);
  padding:6px 13px;
  font-size:12.5px;
  font-weight:600;
  cursor:pointer;
}
.voice-join-btn:hover{ background:var(--mint); color:#08150F; }
.voice-join-btn.in-call{ background:var(--danger-soft); color:var(--danger); }
.voice-join-btn.in-call:hover{ background:var(--danger); color:#fff; }

.voice-participants{ display:flex; flex-direction:column; gap:6px; padding:0 6px; min-height:4px; }
.voice-empty{ font-size:12.5px; color:var(--text-tertiary); padding:2px 8px 4px; }
.voice-participant{
  display:flex; align-items:center; gap:9px;
  padding:6px 8px;
  border-radius:var(--radius-sm);
  font-size:13.5px;
  color:var(--text-secondary);
}
.voice-participant .vp-avatar{
  width:24px; height:24px; border-radius:50%;
  background:var(--bg-panel-raised);
  display:flex; align-items:center; justify-content:center;
  font-size:11px; font-weight:700; color:var(--text-primary);
  flex:none; position:relative;
  border:2px solid var(--mint);
}
.voice-participant.speaking-off .vp-avatar{ border-color:var(--border); }
.voice-participant .mic-icon{ margin-left:auto; font-size:12px; color:var(--text-tertiary); }
.voice-participant .mic-icon.muted{ color:var(--danger); }
.voice-controls{
  display:flex; gap:8px; padding:8px 6px 0;
}
.icon-btn{
  flex:1;
  background:var(--bg-input);
  border:1px solid var(--border);
  color:var(--text-secondary);
  padding:8px 0;
  border-radius:var(--radius-sm);
  font-size:12.5px;
  font-weight:600;
  cursor:pointer;
}
.icon-btn:hover{ background:var(--bg-hover); color:var(--text-primary); }
.icon-btn.active{ background:var(--danger-soft); color:var(--danger); border-color:transparent; }

.user-panel{
  border-top:1px solid var(--border);
  padding:12px 14px;
  display:flex;
  align-items:center;
  gap:10px;
  flex:none;
}
.user-panel .avatar{
  width:34px; height:34px; border-radius:50%;
  background:linear-gradient(135deg, var(--brand), #8B7CF6);
  display:flex; align-items:center; justify-content:center;
  font-weight:700; font-size:14px; color:#fff; flex:none;
}
.user-panel .who{ min-width:0; flex:1; }
.user-panel .uname{
  font-size:14px; font-weight:600; color:var(--text-primary);
  overflow:hidden; text-overflow:ellipsis; white-space:nowrap;
  display:flex; align-items:center; gap:6px;
}
.owner-badge{
  font-size:10px; font-weight:700; color:#3A2E00;
  background:var(--amber);
  padding:1.5px 6px; border-radius:5px;
  letter-spacing:.02em;
}
.user-panel .ustatus{ font-size:11.5px; color:var(--mint); }
.logout-btn{
  background:transparent; border:none; color:var(--text-tertiary);
  cursor:pointer; padding:6px; border-radius:var(--radius-sm); font-size:16px;
  flex:none;
}
.logout-btn:hover{ background:var(--bg-hover); color:var(--danger); }

/* ============================================================
   CHAT MAIN
   ============================================================ */
.chat-main{
  flex:1 1 auto;
  display:flex;
  flex-direction:column;
  min-width:0;
  height:100%;
  background:var(--bg-app);
}
.chat-header{
  display:flex; align-items:center; gap:10px;
  padding:16px 22px;
  border-bottom:1px solid var(--border);
  flex:none;
}
.chat-header .mobile-toggle{
  display:none;
  background:transparent; border:none; color:var(--text-secondary);
  font-size:20px; cursor:pointer; padding:2px 4px;
}
.chat-header .chan-title{
  font-family:var(--font-display);
  font-weight:600;
  font-size:16.5px;
}
.chat-header .chan-title .hash{ color:var(--text-tertiary); margin-right:2px; }
.chat-header .chan-sub{ color:var(--text-tertiary); font-size:12.5px; margin-left:6px; }

.messages{
  flex:1 1 auto;
  overflow-y:auto;
  padding:18px 22px 8px;
  display:flex;
  flex-direction:column;
  gap:2px;
}
.empty-state{
  margin:auto;
  text-align:center;
  color:var(--text-tertiary);
  max-width:320px;
  padding:40px 20px;
}
.empty-state .glyph{
  width:56px; height:56px; border-radius:16px;
  background:var(--bg-panel-raised);
  display:flex; align-items:center; justify-content:center;
  font-size:24px; margin:0 auto 16px;
}
.empty-state h3{ color:var(--text-secondary); font-size:15px; margin:0 0 6px; font-family:var(--font-display); }
.empty-state p{ font-size:13px; line-height:1.5; margin:0; }

.loading-row, .error-row{
  margin:auto;
  color:var(--text-tertiary);
  font-size:13.5px;
  padding:30px 0;
  text-align:center;
}
.error-row{ color:var(--danger); }

.msg{
  display:flex;
  gap:13px;
  padding:8px 10px;
  border-radius:var(--radius-md);
  position:relative;
}
.msg:hover{ background:var(--bg-panel); }
.msg .m-avatar{
  width:38px; height:38px; border-radius:50%;
  background:linear-gradient(135deg, var(--brand), #8B7CF6);
  display:flex; align-items:center; justify-content:center;
  font-weight:700; font-size:14.5px; color:#fff; flex:none; margin-top:1px;
}
.msg .m-body{ min-width:0; flex:1; }
.msg .m-head{ display:flex; align-items:baseline; gap:8px; margin-bottom:2px; flex-wrap:wrap; }
.msg .m-name{ font-weight:600; font-size:14.5px; color:var(--text-primary); }
.msg .m-time{ font-size:11.5px; color:var(--text-tertiary); }
.msg .m-edited{ font-size:11px; color:var(--text-tertiary); font-style:italic; }
.msg .m-text{
  font-size:14.5px; line-height:1.5; color:var(--text-secondary);
  white-space:pre-wrap; word-break:break-word;
}
.msg .m-actions{
  position:absolute; top:-14px; right:10px;
  display:none;
  background:var(--bg-panel-raised);
  border:1px solid var(--border);
  border-radius:var(--radius-sm);
  overflow:hidden;
}
.msg:hover .m-actions{ display:flex; }
.msg .m-actions button{
  background:transparent; border:none; color:var(--text-secondary);
  padding:6px 10px; font-size:12.5px; cursor:pointer;
}
.msg .m-actions button:hover{ background:var(--bg-hover); color:var(--text-primary); }
.msg .m-actions button.danger:hover{ color:var(--danger); }
.msg.editing .m-text{ display:none; }
.edit-box{ display:flex; flex-direction:column; gap:6px; }
.edit-box textarea{
  background:var(--bg-input); border:1px solid var(--brand);
  color:var(--text-primary); border-radius:var(--radius-sm);
  padding:8px 10px; font-size:14.5px; resize:vertical; min-height:40px;
}
.edit-actions{ display:flex; gap:8px; }
.edit-actions button{
  font-size:12px; padding:5px 10px; border-radius:6px; border:none; cursor:pointer;
}
.edit-save{ background:var(--brand); color:#fff; }
.edit-cancel{ background:var(--bg-hover); color:var(--text-secondary); }

.composer{
  flex:none;
  padding:14px 22px 20px;
}
.composer-inner{
  display:flex;
  align-items:flex-end;
  gap:10px;
  background:var(--bg-input);
  border:1px solid var(--border);
  border-radius:var(--radius-lg);
  padding:10px 10px 10px 16px;
  transition:border-color .15s ease;
}
.composer-inner:focus-within{ border-color:var(--brand); }
.composer textarea{
  flex:1;
  background:transparent;
  border:none;
  color:var(--text-primary);
  font-size:15px;
  resize:none;
  max-height:160px;
  line-height:1.5;
  padding:6px 0;
}
.composer textarea:focus{ outline:none; }
.composer textarea::placeholder{ color:var(--text-tertiary); }
.send-btn{
  background:var(--brand);
  color:#fff;
  border:none;
  width:38px; height:38px;
  border-radius:50%;
  flex:none;
  cursor:pointer;
  display:flex; align-items:center; justify-content:center;
  font-size:16px;
  transition:background .15s ease, opacity .15s ease;
}
.send-btn:hover{ background:var(--brand-hover); }
.send-btn:disabled{ opacity:.4; cursor:not-allowed; }
.composer-locked{
  display:flex; align-items:center; gap:8px;
  padding:13px 16px;
  background:var(--bg-panel);
  border:1px solid var(--border-soft);
  border-radius:var(--radius-lg);
  color:var(--text-tertiary);
  font-size:13.5px;
}

.toast-wrap{
  position:fixed; bottom:20px; right:20px;
  display:flex; flex-direction:column; gap:8px;
  z-index:200;
}
.toast{
  background:var(--bg-panel-raised);
  border:1px solid var(--border);
  color:var(--text-primary);
  padding:12px 16px;
  border-radius:var(--radius-md);
  font-size:13.5px;
  box-shadow:var(--shadow-panel);
  max-width:320px;
  animation:toastIn .2s ease;
}
.toast.err{ border-color:var(--danger); color:var(--danger); }
@keyframes toastIn{ from{ transform:translateY(8px); opacity:0; } to{ transform:translateY(0); opacity:1; } }

.sidebar-backdrop{
  display:none;
}

/* ============================================================
   RESPONSIVE
   ============================================================ */
@media (max-width: 860px){
  .auth-wrap{ grid-template-columns:1fr; min-height:auto; }
  .auth-hero{ border-right:none; border-bottom:1px solid var(--border); padding:36px 28px; }
  .auth-forms{ padding:32px 28px; }
}

@media (max-width: 760px){
  :root{ --sidebar-w:82vw; }
  .chat-header .mobile-toggle{ display:inline-flex; }
  .sidebar{
    position:fixed;
    top:0; left:0; bottom:0;
    z-index:120;
    transform:translateX(-100%);
    transition:transform .22s ease;
    box-shadow:0 0 0 rgba(0,0,0,0);
  }
  .sidebar.open{ transform:translateX(0); box-shadow:20px 0 40px rgba(0,0,0,.4); }
  .sidebar-backdrop.show{
    display:block;
    position:fixed; inset:0; background:rgba(0,0,0,.5); z-index:110;
  }
  .chat-header{ padding:14px 14px; }
  .messages{ padding:14px 14px 6px; }
  .composer{ padding:10px 12px 16px; }
  .msg .m-actions{ position:static; display:flex !important; margin-top:6px; background:transparent; border:none; padding-left:50px; }
  .msg .m-actions button{ padding:4px 8px; }
}
</style>
</head>
<body>

<!-- ================= AUTH SCREEN ================= -->
<div id="authScreen">
  <div class="auth-wrap">
    <div class="auth-hero">
      <div class="mark">D</div>
      <h1>Hang out on DudeChat.</h1>
      <p>One server, four channels, real voice chat. No clutter, no setup — just sign in and talk.</p>
      <div class="hero-tags">
        <div class="hero-tag"><span class="dot"></span>Live messages, synced instantly</div>
        <div class="hero-tag"><span class="dot"></span>Real multi-person voice chat</div>
        <div class="hero-tag"><span class="dot"></span>Just a username, no email required</div>
      </div>
    </div>
    <div class="auth-forms">
      <div class="auth-toggle">
        <button id="tabLogin" class="active" type="button">Log in</button>
        <button id="tabSignup" type="button">Sign up</button>
      </div>

      <div id="authErrorBox" class="auth-error hidden"></div>

      <form id="loginForm" class="auth-form">
        <div class="field">
          <label for="loginUsername">Username</label>
          <input id="loginUsername" type="text" autocomplete="username" required maxlength="20" />
        </div>
        <div class="field">
          <label for="loginPassword">Password</label>
          <input id="loginPassword" type="password" autocomplete="current-password" required />
        </div>
        <button type="submit" id="loginSubmit" class="btn btn-primary">Log in</button>
      </form>

      <form id="signupForm" class="auth-form hidden">
        <div class="field">
          <label for="signupUsername">Username</label>
          <input id="signupUsername" type="text" autocomplete="username" required minlength="3" maxlength="20" />
          <span class="field-hint">3–20 characters: letters, numbers, underscores.</span>
        </div>
        <div class="field">
          <label for="signupPassword">Password</label>
          <input id="signupPassword" type="password" autocomplete="new-password" required minlength="6" />
          <span class="field-hint">At least 6 characters.</span>
        </div>
        <div class="field">
          <label for="signupConfirm">Confirm password</label>
          <input id="signupConfirm" type="password" autocomplete="new-password" required minlength="6" />
        </div>
        <button type="submit" id="signupSubmit" class="btn btn-primary">Create account</button>
      </form>

      <p class="auth-note">The first account ever created on DudeChat automatically becomes the server owner. Your microphone is only ever used for live voice chat — nothing is recorded or saved.</p>
    </div>
  </div>
</div>

<!-- ================= APP SCREEN ================= -->
<div id="appScreen" class="hidden">
  <div class="sidebar-backdrop" id="sidebarBackdrop"></div>
  <aside class="sidebar" id="sidebar">
    <div class="server-header">
      <div class="mark">D</div>
      <div>
        <div class="server-name">DudeChat</div>
        <div class="server-sub">1 server &middot; 4 channels</div>
      </div>
    </div>

    <nav class="channel-list" id="channelList">
      <div class="section-label">Text channels</div>
      <!-- channel buttons injected here -->
    </nav>

    <div class="voice-section">
      <div class="voice-header">
        <div class="section-label">Voice chat</div>
        <button id="voiceJoinBtn" class="voice-join-btn" type="button">Join voice</button>
      </div>
      <div class="voice-participants" id="voiceParticipantsList">
        <div class="voice-empty" id="voiceEmptyMsg">No one's in voice right now.</div>
      </div>
      <div class="voice-controls hidden" id="voiceControls">
        <button id="muteBtn" class="icon-btn" type="button">Mute</button>
      </div>
    </div>

    <div class="user-panel">
      <div class="avatar" id="myAvatar">?</div>
      <div class="who">
        <div class="uname"><span id="myUsername">&nbsp;</span><span id="myOwnerBadge" class="owner-badge hidden">OWNER</span></div>
        <div class="ustatus">Online</div>
      </div>
      <button id="logoutBtn" class="logout-btn" title="Sign out" type="button">&#9211;</button>
    </div>
  </aside>

  <main class="chat-main">
    <header class="chat-header">
      <button class="mobile-toggle" id="mobileToggle" type="button">&#9776;</button>
      <div class="chan-title"><span class="hash">#</span><span id="chanTitleText">general</span></div>
      <div class="chan-sub" id="chanSubText"></div>
    </header>

    <div class="messages" id="messagesEl">
      <div class="loading-row">Loading messages&hellip;</div>
    </div>

    <div class="composer">
      <div class="composer-inner" id="composerInner">
        <textarea id="messageInput" rows="1" placeholder="Message #general" maxlength="4000"></textarea>
        <button id="sendBtn" class="send-btn" title="Send" type="button">&#10148;</button>
      </div>
      <div class="composer-locked hidden" id="composerLocked">Only the owner can post in #announcements.</div>
    </div>
  </main>
</div>

<div class="toast-wrap" id="toastWrap"></div>

<!-- hidden container for voice audio elements -->
<div id="audioSinks" style="position:absolute;width:0;height:0;overflow:hidden;"></div>

<script type="module">
/* ============================================================
   DUDECHAT — APP LOGIC
   Sections:
     1. Firebase setup
     2. Constants / state
     3. Utility helpers (DOM, toast, time)
     4. Auth (signup / login / logout / owner claim)
     5. Channel + message logic
     6. Voice chat (WebRTC + Firestore signaling)
     7. UI wiring (event listeners, screen switching)
   ============================================================ */

import { initializeApp } from "https://www.gstatic.com/firebasejs/10.14.1/firebase-app.js";
import {
  getAuth, createUserWithEmailAndPassword, signInWithEmailAndPassword,
  signOut, onAuthStateChanged, updateProfile
} from "https://www.gstatic.com/firebasejs/10.14.1/firebase-auth.js";
import {
  getFirestore, doc, setDoc, getDoc, addDoc, collection, query, orderBy,
  onSnapshot, serverTimestamp, runTransaction, deleteDoc, updateDoc, limit,
  getDocs, writeBatch
} from "https://www.gstatic.com/firebasejs/10.14.1/firebase-firestore.js";

/* ---------------- 1. FIREBASE SETUP ---------------- */
const firebaseConfig = {
  apiKey: "AIzaC1wA_94mDuDeChAt3ed2eSeCrEt",
  authDomain: "dudechat-3ed2e.firebaseapp.com",
  projectId: "dudechat-3ed2e",
  storageBucket: "dudechat-3ed2e.firebasestorage.app",
  messagingSenderId: "66639217194",
  appId: "1:66639217194:web:0cf476903e1a8fd38c6d4a"
};
const firebaseApp = initializeApp(firebaseConfig);
const auth = getAuth(firebaseApp);
const db = getFirestore(firebaseApp);

/* Synthetic-email domain used internally so Firebase Auth (which requires
   an email) can be driven purely by username + password. Firebase Auth's
   own atomic email-uniqueness check is what makes usernames unique —
   see the writeup that accompanies this file for why. */
const AUTH_EMAIL_DOMAIN = "dudechat.local-users";

const CHANNELS = [
  { id: "general", name: "general" },
  { id: "gaming", name: "gaming" },
  { id: "memes", name: "memes" },
  { id: "announcements", name: "announcements", ownerOnly: true }
];

/* ---------------- 2. STATE ---------------- */
const state = {
  user: null,          // firebase auth user
  username: null,
  isOwner: false,
  ownerUid: null,
  activeChannel: "general",
  unsubMessages: null,
  editingMsgId: null,
  // voice
  inVoice: false,
  muted: false,
  localStream: null,
  peers: new Map(),        // uid -> { pc, audioEl }
  unsubVoiceParticipants: null,
  unsubVoiceSignals: null,
  voiceCleaningUp: false
};

/* ---------------- 3. UTILITY HELPERS ---------------- */
const $ = (id) => document.getElementById(id);

function toast(msg, isErr) {
  const wrap = $("toastWrap");
  const el = document.createElement("div");
  el.className = "toast" + (isErr ? " err" : "");
  el.textContent = msg;
  wrap.appendChild(el);
  setTimeout(() => el.remove(), 4500);
}

function initials(name) {
  return (name || "?").trim().slice(0, 1).toUpperCase();
}

function formatTime(ts) {
  if (!ts) return "sending…";
  const d = ts.toDate ? ts.toDate() : new Date(ts);
  const now = new Date();
  const sameDay = d.toDateString() === now.toDateString();
  const time = d.toLocaleTimeString([], { hour: "numeric", minute: "2-digit" });
  if (sameDay) return time;
  return d.toLocaleDateString([], { month: "short", day: "numeric" }) + " " + time;
}

function usernameToEmail(usernameLower) {
  return `${usernameLower}@${AUTH_EMAIL_DOMAIN}.com`;
}

function validUsername(name) {
  return /^[a-zA-Z0-9_]{3,20}$/.test(name);
}

function clearNode(node) {
  while (node.firstChild) node.removeChild(node.firstChild);
}

/* ---------------- 4. AUTH ---------------- */
function showAuthError(msg) {
  const box = $("authErrorBox");
  box.textContent = msg;
  box.classList.remove("hidden");
}
function clearAuthError() {
  $("authErrorBox").classList.add("hidden");
  $("authErrorBox").textContent = "";
}

function friendlyAuthError(err) {
  const code = err && err.code;
  if (code === "auth/email-already-in-use") return "That username is already taken.";
  if (code === "auth/invalid-credential" || code === "auth/wrong-password" || code === "auth/user-not-found")
    return "Incorrect username or password.";
  if (code === "auth/weak-password") return "Password must be at least 6 characters.";
  if (code === "auth/network-request-failed") return "Network error. Check your connection and try again.";
  if (code === "auth/too-many-requests") return "Too many attempts. Please wait a moment and try again.";
  return "Something went wrong. Please try again.";
}

async function handleSignup(e) {
  e.preventDefault();
  clearAuthError();
  const username = $("signupUsername").value.trim();
  const password = $("signupPassword").value;
  const confirm = $("signupConfirm").value;

  if (!validUsername(username)) {
    showAuthError("Usernames must be 3–20 characters: letters, numbers, underscores only.");
    return;
  }
  if (password.length < 6) {
    showAuthError("Password must be at least 6 characters.");
    return;
  }
  if (password !== confirm) {
    showAuthError("Passwords do not match.");
    return;
  }

  const submitBtn = $("signupSubmit");
  submitBtn.disabled = true;
  submitBtn.textContent = "Creating account…";

  const usernameLower = username.toLowerCase();
  const email = usernameToEmail(usernameLower);

  try {
    // Firebase Auth enforces email uniqueness atomically server-side —
    // this is what makes username uniqueness race-safe (see writeup).
    const cred = await createUserWithEmailAndPassword(auth, email, password);
    const uid = cred.user.uid;

    await updateProfile(cred.user, { displayName: username });

    await setDoc(doc(db, "users", uid), {
      uid,
      username,
      usernameLower,
      createdAt: serverTimestamp()
    });

    await claimOwnerIfUnclaimed(uid, username);
    // onAuthStateChanged will pick up the session and load the app.
  } catch (err) {
    console.error(err);
    showAuthError(friendlyAuthError(err));
    submitBtn.disabled = false;
    submitBtn.textContent = "Create account";
  }
}

async function handleLogin(e) {
  e.preventDefault();
  clearAuthError();
  const username = $("loginUsername").value.trim();
  const password = $("loginPassword").value;
  if (!username || !password) {
    showAuthError("Enter your username and password.");
    return;
  }
  const submitBtn = $("loginSubmit");
  submitBtn.disabled = true;
  submitBtn.textContent = "Logging in…";

  const email = usernameToEmail(username.toLowerCase());
  try {
    await signInWithEmailAndPassword(auth, email, password);
  } catch (err) {
    console.error(err);
    showAuthError(friendlyAuthError(err));
    submitBtn.disabled = false;
    submitBtn.textContent = "Log in";
  }
}

/* Owner claim: uses a Firestore transaction so the check-then-write is
   atomic from Firestore's point of view (optimistic concurrency — if two
   clients race, the loser's transaction is retried, sees the doc now
   exists, and does nothing). Security rules independently enforce that
   config/owner can only ever be created, never updated or deleted, and
   only by the uid it names — so this can't be forged client-side either. */
async function claimOwnerIfUnclaimed(uid, username) {
  try {
    await runTransaction(db, async (tx) => {
      const ownerRef = doc(db, "config", "owner");
      const snap = await tx.get(ownerRef);
      if (!snap.exists()) {
        tx.set(ownerRef, { uid, username, createdAt: serverTimestamp() });
      }
    });
  } catch (err) {
    // Non-fatal: if this fails (e.g. offline), the account still works,
    // it just won't be owner. See writeup for the honest limitation here.
    console.warn("Owner claim skipped:", err);
  }
}

async function refreshOwnerStatus() {
  try {
    const snap = await getDoc(doc(db, "config", "owner"));
    if (snap.exists()) {
      state.ownerUid = snap.data().uid;
      state.isOwner = state.ownerUid === state.user.uid;
    } else {
      state.ownerUid = null;
      state.isOwner = false;
    }
  } catch (err) {
    console.error("Could not load owner status", err);
    state.ownerUid = null;
    state.isOwner = false;
  }
  renderOwnerUI();
}

function renderOwnerUI() {
  $("myOwnerBadge").classList.toggle("hidden", !state.isOwner);
  renderChannelList();
  updateComposerLockState();
}

async function handleLogout() {
  try {
    if (state.inVoice) await leaveVoice();
  } catch (err) { console.warn(err); }
  try {
    await signOut(auth);
  } catch (err) {
    console.error(err);
    toast("Could not sign out cleanly.", true);
  }
}

onAuthStateChanged(auth, async (user) => {
  if (user) {
    state.user = user;
    state.username = user.displayName || "user";
    $("myUsername").textContent = state.username;
    $("myAvatar").textContent = initials(state.username);

    await refreshOwnerStatus();
    showApp();
    switchChannel("general");
  } else {
    state.user = null;
    state.username = null;
    state.isOwner = false;
    if (state.unsubMessages) { state.unsubMessages(); state.unsubMessages = null; }
    showAuthScreen();
  }
});

/* ---------------- 5. CHANNELS + MESSAGES ---------------- */
function renderChannelList() {
  const list = $("channelList");
  clearNode(list);
  const label = document.createElement("div");
  label.className = "section-label";
  label.textContent = "Text channels";
  list.appendChild(label);

  CHANNELS.forEach((ch) => {
    const btn = document.createElement("button");
    btn.type = "button";
    btn.className = "channel-btn" + (ch.id === state.activeChannel ? " active" : "");
    btn.dataset.channel = ch.id;

    const hash = document.createElement("span");
    hash.className = "hash";
    hash.textContent = "#";
    btn.appendChild(hash);

    const nameSpan = document.createElement("span");
    nameSpan.textContent = ch.name;
    btn.appendChild(nameSpan);

    if (ch.ownerOnly && !state.isOwner) {
      const lock = document.createElement("span");
      lock.className = "lock";
      lock.textContent = "🔒";
      lock.title = "Only the owner can post here";
      btn.appendChild(lock);
    }

    btn.addEventListener("click", () => switchChannel(ch.id));
    list.appendChild(btn);
  });
}

function updateComposerLockState() {
  const ch = CHANNELS.find((c) => c.id === state.activeChannel);
  const locked = !!(ch && ch.ownerOnly && !state.isOwner);
  $("composerInner").classList.toggle("hidden", locked);
  $("composerLocked").classList.toggle("hidden", !locked);
  $("messageInput").placeholder = `Message #${state.activeChannel}`;
}

function switchChannel(channelId) {
  state.activeChannel = channelId;
  const ch = CHANNELS.find((c) => c.id === channelId);
  $("chanTitleText").textContent = ch ? ch.name : channelId;
  $("chanSubText").textContent = ch && ch.ownerOnly ? "Owner-only announcements" : "";
  renderChannelList();
  updateComposerLockState();
  closeMobileSidebar();
  listenMessages(channelId);
}

function messageEl(id, data) {
  const wrap = document.createElement("div");
  wrap.className = "msg";
  wrap.dataset.id = id;

  const avatar = document.createElement("div");
  avatar.className = "m-avatar";
  avatar.textContent = initials(data.username);
  wrap.appendChild(avatar);

  const body = document.createElement("div");
  body.className = "m-body";

  const head = document.createElement("div");
  head.className = "m-head";

  const name = document.createElement("span");
  name.className = "m-name";
  name.textContent = data.username || "unknown";
  head.appendChild(name);

  if (data.uid === state.ownerUid) {
    const badge = document.createElement("span");
    badge.className = "owner-badge";
    badge.textContent = "OWNER";
    head.appendChild(badge);
  }

  const time = document.createElement("span");
  time.className = "m-time";
  time.textContent = formatTime(data.createdAt);
  head.appendChild(time);

  if (data.editedAt) {
    const edited = document.createElement("span");
    edited.className = "m-edited";
    edited.textContent = "(edited)";
    head.appendChild(edited);
  }

  body.appendChild(head);

  const textEl = document.createElement("div");
  textEl.className = "m-text";
  textEl.textContent = data.text || "";
  body.appendChild(textEl);

  wrap.appendChild(body);

  const canEdit = data.uid === state.user.uid;
  const canDelete = data.uid === state.user.uid || state.isOwner;

  if (canEdit || canDelete) {
    const actions = document.createElement("div");
    actions.className = "m-actions";
    if (canEdit) {
      const editBtn = document.createElement("button");
      editBtn.type = "button";
      editBtn.textContent = "Edit";
      editBtn.addEventListener("click", () => startEditMessage(wrap, id, data.text));
      actions.appendChild(editBtn);
    }
    if (canDelete) {
      const delBtn = document.createElement("button");
      delBtn.type = "button";
      delBtn.className = "danger";
      delBtn.textContent = "Delete";
      delBtn.addEventListener("click", () => handleDeleteMessage(id));
      actions.appendChild(delBtn);
    }
    wrap.appendChild(actions);
  }

  return wrap;
}

function startEditMessage(wrap, id, currentText) {
  if (wrap.querySelector(".edit-box")) return;
  wrap.classList.add("editing");
  const body = wrap.querySelector(".m-body");
  const box = document.createElement("div");
  box.className = "edit-box";

  const ta = document.createElement("textarea");
  ta.value = currentText;
  box.appendChild(ta);

  const actionsRow = document.createElement("div");
  actionsRow.className = "edit-actions";
  const save = document.createElement("button");
  save.className = "edit-save";
  save.type = "button";
  save.textContent = "Save";
  const cancel = document.createElement("button");
  cancel.className = "edit-cancel";
  cancel.type = "button";
  cancel.textContent = "Cancel";
  actionsRow.appendChild(save);
  actionsRow.appendChild(cancel);
  box.appendChild(actionsRow);
  body.appendChild(box);
  ta.focus();

  cancel.addEventListener("click", () => {
    wrap.classList.remove("editing");
    box.remove();
  });
  save.addEventListener("click", () => commitEdit(id, ta.value, wrap, box));
  ta.addEventListener("keydown", (e) => {
    if (e.key === "Enter" && !e.shiftKey) {
      e.preventDefault();
      commitEdit(id, ta.value, wrap, box);
    } else if (e.key === "Escape") {
      wrap.classList.remove("editing");
      box.remove();
    }
  });
}

async function commitEdit(id, newText, wrap, box) {
  const trimmed = newText.trim();
  if (!trimmed) { toast("Message can't be empty.", true); return; }
  try {
    await updateDoc(doc(db, "messages", state.activeChannel, "msgs", id), {
      text: trimmed,
      editedAt: serverTimestamp()
    });
    wrap.classList.remove("editing");
    box.remove();
  } catch (err) {
    console.error(err);
    toast("Couldn't save your edit.", true);
  }
}

async function handleDeleteMessage(id) {
  try {
    await deleteDoc(doc(db, "messages", state.activeChannel, "msgs", id));
  } catch (err) {
    console.error(err);
    toast("Couldn't delete that message.", true);
  }
}

function listenMessages(channelId) {
  if (state.unsubMessages) { state.unsubMessages(); state.unsubMessages = null; }
  const container = $("messagesEl");
  clearNode(container);
  const loading = document.createElement("div");
  loading.className = "loading-row";
  loading.textContent = "Loading messages…";
  container.appendChild(loading);

  const q = query(collection(db, "messages", channelId, "msgs"), orderBy("createdAt", "asc"), limit(300));

  state.unsubMessages = onSnapshot(
    q,
    (snap) => {
      if (state.activeChannel !== channelId) return;
      clearNode(container);
      if (snap.empty) {
        const empty = document.createElement("div");
        empty.className = "empty-state";
        empty.innerHTML = "";
        const glyph = document.createElement("div");
        glyph.className = "glyph";
        glyph.textContent = "#";
        const h3 = document.createElement("h3");
        h3.textContent = `Welcome to #${channelId}`;
        const p = document.createElement("p");
        p.textContent = "No messages yet. Say something to get things started.";
        empty.appendChild(glyph); empty.appendChild(h3); empty.appendChild(p);
        container.appendChild(empty);
        return;
      }
      const shouldScroll = isScrolledNearBottom(container);
      snap.forEach((docSnap) => {
        container.appendChild(messageEl(docSnap.id, docSnap.data()));
      });
      if (shouldScroll) container.scrollTop = container.scrollHeight;
    },
    (err) => {
      console.error(err);
      clearNode(container);
      const errRow = document.createElement("div");
      errRow.className = "error-row";
      errRow.textContent = "Couldn't load messages. Check your connection.";
      container.appendChild(errRow);
    }
  );
}

function isScrolledNearBottom(el) {
  return el.scrollHeight - el.scrollTop - el.clientHeight < 120;
}

async function sendMessage() {
  const input = $("messageInput");
  const text = input.value.trim();
  if (!text) return;
  const ch = CHANNELS.find((c) => c.id === state.activeChannel);
  if (ch && ch.ownerOnly && !state.isOwner) return;

  input.value = "";
  autoSizeTextarea(input);
  $("sendBtn").disabled = true;
  try {
    await addDoc(collection(db, "messages", state.activeChannel, "msgs"), {
      text,
      uid: state.user.uid,
      username: state.username,
      createdAt: serverTimestamp(),
      editedAt: null
    });
  } catch (err) {
    console.error(err);
    toast("Message failed to send.", true);
    input.value = text;
  } finally {
    $("sendBtn").disabled = false;
  }
}

function autoSizeTextarea(ta) {
  ta.style.height = "auto";
  ta.style.height = Math.min(ta.scrollHeight, 160) + "px";
}

/* ---------------- 6. VOICE CHAT (WebRTC + Firestore signaling) ---------------- */
const ICE_SERVERS = [
  { urls: "stun:stun.l.google.com:19302" },
  { urls: "stun:stun1.l.google.com:19302" }
];

function myUid() { return state.user.uid; }

async function joinVoice() {
  if (state.inVoice) return;
  try {
    state.localStream = await navigator.mediaDevices.getUserMedia({ audio: true });
  } catch (err) {
    console.error(err);
    toast("Couldn't access your microphone.", true);
    return;
  }
  state.inVoice = true;
  state.muted = false;
  $("voiceJoinBtn").textContent = "Leave voice";
  $("voiceJoinBtn").classList.add("in-call");
  $("voiceControls").classList.remove("hidden");
  $("muteBtn").textContent = "Mute";
  $("muteBtn").classList.remove("active");

  try {
    await setDoc(doc(db, "voiceParticipants", myUid()), {
      uid: myUid(),
      username: state.username,
      muted: false,
      joinedAt: serverTimestamp()
    });
  } catch (err) {
    console.error(err);
    toast("Couldn't join voice chat.", true);
    await leaveVoice();
    return;
  }

  listenVoiceSignals();
  listenVoiceParticipants();
}

function listenVoiceParticipants() {
  if (state.unsubVoiceParticipants) state.unsubVoiceParticipants();
  state.unsubVoiceParticipants = onSnapshot(collection(db, "voiceParticipants"), (snap) => {
    snap.docChanges().forEach((change) => {
      const uid = change.doc.id;
      const data = change.doc.data();
      if (change.type === "removed") {
        removeVoiceParticipantUI(uid);
        cleanupPeer(uid);
        return;
      }
      if (uid === myUid()) {
        renderVoiceParticipantUI(uid, data);
        return;
      }
      renderVoiceParticipantUI(uid, data);
      if (change.type === "added" && !state.peers.has(uid)) {
        // Deterministic initiator: higher uid always makes the offer,
        // so exactly one side of every pair starts the connection.
        if (myUid() > uid) initiateOfferTo(uid);
      }
    });
    renderVoiceEmptyState();
  }, (err) => console.error("voice participants listener error", err));
}

function renderVoiceEmptyState() {
  const list = $("voiceParticipantsList");
  const hasAny = list.querySelector(".voice-participant");
  $("voiceEmptyMsg").classList.toggle("hidden", !!hasAny);
}

function renderVoiceParticipantUI(uid, data) {
  const list = $("voiceParticipantsList");
  let row = list.querySelector(`[data-uid="${cssEscape(uid)}"]`);
  if (!row) {
    row = document.createElement("div");
    row.className = "voice-participant";
    row.dataset.uid = uid;
    const av = document.createElement("div");
    av.className = "vp-avatar";
    row.appendChild(av);
    const nameSpan = document.createElement("span");
    row.appendChild(nameSpan);
    const mic = document.createElement("span");
    mic.className = "mic-icon";
    row.appendChild(mic);
    list.appendChild(row);
  }
  row.querySelector(".vp-avatar").textContent = initials(data.username);
  row.childNodes[1].textContent = data.username + (uid === myUid() ? " (you)" : "");
  const mic = row.querySelector(".mic-icon");
  mic.textContent = data.muted ? "🔇" : "🎙";
  mic.classList.toggle("muted", !!data.muted);
  renderVoiceEmptyState();
}

function removeVoiceParticipantUI(uid) {
  const row = $("voiceParticipantsList").querySelector(`[data-uid="${cssEscape(uid)}"]`);
  if (row) row.remove();
  renderVoiceEmptyState();
}

function cssEscape(s) {
  return String(s).replace(/[^a-zA-Z0-9_-]/g, "\\$&");
}

function createPeerConnection(peerUid) {
  const pc = new RTCPeerConnection({ iceServers: ICE_SERVERS });
  if (state.localStream) {
    state.localStream.getTracks().forEach((t) => pc.addTrack(t, state.localStream));
  }
  pc.ontrack = (e) => {
    let audioEl = document.getElementById("voice-audio-" + peerUid);
    if (!audioEl) {
      audioEl = document.createElement("audio");
      audioEl.id = "voice-audio-" + peerUid;
      audioEl.autoplay = true;
      $("audioSinks").appendChild(audioEl);
    }
    audioEl.srcObject = e.streams[0];
  };
  pc.onicecandidate = (e) => {
    if (e.candidate) {
      sendSignal(peerUid, { type: "ice", candidate: e.candidate.toJSON() });
    }
  };
  pc.onconnectionstatechange = () => {
    if (["failed", "disconnected", "closed"].includes(pc.connectionState)) {
      cleanupPeer(peerUid);
    }
  };
  state.peers.set(peerUid, { pc });
  return pc;
}

async function initiateOfferTo(peerUid) {
  try {
    const pc = createPeerConnection(peerUid);
    const offer = await pc.createOffer();
    await pc.setLocalDescription(offer);
    await sendSignal(peerUid, { type: "offer", sdp: { type: offer.type, sdp: offer.sdp } });
  } catch (err) {
    console.error("Failed to initiate call to", peerUid, err);
  }
}

async function sendSignal(targetUid, payload) {
  try {
    await addDoc(collection(db, "voiceSignals", targetUid, "messages"), {
      from: myUid(),
      ...payload,
      createdAt: serverTimestamp()
    });
  } catch (err) {
    console.error("Failed to send signal", err);
  }
}

function listenVoiceSignals() {
  if (state.unsubVoiceSignals) state.unsubVoiceSignals();
  const ref = collection(db, "voiceSignals", myUid(), "messages");
  state.unsubVoiceSignals = onSnapshot(ref, (snap) => {
    snap.docChanges().forEach((change) => {
      if (change.type !== "added") return;
      const data = change.doc.data();
      handleSignal(data).catch((err) => console.error("signal handling error", err));
      deleteDoc(change.doc.ref).catch(() => {});
    });
  }, (err) => console.error("voice signals listener error", err));
}

async function handleSignal(data) {
  const from = data.from;
  if (!from || from === myUid()) return;

  if (data.type === "offer") {
    let entry = state.peers.get(from);
    const pc = entry ? entry.pc : createPeerConnection(from);
    await pc.setRemoteDescription(new RTCSessionDescription(data.sdp));
    const answer = await pc.createAnswer();
    await pc.setLocalDescription(answer);
    await sendSignal(from, { type: "answer", sdp: { type: answer.type, sdp: answer.sdp } });
  } else if (data.type === "answer") {
    const entry = state.peers.get(from);
    if (entry) await entry.pc.setRemoteDescription(new RTCSessionDescription(data.sdp));
  } else if (data.type === "ice") {
    const entry = state.peers.get(from);
    if (entry) {
      try { await entry.pc.addIceCandidate(new RTCIceCandidate(data.candidate)); }
      catch (err) { console.warn("Failed to add ICE candidate", err); }
    }
  }
}

function cleanupPeer(uid) {
  const entry = state.peers.get(uid);
  if (entry) {
    try { entry.pc.close(); } catch (e) {}
    state.peers.delete(uid);
  }
  const audioEl = document.getElementById("voice-audio-" + uid);
  if (audioEl) { audioEl.srcObject = null; audioEl.remove(); }
}

async function toggleMute() {
  if (!state.inVoice) return;
  state.muted = !state.muted;
  if (state.localStream) {
    state.localStream.getAudioTracks().forEach((t) => { t.enabled = !state.muted; });
  }
  $("muteBtn").textContent = state.muted ? "Unmute" : "Mute";
  $("muteBtn").classList.toggle("active", state.muted);
  try {
    await updateDoc(doc(db, "voiceParticipants", myUid()), { muted: state.muted });
  } catch (err) { console.error(err); }
}

async function leaveVoice() {
  if (state.voiceCleaningUp) return;
  state.voiceCleaningUp = true;
  try {
    if (state.localStream) {
      state.localStream.getTracks().forEach((t) => t.stop());
      state.localStream = null;
    }
    for (const uid of Array.from(state.peers.keys())) cleanupPeer(uid);

    if (state.unsubVoiceParticipants) { state.unsubVoiceParticipants(); state.unsubVoiceParticipants = null; }
    if (state.unsubVoiceSignals) { state.unsubVoiceSignals(); state.unsubVoiceSignals = null; }

    if (state.user) {
      try { await deleteDoc(doc(db, "voiceParticipants", myUid())); } catch (e) { console.warn(e); }
      try {
        const leftover = await getDocs(collection(db, "voiceSignals", myUid(), "messages"));
        if (!leftover.empty) {
          const batch = writeBatch(db);
          leftover.forEach((d) => batch.delete(d.ref));
          await batch.commit();
        }
      } catch (e) { console.warn(e); }
    }

    clearNode($("voiceParticipantsList"));
    const emptyMsg = document.createElement("div");
    emptyMsg.className = "voice-empty";
    emptyMsg.id = "voiceEmptyMsg";
    emptyMsg.textContent = "No one's in voice right now.";
    $("voiceParticipantsList").appendChild(emptyMsg);

    state.inVoice = false;
    state.muted = false;
    $("voiceJoinBtn").textContent = "Join voice";
    $("voiceJoinBtn").classList.remove("in-call");
    $("voiceControls").classList.add("hidden");
  } finally {
    state.voiceCleaningUp = false;
  }
}

/* Best-effort cleanup on tab close. Firestore-only signaling has no true
   server-side "on disconnect" like Realtime Database does, so a hard
   crash/kill can leave a stale voice entry — see writeup limitations. */
window.addEventListener("beforeunload", () => {
  if (state.inVoice) {
    try { navigator.sendBeacon && null; } catch (e) {}
    leaveVoice();
  }
});

/* ---------------- 7. UI WIRING ---------------- */
function showApp() {
  $("authScreen").classList.add("hidden");
  $("appScreen").classList.remove("hidden");
}
function showAuthScreen() {
  $("appScreen").classList.add("hidden");
  $("authScreen").classList.remove("hidden");
  $("loginForm").reset();
  $("signupForm").reset();
  $("loginSubmit").disabled = false;
  $("loginSubmit").textContent = "Log in";
  $("signupSubmit").disabled = false;
  $("signupSubmit").textContent = "Create account";
}

function openMobileSidebar() {
  $("sidebar").classList.add("open");
  $("sidebarBackdrop").classList.add("show");
}
function closeMobileSidebar() {
  $("sidebar").classList.remove("open");
  $("sidebarBackdrop").classList.remove("show");
}

$("tabLogin").addEventListener("click", () => {
  $("tabLogin").classList.add("active");
  $("tabSignup").classList.remove("active");
  $("loginForm").classList.remove("hidden");
  $("signupForm").classList.add("hidden");
  clearAuthError();
});
$("tabSignup").addEventListener("click", () => {
  $("tabSignup").classList.add("active");
  $("tabLogin").classList.remove("active");
  $("signupForm").classList.remove("hidden");
  $("loginForm").classList.add("hidden");
  clearAuthError();
});

$("loginForm").addEventListener("submit", handleLogin);
$("signupForm").addEventListener("submit", handleSignup);
$("logoutBtn").addEventListener("click", handleLogout);

$("sendBtn").addEventListener("click", sendMessage);
$("messageInput").addEventListener("keydown", (e) => {
  if (e.key === "Enter" && !e.shiftKey) {
    e.preventDefault();
    sendMessage();
  }
});
$("messageInput").addEventListener("input", (e) => autoSizeTextarea(e.target));

$("voiceJoinBtn").addEventListener("click", () => {
  if (state.inVoice) leaveVoice(); else joinVoice();
});
$("muteBtn").addEventListener("click", toggleMute);

$("mobileToggle").addEventListener("click", openMobileSidebar);
$("sidebarBackdrop").addEventListener("click", closeMobileSidebar);

renderVoiceEmptyState();
</script>
</body>
</html>

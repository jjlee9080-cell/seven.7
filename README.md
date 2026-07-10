<!doctype html>

<html lang="ko">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
  <title>웰에이징 브레인팜 · 마을</title>
  <style>
    /* BRAIN FARM 디자인 시스템 (이미지 반영, req14) */
    :root {
      --ink: #2f3a2c; --muted: #7c8570; --line: #e6ddca; --paper: #faf6ea; --panel: #ffffff;
      /* 캐릭터 누끼(올리브 니트·자연 톤)에 맞춘 브랜드 그린 (요구사항6-4) */
      --teal: #5a8a3b; --brand-dark: #3f6a28; --brand-light: #97bf5c;
      --leaf: #7bbf5a; --coral: #e08a63; --sun: #e6b53f; --blue: #6a9ec0;
      --graphite: #40522f; --gold: #dcae2a;
      /* 파스텔 카테고리 타일 배경 */
      --t-green:#e3efd6; --t-yellow:#f6ecc8; --t-peach:#f7e0d4; --t-blue:#dbe8f0; --t-purple:#e6e0f0; --t-mint:#dcefe2;
      --shadow: 0 14px 34px rgba(60, 80, 51, .14); --radius: 14px; color-scheme: light;
    }
    * { box-sizing: border-box; }
    body {
      margin: 0; min-height: 100vh; color: var(--ink);
      background: radial-gradient(circle at 18% 12%, rgba(134,192,90,.10), transparent 40%),
        radial-gradient(circle at 82% 78%, rgba(233,185,73,.10), transparent 42%), #f2ecdb;
      font-family: "Pretendard","Segoe UI",Arial,sans-serif;
      overscroll-behavior: none;
    }
    button, input, select { font: inherit; }
    button { -webkit-tap-highlight-color: transparent; cursor: pointer; }

    .app-shell {
      width: min(100%, 460px); min-height: 100vh; margin: 0 auto;
      background: var(--paper); box-shadow: 0 0 0 1px rgba(24,33,47,.08);
      display: grid; grid-template-rows: auto 1fr auto; position: relative;
    }
    .topbar {
      position: sticky; top: 0; z-index: 5; display: grid;
      grid-template-columns: 44px 1fr 44px; align-items: center; gap: 10px;
      padding: 12px 14px 10px; border-bottom: 1px solid var(--line);
      background: rgba(251,252,248,.94); backdrop-filter: blur(12px);
    }
    .topbar h1, .topbar p { margin: 0; }
    .topbar h1 { font-size: 20px; line-height: 1.05; }
    .eyebrow { color: var(--teal); font-size: 11px; font-weight: 800; text-transform: uppercase; }
    .coin-chip {
      display: inline-flex; align-items: center; gap: 5px; margin-top: 3px;
      font-size: 13px; font-weight: 800; color: #7a5a10;
    }
    .screen { padding: 16px 16px 96px; }
    .screen.flush { padding: 0 0 96px; }

    .icon-button {
      width: 42px; height: 42px; display: inline-grid; place-items: center;
      border: 1px solid var(--line); border-radius: var(--radius);
      background: var(--panel); color: var(--ink);
    }
    .icon-button svg { width: 21px; height: 21px; fill: currentColor; }

    .tabbar {
      position: sticky; bottom: 0; z-index: 6; display: grid;
      grid-template-columns: repeat(7, 1fr); gap: 1px; padding: 7px 4px 9px;
      border-top: 1px solid var(--line); background: rgba(255,255,255,.97); backdrop-filter: blur(14px);
    }
    .tab {
      min-height: 54px; border: 0; border-radius: 12px; background: transparent;
      color: var(--muted); display: grid; place-items: center; align-content: center; gap: 3px;
    }
    .tab svg { width: 20px; height: 20px; fill: currentColor; }
    .tab span { font-size: 10px; font-weight: 800; }
    .tab.active { background: var(--graphite); color: #fff; }

    .hero { display: grid; grid-template-columns: 1fr 116px; gap: 12px; align-items: stretch; margin-bottom: 14px; }
    .hero-copy { min-width: 0; }
    .hero h2 { margin: 0 0 8px; font-size: 26px; line-height: 1.1; }
    .hero p { margin: 0; color: var(--muted); font-size: 14px; line-height: 1.5; }
    .avatar-scene {
      min-height: 148px; border: 1px solid var(--line); border-radius: var(--radius);
      background: linear-gradient(180deg,#dcebe8,#fffdf5 66%,#d8ead2); overflow: hidden; position: relative;
    }
    .avatar-scene svg { position: absolute; inset: 0; width: 100%; height: 100%; }

    .stats-row { display: grid; grid-template-columns: repeat(3,1fr); gap: 8px; margin-bottom: 14px; }
    .stat { min-height: 76px; padding: 10px; border: 1px solid var(--line); border-radius: var(--radius); background: var(--panel); }
    .stat strong { display: block; font-size: 22px; line-height: 1; }
    .stat span { display: block; margin-top: 7px; color: var(--muted); font-size: 12px; font-weight: 700; }

    .routine-list, .stack { display: grid; gap: 10px; }
    .section-title { display: flex; justify-content: space-between; align-items: center; gap: 12px; margin: 18px 0 10px; }
    .section-title h3 { margin: 0; font-size: 18px; }
    .section-title span { color: var(--muted); font-size: 12px; font-weight: 800; }

    .routine-card, .panel {
      border: 1px solid var(--line); border-radius: var(--radius); background: var(--panel);
      box-shadow: 0 1px 0 rgba(24,33,47,.04);
    }
    .routine-card {
      display: grid; grid-template-columns: 44px 1fr auto; gap: 10px; align-items: center;
      min-height: 74px; padding: 12px; text-align: left; width: 100%; color: inherit;
    }
    .routine-icon { width: 44px; height: 44px; border-radius: var(--radius); display: grid; place-items: center; color: #fff; }
    .routine-icon svg { width: 24px; height: 24px; fill: currentColor; }
    .routine-card h4, .routine-card p { margin: 0; }
    .routine-card h4 { font-size: 15px; }
    .routine-card p { margin-top: 3px; color: var(--muted); font-size: 13px; line-height: 1.35; }
    .status-pill { min-width: 56px; padding: 6px 8px; border-radius: var(--radius); text-align: center; font-size: 12px; font-weight: 900; background: #edf2f7; color: var(--graphite); }
    .status-pill.done { background: #e5f2e1; color: #2f6629; }

    .primary-button, .secondary-button, .danger-button, .choice-button {
      border: 1px solid transparent; border-radius: var(--radius); min-height: 48px; padding: 11px 14px; font-weight: 900;
    }
    .primary-button { color: #fff; background: var(--teal); box-shadow: var(--shadow); }
    .secondary-button { color: var(--ink); background: #fff; border-color: var(--line); }
    .danger-button { color: #fff; background: #a33b2e; }
    .primary-button:disabled, .secondary-button:disabled { opacity: .5; box-shadow: none; }
    .button-row { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-top: 12px; }
    .full-width { width: 100%; }

    .panel { padding: 14px; }
    .panel h2, .panel h3, .panel p { margin-top: 0; }
    .panel p { color: var(--muted); line-height: 1.5; }

    .progress-track { height: 12px; border-radius: 999px; background: #e7edf1; overflow: hidden; }
    .progress-fill { height: 100%; width: var(--progress,0%); border-radius: inherit; background: linear-gradient(90deg,var(--teal),var(--leaf)); transition: width .25s ease; }

    .big-number { display: flex; align-items: end; gap: 6px; margin: 6px 0; }
    .big-number strong { font-size: 40px; line-height: 1; }
    .big-number span { color: var(--muted); font-weight: 800; padding-bottom: 5px; }

    .team-table { width: 100%; border-collapse: collapse; }
    .team-table th, .team-table td { padding: 10px 8px; text-align: left; border-bottom: 1px solid var(--line); font-size: 14px; }
    .team-table th { color: var(--muted); font-size: 12px; }
    .team-table tr:last-child td { border-bottom: 0; }
    .team-table tr.me td { background: #eef4f5; font-weight: 800; }

    /* 두뇌 게임 */
    .game-stage { display: grid; gap: 12px; }
    .game-card {
      min-height: 240px; display: grid; align-content: center; justify-items: center; gap: 12px;
      padding: 18px; border: 1px solid var(--line); border-radius: var(--radius);
      background: linear-gradient(180deg, rgba(58,114,184,.1), transparent 38%), #fff;
    }
    .area-badge { padding: 6px 10px; border-radius: var(--radius); background: #eef4f5; color: var(--teal); font-size: 12px; font-weight: 900; }
    .prompt { margin: 0; text-align: center; font-size: 22px; font-weight: 900; line-height: 1.3; }
    .stimulus {
      display: grid; place-items: center; min-width: 128px; min-height: 88px; padding: 8px 16px;
      border: 2px solid var(--graphite); border-radius: var(--radius); background: #f7faf7;
      font-size: 32px; font-weight: 900; letter-spacing: 6px; text-align: center;
    }
    .choice-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; width: 100%; }
    .choice-button { background: #fff; border-color: var(--line); color: var(--ink); }
    .choice-button.correct { border-color: #5b8d3a; background: #e8f4e3; }
    .choice-button.wrong { border-color: #d7644f; background: #fff0ec; }
    .choice-button:disabled { cursor: default; }
    .game-meta { display: grid; grid-template-columns: 1fr auto; gap: 10px; align-items: center; color: var(--muted); font-size: 13px; font-weight: 800; }

    .area-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
    .area-tile { border: 1px solid var(--line); border-radius: var(--radius); background: #fff; padding: 12px; text-align: left; display: grid; gap: 6px; }
    .area-tile strong { font-size: 15px; }
    .area-tile small { color: var(--muted); font-size: 12px; }

    .seg { display: inline-grid; grid-auto-flow: column; gap: 4px; padding: 4px; background: #eef2f6; border-radius: 10px; }
    .seg button { border: 0; background: transparent; padding: 8px 12px; border-radius: 7px; font-weight: 800; font-size: 13px; color: var(--muted); }
    .seg button.on { background: #fff; color: var(--ink); box-shadow: 0 1px 4px rgba(0,0,0,.08); }

    /* 리포트 */
    .report-grid { display: grid; gap: 10px; }
    .bar-row { display: grid; grid-template-columns: 76px 1fr 42px; align-items: center; gap: 10px; }
    .bar-row span, .bar-row strong { font-size: 13px; }
    .bar { height: 12px; border-radius: 999px; background: #e7edf1; overflow: hidden; }
    .bar i { display: block; height: 100%; width: var(--score,0%); border-radius: inherit; background: var(--bar-color,var(--teal)); transition: width .3s ease; }

    /* 아바타 꾸미기 */
    .avatar-stage { display: grid; grid-template-columns: 1fr; gap: 12px; }
    .avatar-big { min-height: 240px; border: 1px solid var(--line); border-radius: var(--radius); background: linear-gradient(180deg,#e7f1ea,#fffdf5 70%,#dfeed6); position: relative; overflow: hidden; }
    .avatar-big svg { position: absolute; inset: 0; width: 100%; height: 100%; }
    .swatches { display: flex; flex-wrap: wrap; gap: 8px; }
    .swatch { width: 34px; height: 34px; border-radius: 50%; border: 2px solid #fff; box-shadow: 0 0 0 1px var(--line); }
    .swatch.on { box-shadow: 0 0 0 2px var(--teal); transform: scale(1.08); }
    .opt-row { display: flex; gap: 8px; flex-wrap: wrap; }
    .chip { padding: 8px 12px; border: 1px solid var(--line); border-radius: 999px; background: #fff; font-weight: 800; font-size: 13px; }
    .chip.on { border-color: var(--teal); background: #e8f4f3; color: var(--teal); }

    .pet-grid { display: grid; grid-template-columns: repeat(2,1fr); gap: 8px; }
    .pet-card { border: 1px solid var(--line); border-radius: var(--radius); background: #fff; padding: 12px; text-align: center; display: grid; gap: 6px; justify-items: center; }
    .pet-emoji { font-size: 44px; line-height: 1; }
    .pet-card.active-pet { border-color: var(--leaf); background: #f1f8ec; }
    .aff-track { width: 100%; height: 8px; border-radius: 999px; background: #eee; overflow: hidden; }
    .aff-track i { display: block; height: 100%; width: var(--aff,0%); background: var(--coral); }

    /* 랭킹 */
    .podium { display: grid; grid-template-columns: 1fr 1fr 1fr; align-items: end; gap: 8px; margin: 6px 0 14px; }
    .pod { border-radius: var(--radius); padding: 10px 6px; text-align: center; color: #fff; }
    .pod .pn { font-size: 12px; font-weight: 800; }
    .pod .ps { font-size: 15px; font-weight: 900; margin-top: 2px; }
    .pod .medal { font-size: 22px; }
    .pod.p1 { background: linear-gradient(180deg,#e6b800,#c99700); min-height: 110px; }
    .pod.p2 { background: linear-gradient(180deg,#9aa6b2,#7d8996); min-height: 92px; }
    .pod.p3 { background: linear-gradient(180deg,#c98a52,#a86e3c); min-height: 78px; }
    .rank-row { display: grid; grid-template-columns: 34px 1fr auto; gap: 10px; align-items: center; padding: 11px 8px; border-bottom: 1px solid var(--line); }
    .rank-row:last-child { border-bottom: 0; }
    .rank-row.me { background: #eef4f5; border-radius: var(--radius); font-weight: 800; }
    .rank-no { font-weight: 900; color: var(--muted); text-align: center; }

    /* 함께하기 */
    .friend-strip { display: flex; gap: 8px; overflow-x: auto; padding-bottom: 4px; }
    .friend-ava { flex: 0 0 auto; width: 54px; text-align: center; }
    .friend-ava .fa-face { width: 48px; height: 48px; border-radius: 50%; display: grid; place-items: center; font-size: 24px; color: #fff; margin: 0 auto; }
    .friend-ava small { font-size: 11px; color: var(--muted); }

    /* 3D 마을 */
    .village-wrap { position: relative; width: 100%; height: calc(100vh - 170px); min-height: 380px; background: #bfe3d0; overflow: hidden; }
    #villageCanvas { position: absolute; inset: 0; }
    #villageCanvas canvas { display: block; width: 100% !important; height: 100% !important; }
    .vil-hud { position: absolute; top: 10px; left: 10px; right: 10px; display: flex; justify-content: space-between; gap: 8px; pointer-events: none; }
    .vil-tag { background: rgba(24,33,47,.72); color: #fff; font-size: 12px; font-weight: 800; padding: 7px 11px; border-radius: 999px; }
    .vil-prompt {
      position: absolute; top: 50%; left: 50%; transform: translate(-50%,-140px);
      background: var(--sun); color: #3a2a04; font-weight: 900; padding: 9px 15px; border-radius: 999px;
      box-shadow: 0 6px 18px rgba(0,0,0,.25); font-size: 14px; animation: bob 1s ease-in-out infinite;
    }
    @keyframes bob { 0%,100% { transform: translate(-50%,-140px);} 50% { transform: translate(-50%,-150px);} }
    .dpad { display: none !important; } /* 방향키 제거 (req7): PC는 키보드, 모바일은 터치 이동 */
    /* 확인(A) → 음성 마이크 버튼, 5pt 정도 작게 (req6) */
    .act-btn {
      position: absolute; right: 18px; bottom: 26px; width: 69px; height: 69px; border-radius: 50%;
      border: 0; background: var(--teal); color: #fff; font-size: 11px; font-weight: 900;
      box-shadow: 0 6px 18px rgba(74,143,76,.5); display: grid; place-items: center; gap:2px; line-height: 1.1;
    }
    .act-btn svg { width: 24px; height: 24px; fill: currentColor; }
    .act-btn:active { transform: scale(.94); }
    .act-btn.listening { background: var(--coral); animation: micPulse 1s infinite; }
    .move-hint { position: absolute; left: 50%; bottom: 16px; transform: translateX(-50%); z-index: 7; background: rgba(24,33,47,.6); color:#fff; font-size: 11px; font-weight: 700; padding: 6px 12px; border-radius: 999px; pointer-events: none; }
    .vil-fallback { padding: 40px 20px; text-align: center; color: var(--graphite); }

    /* 스마트팜 모달 */
    .modal { width: min(94vw, 400px); border: 0; border-radius: 14px; padding: 0; box-shadow: var(--shadow); }
    .modal::backdrop { background: rgba(24,33,47,.5); }
    .modal-content { padding: 14px; background: #fff; }
    .modal-head { display: flex; align-items: center; justify-content: space-between; gap: 12px; margin-bottom: 12px; }
    .modal-head h2 { margin: 0; font-size: 19px; }
    .live-badge { display: inline-flex; align-items: center; gap: 5px; background: #ffe9e6; color: #b23; font-size: 11px; font-weight: 900; padding: 3px 8px; border-radius: 999px; }
    .live-dot { width: 7px; height: 7px; border-radius: 50%; background: #e0453e; animation: blink 1s infinite; }
    @keyframes blink { 50% { opacity: .25; } }
    /* 작물 키우기 화면 9:16 비율 (req12) */
    #farmFeed { width: 100%; max-width: min(62vh, 300px); aspect-ratio: 9 / 16; height: auto; margin: 0 auto; border-radius: 10px; display: block; background: #ffffff; border: 1px solid var(--line); }
    .modal { width: min(94vw, 420px); }
    /* 온도·습도·토양수분 3개를 한 줄에 표시 (req13) */
    .sensor-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 6px; margin-top: 12px; }
    .sensor { border: 1px solid var(--line); border-radius: 10px; padding: 8px 6px; text-align: center; }
    .sensor small { color: var(--muted); font-size: 10.5px; font-weight: 700; white-space: nowrap; }
    .sensor strong { display: block; font-size: 16px; margin-top: 3px; }

    /* 취침 오버레이 */
    .sleep-overlay {
      position: fixed; inset: 0; z-index: 300; display: none; place-items: center;
      background: radial-gradient(120% 100% at 50% 0%, #1b2a4a, #0a1122);
      color: #eef; text-align: center; padding: 30px;
    }
    .sleep-overlay.show { display: grid; }
    .sleep-overlay .moon { font-size: 76px; }
    .sleep-overlay h2 { margin: 12px 0 6px; font-size: 24px; }
    .sleep-overlay p { color: #b9c4e0; max-width: 300px; line-height: 1.6; }
    .stars { position: absolute; inset: 0; overflow: hidden; }
    .stars i { position: absolute; width: 3px; height: 3px; background: #fff; border-radius: 50%; opacity: .8; animation: tw 2.5s infinite; }
    @keyframes tw { 50% { opacity: .2; } }

    .badge-pill { display: inline-block; padding: 4px 8px; border-radius: 999px; background: #eef4f5; color: var(--teal); font-size: 11px; font-weight: 900; }
    .tiny { color: var(--muted); font-size: 12px; line-height: 1.45; }
    .empty { padding: 18px; border: 1px dashed var(--line); border-radius: var(--radius); color: var(--muted); text-align: center; }
    .hidden { display: none !important; }

    .toast {
      position: fixed; left: 50%; bottom: 100px; transform: translateX(-50%) translateY(16px);
      background: rgba(24,33,47,.95); color: #fff; padding: 12px 18px; border-radius: 999px;
      font-size: 13px; font-weight: 800; z-index: 400; opacity: 0; transition: .25s; pointer-events: none; white-space: nowrap;
    }
    .toast.show { opacity: 1; transform: translateX(-50%) translateY(0); }

    .banner-reward {
      margin: 0 0 14px; padding: 14px; border-radius: var(--radius);
      background: linear-gradient(120deg,#2b3d6b,#3f5aa6); color: #fff;
    }
    .banner-reward strong { font-size: 16px; }

    /* ── 스플래시(로딩) ── */
    .splash {
      position: fixed; inset: 0; z-index: 1000; display: grid; place-items: center;
      /* req26: 다크 네이비 → 브레인 팜과 어울리는 제주 하늘·초원(팜) 배경 */
      background:
        radial-gradient(60% 40% at 78% 20%, rgba(255,240,190,.85), transparent 60%),
        radial-gradient(120% 95% at 50% 16%, #cdeeff 0%, #eaf7dd 46%, #a7d178 100%);
      transition: opacity .6s ease; overflow: hidden;
    }
    .splash.hide { opacity: 0; pointer-events: none; }
    .splash-inner { text-align: center; color: #2f5a20; position: relative; z-index: 2; }
    .splash-logo {
      width: 210px; height: 165px; margin: 0 auto;
      /* 브레인 팜 로고 — 카카오톡 이미지의 뇌 로고 부분만 추출(흰 라인 투명 PNG) */
      background: url("logo-brain.png") center/contain no-repeat;
      filter: blur(22px) drop-shadow(0 6px 24px rgba(90,140,60,.35));
      opacity: 0; transform: scale(.45);
      animation: logoIn 2.6s cubic-bezier(.2,.7,.2,1) forwards;
    }
    .splash-title {
      margin-top: 20px; font-size: 34px; font-weight: 900; letter-spacing: 8px;
      color: #2f5a20; opacity: 0; animation: titleIn 2.6s ease forwards;
      text-shadow: 0 3px 18px rgba(255,255,255,.7), 0 4px 26px rgba(120,180,80,.35);
    }
    .splash-sub { margin-top: 8px; font-size: 13px; letter-spacing: 3px; color: #567f38; opacity: 0; animation: titleIn 3s ease forwards; }
    /* 배경 장식: 언덕·구름·태양 (팜 분위기) */
    .splash-scenery { position: absolute; inset: 0; z-index: 1; pointer-events: none; }
    .splash-scenery .s-hill { position: absolute; bottom: -40px; border-radius: 50%; opacity: .9; }
    .splash-scenery .s-cloud { position: absolute; background: rgba(255,255,255,.85); border-radius: 999px; filter: blur(1px); }
    @keyframes logoIn {
      0%   { opacity: 0; filter: blur(22px) drop-shadow(0 6px 24px rgba(90,140,60,.35)); transform: scale(.45); }
      55%  { opacity: 1; filter: blur(6px)  drop-shadow(0 6px 24px rgba(90,140,60,.35)); transform: scale(1.06); }
      100% { opacity: 1; filter: blur(0)    drop-shadow(0 6px 24px rgba(90,140,60,.35)); transform: scale(1); }
    }
    @keyframes titleIn { 0%,35% { opacity: 0; transform: translateY(6px);} 100% { opacity: 1; transform: translateY(0);} }

    /* ── 작물 근접 미리보기 창 (req11) ── */
    .crop-peek {
      position: absolute; top: 12px; left: 50%; transform: translateX(-50%) translateY(-10px);
      width: min(90%, 320px); background: rgba(10,20,14,.92); border: 2px solid #7ce0a0;
      border-radius: 14px; padding: 8px; box-shadow: 0 10px 30px rgba(0,0,0,.35);
      opacity: 0; pointer-events: none; transition: opacity .25s, transform .25s; z-index: 8;
    }
    .crop-peek.show { opacity: 1; transform: translateX(-50%) translateY(0); }
    .crop-peek canvas { width: 100%; height: 150px; display: block; border-radius: 9px; background: #ffffff; }
    .crop-peek .cp-head { display: flex; justify-content: space-between; align-items: center; color: #fff; font-size: 12px; font-weight: 800; margin: 0 2px 6px; }
    .crop-peek .cp-open { margin-top: 8px; }

    /* ── 마이크 음성인식 (req10) ── */
    .mic-btn {
      width: 66px; height: 66px; border-radius: 50%; border: 0; margin: 4px auto 0;
      display: grid; place-items: center; color: #fff; background: var(--teal);
      box-shadow: 0 6px 18px rgba(22,124,128,.45);
    }
    .mic-btn svg { width: 30px; height: 30px; fill: currentColor; }
    .mic-btn.listening { background: var(--coral); animation: micPulse 1s infinite; }
    @keyframes micPulse { 0%,100% { box-shadow: 0 0 0 0 rgba(215,100,79,.5);} 50% { box-shadow: 0 0 0 14px rgba(215,100,79,0);} }
    .mode-note { text-align: center; color: var(--muted); font-size: 12px; font-weight: 700; margin: 4px 0 0; }
    .heard { text-align: center; font-size: 13px; color: var(--teal); font-weight: 800; min-height: 18px; }

    /* ── 리워드 상점 (req12) ── */
    .reward-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; }
    .reward-card { border: 1px solid var(--line); border-radius: var(--radius); background: #fff; padding: 12px; text-align: center; display: grid; gap: 6px; justify-items: center; }
    .reward-card .rc-emoji { font-size: 36px; }
    .reward-card strong { font-size: 14px; }
    .reward-card .rc-cost { color: #7a5a10; font-weight: 900; font-size: 13px; }
    .reward-card button { min-height: 38px; width: 100%; }

    /* ── 매일 도전과제 / 커뮤니티 (req14) ── */
    .challenge { display: grid; grid-template-columns: 46px 1fr auto; gap: 10px; align-items: center; padding: 12px; border: 1px solid var(--line); border-radius: var(--radius); background: linear-gradient(120deg,#fff7e8,#fff); }
    .challenge .ch-emoji { font-size: 30px; }
    .feed-item { display: grid; grid-template-columns: 40px 1fr; gap: 10px; padding: 11px 4px; border-bottom: 1px solid var(--line); }
    .feed-item:last-child { border-bottom: 0; }
    .feed-face { width: 40px; height: 40px; border-radius: 50%; display: grid; place-items: center; font-size: 20px; color: #fff; }
    .feed-item p { margin: 0; font-size: 13px; line-height: 1.4; }
    .feed-item small { color: var(--muted); font-size: 11px; }
    .cheer-btn { border: 1px solid var(--line); background: #fff; border-radius: 999px; padding: 4px 10px; font-size: 12px; font-weight: 800; margin-top: 5px; }

    /* 음소거 토글 */
    .sound-toggle { position: absolute; right: 14px; top: 12px; z-index: 8; width: 40px; height: 40px; border-radius: 50%; border: 0; background: rgba(24,33,47,.72); color: #fff; font-size: 18px; }

    /* ── 디자인 시스템 리스킨 (이미지 반영, req14) ── */
    .app-shell { background: var(--paper); box-shadow: 0 0 0 1px rgba(60,80,51,.10); }
    .topbar { background: rgba(250,246,234,.95); border-bottom-color: var(--line); }
    .eyebrow { color: var(--brand-dark); letter-spacing: .2px; }
    .chip-row { display: inline-flex; gap: 7px; align-items: center; margin-top: 4px; flex-wrap: wrap; }
    .coin-chip { margin-top: 0; background: #f4edd7; border-radius: 999px; padding: 3px 9px; }
    /* 음소거 버튼: 코인 옆, 코인과 같은 크기·디자인 (req8) */
    .mute-chip { border: 0; }
    .mute-chip.off { color: #b23c2e; background: #f7ddd8; }
    .icon-button { border-radius: 12px; }
    .tab { color: #9aa38c; border-radius: 12px; }
    .tab.active { background: var(--brand-dark); color: #fff; }
    .tabbar { background: rgba(255,255,255,.97); border-top-color: var(--line); }
    .primary-button { background: var(--brand-dark); }
    .status-pill.done { background: #e3efd6; color: var(--brand-dark); }
    .area-badge { background: var(--t-green); color: var(--brand-dark); }
    .badge-pill { background: var(--t-green); color: var(--brand-dark); }
    /* 카테고리 아이콘 타일 (이미지 스타일) */
    .area-tile { border-radius: 16px; border-color: var(--line); }
    .cat-ico { width: 46px; height: 46px; border-radius: 14px; display: grid; place-items: center; font-size: 24px; margin-bottom: 2px; }
    .routine-icon { border-radius: 12px; }
    .reward-card, .pet-card, .panel { border-radius: 16px; }

    /* 집 내부 꾸미기 (req3) */
    .room {
      position: relative; width: 100%; height: 260px; border-radius: 14px; overflow: hidden;
      background: linear-gradient(180deg,#f3e7d0 0%,#efe0c4 55%,#c69a63 55%,#b98a52 100%);
      border: 1px solid var(--line);
    }
    .room .furn { position: absolute; font-size: 40px; filter: drop-shadow(0 3px 3px rgba(0,0,0,.2)); user-select: none; cursor: grab; touch-action: none; transform: translate(-50%,-50%); }
    .room .furn:active { cursor: grabbing; }
    .room .room-char { position: absolute; left: 50%; bottom: 2px; transform: translateX(-50%); width: 158px; height: 205px; pointer-events: none; z-index: 1; }
    .room .room-char svg { width: 100%; height: 100%; }
    .room .furn { z-index: 2; }
    .room .furn.sel { outline: 3px dashed var(--brand-dark); outline-offset: 4px; border-radius: 8px; }
    .furn-chip.buy { border-style: dashed; color: #7a5a10; }
    /* 가구 크기 조절 (req11) */
    .furn-sizer { margin-top: 10px; padding: 10px 12px; border: 1px solid var(--line); border-radius: 12px; background: var(--t-green); }
    .furn-sizer input[type=range] { width: 100%; margin-top: 6px; accent-color: var(--brand-dark); }
    .room .rug { position: absolute; left: 50%; bottom: 12px; transform: translateX(-50%); width: 62%; height: 42px; border-radius: 50%; background: radial-gradient(#e79a7a,#c76b4c); opacity:.85; }
    .furn-tray { display: flex; gap: 8px; flex-wrap: wrap; margin-top: 10px; }
    .furn-chip { border: 1px solid var(--line); background: #fff; border-radius: 12px; padding: 8px 10px; font-size: 20px; }
    .furn-chip.on { border-color: var(--brand-light); background: var(--t-green); }

    /* 바다 유람 안내 배너 */
    /* 항해 안내문구: 상단 HUD(오늘의 미션 버튼·코인)와 겹치지 않게 아래로 내림 (req8) */
    .sail-banner { position: absolute; left: 50%; top: 62px; transform: translateX(-50%); z-index: 8; background: rgba(24,60,90,.85); color:#fff; padding: 8px 14px; border-radius: 999px; font-size: 12.5px; font-weight: 800; display:none; max-width: 90%; text-align:center; box-shadow: 0 4px 12px rgba(0,0,0,.25); }
    .sail-banner.show { display: block; }

    /* ── 요구사항4 추가 스타일 ── */
    .vil-hud { align-items: flex-start; }
    .mission-tag { border: 0; cursor: pointer; background: var(--gold); color: #3a2a04; pointer-events: auto; box-shadow: 0 4px 12px rgba(0,0,0,.2); }
    .mission-tag:active { transform: scale(.96); }
    .avatar-scene .ava-hint { position: absolute; left: 50%; bottom: 6px; transform: translateX(-50%); background: rgba(55,115,47,.9); color:#fff; font-size: 11px; font-weight: 800; padding: 3px 9px; border-radius: 999px; }
    /* 배에서 내리기 버튼 (req20) */
    .disembark-btn { position: absolute; left: 50%; bottom: 26px; transform: translateX(-50%); z-index: 8; border: 0; background: #c65a2e; color: #fff; font-weight: 900; font-size: 14px; padding: 12px 20px; border-radius: 999px; box-shadow: 0 6px 18px rgba(0,0,0,.3); }
    .disembark-btn:active { transform: translateX(-50%) scale(.95); }
    /* 배치 편집 버튼 (req22) */
    .edit-btn { position: absolute; left: 14px; bottom: 26px; z-index: 8; border: 0; background: rgba(24,33,47,.72); color: #fff; font-weight: 800; font-size: 13px; padding: 10px 14px; border-radius: 999px; }
    .edit-btn.on { background: var(--brand-dark); box-shadow: 0 0 0 3px rgba(134,192,90,.5); }
    /* 공용 마을 버튼 (req15) */
    .common-exit { position: absolute; left: 10px; top: 52px; z-index: 8; border: 0; background: rgba(24,33,47,.72); color:#fff; font-weight: 800; font-size: 13px; padding: 9px 14px; border-radius: 999px; }
    .common-game { position: absolute; left: 50%; bottom: 26px; transform: translateX(-50%); z-index: 8; border: 0; background: var(--brand-dark); color:#fff; font-weight: 900; font-size: 14px; padding: 12px 18px; border-radius: 999px; box-shadow: 0 4px 0 #285a22, 0 6px 18px rgba(0,0,0,.3); }
    .common-game:active { transform: translateX(-50%) translateY(2px); }
    /* 오늘의 미션 모달 (req6) */
    .mission-list { display: grid; gap: 10px; margin-top: 6px; }
    .mission-item { display: grid; grid-template-columns: 44px 1fr 34px; gap: 10px; align-items: center; padding: 12px; border: 1px solid var(--line); border-radius: 14px; background: #fff; text-align: left; }
    .mission-item.done { background: var(--t-green); border-color: var(--brand-light); }
    .mission-item .mi-ico { width: 44px; height: 44px; border-radius: 12px; display: grid; place-items: center; color:#fff; }
    .mission-item .mi-ico svg { width: 24px; height: 24px; fill: currentColor; }
    .mission-item h4 { margin: 0; font-size: 15px; }
    .mission-item p { margin: 2px 0 0; color: var(--muted); font-size: 12px; }
    .mi-check { width: 30px; height: 30px; border-radius: 9px; border: 2px solid var(--line); background:#fff; display:grid; place-items:center; font-size:18px; color: var(--brand-dark); }
    .mi-check.on { background: var(--brand-dark); border-color: var(--brand-dark); color:#fff; }

    /* ── 동물의 숲 스타일 게임 리스킨 (req25) ── */
    .game-card {
      border-radius: 22px; border: 2px solid #e4d7b3;
      background: radial-gradient(circle at 50% 0%, #fbf6e3, #f3ead0 70%);
      box-shadow: inset 0 2px 0 #fff, 0 10px 26px rgba(90,110,70,.16);
    }
    .area-badge { border-radius: 999px; padding: 7px 14px; box-shadow: 0 2px 0 rgba(0,0,0,.06); }
    .stimulus {
      border: 3px solid #8a5f30; border-radius: 18px;
      background: linear-gradient(180deg,#fffbe9,#fdf1cf);
      box-shadow: inset 0 3px 8px rgba(138,95,48,.15), 0 4px 0 #c8a86f;
      color: #3a2a10;
    }
    .choice-button {
      border-radius: 999px; border: 2px solid #d9cba4; background: #fffdf6;
      box-shadow: 0 3px 0 #e0d3ad; font-weight: 900; transition: transform .08s;
    }
    .choice-button:active { transform: translateY(2px); box-shadow: 0 1px 0 #e0d3ad; }
    .choice-button.correct { border-color: #5b8d3a; background: #e8f4e3; box-shadow: 0 3px 0 #b6d69b; }
    .choice-button.wrong { border-color: #d7644f; background: #fff0ec; box-shadow: 0 3px 0 #f0c3b7; }
    .prompt { color: #3a4a2c; }
    .cat-ico { box-shadow: inset 0 2px 0 rgba(255,255,255,.5), 0 3px 8px rgba(0,0,0,.08); border-radius: 18px; }
    .area-tile { background: linear-gradient(180deg,#fffdf6,#f7f1df); border: 2px solid #ece1c4; }
    .mic-btn { box-shadow: 0 4px 0 #2c5f45, 0 6px 18px rgba(22,124,128,.4); }
    .primary-button { border-radius: 999px; box-shadow: 0 4px 0 #285a22, var(--shadow); }
    .primary-button:active { transform: translateY(2px); box-shadow: 0 2px 0 #285a22; }
    .secondary-button { border-radius: 999px; box-shadow: 0 3px 0 #e0d3ad; }

    /* ── 두뇌 챌린지 리디자인 (진행바 + 응원 코치 캐릭터) ── */
    .game-stage { gap: 14px; }
    .q-progress { height: 11px; border-radius: 999px; background: #eadfc2; overflow: hidden; box-shadow: inset 0 1px 3px rgba(138,95,48,.2); }
    .q-progress i { display: block; height: 100%; width: var(--qp,0%); border-radius: inherit; background: linear-gradient(90deg,var(--brand-dark),var(--leaf)); transition: width .4s cubic-bezier(.3,.8,.3,1); }
    .game-meta { background: #fffdf6; border: 2px solid #ece1c4; border-radius: 999px; padding: 9px 16px; box-shadow: 0 2px 0 #e6d8b4; color: #6a7358; }
    .game-meta .gm-score { color: var(--brand-dark); font-weight: 900; }

    /* 응원 코치 = 내 캐릭터 앞모습(얼굴) + 말풍선 */
    .coach { display: grid; grid-template-columns: 88px 1fr; gap: 12px; align-items: center; }
    .coach-face {
      width: 88px; height: 88px; border-radius: 50%; overflow: hidden; justify-self: center;
      background: radial-gradient(circle at 50% 28%, #eef7e1, #d6ecc4);
      border: 3px solid #fff; box-shadow: 0 4px 0 #cdbd93, 0 9px 20px rgba(90,110,70,.22);
    }
    .coach-face svg { width: 100%; height: 100%; display: block; }
    .coach.react .coach-face { animation: coachPop .55s ease; }
    @keyframes coachPop { 0%{transform:scale(1)} 38%{transform:scale(1.16) rotate(-4deg)} 70%{transform:scale(.97) rotate(2deg)} 100%{transform:scale(1)} }
    .speech {
      position: relative; align-self: center; background: #fff; border: 2px solid #e4d7b3; border-radius: 16px;
      padding: 11px 14px; font-weight: 800; font-size: 15px; line-height: 1.35; color: #3a4a2c;
      box-shadow: 0 3px 0 #e6d8b4; min-height: 46px; display: grid; align-items: center;
    }
    .speech::before { content:''; position:absolute; left:-11px; top:50%; margin-top:-8px; border:8px solid transparent; border-right-color:#e4d7b3; }
    .speech::after  { content:''; position:absolute; left:-7px;  top:50%; margin-top:-6px; border:6px solid transparent; border-right-color:#fff; }
    .speech.correct { background: #eef8e4; border-color: #a9d488; color: #2f6629; }
    .speech.correct::after { border-right-color:#eef8e4; }
    .speech.wrong { background: #fdeee9; border-color: #f0bfae; color: #a8442f; }
    .speech.wrong::after { border-right-color:#fdeee9; }

    .prompt { animation: promptIn .4s ease; }
    @keyframes promptIn { 0%{opacity:0; transform:translateY(8px)} 100%{opacity:1; transform:translateY(0)} }
    .game-card .choice-button { font-size: 16px; min-height: 54px; }
    .brain-intro-coach { display:grid; grid-template-columns:76px 1fr; gap:12px; align-items:center; margin-bottom:12px; padding:12px 14px; border-radius:18px; border:2px solid #e4d7b3; background:radial-gradient(circle at 12% 0%, #fbf6e3, #f3ead0 75%); box-shadow: inset 0 2px 0 #fff, 0 6px 16px rgba(90,110,70,.12); }
    .brain-intro-coach .coach-face { width:76px; height:76px; }
    .brain-intro-coach p { margin:0; font-size:14px; font-weight:800; color:#3a4a2c; line-height:1.4; }
    .brain-intro-coach small { color: var(--muted); font-weight:700; }

    /* ── 작물 가방 · 배송 (req16~22) ── */
    .bag-btn { position: absolute; right: 10px; top: 52px; z-index: 8; border: 0; background: linear-gradient(180deg,#ffd84d,#f2c200); color: #5a4500; font-weight: 900; font-size: 13px; padding: 9px 13px; border-radius: 999px; box-shadow: 0 4px 12px rgba(0,0,0,.25); display:flex; align-items:center; gap:5px; }
    .bag-btn:active { transform: scale(.95); }
    .bag-btn .bag-badge { background:#c65a2e; color:#fff; border-radius:999px; font-size:11px; padding:1px 6px; font-weight:900; }
    .harvest-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(66px,1fr)); gap:8px; margin:10px 0; }
    .harvest-item { border:1px solid var(--line); border-radius:12px; background:#fff; padding:9px 4px; text-align:center; }
    .harvest-item .hi-e { font-size:28px; line-height:1; }
    .harvest-item small { display:block; font-size:11px; color:var(--muted); margin-top:3px; }
    .addr-field { width:100%; margin:8px 0; padding:11px 12px; border:1px solid var(--line); border-radius:12px; font-size:15px; background:#fff; }
    textarea.addr-field { min-height:64px; resize:vertical; }
    .gift-box { display:inline-block; font-size:76px; animation: giftBob 1s ease-in-out infinite; }
    @keyframes giftBob { 0%,100%{transform:translateY(0) rotate(-3deg)} 50%{transform:translateY(-12px) rotate(3deg)} }
    .deliver-note { text-align:center; padding:12px 6px; }

    /* ── 반려동물 키우기 (req16~25) ── */
    .pet-stage { position:relative; height:190px; border-radius:16px; overflow:hidden; display:grid; place-items:center;
      background:linear-gradient(180deg,#eaf6ff 0%,#f6fbe9 58%,#dcefcf 100%); border:1px solid var(--line); }
    .pet-stage .pet-svg { width:160px; height:auto; z-index:1; transition:transform .2s; }
    .pet-stage .pet-svg.bounce { animation: petBounce .5s ease infinite; }
    .pet-stage .pet-svg.walking { animation: petWalk 1.3s ease-in-out; }
    @keyframes petBounce { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-14px)} }
    @keyframes petWalk { 0%{transform:translateX(-70px)} 50%{transform:translateX(60px) scaleX(1)} 100%{transform:translateX(-10px)} }
    .care-prop { position:absolute; z-index:2; font-size:40px; }
    .care-prop.play { left:12%; bottom:16px; animation: ballBounce 1.3s ease; }
    @keyframes ballBounce { 0%{left:-8%;bottom:16px} 45%{left:36%;bottom:110px} 100%{left:64%;bottom:16px} }
    .care-prop.feed { left:50%; transform:translateX(-50%); bottom:12px; animation: fadeUp .35s ease; }
    .care-prop.food { left:50%; transform:translateX(-50%); bottom:44px; animation: fadeUp .35s ease; font-size:24px; }
    .care-prop.bath { top:6px; left:50%; transform:translateX(-50%); animation: showerShake .3s ease-in-out 4; }
    @keyframes showerShake { 0%,100%{transform:translateX(-50%) rotate(-8deg)} 50%{transform:translateX(-50%) rotate(8deg)} }
    .pet-stage.bathing::after { content:'💧💧💧'; position:absolute; top:44px; left:50%; transform:translateX(-50%); font-size:20px; letter-spacing:6px; animation: dropFall .8s linear infinite; }
    @keyframes dropFall { 0%{opacity:.2; transform:translateX(-50%) translateY(0)} 100%{opacity:.9; transform:translateX(-50%) translateY(30px)} }
    .care-prop.walk { left:50%; bottom:20px; transform:translateX(-50%); animation: fadeUp .35s ease; }
    @keyframes fadeUp { 0%{opacity:0; transform:translate(-50%,12px)} 100%{opacity:1; transform:translate(-50%,0)} }
    .pet-stage-dots { display:flex; justify-content:center; gap:8px; margin:12px 0 4px; }
    .pet-stage-dots i { width:26px; height:10px; border-radius:999px; background:#e2ddcb; }
    .pet-stage-dots i.on { background:linear-gradient(90deg,var(--brand-dark),var(--leaf)); }
    .care-actions { display:grid; grid-template-columns:1fr 1fr; gap:8px; margin-top:12px; }
    .care-actions button { min-height:52px; font-size:15px; }
    .pet-list-card { display:grid; grid-template-columns:56px 1fr auto; gap:10px; align-items:center; padding:10px; border:1px solid var(--line); border-radius:14px; background:#fff; margin-bottom:8px; }
    .pet-list-card .plc-ico { width:56px; height:44px; }
    .pet-list-card .plc-ico svg { width:100%; height:100%; }
    .pet-list-card.on { border-color:var(--brand-light); background:var(--t-green); }
    .pet-badge-done { background:var(--gold); color:#3a2a04; font-weight:900; font-size:11px; padding:2px 8px; border-radius:999px; }

    /* ════════════════════════════════════════════════════════
       디자인 업그레이드 — 그래픽·마감만 향상 (기능/요구사항 로직 변경 없음)
       ════════════════════════════════════════════════════════ */
    .app-shell { box-shadow: 0 0 0 1px rgba(60,80,51,.08), 0 30px 80px rgba(60,80,51,.13); }
    /* 카드류: 부드러운 그림자 + 살짝 떠오르는 인터랙션 */
    .routine-card, .panel, .area-tile, .reward-card, .pet-card, .pet-list-card, .stat, .challenge, .harvest-item, .mission-item {
      transition: transform .16s ease, box-shadow .16s ease, border-color .16s ease;
    }
    .routine-card:hover, .reward-card:hover, .area-tile:hover, .pet-card:hover, .pet-list-card:hover, .harvest-item:hover {
      transform: translateY(-2px); box-shadow: 0 10px 24px rgba(60,80,51,.14); border-color: var(--brand-light);
    }
    .primary-button, .secondary-button, .choice-button, .chip { transition: transform .1s ease, filter .12s ease, box-shadow .12s ease, background .12s ease; }
    .primary-button:hover { filter: brightness(1.05) saturate(1.05); }
    .secondary-button:hover { border-color: var(--brand-light); }
    .chip:hover { border-color: var(--brand-light); }
    /* 통계·뱃지·진행바 광택 */
    .stat { background: linear-gradient(180deg,#ffffff,#f6fbef); }
    .stat strong { color: var(--brand-dark); }
    .big-number strong { background: linear-gradient(180deg,var(--brand-dark),var(--leaf)); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent; }
    .badge-pill { box-shadow: inset 0 0 0 1px rgba(63,106,40,.14); }
    .coin-chip { box-shadow: inset 0 0 0 1px rgba(220,174,42,.3); }
    .progress-fill { box-shadow: 0 0 10px rgba(123,191,90,.45); }
    .status-pill.done { box-shadow: inset 0 0 0 1px rgba(63,106,40,.2); }
    /* 상단바·탭바 마감 */
    .topbar { box-shadow: 0 1px 0 rgba(60,80,51,.06), 0 6px 18px rgba(60,80,51,.05); }
    .tab { transition: background .15s ease, color .15s ease, box-shadow .15s ease; }
    .tab.active { box-shadow: 0 6px 16px rgba(63,106,40,.35); }
    .tab.active svg { transform: scale(1.1); }
    .tab svg { transition: transform .14s ease; }
    /* 이모지/아이콘 입체감 */
    .reward-card .rc-emoji, .pet-emoji, .harvest-item .hi-e, .cat-ico, .ch-emoji, .pet-stage-dots i { filter: drop-shadow(0 2px 3px rgba(0,0,0,.12)); }
    /* 아바타 무대 은은한 바닥광 */
    .avatar-scene, .avatar-big { box-shadow: inset 0 -22px 44px rgba(120,180,90,.14); }
    /* 마을 화면 비네트 (클릭 통과) — 3D 정원에 깊이감 */
    .village-wrap::after { content:''; position:absolute; inset:0; pointer-events:none; z-index:1; box-shadow: inset 0 0 140px rgba(20,45,20,.20), inset 0 -60px 90px rgba(20,45,20,.12); }
    /* HUD 태그·버튼 글래스 마감 */
    .vil-tag { backdrop-filter: blur(8px); box-shadow: 0 4px 14px rgba(0,0,0,.2); }
    .mission-tag { box-shadow: 0 6px 16px rgba(220,174,42,.4); }
    .bag-btn { box-shadow: 0 6px 16px rgba(220,174,42,.45); }
    .act-btn { box-shadow: 0 8px 22px rgba(63,106,40,.5); }
    /* 모달 그림자 강화 */
    .modal { box-shadow: 0 28px 70px rgba(24,33,47,.38); }
    /* 게임 카드·자극 텍스트 살짝 더 또렷하게 */
    .game-card { box-shadow: inset 0 2px 0 #fff, 0 14px 32px rgba(90,110,70,.18); }
    .section-title h3 { letter-spacing: -.2px; }
  </style>
</head>
<body>
  <!-- 로딩 스플래시 (요구사항11-26: 팜 테마 배경) -->
  <div class="splash" id="splash">
    <div class="splash-scenery" aria-hidden="true">
      <div class="s-cloud" style="left:14%;top:16%;width:70px;height:22px"></div>
      <div class="s-cloud" style="left:64%;top:10%;width:90px;height:26px"></div>
      <div class="s-cloud" style="left:40%;top:24%;width:56px;height:18px"></div>
      <div class="s-hill" style="left:-8%;width:56%;height:220px;background:#8fc165"></div>
      <div class="s-hill" style="right:-10%;width:60%;height:260px;background:#7bb457"></div>
      <div class="s-hill" style="left:26%;width:52%;height:180px;background:#9cc96f"></div>
    </div>
    <div class="splash-inner">
      <div class="splash-logo" role="img" aria-label="브레인 팜 로고"></div>
      <div class="splash-title">브레인 팜</div>
      <div class="splash-sub">🌱 두뇌가 자라는 웰에이징 팜 🧠</div>
    </div>
  </div>

  <div class="app-shell">
    <header class="topbar">
      <button class="icon-button" id="menuButton" type="button" aria-label="설정">
        <svg viewBox="0 0 24 24"><path d="M12 15.5A3.5 3.5 0 1 0 12 8.5a3.5 3.5 0 0 0 0 7Zm7.4-3.5c0-.5 0-1-.1-1.4l2-1.5-2-3.4-2.3 1a7 7 0 0 0-2.4-1.4L14 2h-4l-.5 2.8a7 7 0 0 0-2.4 1.4l-2.3-1-2 3.4 2 1.5c-.1.4-.1.9-.1 1.4s0 1 .1 1.4l-2 1.5 2 3.4 2.3-1a7 7 0 0 0 2.4 1.4L10 22h4l.5-2.8a7 7 0 0 0 2.4-1.4l2.3 1 2-3.4-2-1.5c.1-.4.1-.9.1-1.4Z"/></svg>
      </button>
      <div>
        <p class="eyebrow">🧠🌱 BRAIN FARM · 브레인 팜</p>
        <h1 id="topTitle">우*수 정원</h1>
        <span class="chip-row">
          <span class="coin-chip">🪙 <span id="coinTop">0</span> 코인</span>
          <button class="coin-chip mute-chip" id="muteChip" type="button" aria-label="효과음">🔊 <span id="muteLabel">소리</span></button>
        </span>
      </div>
      <button class="icon-button" id="resetButton" type="button" aria-label="초기화">
        <svg viewBox="0 0 24 24"><path d="M4.4 10.9a7.7 7.7 0 0 1 13.1-4.8l1.1 1.1V4h2v6.8h-6.8v-2h3.3l-1-1a5.7 5.7 0 1 0 1.5 5.6h2.1a7.7 7.7 0 0 1-15.3-2.5Z"/></svg>
      </button>
    </header>

    <main id="app" class="screen" aria-live="polite"></main>

    <nav class="tabbar" aria-label="주요 메뉴">
      <button class="tab active" type="button" data-tab="village">
        <svg viewBox="0 0 24 24"><path d="M12 3 3 10v11h6v-6h6v6h6V10Z"/></svg><span>정원</span>
      </button>
      <button class="tab" type="button" data-tab="brain">
        <svg viewBox="0 0 24 24"><path d="M9 4a3.5 3.5 0 0 0-3.5 3.5c0 .5.1 1 .3 1.4A3.6 3.6 0 0 0 7.4 16H9v-1.6H7.4a2 2 0 0 1-.5-3.9l1.2-.3-.7-1a1.9 1.9 0 0 1 1.6-3l1 .1.3-1a2 2 0 0 1 3.9.5c0 .3-.1.6-.2.9l-.5 1 1.2.2a2.6 2.6 0 0 1-.5 5.1h-1V16h1a4.2 4.2 0 0 0 1.2-8.2A3.6 3.6 0 0 0 11.9 5 3.5 3.5 0 0 0 9 4Z"/></svg><span>두뇌</span>
      </button>
      <button class="tab" type="button" data-tab="coop">
        <svg viewBox="0 0 24 24"><path d="M8 11a3 3 0 1 0 0-6 3 3 0 0 0 0 6Zm8 0a3 3 0 1 0 0-6 3 3 0 0 0 0 6ZM2 20v-1c0-2.5 3-4 6-4s6 1.5 6 4v1H2Zm14.5 0v-1c0-1.6-.8-2.8-2-3.6 3 .2 5.5 1.6 5.5 3.6v1h-3.5Z"/></svg><span>함께</span>
      </button>
      <button class="tab" type="button" data-tab="rank">
        <svg viewBox="0 0 24 24"><path d="M7 4h10v2h3v3a4 4 0 0 1-4 4h-.4A5 5 0 0 1 13 15.9V18h3v2H8v-2h3v-2.1A5 5 0 0 1 8.4 13H8a4 4 0 0 1-4-4V6h3V4Zm10 4V6h-2v3a2 2 0 0 0 2-2Zm-10 0a2 2 0 0 0 2 1V6H7v2Z"/></svg><span>랭킹</span>
      </button>
      <button class="tab" type="button" data-tab="reward">
        <svg viewBox="0 0 24 24"><path d="M20 7h-2.2a3 3 0 0 0-4.8-3.4A3 3 0 0 0 8.2 7H6a2 2 0 0 0-2 2v2h16V9a2 2 0 0 0-2-2ZM4 13v6a2 2 0 0 0 2 2h5v-8H4Zm9 8h5a2 2 0 0 0 2-2v-6h-7v8Z"/></svg><span>상점</span>
      </button>
      <button class="tab" type="button" data-tab="avatar">
        <svg viewBox="0 0 24 24"><path d="M6 3h12l1.5 4.5-3 1V21h-9V8.5l-3-1L6 3Zm2.4 2-.6 1.8 2.2.7V19h4V7.5l2.2-.7L17.6 5H8.4Z"/></svg><span>옷장</span>
      </button>
      <button class="tab" type="button" data-tab="my">
        <svg viewBox="0 0 24 24"><path d="M12 12.3a4.3 4.3 0 1 0 0-8.5 4.3 4.3 0 0 0 0 8.5Zm0 2.2c-4.1 0-7.5 2.2-7.5 4.9v.8h15v-.8c0-2.7-3.4-4.9-7.5-4.9Z"/></svg><span>마이</span>
      </button>
    </nav>
  </div>

  <!-- 설정/데모 다이얼로그 -->
  <dialog id="menuDialog" class="modal">
    <div class="modal-content">
      <div class="modal-head"><h2>설정 · 데모</h2><button class="icon-button" data-close><svg viewBox="0 0 24 24"><path d="m6.4 5 12.6 12.6-1.4 1.4L5 6.4 6.4 5Zm12.6 1.4L6.4 19 5 17.6 17.6 5 19 6.4Z"/></svg></button></div>
      <div class="panel" style="border:0;padding:0;">
        <p class="tiny" style="margin:0 0 10px;">취침모드는 밤 11시~아침 6시에 자동 작동합니다. 아래 토글로 밤 시간을 시뮬레이션할 수 있어요.</p>
        <div class="opt-row" style="margin-bottom:12px;">
          <button class="chip" id="nightToggle" type="button">🌙 밤 시뮬레이션</button>
        </div>
        <div style="margin:6px 0 10px;border-top:1px dashed var(--line);padding-top:12px">
          <p class="tiny" style="margin:0 0 8px"><b>🛠 개발 모드</b> · 내가 다시 끌 때까지 유지돼요</p>
          <div class="opt-row">
            <button class="chip" id="sleepOffToggle" type="button">🌙 취침모드 일시중지</button>
            <button class="chip" id="coinUnlimitedToggle" type="button">🪙 코인 무제한</button>
          </div>
        </div>
        <button class="secondary-button full-width" id="sleepTestBtn" type="button">취침 미션(8시간) 테스트 지급</button>
      </div>
    </div>
  </dialog>

  <!-- 식물 키우기(스마트팜) 모달 (req13,16) -->
  <dialog id="farmDialog" class="modal">
    <div class="modal-content">
      <div class="modal-head">
        <h2 id="farmTitle">🌱 식물 키우기</h2>
        <button class="icon-button" data-close><svg viewBox="0 0 24 24"><path d="m6.4 5 12.6 12.6-1.4 1.4L5 6.4 6.4 5Zm12.6 1.4L6.4 19 5 17.6 17.6 5 19 6.4Z"/></svg></button>
      </div>
      <div style="display:flex;justify-content:flex-end;align-items:center;margin-bottom:8px;">
        <span class="tiny" id="farmStage">성장 0%</span>
      </div>
      <canvas id="farmFeed" width="360" height="640"></canvas>
      <!-- 성장 스토리 + 영양분 게이지 (req11) -->
      <div style="margin-top:10px">
        <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:4px">
          <strong id="growStory" style="font-size:14px">🌰 씨앗 단계</strong>
          <span class="tiny" id="waterPct">영양분 0%</span>
        </div>
        <div class="progress-track"><div class="progress-fill" id="waterFill" style="--progress:0%"></div></div>
      </div>
      <div class="sensor-grid" id="sensorGrid"></div>
      <div class="button-row">
        <button class="secondary-button" id="farmWater" type="button">💧 영양분 주기 (-10)</button>
        <button class="primary-button" id="farmHarvest" type="button">🧺 수확</button>
      </div>
    </div>
  </dialog>

  <!-- 집안 꾸미기 모달 (req3) -->
  <dialog id="houseDialog" class="modal">
    <div class="modal-content">
      <div class="modal-head">
        <h2>🏠 우리 집 꾸미기</h2>
        <button class="icon-button" data-close><svg viewBox="0 0 24 24"><path d="m6.4 5 12.6 12.6-1.4 1.4L5 6.4 6.4 5Zm12.6 1.4L6.4 19 5 17.6 17.6 5 19 6.4Z"/></svg></button>
      </div>
      <div class="room" id="room"></div>
      <p class="tiny" style="margin:10px 0 4px">코인으로 가구를 <b>구매</b>하면 방에 놓여요. 구매한 가구만 방에 나타나며, 방 안 가구를 <b>드래그</b>해 옮기거나 <b>클릭</b>해 크기를 바꿀 수 있어요.</p>
      <div class="furn-sizer" id="furnSizer" style="display:none">
        <span class="tiny" id="furnSizerLabel">가구 크기</span>
        <input type="range" id="furnSizeRange" min="24" max="92" value="40">
        <button class="danger-button full-width" id="furnDeleteBtn" type="button" style="margin-top:10px;min-height:40px">🗑 이 가구 삭제</button>
      </div>
      <div class="furn-tray" id="furnTray"></div>
    </div>
  </dialog>

  <!-- 오늘의 나의 미션 모달 (req6) -->
  <dialog id="missionDialog" class="modal">
    <div class="modal-content">
      <div class="modal-head">
        <h2>🎯 오늘의 나의 미션</h2>
        <button class="icon-button" data-close><svg viewBox="0 0 24 24"><path d="m6.4 5 12.6 12.6-1.4 1.4L5 6.4 6.4 5Zm12.6 1.4L6.4 19 5 17.6 17.6 5 19 6.4Z"/></svg></button>
      </div>
      <p class="tiny" style="margin:0 0 4px">오늘의 루틴을 하나씩 실행하고 체크하면 리워드(코인)를 받아요.</p>
      <div class="progress-track" style="margin:8px 0"><div class="progress-fill" id="missionFill" style="--progress:0%"></div></div>
      <div class="mission-list" id="missionList"></div>
    </div>
  </dialog>

  <!-- 작물 가방 · 배송 모달 (req17~24) -->
  <dialog id="backpackDialog" class="modal">
    <div class="modal-content">
      <div class="modal-head">
        <h2 id="backpackTitle">🎒 나의 작물 가방</h2>
        <button class="icon-button" data-close><svg viewBox="0 0 24 24"><path d="m6.4 5 12.6 12.6-1.4 1.4L5 6.4 6.4 5Zm12.6 1.4L6.4 19 5 17.6 17.6 5 19 6.4Z"/></svg></button>
      </div>
      <div id="backpackBody"></div>
    </div>
  </dialog>

  <!-- 반려동물 키우기 모달 (요구사항11-16~25) -->
  <dialog id="petCareDialog" class="modal">
    <div class="modal-content">
      <div class="modal-head">
        <h2 id="petCareTitle">🐾 반려동물 키우기</h2>
        <button class="icon-button" data-close><svg viewBox="0 0 24 24"><path d="m6.4 5 12.6 12.6-1.4 1.4L5 6.4 6.4 5Zm12.6 1.4L6.4 19 5 17.6 17.6 5 19 6.4Z"/></svg></button>
      </div>
      <div id="petCareBody"></div>
    </div>
  </dialog>

  <!-- 취침 오버레이 -->
  <div class="sleep-overlay" id="sleepOverlay">
    <div class="stars" id="stars"></div>
    <div style="position:relative;">
      <div class="moon">🌙</div>
      <h2>취침 시간이에요</h2>
      <p>밤 11시부터 아침 6시까지는 눈과 뇌를 쉬게 하는 시간이에요. 푹 주무시고 내일 아침 마을에서 만나요.</p>
      <p class="tiny" id="sleepClock" style="color:#8fa0c8;margin-top:14px;"></p>
    </div>
  </div>

  <div class="toast" id="toast"></div>

  <script type="module">
  'use strict';

  /* ============================================================
     웰에이징 브레인팜 v2 — 요구사항.md 반영 업그레이드
     통합 단일 파일 (HTML+CSS+JS). three.js는 CDN 동적 로드.
     ============================================================ */

  const STORE_KEY = 'brainfarm_v4';

  const AREAS = [
    { id:'attention',    name:'집중력',   emoji:'🍅', tile:'var(--t-green)',  color:'var(--teal)'  },
    { id:'memory',       name:'기억력',   emoji:'🌱', tile:'var(--t-yellow)', color:'var(--blue)'  },
    { id:'language',     name:'언어력',   emoji:'💡', tile:'var(--t-peach)',  color:'var(--leaf)'  },
    { id:'visuospatial', name:'시간관리', emoji:'⏰', tile:'var(--t-blue)',   color:'var(--sun)'   },
    { id:'executive',    name:'수행기능', emoji:'🪴', tile:'var(--t-purple)', color:'var(--coral)' },
  ];
  const LEVELS = { easy:'쉬움', normal:'보통', hard:'어려움' };
  const DIFF = {
    easy:   { seqLen:3, numMax:12, step:2, choices:3, hideMs:2300, flankers:2, dirs:2, coin:5 },
    normal: { seqLen:4, numMax:30, step:3, choices:4, hideMs:1500, flankers:4, dirs:2, coin:7 },
    hard:   { seqLen:6, numMax:60, step:5, choices:4, hideMs:1000, flankers:6, dirs:4, coin:10 },
  };
  const CROPS = [
    { key:'tomato', name:'방울토마토', emoji:'🍅', color:'#e0453e' },
    { key:'lettuce',name:'상추',       emoji:'🥬', color:'#6fae48' },
    { key:'melon',  name:'수박',       emoji:'🍉', color:'#3a9d3a' },  // req12: 딸기→수박
    { key:'corn',   name:'옥수수',     emoji:'🌽', color:'#f2c200' },  // req11: 파프리카→옥수수
  ];
  // 반려동물 — 몸통·꼬리·다리를 그리기 위한 색상 포함 (요구사항11-11)
  const PETS = [
    { type:'dog',   name:'강아지', emoji:'🐶', price:80,  body:'#d1a05e', ear:'#a9773f', belly:'#f0dcc0' },
    { type:'cat',   name:'고양이', emoji:'🐱', price:80,  body:'#9a9a9a', ear:'#7a7a7a', belly:'#e8e8e8' },
    { type:'rabbit',name:'토끼',   emoji:'🐰', price:120, body:'#efe7dc', ear:'#e3d2c8', belly:'#ffffff' },
    { type:'bird',  name:'새',     emoji:'🐦', price:60,  body:'#6a9ec0', ear:'#5b87a3', belly:'#dbe8f0' },
  ];
  const PET_STAGE_NAMES = ['아기','어린이','청소년','어른','완전체']; // 5단계 (req22,24)
  const SKINS   = ['#f3cea2','#eec39a','#e8b891','#c98d63','#8a5a3b'];
  // 참고 이미지 반영: 올리브 니트(남)·회색 니트(여)를 앞쪽에 배치 (req3,4)
  const OUTFITS = ['#7c8a3f','#9ea3a8','#3a72b8','#5b8d3a','#d7644f','#167c80','#d99a25'];
  const HATS    = [ {id:'none',label:'없음'}, {id:'cap',label:'모자'}, {id:'flower',label:'꽃'}, {id:'crown',label:'왕관'} ];
  // 검정(남)·갈색(여) 머리를 앞쪽에 (req3)
  const HAIRS   = ['#141414','#5a3d28','#3a2a1c','#6b4a2b','#b5651d','#9a9a9a','#d8b070'];

  // 리워드/포인트 교환 상점 — 코인=포인트 (요구사항11: 씨앗 교환·이벤트 박스로 개편)
  const REWARDS = [
    { id:'melonSeed',  emoji:'🍉', name:'수박 씨앗 교환',       cost:300 },  // req1
    { id:'cornSeed',   emoji:'🌽', name:'옥수수 씨앗 교환',     cost:300 },  // req2
    { id:'lettuceSeed',emoji:'🥬', name:'상추 씨앗 교환',       cost:300 },  // req3
    { id:'tomatoSeed', emoji:'🍅', name:'방울토마토 씨앗 교환', cost:300 },  // req4
    { id:'event',      emoji:'🎁', name:'특별 이벤트 박스',     cost:2000 }, // req6, req8: 건강식품세트 위치로
    { id:'health',     emoji:'💊', name:'건강식품 세트',        cost:30000 },// req5, req7: 이벤트 박스 위치로
  ];

  // 코인으로 사는 꾸미기 상점 — 옷·악세서리·신발·정원 디자인 (요구사항11-9)
  const SHOP_ITEMS = [
    { id:'cl_tee',   cat:'옷',       emoji:'👕', name:'캐주얼 티셔츠', price:120 },
    { id:'cl_coat',  cat:'옷',       emoji:'🧥', name:'따뜻한 코트',   price:200 },
    { id:'cl_dress', cat:'옷',       emoji:'👗', name:'예쁜 원피스',   price:180 },
    { id:'ac_cap',   cat:'악세서리', emoji:'🧢', name:'멋진 모자',     price:90  },
    { id:'ac_glass', cat:'악세서리', emoji:'🕶️', name:'선글라스',      price:110 },
    { id:'ac_scarf', cat:'악세서리', emoji:'🧣', name:'포근한 목도리', price:100 },
    { id:'sh_sneak', cat:'신발',     emoji:'👟', name:'운동화',        price:130 },
    { id:'sh_boot',  cat:'신발',     emoji:'🥾', name:'튼튼한 장화',   price:150 },
    { id:'ds_flower',cat:'정원 디자인', emoji:'🌷', name:'꽃길 디자인',  price:160 },
    { id:'ds_fount', cat:'정원 디자인', emoji:'⛲', name:'분수 디자인',  price:220 },
    { id:'ds_tree',  cat:'정원 디자인', emoji:'🌳', name:'큰 나무 디자인', price:190 },
  ];
  const SHOP_CATS = ['옷','악세서리','신발','정원 디자인'];

  // 매일 다른 도전과제 (req14) — 날짜 기반으로 순환
  const DAILY_CHALLENGES = [
    { emoji:'🧠', title:'두뇌 게임 3판 하기',   reward:20 },
    { emoji:'💧', title:'작물에 물 2번 주기',    reward:15 },
    { emoji:'🚶', title:'6천 걸음 걷기',         reward:25 },
    { emoji:'🗣️', title:'음성으로 문제 풀기',    reward:20 },
    { emoji:'🌷', title:'정원 꾸미기 아이템 두기', reward:18 },
    { emoji:'💕', title:'반려동물과 놀아주기',    reward:15 },
    { emoji:'🤝', title:'친구 응원 남기기',       reward:12 },
  ];
  // 집안 꾸미기 가구 (req3) — 방 안 프리셋 위치에 배치
  const FURNITURE = [
    { id:'sofa',  e:'🛋️', name:'소파',   price:40, x:22, y:60 },
    { id:'plant', e:'🪴', name:'화분',   price:20, x:78, y:52 },
    { id:'lamp',  e:'💡', name:'조명',   price:25, x:60, y:30 },
    { id:'tv',    e:'📺', name:'TV',     price:60, x:44, y:34 },
    { id:'clock', e:'🕰️', name:'괘종시계', price:35, x:12, y:32 },
    { id:'picture',e:'🖼️',name:'액자',   price:15, x:70, y:22 },
    { id:'cat',   e:'🐱', name:'고양이', price:50, x:50, y:66 },
    { id:'rug',   e:'🟫', name:'러그',   price:30, x:50, y:78 },
  ];

  // 커뮤니티 피드 (req14)
  const COMMUNITY = [
    { n:'복순', e:'👵', c:'#3a72b8', t:'오늘 감귤나무 3단계까지 키웠어요! 손주 자랑해야지 🍊' },
    { n:'영호', e:'👴', c:'#5b8d3a', t:'기억력 게임 어려움 단계 성공! 나이는 숫자일 뿐~' },
    { n:'미자', e:'👵', c:'#d7644f', t:'매일 걷기 도전 7일째 연속 달성 중입니다 👟' },
    { n:'상철', e:'👴', c:'#d99a25', t:'음성으로 문제 푸니 눈이 편하고 좋네요.' },
    { n:'정순', e:'👵', c:'#7a4fd7', t:'공동 밭에 물 주고 왔어요. 다들 힘내세요!' },
  ];

  function defaultState() {
    return {
      coins: 200, streak: 3, steps: 4200, stepGoal: 8000,
      lastPlayTs: null, sleepClaimedDate: null, forceNight: false,
      // 참고 이미지(남성 누끼) 기본값: 올리브 니트·검정 머리·안경 (req3)
      avatar: { skin: SKINS[0], outfit: '#7c8a3f', hat: 'none', hair: '#141414', gender: 'male', glasses: true },
      house: { owned: [], items: [], pos: {}, size: {} }, // 구매(owned)·배치(items)·좌표(pos)·크기(size) (req15,17,11)
      layout: {},                              // 정원 오브젝트 커스텀 배치 좌표 (req22)
      pet: { adopted: [], active: [], seq: 0 }, // adopted:[{id,type,affection,stage,complete,rewarded}] active:[id](최대2) (req12,14,22)
      scores: { attention:62, memory:55, language:70, visuospatial:48, executive:60 },
      brain: {
        level: { attention:'normal', memory:'normal', language:'normal', visuospatial:'normal', executive:'normal' },
        stats: { attention:[], memory:[], language:[], visuospatial:[], executive:[] }, // 최근 정오답 기록(true/false)
      },
      farm: CROPS.map((c,i) => ({ key:c.key, stage: i===0?2:0, water: 0 })), // stage 0~4
      harvested: [],                           // 그동안 수확(재배)한 작물 모음 (req17,18)
      delivery: { done:false, addr:'' },       // 작물 배송 상태 (req19~22)
      routines: [
        { id:'water',  title:'아침 물 한 잔',   desc:'기상 후 수분 보충', icon:'drop',  color:'var(--blue)',  done:false },
        { id:'walk',   title:'10분 걷기',        desc:'가벼운 활동으로 혈류 깨우기', icon:'walk', color:'var(--teal)', done:false },
        { id:'game',   title:'두뇌 게임 한 판',   desc:'인지 5개 영역 훈련', icon:'brain', color:'var(--coral)', done:false },
        { id:'farm',   title:'스마트팜 돌보기',   desc:'마을에서 작물에 물주기', icon:'leaf', color:'var(--leaf)', done:false },
        { id:'family', title:'가족·친구 안부',    desc:'연결감이 인지 건강을 지켜요', icon:'heart', color:'var(--sun)', done:false },
      ],
      coop: {
        mission: { title:'마을 단체 미션 · 두뇌 게임 200판', goal:200, base:126 },
        field: { goal:100, base:64 },   // 공동 작물 밭 진행 %
        myContribGame: 0, myContribField: 0,
        decos: [],
        layout: {},                     // 공용 마을 배치 좌표 (req15)
      },
      daily: { date:null, done:false },        // 매일 도전과제 (req14)
      cheers: {},                              // 커뮤니티 응원 누른 항목 (req14)
      rewardsOwned: [],                        // 교환한 리워드 (req12)
      shopOwned: [],                           // 코인으로 구매한 꾸미기 아이템 (요구사항11-9)
      muted: false,                            // 효과음 음소거 (req19)
      reqv6: false,                            // 요구사항6 외형 마이그레이션 플래그
      sleepOff: true,                          // 개발용: 취침모드 일시중지 (내가 다시 켤 때까지)
      unlimitedCoins: true,                    // 개발용: 코인 무제한
    };
  }

  // 성별별 참고 이미지 외형 프리셋 (req3) — 남: 올리브·검정·안경 / 여: 회색·갈색·안경X
  function applyGenderLook(av, gender){
    av.gender = gender;
    if(gender==='female'){ av.outfit='#9ea3a8'; av.hair='#5a3d28'; av.glasses=false; }
    else { av.outfit='#7c8a3f'; av.hair='#141414'; av.glasses=true; }
    return av;
  }

  let state = load();
  // 요구사항6: 기존 저장 데이터도 참고 이미지 외형으로 1회 갱신 (진행상황은 유지)
  if(!state.reqv6){
    state.avatar = state.avatar || {};
    applyGenderLook(state.avatar, state.avatar.gender==='female'?'female':'male');
    if(!state.avatar.skin) state.avatar.skin = SKINS[0];
    if(!state.avatar.hat) state.avatar.hat = 'none';
    state.reqv6 = true; save();
  }
  if(state.unlimitedCoins) state.coins = 9999999; // 개발용: 코인 무제한
  // 작물 목록 변경(수박·옥수수) 반영 — 기존 저장 데이터의 밭 키를 현재 CROPS에 맞춰 동기화 (req11,12)
  if(!Array.isArray(state.farm) || state.farm.length!==CROPS.length){
    state.farm = CROPS.map((c,i)=>({ key:c.key, stage: (state.farm&&state.farm[i]?state.farm[i].stage:(i===0?2:0)), water:(state.farm&&state.farm[i]?state.farm[i].water:0) }));
  }
  state.farm.forEach((f,i)=>{ if(CROPS[i]) f.key=CROPS[i].key; });
  if(!Array.isArray(state.harvested)) state.harvested = [];
  if(!state.delivery) state.delivery = { done:false, addr:'' };
  if(!Array.isArray(state.shopOwned)) state.shopOwned = [];
  // 반려동물 모델 마이그레이션 (구버전 {type} → 신버전 id 기반 다마리·동행 2·성장단계) (req11~25)
  if(!state.pet) state.pet = { adopted:[], active:[], seq:0 };
  if(!Number.isInteger(state.pet.seq)) state.pet.seq = 0;
  if(!Array.isArray(state.pet.active)){ const old=state.pet.active; state.pet.active = (old&&old.type)?[old.type]:[]; }
  state.pet.adopted = (state.pet.adopted||[]).map(p=>{
    if(!p.id) p.id = 'p'+(++state.pet.seq);
    if(typeof p.stage!=='number') p.stage = 1;
    if(typeof p.affection!=='number') p.affection = 20;
    if(typeof p.complete!=='boolean') p.complete = false;
    if(typeof p.rewarded!=='boolean') p.rewarded = false;
    return p;
  });
  // active 항목이 타입 문자열이면 해당 타입의 첫 반려동물 id로 변환 후, id만 최대 2개 유지
  state.pet.active = state.pet.active.map(a=>{
    if(typeof a==='string' && a[0]==='p' && state.pet.adopted.some(p=>p.id===a)) return a;
    const f=state.pet.adopted.find(p=>p.type===a); return f?f.id:null;
  }).filter(Boolean).slice(0,2);
  let activeTab = 'village';
  let villageCleanup = null;
  let villageApi = null;   // 정원 3D 씬 제어 API (밭 갱신 등, req5)

  function load() {
    try {
      const raw = localStorage.getItem(STORE_KEY);
      if (raw) return Object.assign(defaultState(), JSON.parse(raw));
    } catch(e) {}
    return defaultState();
  }
  function save() { try { localStorage.setItem(STORE_KEY, JSON.stringify(state)); } catch(e){} }

  /* ---------- 유틸 ---------- */
  const $ = (s, r=document) => r.querySelector(s);
  const app = $('#app');
  const esc = (s) => String(s).replace(/[&<>"]/g, c => ({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]));
  const nf = (n) => Number(n).toLocaleString('ko-KR');
  const rand = (n) => Math.floor(Math.random()*n);
  const clamp = (v,a,b) => Math.max(a, Math.min(b, v));
  function shuffle(arr){ const a=arr.slice(); for(let i=a.length-1;i>0;i--){ const j=rand(i+1); [a[i],a[j]]=[a[j],a[i]]; } return a; }
  const avgScore = () => Math.round(AREAS.reduce((s,a)=>s+state.scores[a.id],0)/AREAS.length);
  const brainAge = () => clamp(Math.round(72 - avgScore()*0.22), 45, 90);

  let toastTimer=null;
  function toast(msg){ const t=$('#toast'); t.textContent=msg; t.classList.add('show'); clearTimeout(toastTimer); toastTimer=setTimeout(()=>t.classList.remove('show'),1800); }
  function addCoins(n){ if(state.unlimitedCoins){ state.coins=9999999; syncCoins(); return; } state.coins=Math.max(0,state.coins+n); syncCoins(); } // 무제한 모드에선 항상 가득
  function syncCoins(){ const el=$('#coinTop'); if(el) el.textContent=nf(state.coins); }
  function bumpScore(id,d){ state.scores[id]=clamp(Math.round(state.scores[id]+d),0,100); }
  function completeRoutine(id){ const r=state.routines.find(x=>x.id===id); if(r&&!r.done){ r.done=true; addCoins(10);} }

  /* ---------- 효과음 엔진 (req19) ---------- */
  const Sound = (() => {
    let ctx=null, windNode=null, windGain=null, seaTimer=null;
    function ac(){ if(!ctx){ try{ ctx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){ ctx=null; } } return ctx; }
    function resume(){ const c=ac(); if(c && c.state==='suspended') c.resume(); }
    function blip(freq, dur, type, vol){
      if(state.muted) return; const c=ac(); if(!c) return;
      const o=c.createOscillator(), g=c.createGain();
      o.type=type||'sine'; o.frequency.value=freq;
      g.gain.setValueAtTime(0, c.currentTime);
      g.gain.linearRampToValueAtTime(vol||0.15, c.currentTime+0.01);
      g.gain.exponentialRampToValueAtTime(0.0001, c.currentTime+(dur||0.15));
      o.connect(g).connect(c.destination); o.start(); o.stop(c.currentTime+(dur||0.15)+0.02);
    }
    return {
      resume,
      step(){ blip(180+rand(40), 0.08, 'triangle', 0.05); },
      correct(){ blip(660,0.1,'sine',0.16); setTimeout(()=>blip(880,0.14,'sine',0.16),90); },
      wrong(){ blip(200,0.25,'sawtooth',0.12); },
      water(){ blip(500,0.12,'sine',0.1); setTimeout(()=>blip(700,0.12,'sine',0.08),80); },
      harvest(){ blip(523,0.12,'sine',0.16); setTimeout(()=>blip(659,0.12,'sine',0.16),110); setTimeout(()=>blip(784,0.2,'sine',0.16),220); },
      coin(){ blip(988,0.08,'square',0.1); setTimeout(()=>blip(1319,0.12,'square',0.1),70); },
      tap(){ blip(420,0.05,'sine',0.06); },
      // 바람소리 (나무 흔들림) — 필터링된 노이즈 루프
      windStart(){
        if(state.muted) return; const c=ac(); if(!c || windNode) return;
        const buf=c.createBuffer(1, c.sampleRate*2, c.sampleRate);
        const data=buf.getChannelData(0);
        for(let i=0;i<data.length;i++) data[i]=(Math.random()*2-1);
        windNode=c.createBufferSource(); windNode.buffer=buf; windNode.loop=true;
        const lp=c.createBiquadFilter(); lp.type='lowpass'; lp.frequency.value=550;
        windGain=c.createGain(); windGain.gain.value=0.0;
        windNode.connect(lp).connect(windGain).connect(c.destination); windNode.start();
      },
      windGust(strength){ // 나무가 흔들릴 때 바람소리 커졌다 작아짐
        if(state.muted || !windGain || !ctx) return;
        const t=ctx.currentTime, v=clamp(strength,0,1)*0.09;
        windGain.gain.cancelScheduledValues(t);
        windGain.gain.setValueAtTime(windGain.gain.value, t);
        windGain.gain.linearRampToValueAtTime(v, t+0.6);
        windGain.gain.linearRampToValueAtTime(0.008, t+2.2);
      },
      windStop(){ try{ if(windNode){ windNode.stop(); windNode.disconnect(); } }catch(e){} windNode=null; windGain=null; },
      // 바다 유람 신나는 음악 (req5) — 밝은 아르페지오 루프
      seaMusicStart(){
        if(state.muted || seaTimer) return; this.resume(); const c=ac(); if(!c) return;
        const scale=[523,587,659,784,880,784,659,587]; let i=0;
        const play=()=>{ if(state.muted){ this.seaMusicStop(); return; }
          const o=c.createOscillator(), g=c.createGain();
          o.type='triangle'; o.frequency.value=scale[i%scale.length];
          g.gain.setValueAtTime(0,c.currentTime); g.gain.linearRampToValueAtTime(0.08,c.currentTime+0.03);
          g.gain.exponentialRampToValueAtTime(0.0001,c.currentTime+0.28);
          o.connect(g).connect(c.destination); o.start(); o.stop(c.currentTime+0.3);
          // 베이스
          const b=c.createOscillator(), bg=c.createGain(); b.type='sine'; b.frequency.value=scale[i%scale.length]/2;
          bg.gain.setValueAtTime(0.05,c.currentTime); bg.gain.exponentialRampToValueAtTime(0.0001,c.currentTime+0.3);
          b.connect(bg).connect(c.destination); b.start(); b.stop(c.currentTime+0.3);
          i++;
        };
        play(); seaTimer=setInterval(play,300);
      },
      seaMusicStop(){ if(seaTimer){ clearInterval(seaTimer); seaTimer=null; } },
      muteAll(m){ state.muted=m; if(m){ this.windStop(); this.seaMusicStop(); } },
    };
  })();

  /* ---------- 매일 도전과제 (req14) ---------- */
  function todayChallenge(){
    const d=new Date(); const idx=(d.getFullYear()*372 + d.getMonth()*31 + d.getDate()) % DAILY_CHALLENGES.length;
    return Object.assign({ idx }, DAILY_CHALLENGES[idx]);
  }
  function ensureDaily(){ const ds=todayStr(); if(!state.daily || state.daily.date!==ds){ state.daily={ date:ds, done:false }; save(); } }

  /* ---------- 음성 인식 (req10) ---------- */
  const Voice = (() => {
    const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
    let rec=null, active=false, onResultCb=null;
    const supported = !!SR;
    function start(onResult, onEnd){
      if(!supported) return false;
      try {
        rec = new SR(); rec.lang='ko-KR'; rec.interimResults=false; rec.maxAlternatives=3;
        onResultCb=onResult; active=true;
        rec.onresult=(e)=>{ const alts=[]; for(let i=0;i<e.results[0].length;i++) alts.push(e.results[0][i].transcript.trim()); if(onResultCb) onResultCb(alts); };
        rec.onerror=()=>{ active=false; if(onEnd) onEnd('error'); };
        rec.onend=()=>{ active=false; if(onEnd) onEnd('end'); };
        rec.start(); return true;
      } catch(e){ active=false; return false; }
    }
    function stop(){ try{ if(rec) rec.stop(); }catch(e){} active=false; }
    return { supported, start, stop, isActive:()=>active };
  })();
  // 발화 → 보기 매칭 (숫자/낱말)
  function matchChoice(alts, choices){
    const norm=(s)=>String(s).replace(/[\s.,!?~]/g,'').toLowerCase();
    for(const raw of alts){
      const a=norm(raw);
      // 정확/부분 일치
      for(let i=0;i<choices.length;i++){ const c=norm(choices[i].t); if(c && (a===c || a.includes(c) || c.includes(a))) return i; }
      // 숫자만 추출해 비교
      const num=raw.replace(/[^0-9]/g,'');
      if(num){ for(let i=0;i<choices.length;i++){ if(String(choices[i].t).replace(/[^0-9]/g,'')===num) return i; } }
      // 번호로 말한 경우 (첫번째/1번 등)
      const ord=raw.match(/([1-4]|첫|둘|셋|넷|하나|두|세|네)/);
      if(ord){ const mp={'1':0,'첫':0,'하나':0,'2':1,'둘':1,'두':1,'3':2,'셋':2,'세':2,'4':3,'넷':3,'네':3}; const idx=mp[ord[1]]; if(idx!=null && idx<choices.length) return idx; }
    }
    return -1;
  }
  function bumpDaily(kind){
    ensureDaily(); if(state.daily.done) return;
    const ch=todayChallenge();
    const map={ game:0, water:1, walk:2, voice:3, deco:4, pet:5, cheer:6 };
    if(map[kind]===ch.idx){ state.daily.done=true; addCoins(ch.reward); Sound.coin(); save(); toast('🎯 오늘의 도전과제 완료! +'+ch.reward+' 코인'); }
  }

  const ICONS = {
    drop:'<path d="M12 3s6 6.6 6 11a6 6 0 1 1-12 0c0-4.4 6-11 6-11Z"/>',
    walk:'<path d="M13 4a2 2 0 1 1-2 2 2 2 0 0 1 2-2Zm-1.4 4.5h1.6l2 3 2.6 1.3-.8 1.7-3.1-1.5-1-1.5-.7 2.7 2 2-1.2 3.9-1.8-.5 1-3.2-2.4-2.4.7-3.7Z"/>',
    brain:'<path d="M9 4a3.5 3.5 0 0 0-3.5 3.5c0 .5.1 1 .3 1.4A3.6 3.6 0 0 0 7.4 16H9v-1.6H7.4a2 2 0 0 1-.5-3.9l1.2-.3-.7-1a1.9 1.9 0 0 1 1.6-3l1 .1.3-1a2 2 0 0 1 3.9.5c0 .3-.1.6-.2.9l-.5 1 1.2.2a2.6 2.6 0 0 1-.5 5.1h-1V16h1a4.2 4.2 0 0 0 1.2-8.2A3.6 3.6 0 0 0 11.9 5 3.5 3.5 0 0 0 9 4Z"/>',
    leaf:'<path d="M5 19c0-7 5.5-13 14-13 0 8.5-6 14-14 14v-1Z"/>',
    heart:'<path d="M12 20C7 16 4 13 4 9.7A3.7 3.7 0 0 1 12 7a3.7 3.7 0 0 1 8 2.7C20 13 17 16 12 20Z"/>',
  };
  const routineIcon = (k) => '<svg viewBox="0 0 24 24">'+(ICONS[k]||ICONS.leaf)+'</svg>';

  /* ---------- 아바타 SVG (꾸미기 반영) ---------- */
  function avatarSvg(big){
    const a = state.avatar;
    const hair = a.hair || HAIRS[0];
    const female = a.gender==='female';
    let hat = '';
    if (a.hat==='cap')    hat = '<path d="M38 34a22 22 0 0 1 44 0l-44 2Z" fill="#8a7b52"/><rect x="58" y="32" width="30" height="5" rx="2" fill="#6f6340"/>';
    if (a.hat==='flower') hat = '<circle cx="44" cy="26" r="6.5" fill="#e2445c"/><circle cx="44" cy="26" r="2.6" fill="#ffd34d"/><circle cx="38" cy="30" r="3" fill="#6fae48"/>';
    if (a.hat==='crown')  hat = '<path d="M42 30l4-10 7 7 7-7 7 7 4-10v13H42Z" fill="#e2b32b"/><circle cx="46" cy="20" r="2" fill="#fff"/><circle cx="60" cy="17" r="2" fill="#fff"/><circle cx="74" cy="20" r="2" fill="#fff"/>';
    // 안경 액세서리 (이미지 반영)
    const glasses = a.glasses
      ? '<g fill="none" stroke="#2a3342" stroke-width="2"><circle cx="52" cy="46" r="6"/><circle cx="68" cy="46" r="6"/><path d="M58 46h4M46 44l-4-2M74 44l4-2" stroke-linecap="round"/></g>'
      : '';
    // 성별에 따른 머리카락
    const backHair = female
      ? '<path d="M32 48a28 28 0 0 1 56 0c0 18-4 30-8 40l-6-2c3-14 4-26 2-36-2-12-10-18-16-18s-14 6-16 18c-2 10-1 22 2 36l-6 2c-4-10-8-22-8-40Z" fill="'+hair+'"/>'
      : '<path d="M36 46a24 24 0 0 1 48 0c0 6-2 10-4 12 0-14-8-22-20-22s-20 8-20 22c-2-2-4-6-4-12Z" fill="'+hair+'"/>';
    const frontHair = female
      ? '<path d="M39 44q3-19 21-19t21 19q-7-9-21-9t-21 9Z" fill="'+hair+'"/>'
      : '<path d="M40 42q4-16 20-16t20 16q-6-8-20-8t-20 8Z" fill="'+hair+'"/>';
    // 동행 반려동물(최대 2마리)을 아바타 옆에 표시 (req13,14)
    const activeIds = state.pet.active||[];
    const petEmojis = activeIds.map(id=>{ const ad=(state.pet.adopted||[]).find(p=>p.id===id); const info=ad?PETS.find(x=>x.type===ad.type):null; return info?info.emoji:''; }).filter(Boolean);
    const petSvg = petEmojis.length ? '<text x="82" y="134" font-size="20">'+petEmojis.join('')+'</text>' : '';
    return '<svg viewBox="0 0 120 150">'+
      backHair+
      '<circle cx="60" cy="47" r="21" fill="'+a.skin+'"/>'+
      frontHair+
      hat+
      '<circle cx="48" cy="53" r="3.5" fill="#ff9d9d" opacity=".6"/><circle cx="72" cy="53" r="3.5" fill="#ff9d9d" opacity=".6"/>'+
      '<circle cx="52" cy="46" r="3.4" fill="#2a3342"/><circle cx="68" cy="46" r="3.4" fill="#2a3342"/>'+
      '<circle cx="53.2" cy="44.8" r="1" fill="#fff"/><circle cx="69.2" cy="44.8" r="1" fill="#fff"/>'+
      glasses+
      '<path d="M53 55q7 6 14 0" stroke="#b06a44" stroke-width="2.2" fill="none" stroke-linecap="round"/>'+
      // 스웨터 몸통
      '<rect x="43" y="72" width="34" height="40" rx="15" fill="'+a.outfit+'"/>'+
      // 노란색 백팩 — 양쪽 어깨 끈 + 옆으로 보이는 가방 (req16)
      '<rect x="37" y="80" width="7.5" height="22" rx="3" fill="#f2c200"/>'+
      '<rect x="75.5" y="80" width="7.5" height="22" rx="3" fill="#e0ad00"/>'+
      '<path d="M50 73v34" stroke="#f2c200" stroke-width="4.6" stroke-linecap="round"/>'+
      '<path d="M70 73v34" stroke="#f2c200" stroke-width="4.6" stroke-linecap="round"/>'+
      // 팔 (스웨터 소매 + 손)
      '<rect x="33" y="76" width="9" height="26" rx="4.5" fill="'+a.outfit+'"/><circle cx="37.5" cy="103" r="4.5" fill="'+a.skin+'"/>'+
      '<rect x="78" y="76" width="9" height="26" rx="4.5" fill="'+a.outfit+'"/><circle cx="82.5" cy="103" r="4.5" fill="'+a.skin+'"/>'+
      // 청바지 다리
      '<rect x="50" y="110" width="9" height="20" rx="3" fill="#33456b"/><rect x="61" y="110" width="9" height="20" rx="3" fill="#33456b"/>'+
      // 갈색 장화 (이미지 반영)
      '<path d="M49 128h11v6q0 5-5.5 5T49 134Z" fill="#6b4a2b"/><path d="M60 128h11v6q0 5-5.5 5T60 134Z" fill="#6b4a2b"/>'+
      '<ellipse cx="53" cy="140" rx="6.5" ry="3" fill="#5a3d22"/><ellipse cx="66.5" cy="140" rx="6.5" ry="3" fill="#5a3d22"/>'+
      petSvg+
      '</svg>';
  }

  /* ---------- 코치 얼굴 SVG (내 캐릭터 앞모습·표정 반응) ---------- */
  function coachFace(mood){
    const a = state.avatar;
    const hair = a.hair || HAIRS[0], skin = a.skin || SKINS[0], outfit = a.outfit || OUTFITS[0];
    const female = a.gender==='female';
    const back = female
      ? '<path d="M22 60a38 38 0 0 1 76 0c0 22-6 34-11 46H33c-5-12-11-24-11-46Z" fill="'+hair+'"/>'
      : '<path d="M26 58a34 34 0 0 1 68 0c0 11-3 18-6 22 0-21-11-31-28-31S32 69 32 80c-3-4-6-11-6-22Z" fill="'+hair+'"/>';
    // 어깨(니트) + 목
    const shoulders = '<path d="M14 120v-10a46 46 0 0 1 92 0v10Z" fill="'+outfit+'"/>'
      + '<path d="M48 90h24v16a12 12 0 0 1-24 0Z" fill="'+skin+'"/>';
    const faceBase = '<ellipse cx="60" cy="58" rx="31" ry="33" fill="'+skin+'"/>';
    const bangs = female
      ? '<path d="M29 54q4-27 31-27t31 27q-9-13-31-13t-31 13Z" fill="'+hair+'"/>'
      : '<path d="M31 51q5-23 29-23t29 23q-8-12-29-12t-29 12Z" fill="'+hair+'"/>';
    let eyes, mouth, brows='', cheekOp='.5';
    if (mood==='correct') {
      eyes = '<path d="M42 59q7-9 14 0M64 59q7-9 14 0" stroke="#2a3342" stroke-width="3.4" fill="none" stroke-linecap="round"/>';
      mouth = '<path d="M47 73q13 15 26 0q-13 7-26 0Z" fill="#b0503f"/>';
      cheekOp = '.8';
    } else if (mood==='wrong') {
      eyes = '<circle cx="49" cy="59" r="4.4" fill="#2a3342"/><circle cx="71" cy="59" r="4.4" fill="#2a3342"/>';
      mouth = '<path d="M51 79q9-5 18 0" stroke="#b0503f" stroke-width="3" fill="none" stroke-linecap="round"/>';
      brows = '<path d="M43 50l12 3M77 50l-12 3" stroke="'+(female?'#5a3d28':'#20160e')+'" stroke-width="2.6" stroke-linecap="round" fill="none"/>';
    } else if (mood==='think') {
      eyes = '<circle cx="49" cy="59" r="4.4" fill="#2a3342"/><circle cx="71" cy="59" r="4.4" fill="#2a3342"/>'
           + '<circle cx="50.4" cy="57.6" r="1.3" fill="#fff"/><circle cx="72.4" cy="57.6" r="1.3" fill="#fff"/>';
      mouth = '<path d="M53 76h14" stroke="#b0503f" stroke-width="3" fill="none" stroke-linecap="round"/>';
    } else { // idle
      eyes = '<circle cx="49" cy="59" r="4.6" fill="#2a3342"/><circle cx="50.4" cy="57.6" r="1.4" fill="#fff"/>'
           + '<circle cx="71" cy="59" r="4.6" fill="#2a3342"/><circle cx="72.4" cy="57.6" r="1.4" fill="#fff"/>';
      mouth = '<path d="M50 74q10 8 20 0" stroke="#b0503f" stroke-width="3" fill="none" stroke-linecap="round"/>';
    }
    const glasses = a.glasses
      ? '<g fill="none" stroke="#20242c" stroke-width="2.4"><circle cx="49" cy="59" r="8.6"/><circle cx="71" cy="59" r="8.6"/><path d="M57.6 59h4.8M40.4 56l-6-2M79.6 56l6-2" stroke-linecap="round"/></g>'
      : '';
    const cheeks = '<circle cx="41" cy="67" r="5" fill="#ff9d9d" opacity="'+cheekOp+'"/><circle cx="79" cy="67" r="5" fill="#ff9d9d" opacity="'+cheekOp+'"/>';
    return '<svg viewBox="0 0 120 120">'+back+shoulders+faceBase+bangs+cheeks+eyes+brows+glasses+mouth+'</svg>';
  }
  const COACH_OK = ['정답이에요! 잘하셨어요 🎉','멋져요, 맞았어요! 👏','역시! 좋은 감각이에요 ✨','완벽해요! 계속 가요 🌟'];

  /* ============================================================
     탭 라우팅
     ============================================================ */
  const RENDER = { village:renderVillage, my:renderMy, brain:renderBrain, avatar:renderAvatar, coop:renderCoop, rank:renderRank, reward:renderReward };
  const TITLES = { village:'우*수 정원', my:'마이페이지', brain:'두뇌 챌린지', avatar:'옷장 · 반려동물', coop:'함께하기', rank:'랭킹', reward:'리워드 상점' };

  function setTab(tab){
    if (isSleepTime()) { showSleep(); return; }
    if (villageCleanup){ villageCleanup(); villageCleanup=null; } // 개인/공용 마을 정리 (req15)
    activeTab = tab;
    if (tab!=='brain') brain.active=false;
    $('#topTitle').textContent = TITLES[tab] || '브레인팜';
    document.querySelectorAll('.tab').forEach(b=>b.classList.toggle('active', b.dataset.tab===tab));
    app.classList.toggle('flush', tab==='village');
    (RENDER[tab]||renderVillage)();
    app.scrollTop=0; window.scrollTo({top:0});
    touchPlay();
  }
  document.querySelectorAll('.tab').forEach(b=>b.addEventListener('click',()=>setTab(b.dataset.tab)));

  /* ============================================================
     1) 3D 마을 (동물의 숲 스타일, three.js)
     ============================================================ */
  function renderVillage(){
    app.innerHTML =
      '<div class="village-wrap">'+
        '<div id="villageCanvas"></div>'+
        '<div class="vil-hud">'+
          '<button class="vil-tag mission-tag" id="missionBtn" type="button">🎯 오늘의 나의 미션</button>'+
          '<span class="vil-tag">🪙 '+nf(state.coins)+'</span>'+
        '</div>'+
        // 노란색 작물 가방 버튼 (req17)
        '<button class="bag-btn" id="bagBtn" type="button" title="내 작물 가방">🎒 <span class="bag-badge">0</span></button>'+
        '<div class="sail-banner" id="sailBanner">⛵ 항해 중 · 제주 바다에서 한라산 풍경을 둘러보세요</div>'+
        '<div class="vil-prompt hidden" id="vilPrompt">🌱 도착!</div>'+
        '<div class="move-hint" id="moveHint">🎮 PC: ↑↓ 앞/뒤 · ←→ 돌면서 이동 · 클릭 이동 · 먼 섬/오름 클릭=친구 정원 · 📱 밀어서 이동</div>'+
        // 배치 편집 버튼 (req22)
        '<button class="edit-btn" id="editBtn" type="button" title="배치 편집">✋ 배치</button>'+
        // 배에서 내리기 버튼 (req20)
        '<button class="disembark-btn hidden" id="disembarkBtn" type="button">🚣 배에서 내리기</button>'+
        // 확인(A) → 음성 마이크 버튼 (req6)
        '<button class="act-btn" id="actBtn" title="음성"><svg viewBox="0 0 24 24"><path d="M12 15a3 3 0 0 0 3-3V6a3 3 0 0 0-6 0v6a3 3 0 0 0 3 3Zm5-3a5 5 0 0 1-10 0H5a7 7 0 0 0 6 6.9V21h2v-2.1A7 7 0 0 0 19 12h-2Z"/></svg><span>음성</span></button>'+
      '</div>';
    const container = $('#villageCanvas');
    // 오늘의 나의 미션 버튼 → 루틴 체크 모달 (req6)
    const mBtn=$('#missionBtn'); if(mBtn) mBtn.addEventListener('click',()=>{ Sound.tap(); openMission(); });
    // 작물 가방 버튼 (req17)
    const bagBtn=$('#bagBtn'); if(bagBtn) bagBtn.addEventListener('click',()=>{ Sound.tap(); openBackpack('list'); });
    syncBagBadge();
    initVillage(container, { onPortal: visitFriendGarden }).then(cleanup => { villageCleanup = cleanup; }); // req11
    setTimeout(()=>{ const h=$('#moveHint'); if(h) h.style.display='none'; }, 6000);
  }

  /* ── 친구 정원 방문 (먼 섬·오름 클릭으로 연결, req11) ── */
  const FRIEND_LAYOUTS = {}; // 친구 정원 배치(세션 내 유지)
  function visitFriendGarden(name){
    if(!name) return;
    if (villageCleanup){ villageCleanup(); villageCleanup=null; }
    if(!FRIEND_LAYOUTS[name]) FRIEND_LAYOUTS[name]={};
    app.classList.add('flush');
    $('#topTitle').textContent = name+' 님의 정원';
    toast('⛵ '+name+' 님의 정원에 놀러왔어요');
    app.innerHTML =
      '<div class="village-wrap">'+
        '<div id="villageCanvas"></div>'+
        '<div class="vil-hud">'+
          '<span class="vil-tag">🌷 '+name+' 님의 정원</span>'+
          '<span class="vil-tag">🪙 '+nf(state.coins)+'</span>'+
        '</div>'+
        '<div class="sail-banner" id="sailBanner">⛵ 항해 중 · 제주 바다를 둘러보세요</div>'+
        '<div class="vil-prompt hidden" id="vilPrompt">🌱 도착!</div>'+
        '<div class="move-hint" id="moveHint">🎮 PC: 방향키·클릭 이동 · 📱 밀어서 이동</div>'+
        '<button class="edit-btn" id="editBtn" type="button" title="배치 편집">✋ 배치</button>'+
        '<button class="disembark-btn hidden" id="disembarkBtn" type="button">🚣 배에서 내리기</button>'+
        '<button class="act-btn" id="actBtn" title="음성"><svg viewBox="0 0 24 24"><path d="M12 15a3 3 0 0 0 3-3V6a3 3 0 0 0-6 0v6a3 3 0 0 0 3 3Zm5-3a5 5 0 0 1-10 0H5a7 7 0 0 0 6 6.9V21h2v-2.1A7 7 0 0 0 19 12h-2Z"/></svg><span>음성</span></button>'+
        '<button class="common-exit" id="commonExit" type="button">← 내 정원으로</button>'+
      '</div>';
    const container = $('#villageCanvas');
    const ex=$('#commonExit'); if(ex) ex.addEventListener('click',()=>{ Sound.tap(); setTab('village'); });
    initVillage(container, { communal:true, layout: FRIEND_LAYOUTS[name] }).then(cleanup => { villageCleanup = cleanup; });
    setTimeout(()=>{ const h=$('#moveHint'); if(h) h.style.display='none'; }, 6000);
  }

  async function initVillage(container, opts){
    opts = opts || {};
    const LAYOUT = opts.layout || state.layout;   // 배치 좌표 네임스페이스 (개인/공용 분리, req13,15)
    const COMMUNAL = !!opts.communal;             // 공용 마을 여부 (req15)
    const onPortal = opts.onPortal;               // 먼 섬·오름 클릭 시 친구 정원으로 이동하는 콜백 (req11)
    let THREE;
    try {
      THREE = await import('https://unpkg.com/three@0.160.0/build/three.module.js');
    } catch(e){
      container.innerHTML = '<div class="vil-fallback"><div style="font-size:52px">🌿</div>'+
        '<h3>3D 정원을 불러오지 못했어요</h3>'+
        '<p class="tiny">인터넷 연결 시 제주도 느낌의 나만의 3D 정원이 나타납니다.<br>지금은 오프라인 폴백 화면이에요. 아래 버튼으로 작물을 볼 수 있어요.</p>'+
        '<button class="primary-button" id="fbFarm" style="margin-top:12px">🌱 스마트팜 작물 보기</button></div>';
      const b=$('#fbFarm'); if(b) b.addEventListener('click',()=>openFarm(0));
      return ()=>{};
    }

    // 효과음(바람) 시작 (req19)
    Sound.resume(); Sound.windStart();

    const W = container.clientWidth || 400, H = container.clientHeight || 420;
    const scene = new THREE.Scene();
    scene.background = new THREE.Color('#bfe6f2');
    scene.fog = new THREE.Fog('#cfeaf2', 34, 78);

    const camera = new THREE.PerspectiveCamera(55, W/H, 0.1, 200);
    const renderer = new THREE.WebGLRenderer({ antialias:true });
    renderer.setPixelRatio(Math.min(2, window.devicePixelRatio||1));
    renderer.setSize(W, H);
    container.appendChild(renderer.domElement);

    // 동물의 숲 스타일: 부드러운 카툰(툰) 셰이딩 재질 (req25)
    const toon = (color)=> new THREE.MeshToonMaterial({ color });
    const GROUND_Y = 0.2; // 캐릭터 발 높이 보정 (발 깜빡임 방지, req9)

    // 조명 (따뜻한 제주 햇살)
    scene.add(new THREE.HemisphereLight('#ffffff', '#8fbf72', 1.0));
    const sun = new THREE.DirectionalLight('#fff2cf', 1.05);
    sun.position.set(8, 20, 6); scene.add(sun);
    scene.add(new THREE.AmbientLight('#ffffff', 0.35));

    // 섬(원형 잔디) + 모래 + 바다
    const island = new THREE.Mesh(new THREE.CylinderGeometry(16,16,1,60), toon('#89cf67'));
    island.position.y=-0.5; scene.add(island);
    const beach = new THREE.Mesh(new THREE.CylinderGeometry(18,18,0.6,60), toon('#f0e0a6'));
    beach.position.y=-0.75; scene.add(beach);
    const water = new THREE.Mesh(new THREE.CircleGeometry(90,64), toon('#4ec1e6'));
    water.rotation.x=-Math.PI/2; water.position.y=-1.05; scene.add(water);

    const swayers=[]; // 바람에 흔들리는 오브젝트 모음
    const friendTags=[]; // 공용 마을 친구 이름표 (req15)
    const portals=[];  // req11: 클릭하면 친구 정원으로 연결되는 먼 섬·오름
    const portalTags=[]; // req10: 각 섬·오름 위에 뜨는 '어느 친구네 집' 이름표
    const treeGroups=[]; // req7: 시야를 가릴 수 있는 나무들(가림 시 반투명 처리)
    let windmillBlades=null; // req8: 집 주변 풍차 날개(회전 애니메이션)
    const houseDecor=[]; // 요구사항9-6: 배치(드래그) 대상에 포함할 집 주변 꾸미기 소품들
    const FRIEND_NAMES=['복순','영호','미자','상철','정순']; // req11 연결 대상

    // ── 제주 한라산 + 원경 풍경 (req18,19) ──
    function hallasan(){
      const g=new THREE.Group();
      const base=new THREE.Mesh(new THREE.ConeGeometry(20,22,28), toon('#5f9e57')); base.position.y=9; g.add(base);
      const mid=new THREE.Mesh(new THREE.ConeGeometry(12,15,26), toon('#6fae62')); mid.position.y=14; g.add(mid);
      const snow=new THREE.Mesh(new THREE.ConeGeometry(5.5,6,24), toon('#f4f7fb')); snow.position.y=21; g.add(snow);
      // 백록담 분화구 느낌
      const crater=new THREE.Mesh(new THREE.CylinderGeometry(2.4,2.4,0.6,20), toon('#cfe6ee')); crater.position.y=23.4; g.add(crater);
      g.position.set(0,-1,-58); scene.add(g); return g;
    }
    hallasan();
    // 원경 오름(작은 언덕들) — 다양한 제주 풍경 (req19)
    [['#6fae5f',-40,-30,10,7],['#7cb86a',34,-34,12,9],['#67a558',-52,4,8,6],['#77b263',50,10,9,7],['#6aa95a',20,-52,11,8],['#72b060',-30,-48,9,6]].forEach(([c,x,z,r,h],i)=>{
      const hill=new THREE.Mesh(new THREE.SphereGeometry(r,20,16,0,Math.PI*2,0,Math.PI/2), toon(c));
      hill.scale.y=h/r; hill.position.set(x,-1,z);
      if(onPortal){
        const nm=FRIEND_NAMES[i%FRIEND_NAMES.length];
        hill.userData.portal={name:nm}; portals.push(hill); // req11
        const lbl=new THREE.Mesh(new THREE.PlaneGeometry(7,3.9), new THREE.MeshBasicMaterial({map:signTexture('🏡',nm+' 님 집'),transparent:true})); // req10
        lbl.position.set(x, h+2, z); scene.add(lbl); portalTags.push(lbl);
      }
      scene.add(hill);
    });
    // 원경 작은 섬들 (바다에 떠 있는 제주 부속섬, req18,19)
    [[ -34,34],[38,30],[-44,-14],[46,-20],[10,46],[-16,44]].forEach(([x,z],i)=>{
      const g=new THREE.Group();
      const land=new THREE.Mesh(new THREE.CylinderGeometry(3.4,4,1.2,18), toon('#8bcc6a')); land.position.y=-0.4; g.add(land);
      const hill=new THREE.Mesh(new THREE.SphereGeometry(2.4,14,12,0,Math.PI*2,0,Math.PI/2), toon('#6fae5f')); hill.scale.y=1.4; hill.position.y=0.1; g.add(hill);
      const tr=new THREE.Mesh(new THREE.ConeGeometry(1,2.4,10), toon('#3f9d4a')); tr.position.set(1,1.4,0.6); g.add(tr);
      g.position.set(x,0,z);
      if(onPortal){
        const nm=FRIEND_NAMES[(i+2)%FRIEND_NAMES.length];
        g.userData.portal={name:nm}; portals.push(g); // req11
        const lbl=new THREE.Mesh(new THREE.PlaneGeometry(5.5,3.1), new THREE.MeshBasicMaterial({map:signTexture('🏡',nm+' 님 집'),transparent:true})); // req10
        lbl.position.set(x, 5, z); scene.add(lbl); portalTags.push(lbl);
      }
      scene.add(g);
    });
    // 구름 (원경 하늘)
    [[ -20,20,-30],[24,22,-40],[0,26,-50],[-30,18,10]].forEach(([x,y,z])=>{
      const cl=new THREE.Group();
      for(let i=0;i<3;i++){ const p=new THREE.Mesh(new THREE.SphereGeometry(2.2-i*0.3,12,10), toon('#ffffff')); p.position.set(i*2.4-2.4,Math.sin(i)*0.4,0); cl.add(p); }
      cl.position.set(x,y,z); scene.add(cl);
    });

    // ── 나무: 실제 나무처럼 층층이 (req14, 동물의 숲 스타일 req25) ──
    function gamgyulTree(x,z){
      const g=new THREE.Group();
      const trunk=new THREE.Mesh(new THREE.CylinderGeometry(0.26,0.42,2.4,10), toon('#8a5a34'));
      trunk.position.y=1.2; g.add(trunk);
      const crown=new THREE.Group(); crown.position.y=3.0;
      // 여러 겹의 잎 덩어리 → 실제 나무 수관
      [[0,0,0,1.5,'#3f9d4a'],[ -0.9,0.5,0.3,1.0,'#47a851'],[0.9,0.5,-0.3,1.0,'#379143'],[0,1.1,0,1.05,'#4bad55'],[0.2,0.4,0.9,0.9,'#42a04c']].forEach(([lx,ly,lz,r,c])=>{
        const b=new THREE.Mesh(new THREE.SphereGeometry(r,14,14), toon(c)); b.position.set(lx,ly,lz); crown.add(b);
      });
      for(let i=0;i<8;i++){ // 감귤
        const o=new THREE.Mesh(new THREE.SphereGeometry(0.22,10,10), toon('#f59122'));
        const a=i/8*Math.PI*2; o.position.set(Math.cos(a)*1.35, Math.sin(i*1.7)*0.7, Math.sin(a)*1.35); crown.add(o);
      }
      g.add(crown); g.position.set(x,0,z); scene.add(g);
      swayers.push({obj:crown, base:0, amp:0.05, ph:x+z});
      return g;
    }
    function palm(x,z){
      const g=new THREE.Group();
      // 살짝 휜 줄기 (여러 마디)
      const trunk=new THREE.Group();
      for(let i=0;i<5;i++){ const seg=new THREE.Mesh(new THREE.CylinderGeometry(0.2-i*0.02,0.28-i*0.02,0.8,8), toon('#b0824f')); seg.position.set(Math.sin(i*0.4)*0.25, 0.4+i*0.72, 0); seg.rotation.z=-Math.sin(i*0.4)*0.16; trunk.add(seg); }
      g.add(trunk);
      const top=new THREE.Group(); top.position.set(Math.sin(2)*0.25,3.9,0);
      for(let i=0;i<7;i++){ const fr=new THREE.Mesh(new THREE.ConeGeometry(0.38,2.6,6), toon('#4aa35a')); fr.rotation.z=Math.PI/2.3; fr.rotation.y=i/7*Math.PI*2; fr.translateY(1.2); top.add(fr); }
      const coco=new THREE.Mesh(new THREE.SphereGeometry(0.5,12,12), toon('#3f8f4c')); top.add(coco);
      g.add(top); g.position.set(x,0,z); scene.add(g);
      swayers.push({obj:top, base:0, amp:0.08, ph:x-z});
      return g;
    }

    // ── 꽃 모양 (도형 동그라미 → 꽃, req23) ──
    const flowerGeoPetal=new THREE.SphereGeometry(0.13,8,8);
    const flowerGeoCore=new THREE.SphereGeometry(0.09,8,8);
    const coreMat=toon('#ffd34d');
    function makeFlower(color){
      const f=new THREE.Group();
      const petalMat=toon(color);
      for(let p=0;p<5;p++){ const pet=new THREE.Mesh(flowerGeoPetal, petalMat); pet.scale.set(1,0.4,1.3); const a=p/5*Math.PI*2; pet.position.set(Math.cos(a)*0.16,0,Math.sin(a)*0.16); f.add(pet); }
      const core=new THREE.Mesh(flowerGeoCore, coreMat); core.position.y=0.04; f.add(core);
      const stem=new THREE.Mesh(new THREE.CylinderGeometry(0.02,0.02,0.34,6), toon('#4f9d43')); stem.position.y=-0.18; f.add(stem);
      return f;
    }
    for(let i=0;i<44;i++){
      const fx=(Math.random()*2-1)*13, fz=(Math.random()*2-1)*13;
      if(Math.hypot(fx,fz)>13.5) continue;
      const fl=makeFlower(Math.random()<0.6?'#f4d13a':(Math.random()<0.6?'#ff8ab0':'#e2647c'));
      fl.position.set(fx,0.35,fz); fl.rotation.y=Math.random()*Math.PI; scene.add(fl);
    }

    // 돌하르방 (제주 상징 석상)
    function dolhareubang(x,z){
      const g=new THREE.Group();
      const bodyMat=toon('#8d9298');
      const bd=new THREE.Mesh(new THREE.CylinderGeometry(0.55,0.7,1.5,12), bodyMat); bd.position.y=0.75; g.add(bd);
      const hd=new THREE.Mesh(new THREE.SphereGeometry(0.55,14,14), bodyMat); hd.position.y=1.7; g.add(hd);
      const hat=new THREE.Mesh(new THREE.CylinderGeometry(0.42,0.5,0.5,12), bodyMat); hat.position.y=2.15; g.add(hat);
      const nose=new THREE.Mesh(new THREE.ConeGeometry(0.12,0.28,8), toon('#7d8288')); nose.position.set(0,1.65,0.5); nose.rotation.x=Math.PI/2; g.add(nose);
      const eL=new THREE.Mesh(new THREE.SphereGeometry(0.1,8,8), toon('#4a4f55')); eL.position.set(-0.2,1.8,0.46); g.add(eL);
      const eR=eL.clone(); eR.position.x=0.2; g.add(eR);
      g.position.set(x,0,z); scene.add(g); return g;
    }
    const dol1=dolhareubang(-3.2,-9.4), dol2=dolhareubang(-8.8,-9.4);

    // 집 (나만의 정원 집, 동물의 숲 스타일)
    const house = new THREE.Group();
    const hbody = new THREE.Mesh(new THREE.BoxGeometry(4,3,4), toon('#f6eccf'));
    hbody.position.y=1.5; house.add(hbody);
    const roof = new THREE.Mesh(new THREE.ConeGeometry(3.3,2,4), toon('#d1633f'));
    roof.position.y=4; roof.rotation.y=Math.PI/4; house.add(roof);
    const door = new THREE.Mesh(new THREE.BoxGeometry(1,1.6,0.12), toon('#8a5a34'));
    door.position.set(0,0.8,2.02); house.add(door);
    const win = new THREE.Mesh(new THREE.BoxGeometry(0.9,0.9,0.1), toon('#bfe3f0'));
    win.position.set(-1.2,1.7,2.02); house.add(win);
    house.position.set(-6.5,0,-9); scene.add(house);

    // ── 집 주변 풍경: 산·섬 말고 다양한 소품으로 채우기 (req8) ──
    // 요구사항9-6: 각 소품을 그룹 단위로 만들어 배치(드래그) 대상(houseDecor)에 등록
    (function houseSurroundings(){
      const hx=-6.5, hz=-9;
      function place(g,x,z,rot){ g.position.set(x,0,z); if(rot) g.rotation.y=rot; scene.add(g); houseDecor.push(g); return g; }
      // 제주 현무암 돌담 (낮게 둘러 시야는 안 가림)
      const wallMat=toon('#7d8084');
      function stoneWall(x,z,len,rot){
        const w=new THREE.Group();
        for(let i=0;i<len;i++){
          const s=new THREE.Mesh(new THREE.SphereGeometry(0.26+(i%2)*0.05,8,6), wallMat); s.position.set(i*0.44-len*0.22,0.22+(i%2)*0.05,0); s.scale.set(1,0.8,1); w.add(s);
          const s2=new THREE.Mesh(new THREE.SphereGeometry(0.2,8,6), wallMat); s2.position.set(i*0.44-len*0.22,0.5,0.02); w.add(s2);
        }
        place(w,x,z,rot);
      }
      stoneWall(hx, hz-3.1, 8, 0);             // 집 뒤 돌담
      stoneWall(hx-3.6, hz-0.5, 5, Math.PI/2); // 집 왼쪽 돌담
      // 작은 연못 + 오리 (한 그룹)
      const pondG=new THREE.Group();
      const pond=new THREE.Mesh(new THREE.CircleGeometry(1.5,26), toon('#5fb8d6')); pond.rotation.x=-Math.PI/2; pond.position.y=0.06; pondG.add(pond);
      const duck=new THREE.Group();
      duck.add(new THREE.Mesh(new THREE.SphereGeometry(0.2,12,12),toon('#fafafa')));
      const dh=new THREE.Mesh(new THREE.SphereGeometry(0.12,10,10),toon('#fafafa')); dh.position.set(0.16,0.14,0); duck.add(dh);
      const bk=new THREE.Mesh(new THREE.ConeGeometry(0.05,0.12,8),toon('#e6a23c')); bk.rotation.z=-Math.PI/2; bk.position.set(0.3,0.14,0); duck.add(bk);
      duck.position.set(0,0.24,0); pondG.add(duck);
      place(pondG,hx+4.4,hz+0.6);
      // 풍차(제주 바람) — 뒤쪽 코너, 날개는 loop에서 회전
      const mill=new THREE.Group();
      const pole=new THREE.Mesh(new THREE.CylinderGeometry(0.1,0.15,2.6,10),toon('#cdba91')); pole.position.y=1.3; mill.add(pole);
      const blades=new THREE.Group(); blades.position.set(0,2.5,0.2);
      for(let i=0;i<4;i++){ const bg=new THREE.Group(); const bl=new THREE.Mesh(new THREE.BoxGeometry(0.14,1.05,0.03),toon('#efe3c2')); bl.position.y=0.55; bg.add(bl); bg.rotation.z=i*Math.PI/2; blades.add(bg); }
      mill.add(blades); place(mill,hx-5.0,hz-2.4); windmillBlades=blades;
      // 나무 벤치
      const bench=new THREE.Group();
      const seatb=new THREE.Mesh(new THREE.BoxGeometry(1.6,0.12,0.5),toon('#a9773f')); seatb.position.set(0,0.45,0); bench.add(seatb);
      [-0.7,0.7].forEach(lx=>{ const legb=new THREE.Mesh(new THREE.BoxGeometry(0.12,0.45,0.12),toon('#8a5f30')); legb.position.set(lx,0.22,0); bench.add(legb); });
      const backb=new THREE.Mesh(new THREE.BoxGeometry(1.6,0.4,0.1),toon('#a9773f')); backb.position.set(0,0.7,-0.2); bench.add(backb);
      place(bench,hx+2.8,hz-1.4,-0.4);
      // 꽃밭 화단 (여러 색 꽃) — 각 화단을 한 그룹으로
      [[hx+1.8,hz+1.8],[hx-1.9,hz+1.6]].forEach(([bxp,bzp])=>{
        const bedG=new THREE.Group();
        const box=new THREE.Mesh(new THREE.BoxGeometry(1.4,0.35,0.6),toon('#b07a44')); box.position.y=0.2; bedG.add(box);
        for(let k=0;k<4;k++){ const fl=makeFlower(['#f4d13a','#ff8ab0','#e2647c','#b98cf0'][k]); fl.position.set(-0.5+k*0.33,0.5,0); fl.scale.setScalar(0.9); bedG.add(fl); }
        place(bedG,bxp,bzp);
      });
      // 관목 덤불 (각각 그룹)
      [[hx-2.8,hz-1.7],[hx+3.6,hz-2.3],[hx-1.4,hz-2.7]].forEach(([bx,bz])=>{
        const bushG=new THREE.Group();
        const bush=new THREE.Mesh(new THREE.SphereGeometry(0.5,12,10),toon('#5aa84e')); bush.scale.set(1,0.7,1); bush.position.y=0.35; bushG.add(bush);
        place(bushG,bx,bz);
      });
    })();

    // ── 팻말 텍스트 텍스처 (req8) ──
    function signTexture(emoji, name){
      const c=document.createElement('canvas'); c.width=256; c.height=140; const x=c.getContext('2d');
      x.fillStyle='#fffdf3'; x.fillRect(0,0,256,140);
      x.strokeStyle='#caa877'; x.lineWidth=8; x.strokeRect(4,4,248,132);
      x.textAlign='center'; x.textBaseline='middle';
      x.font='54px sans-serif'; x.fillText(emoji, 128, 54);
      x.fillStyle='#3a2a10'; x.font='bold 34px sans-serif'; x.fillText(name, 128, 108);
      const tex=new THREE.CanvasTexture(c); tex.anisotropy=4; return tex;
    }

    // ── 작물 밭 + 팻말 (req8) ──
    const plots = [];
    const defFieldPos = [ [6,-3], [9,1], [4,4], [1,7] ];
    function makeField(i){
      const grp=new THREE.Group();
      const soilMat=toon('#6b4326');
      for(let r=-1;r<=1;r++){ const ridge=new THREE.Mesh(new THREE.BoxGeometry(2.6,0.35,0.7), soilMat); ridge.position.set(0,0.18,r*0.85); grp.add(ridge); }
      const base=new THREE.Mesh(new THREE.BoxGeometry(2.9,0.2,2.9), toon('#5a3a22')); base.position.y=0.05; grp.add(base);
      const field=new THREE.Group();
      const leafMat=toon('#4d9d43'); const fruitMat=toon(CROPS[i].color);
      const st=state.farm[i]?state.farm[i].stage:0; const scale=0.4+st*0.22;
      for(let rx=-1;rx<=1;rx++) for(let rz=-1;rz<=1;rz++){
        const plant=new THREE.Group(); const nLeaves=2+st;
        for(let l=0;l<nLeaves;l++){ const leaf=new THREE.Mesh(new THREE.SphereGeometry(0.16,8,8), leafMat); leaf.scale.set(1,0.5,1.6); const a=l/nLeaves*Math.PI*2; leaf.position.set(Math.cos(a)*0.16, 0.35+l*0.06, Math.sin(a)*0.16); plant.add(leaf); }
        if(st>=3){ const fr=new THREE.Mesh(new THREE.SphereGeometry(0.13,8,8), fruitMat); fr.position.y=0.4; plant.add(fr); }
        plant.position.set(rx*0.8, 0.28, rz*0.8); plant.scale.setScalar(scale); field.add(plant);
      }
      grp.add(field); swayers.push({obj:field, base:0, amp:0.04, ph:i*2});
      // 팻말: 기둥 + 작물 이름판 (req8)
      const post=new THREE.Mesh(new THREE.CylinderGeometry(0.06,0.06,1.0,8), toon('#9a6b3d')); post.position.set(-1.1,0.5,1.55); grp.add(post);
      const board=new THREE.Mesh(new THREE.PlaneGeometry(1.5,0.82), new THREE.MeshBasicMaterial({map:signTexture(CROPS[i].emoji,CROPS[i].name), side:THREE.DoubleSide}));
      board.position.set(-0.35,1.05,1.55); grp.add(board);
      return grp;
    }
    defFieldPos.forEach((p,i)=>{
      const grp=makeField(i);
      const saved=LAYOUT['f'+i];
      const px=saved?saved[0]:p[0], pz=saved?saved[1]:p[1];
      grp.position.set(px,0,pz); grp.userData.dragKey='f'+i; scene.add(grp);
      plots.push({ idx:i, pos:grp.position, group:grp }); // pos는 group.position 참조 → 편집 시 자동 동기화
    });

    // ── 나룻배 (req21) : 납작한 목선 + 노 ──
    const boat=new THREE.Group();
    const boatMat=toon('#a9773f'), boatDark=toon('#8a5f30');
    const hullBottom=new THREE.Mesh(new THREE.BoxGeometry(1.5,0.35,4.0), boatMat); hullBottom.position.y=0.15; boat.add(hullBottom);
    // 뱃전(양옆 판)
    const sideL=new THREE.Mesh(new THREE.BoxGeometry(0.14,0.5,4.0), boatDark); sideL.position.set(-0.72,0.42,0); boat.add(sideL);
    const sideR=sideL.clone(); sideR.position.x=0.72; boat.add(sideR);
    // 뾰족한 앞/뒤
    const bow=new THREE.Mesh(new THREE.ConeGeometry(0.75,1.1,4), boatMat); bow.rotation.x=-Math.PI/2; bow.rotation.y=Math.PI/4; bow.position.set(0,0.32,2.4); bow.scale.set(1,0.45,1); boat.add(bow);
    const stern=bow.clone(); stern.position.z=-2.4; stern.rotation.x=Math.PI/2; boat.add(stern);
    // 가로 좌판 2개
    [0.7,-0.7].forEach(z=>{ const seat=new THREE.Mesh(new THREE.BoxGeometry(1.5,0.1,0.4), boatDark); seat.position.set(0,0.5,z); boat.add(seat); });
    // 노 2개 (노 젓기 애니메이션 대상, req3)
    const oars=[];
    [[-0.95,-0.5],[0.95,-0.5]].forEach(([ox,oz],k)=>{ const oar=new THREE.Group(); const shaft=new THREE.Mesh(new THREE.CylinderGeometry(0.05,0.05,2.0,8), toon('#7a5230')); shaft.rotation.z=Math.PI/2.6; shaft.position.set(ox*0.6,0.5,oz); oar.add(shaft); const blade=new THREE.Mesh(new THREE.BoxGeometry(0.06,0.4,0.6), toon('#8a5f30')); blade.position.set(ox*1.4,0.05,oz-0.2); oar.add(blade); oar.position.set(0,0.3,0.2); boat.add(oar); oars.push(oar); });
    const boatPos=new THREE.Vector3(15.5,-0.45,7); boat.position.copy(boatPos); scene.add(boat);

    // ── 3D 캐릭터 (참고 이미지 '여성/남성 누끼 정면' 반영, 발끝=원점 y=0, req8) ──
    // 여성: 회색 니트·갈색 웨이브 단발·볼터치 / 남성: 올리브 니트·검은머리·안경
    function buildCharacter(cfg){
      const g=new THREE.Group();
      // cfg가 있으면 그 설정으로(공용마을 친구용), 없으면 내 아바타로 생성 (req3)
      const a=cfg||state.avatar, skin=a.skin||SKINS[0], outfit=a.outfit||OUTFITS[0], hair=a.hair||HAIRS[0];
      const female = a.gender==='female';
      const hairMat=toon(hair), skinMat=toon(skin), knitMat=toon(outfit);

      // ── 다리 + 청바지 + 갈색 레인부츠 (원점=엉덩이, 아래로 뻗음 → 걷기 스윙 자연스럽게) ──
      const jeansMat=toon('#2f3d5e'), bootMat=toon('#6b5334'), bootDark=toon('#57432a');
      function leg(side){ const l=new THREE.Group(); l.position.set(side*0.2,1.15,0);
        const thigh=new THREE.Mesh(new THREE.CapsuleGeometry(0.17,0.44,6,10),jeansMat); thigh.position.y=-0.3; l.add(thigh);
        const boot=new THREE.Mesh(new THREE.CylinderGeometry(0.185,0.21,0.56,14),bootMat); boot.position.y=-0.8; l.add(boot);
        const foot=new THREE.Mesh(new THREE.BoxGeometry(0.32,0.18,0.5),bootMat); foot.position.set(0,-1.03,0.11); l.add(foot);
        const sole=new THREE.Mesh(new THREE.BoxGeometry(0.34,0.07,0.53),bootDark); sole.position.set(0,-1.12,0.11); l.add(sole);
        g.add(l); return l; }
      const legL=leg(-1), legR=leg(1);

      // ── 몸통(니트 스웨터) ──
      const torso=new THREE.Mesh(new THREE.CapsuleGeometry(female?0.42:0.46,0.5,8,16), knitMat);
      torso.position.y=1.5; torso.scale.z=0.78; g.add(torso);
      const hem=new THREE.Mesh(new THREE.CylinderGeometry(female?0.44:0.48,female?0.42:0.46,0.18,16), knitMat);
      hem.position.y=1.05; hem.scale.z=0.78; g.add(hem);
      const collar=new THREE.Mesh(new THREE.TorusGeometry(0.2,0.05,10,20), knitMat);
      collar.position.y=1.98; collar.rotation.x=Math.PI/2; collar.scale.set(1,0.8,1); g.add(collar);

      // ── 노란색 백팩 (등쪽 가방 + 양쪽 어깨 끈, req16) ──
      const bagMat=toon('#f2c200'), bagDark=toon('#e0ad00');
      const bag=new THREE.Mesh(new THREE.BoxGeometry(0.62,0.72,0.3), bagMat); bag.position.set(0,1.5,-0.42); g.add(bag);
      const bagLid=new THREE.Mesh(new THREE.BoxGeometry(0.64,0.24,0.32), bagDark); bagLid.position.set(0,1.8,-0.42); g.add(bagLid);
      [-1,1].forEach(s=>{ const strap=new THREE.Mesh(new THREE.BoxGeometry(0.08,0.66,0.08), bagMat); strap.position.set(s*0.22,1.6,0.34); strap.rotation.x=0.15; g.add(strap); });

      // ── 목 · 머리 · 귀 ──
      const neck=new THREE.Mesh(new THREE.CylinderGeometry(0.16,0.18,0.2,12), skinMat); neck.position.y=1.94; g.add(neck);
      const head=new THREE.Mesh(new THREE.SphereGeometry(0.56,24,24), skinMat);
      head.position.y=2.36; head.scale.set(0.95,1,0.92); g.add(head);
      [-1,1].forEach(s=>{ const ear=new THREE.Mesh(new THREE.SphereGeometry(0.1,10,10),skinMat); ear.position.set(s*0.53,2.32,0); ear.scale.set(0.7,1,0.7); g.add(ear); });

      // ── 머리카락 (성별 구분: 여성=웨이브 단발, 남성=짧은 머리) ──
      // req1,2: 머리카락(검정)은 '눈 위'까지만 덮고, 그 아래 얼굴은 손과 같은 피부색이 보이도록 앞머리 라인을 올림
      const cap=new THREE.Mesh(new THREE.SphereGeometry(0.6,24,24,0,Math.PI*2,0,Math.PI*(female?0.44:0.40)), hairMat);
      cap.position.y=2.4; cap.scale.set(1.02,1,1.02); g.add(cap);
      // req1,2: 뒤통수 쪽만 머리로 덮고, 앞얼굴~옆(눈에서 귀까지)은 손과 같은 피부색이 보이도록 뒤쪽 반구만 생성 (짱구 옆모습처럼)
      const backHair=new THREE.Mesh(new THREE.SphereGeometry(0.58,20,20,Math.PI,Math.PI,Math.PI*0.28,Math.PI*0.72), hairMat);
      backHair.position.set(0,2.3,-0.05); g.add(backHair);
      if(female){
        // 양옆 웨이브 볼륨 + 아래쪽 컬 (단발)
        [-1,1].forEach(s=>{
          const side=new THREE.Mesh(new THREE.CapsuleGeometry(0.17,0.42,6,10),hairMat);
          side.position.set(s*0.5,2.02,-0.02); side.rotation.z=s*0.12; g.add(side);
          const curl=new THREE.Mesh(new THREE.SphereGeometry(0.19,12,12),hairMat);
          curl.position.set(s*0.47,1.78,0.02); g.add(curl);
        });
      } else {
        // 앞머리 살짝 옆 가르마
        const bang=new THREE.Mesh(new THREE.SphereGeometry(0.6,20,20,0,Math.PI,0,Math.PI*0.4),hairMat);
        bang.position.set(0.03,2.52,0.04); bang.rotation.z=0.15; g.add(bang);
      }

      // ── 얼굴 (앞면 +z) ──
      const face=new THREE.Group(); face.position.set(0,2.34,0); g.add(face);
      const whiteMat=toon('#ffffff'), irisMat=toon('#3a2418'), glintMat=new THREE.MeshBasicMaterial({color:'#fff'});
      [-1,1].forEach(s=>{
        const white=new THREE.Mesh(new THREE.SphereGeometry(0.1,14,14),whiteMat); white.position.set(s*0.19,0.02,0.5); white.scale.set(1,1.2,0.5); face.add(white);
        const iris=new THREE.Mesh(new THREE.SphereGeometry(0.062,12,12),irisMat); iris.position.set(s*0.19,0.01,0.55); iris.scale.set(1,1.2,0.6); face.add(iris);
        const glint=new THREE.Mesh(new THREE.SphereGeometry(0.02,8,8),glintMat); glint.position.set(s*0.19+0.03,0.05,0.6); face.add(glint);
      });
      // 눈썹 (남성은 굵게)
      const browMat=toon(female?'#5a3d28':'#20160e'); const bw=female?0.032:0.05;
      [-1,1].forEach(s=>{ const b=new THREE.Mesh(new THREE.BoxGeometry(0.18,bw,0.04),browMat); b.position.set(s*0.19,0.2,0.53); b.rotation.z=s*-0.08; face.add(b); });
      // 코
      const nose=new THREE.Mesh(new THREE.SphereGeometry(0.06,10,10),skinMat); nose.position.set(0,-0.03,0.56); nose.scale.set(1,0.85,1); face.add(nose);
      // 볼터치
      const cheekMat=new THREE.MeshBasicMaterial({color:'#ff9d9d',transparent:true,opacity:.5});
      [-1,1].forEach(s=>{ const c=new THREE.Mesh(new THREE.CircleGeometry(0.1,16),cheekMat); c.position.set(s*0.3,-0.11,0.48); face.add(c); });
      // 입 (미소)
      const mouth=new THREE.Mesh(new THREE.TorusGeometry(0.09,0.024,8,16,Math.PI), toon('#b0503f')); mouth.position.set(0,-0.22,0.5); mouth.rotation.z=Math.PI; face.add(mouth);
      // 안경 (남성)
      if(a.glasses){ const gm=toon('#20242c');
        [-1,1].forEach(s=>{ const r=new THREE.Mesh(new THREE.TorusGeometry(0.135,0.024,10,20),gm); r.position.set(s*0.19,0.02,0.54); face.add(r); });
        const bridge=new THREE.Mesh(new THREE.BoxGeometry(0.11,0.024,0.024),gm); bridge.position.set(0,0.04,0.56); face.add(bridge);
        [-1,1].forEach(s=>{ const t=new THREE.Mesh(new THREE.BoxGeometry(0.16,0.02,0.02),gm); t.position.set(s*0.34,0.03,0.42); face.add(t); });
      }

      // ── 팔 (원점=어깨, 아래로 뻗음 → 스윙) ──
      function arm(side){ const armG=new THREE.Group(); armG.position.set(side*(female?0.48:0.53),1.92,0);
        const upper=new THREE.Mesh(new THREE.CapsuleGeometry(0.135,0.55,6,10),knitMat); upper.position.y=-0.32; armG.add(upper);
        const hand=new THREE.Mesh(new THREE.SphereGeometry(0.145,12,12),skinMat); hand.position.y=-0.72; hand.scale.set(1,1.15,0.85); armG.add(hand);
        g.add(armG); return armG; }
      const armL=arm(-1), armR=arm(1);

      // 발끝 최저점 ≈ y=0 (엉덩이 1.15 - 1.155) → group을 y=0에 두면 지면에 정확히 접지
      return { group:g, armL, armR, legL, legR };
    }
    // 정원 플레이어: 참고 이미지 기반 3D 캐릭터 (req8, 이전 2D 스프라이트 대체)
    const built = buildCharacter();
    const player = built.group;
    player.position.set(0,0,3);   // 발끝이 원점 → 지면(y=0)에 정확히 접지
    scene.add(player);

    // 공용 마을: 마을 친구들도 메인 캐릭터와 같은 방식(buildCharacter)으로 생성 (req3)
    if(COMMUNAL){
      [
        {skin:'#eec39a', outfit:'#3a72b8', hair:'#3a2a1c', gender:'female', glasses:false, fx:-6, fz:2,  nm:'복순'},
        {skin:'#f3cea2', outfit:'#5b8d3a', hair:'#141414', gender:'male',   glasses:true,  fx:6,  fz:-2, nm:'영호'},
        {skin:'#e8b891', outfit:'#d7644f', hair:'#5a3d28', gender:'female', glasses:false, fx:2,  fz:6,  nm:'미자'},
        {skin:'#c98d63', outfit:'#d99a25', hair:'#3a2a1c', gender:'male',   glasses:false, fx:-4, fz:-4, nm:'상철'},
      ].forEach(f=>{
        const fg = buildCharacter(f).group;         // 내 캐릭터와 동일한 골격·얼굴
        fg.position.set(f.fx, 0, f.fz);
        fg.rotation.y = Math.atan2(-f.fx, -f.fz);   // 마을 중앙을 바라봄
        const tag=new THREE.Mesh(new THREE.PlaneGeometry(1.1,0.6), new THREE.MeshBasicMaterial({map:signTexture('🙂',f.nm),transparent:true})); tag.position.set(0,3.2,0); fg.add(tag); friendTags.push(tag);
        scene.add(fg);
      });
    }

    // ── 반려동물 3D 모델 (몸통·꼬리·다리·귀, req11) ──
    function buildPet3D(type){
      const p=PETS.find(x=>x.type===type)||PETS[0];
      const g=new THREE.Group();
      const bodyMat=toon(p.body), earMat=toon(p.ear), bellyMat=toon(p.belly);
      if(type==='bird'){
        const body=new THREE.Mesh(new THREE.SphereGeometry(0.3,16,16),bodyMat); body.position.y=0.36; body.scale.set(1,0.9,1.2); g.add(body);
        const head=new THREE.Mesh(new THREE.SphereGeometry(0.18,14,14),bodyMat); head.position.set(0,0.62,0.16); g.add(head);
        const beak=new THREE.Mesh(new THREE.ConeGeometry(0.06,0.16,8),toon('#e6a23c')); beak.rotation.x=Math.PI/2; beak.position.set(0,0.62,0.36); g.add(beak);
        [-1,1].forEach(s=>{ const wing=new THREE.Mesh(new THREE.SphereGeometry(0.15,10,10),earMat); wing.scale.set(0.4,0.7,1); wing.position.set(s*0.28,0.38,0); g.add(wing); });
        [-1,1].forEach(s=>{ const leg=new THREE.Mesh(new THREE.CylinderGeometry(0.02,0.02,0.18,6),toon('#e6a23c')); leg.position.set(s*0.09,0.1,0.06); g.add(leg); });
        const tail=new THREE.Mesh(new THREE.ConeGeometry(0.12,0.28,8),earMat); tail.rotation.x=-Math.PI/2.4; tail.position.set(0,0.38,-0.32); g.add(tail);
        return g;
      }
      const body=new THREE.Mesh(new THREE.CapsuleGeometry(0.26,0.5,8,14),bodyMat); body.rotation.z=Math.PI/2; body.position.y=0.44; g.add(body);
      const belly=new THREE.Mesh(new THREE.CapsuleGeometry(0.19,0.42,6,12),bellyMat); belly.rotation.z=Math.PI/2; belly.position.set(0,0.34,0.08); g.add(belly);
      const head=new THREE.Mesh(new THREE.SphereGeometry(0.25,16,16),bodyMat); head.position.set(0.46,0.6,0); g.add(head);
      const snout=new THREE.Mesh(new THREE.SphereGeometry(0.12,10,10),bodyMat); snout.position.set(0.66,0.53,0); snout.scale.set(1,0.8,0.9); g.add(snout);
      const nose=new THREE.Mesh(new THREE.SphereGeometry(0.05,8,8),toon('#3a2a2a')); nose.position.set(0.77,0.54,0); g.add(nose);
      [-1,1].forEach(s=>{ const eye=new THREE.Mesh(new THREE.SphereGeometry(0.035,8,8),toon('#2a2a2a')); eye.position.set(0.6,0.66,s*0.11); g.add(eye); });
      const legs=[]; [[0.26,0.16],[0.26,-0.16],[-0.2,0.16],[-0.2,-0.16]].forEach(([lx,lz])=>{ const leg=new THREE.Mesh(new THREE.CylinderGeometry(0.07,0.06,0.4,8),bodyMat); leg.position.set(lx,0.2,lz); g.add(leg); legs.push(leg); });
      if(type==='dog'){ [-1,1].forEach(s=>{ const ear=new THREE.Mesh(new THREE.CapsuleGeometry(0.055,0.16,4,8),earMat); ear.position.set(0.42,0.72,s*0.18); ear.rotation.x=s*0.35; g.add(ear); }); }
      else if(type==='cat'){ [-1,1].forEach(s=>{ const ear=new THREE.Mesh(new THREE.ConeGeometry(0.1,0.2,4),earMat); ear.position.set(0.44,0.82,s*0.13); g.add(ear); }); }
      else if(type==='rabbit'){ [-1,1].forEach(s=>{ const ear=new THREE.Mesh(new THREE.CapsuleGeometry(0.055,0.34,4,8),earMat); ear.position.set(0.4,0.96,s*0.1); g.add(ear); }); }
      if(type==='rabbit'){ const tail=new THREE.Mesh(new THREE.SphereGeometry(0.12,10,10),toon('#ffffff')); tail.position.set(-0.5,0.5,0); g.add(tail); }
      else { const tail=new THREE.Mesh(new THREE.CapsuleGeometry(0.05,0.3,4,8),bodyMat); tail.position.set(-0.5,0.58,0); tail.rotation.z=type==='cat'?0.7:-0.5; g.add(tail); }
      g.userData.legs=legs;
      return g;
    }
    // 분양받은 모든 반려동물을 정원에 표시 (req12, 마리수 제한 없이)
    const gardenPets=[];
    function randPetTarget(){ return { x:(Math.random()*2-1)*13, z:(Math.random()*2-1)*13 }; }
    (state.pet.adopted||[]).forEach((pd,i)=>{
      const grp=buildPet3D(pd.type);
      const ang=i*1.7, rad=4+ (i%3);
      grp.position.set(Math.cos(ang)*rad, 0, Math.sin(ang)*rad);
      grp.userData.petId=pd.id; grp.userData.petStage=pd.stage;
      grp.scale.setScalar(0.7 + Math.min(5,pd.stage-1)*0.09); // 단계별 크기 (req22)
      scene.add(grp);
      gardenPets.push({ id:pd.id, type:pd.type, group:grp, phase:Math.random()*6.28, tgt:randPetTarget() });
    });

    // ── 이동 상태 ──
    const keys = { up:false, down:false, left:false, right:false };
    const touch = { active:false, x:0, z:0 };
    let heading = 0, walkPhase=0;
    let near = null;
    let sailing = false, sailAngle=0, sailHeading=0, sailElapsed=0, sailStartAngle=0, sailBannerTimer=null; // sailElapsed: 항해 경과 시간(초) (req3~9)
    let editMode = false; // 정원 배치 편집 (req13,22)
    let moveTarget = null; // PC 클릭 이동 목표 (req9)

    const onKey = (e,down)=>{
      const k=e.key.toLowerCase();
      if(k==='arrowup'||k==='w') keys.up=down;
      else if(k==='arrowdown'||k==='s') keys.down=down;
      else if(k==='arrowleft'||k==='a') keys.left=down;
      else if(k==='arrowright'||k==='d') keys.right=down;
      else if((k==='enter'||k===' ') && down){ doContext(); }
      else return;
      e.preventDefault();
    };
    const kd=(e)=>onKey(e,true), ku=(e)=>onKey(e,false);
    window.addEventListener('keydown',kd); window.addEventListener('keyup',ku);

    // ── 배치 편집: 드래그로 나무·밭 옮기기 (req22) ──
    const raycaster = new THREE.Raycaster();
    const groundPlane = new THREE.Plane(new THREE.Vector3(0,1,0), 0);
    const draggables = []; // {group} — userData.dragKey 로 저장
    let dragTarget = null;
    function ndc(e){ const r=cvEl.getBoundingClientRect(); return { x:((e.clientX-r.left)/r.width)*2-1, y:-((e.clientY-r.top)/r.height)*2+1 }; }
    function pickDraggable(e){
      const p=ndc(e); raycaster.setFromCamera(p, camera);
      const hits=raycaster.intersectObjects(draggables.map(d=>d.group), true);
      if(!hits.length) return null;
      let o=hits[0].object; while(o && o.userData.dragKey===undefined) o=o.parent;
      return o||null;
    }
    function moveTargetTo(e){
      const p=ndc(e); raycaster.setFromCamera(p, camera);
      const hit=new THREE.Vector3();
      if(raycaster.ray.intersectPlane(groundPlane, hit)){
        const x=clamp(hit.x,-14,14), z=clamp(hit.z,-14,14);
        dragTarget.position.x=x; dragTarget.position.z=z;
      }
    }
    function saveLayout(){
      const key=dragTarget.userData.dragKey;
      LAYOUT[key]=[Math.round(dragTarget.position.x*100)/100, Math.round(dragTarget.position.z*100)/100];
      save();
    }

    // 터치/마우스 입력: 모바일=상대 조이스틱, PC=클릭 이동(req9), 편집=드래그 배치
    const cvEl = renderer.domElement;
    let dragId=null, ox=0, oy=0, downX=0, downY=0, pType='mouse', moved=false;
    // req16: 반려동물을 누르면 반려동물 키우기 창이 열림
    function pickPetAt(e){
      if(!gardenPets.length) return false;
      const p=ndc(e); raycaster.setFromCamera(p,camera);
      const ph=raycaster.intersectObjects(gardenPets.map(g=>g.group),true);
      if(!ph.length) return false;
      let o=ph[0].object; while(o && o.userData.petId===undefined) o=o.parent;
      if(o && o.userData.petId){ openPetCare(o.userData.petId); return true; }
      return false;
    }
    function clickToMove(e){
      const p=ndc(e); raycaster.setFromCamera(p,camera);
      // req11: 먼 섬·오름을 클릭하면 그곳과 연결된 친구의 정원으로 이동
      if(onPortal && portals.length){
        const ph=raycaster.intersectObjects(portals,true);
        if(ph.length){ let o=ph[0].object; while(o && !(o.userData&&o.userData.portal)) o=o.parent; if(o&&o.userData.portal){ onPortal(o.userData.portal.name); return; } }
      }
      // req9: 집을 클릭하면 집 주변 아무 곳이 아니라 '집 앞(문 쪽)'으로만 이동
      const hh=raycaster.intersectObject(house,true);
      if(hh.length){ moveTarget=new THREE.Vector3(house.position.x, 0, house.position.z+3.2); return; }
      const hit=new THREE.Vector3();
      if(raycaster.ray.intersectPlane(groundPlane,hit)){
        moveTarget=new THREE.Vector3(clamp(hit.x,-14.5,14.5),0,clamp(hit.z,-14.5,14.5));
      }
    }
    const tStart=(e)=>{
      Sound.resume();
      if(editMode){ const t=pickDraggable(e); if(t){ dragTarget=t; dragId=e.pointerId; cvEl.setPointerCapture&&cvEl.setPointerCapture(e.pointerId); } return; }
      dragId=e.pointerId; pType=e.pointerType||'mouse'; downX=ox=e.clientX; downY=oy=e.clientY; moved=false;
      cvEl.setPointerCapture&&cvEl.setPointerCapture(e.pointerId);
      if(pType!=='mouse'){ touch.active=true; touch.x=0; touch.z=0; } // 모바일: 상대 조이스틱
    };
    const tMove=(e)=>{
      if(editMode){ if(dragTarget&&e.pointerId===dragId) moveTargetTo(e); return; }
      if(e.pointerId!==dragId) return;
      if(Math.abs(e.clientX-downX)+Math.abs(e.clientY-downY)>6) moved=true;
      if(pType!=='mouse' && touch.active){ const ddx=(e.clientX-ox)/40, ddy=(e.clientY-oy)/40; touch.x=clamp(ddx,-1,1); touch.z=clamp(ddy,-1,1); }
    };
    const tEnd=(e)=>{
      if(editMode){ if(dragTarget){ saveLayout(); toast('📍 배치를 저장했어요'); } dragTarget=null; dragId=null; return; }
      if(e.pointerId!==dragId) return;
      if(!moved && !sailing && pickPetAt(e)){ touch.active=false; touch.x=0; touch.z=0; dragId=null; return; } // req16: 반려동물 탭 → 키우기 창
      if(pType==='mouse' && !moved && !sailing) clickToMove(e); // PC: 클릭한 곳으로 이동 (req9)
      touch.active=false; touch.x=0; touch.z=0; dragId=null;
    };
    cvEl.addEventListener('pointerdown',tStart); cvEl.addEventListener('pointermove',tMove);
    cvEl.addEventListener('pointerup',tEnd); cvEl.addEventListener('pointercancel',tEnd);

    // 나무 배치 (편집 대상, req14,22)
    function addTree(kind,x,z,key){
      const g = kind==='palm'?palm(x,z):gamgyulTree(x,z);
      g.userData.dragKey=key; const saved=LAYOUT[key]; if(saved){ g.position.x=saved[0]; g.position.z=saved[1]; }
      // req7: 가림 처리를 위해 나무 재질을 반투명 가능 상태로 두고 목록에 등록
      g.traverse(o=>{ if(o.material){ o.material.transparent=true; o.material.opacity=1; } });
      treeGroups.push(g);
      draggables.push({group:g}); return g;
    }
    addTree('gam',-9,-6,'t0'); addTree('gam',10,5,'t1'); addTree('gam',-11,4,'t2'); addTree('gam',-5,10,'t3');
    addTree('palm',11,-7,'t4'); addTree('palm',0,-12,'t5');
    plots.forEach(pl=> draggables.push({group:pl.group})); // 밭도 편집 대상
    // 정원의 모든 아이템(돌하르방·집 등)도 자유 배치 (req13)
    function registerDrag(g,key){ g.userData.dragKey=key; const s=LAYOUT[key]; if(s){ g.position.x=s[0]; g.position.z=s[1]; } draggables.push({group:g}); }
    registerDrag(dol1,'dol0'); registerDrag(dol2,'dol1'); registerDrag(house,'house');
    // 요구사항9-6: 집 주변 꾸미기 소품(돌담·연못·풍차·벤치·화단·덤불)도 모두 배치 대상에 포함 (캐릭터 제외)
    houseDecor.forEach((g,i)=>registerDrag(g,'hd'+i));

    // ── HUD 참조 ──
    const actBtn = container.parentElement.querySelector('#actBtn');
    const promptEl = container.parentElement.querySelector('#vilPrompt');
    const sailBanner = container.parentElement.querySelector('#sailBanner');
    const disembarkBtn = container.parentElement.querySelector('#disembarkBtn');
    const editBtn = container.parentElement.querySelector('#editBtn');

    // 캐릭터가 대상 정면을 향하는지 (앞모습으로 접근했는지, req13)
    function facingFront(targetPos){
      const fwd=new THREE.Vector3(Math.sin(heading),0,Math.cos(heading));
      const dir=new THREE.Vector3(targetPos.x-player.position.x,0,targetPos.z-player.position.z).normalize();
      return fwd.dot(dir) > 0.35;
    }

    function doContext(){
      if(sailing){ disembark(); return; }
      if(editMode){ toast('배치 편집 중 · 나무·밭을 드래그해 옮겨요'); return; }
      if(!near){ toast('작물·집·배 근처로 가보세요'); return; }
      if(near.type==='plot'){
        openFarm(near.idx); // req4: 정면이 아니어도 작물 근처면 바로 열기
      }
      else if(near.type==='house') openHouse();
      else if(near.type==='boat') boardBoat();
    }
    const micFn = ()=>{
      if(!Voice.supported){ doContext(); return; }
      if(Voice.isActive()){ Voice.stop(); actBtn.classList.remove('listening'); return; }
      Sound.resume(); actBtn.classList.add('listening'); toast('🎙️ 말해보세요: 식물/게임/집/배/정원/배송');
      Voice.start((alts)=>{
        const s=alts.join(' ');
        if(/정원|돌아|나가|내려/.test(s) && sailing){ disembark(); }
        else if(/배송|택배|가방|받기/.test(s)){ openBackpack('list'); } // req24: 배송 관련 발화 → 작물 배송(가방)으로 연결
        else if(/배|항해|바다/.test(s)){ if(near&&near.type==='boat') boardBoat(); else toast('배 근처로 가보세요'); }
        else if(/집|실내|들어/.test(s)){ if(near&&near.type==='house') openHouse(); else toast('집 근처로 가보세요'); }
        else if(/게임|두뇌|훈련/.test(s)){ setTab('brain'); }
        else if(/식물|작물|물|키우/.test(s)){ if(near&&near.type==='plot'){ openFarm(near.idx); } else toast('작물 근처로 가보세요'); }
        else doContext();
      }, ()=>{ actBtn.classList.remove('listening'); });
    };
    if(actBtn) actBtn.addEventListener('click', micFn);
    if(promptEl){ promptEl.style.pointerEvents='auto'; promptEl.style.cursor='pointer'; promptEl.addEventListener('click', doContext); }

    // 배 승선/하선 (req20)
    function boardBoat(){
      sailing=true; sailElapsed=0;
      sailStartAngle=Math.atan2(boatPos.x, boatPos.z);     // 현재 나룻배 위치에서 순회 시작
      player.visible=true;                                  // req3: 캐릭터가 배에 타고 여행
      if(sailBanner){
        sailBanner.textContent='⛵ 항해 중 · 다양한 제주 풍경을 감상하세요';
        sailBanner.classList.add('show');
        clearTimeout(sailBannerTimer);
        sailBannerTimer=setTimeout(()=>{ if(sailBanner) sailBanner.classList.remove('show'); }, 5000); // req9: 안내문구 5초 후 사라짐
      }
      if(disembarkBtn) disembarkBtn.classList.remove('hidden');
      if(friendVisitBtn) friendVisitBtn.classList.add('hidden');       // req7: 10초 전까지 숨김
      if(friendPicker) friendPicker.classList.add('hidden');
      if(editBtn) editBtn.classList.add('hidden');
      if(promptEl) promptEl.classList.add('hidden');
      Sound.seaMusicStart(); toast('⛵ 출항! 집 주위를 항해하며 풍경을 둘러보세요');
    }
    function disembark(){
      sailing=false; sailElapsed=0; boat.position.copy(boatPos); boat.rotation.set(0,0,0);
      player.visible=true; player.position.set(12,0,7); player.rotation.y=0;
      // 노 젓기 포즈 해제
      built.armL.rotation.x=0; built.armR.rotation.x=0; built.legL.rotation.x=0; built.legR.rotation.x=0;
      oars.forEach(o=>o.rotation.x=0);
      clearTimeout(sailBannerTimer);
      if(sailBanner) sailBanner.classList.remove('show');
      if(disembarkBtn) disembarkBtn.classList.add('hidden');
      if(friendVisitBtn) friendVisitBtn.classList.add('hidden');
      if(friendPicker) friendPicker.classList.add('hidden');
      if(editBtn) editBtn.classList.remove('hidden');
      Sound.seaMusicStop(); toast('🌿 정원으로 돌아왔어요');
    }
    const disembarkFn=()=>disembark();
    if(disembarkBtn) disembarkBtn.addEventListener('click', disembarkFn);

    // req7: 항해 10초 후 나타나는 '친구네 집 이동' 버튼 + 친구 목록 선택
    const wrapEl = container.parentElement;
    const friendVisitBtn = document.createElement('button');
    friendVisitBtn.type='button'; friendVisitBtn.id='friendVisitBtn'; friendVisitBtn.className='disembark-btn hidden';
    friendVisitBtn.style.bottom='88px'; friendVisitBtn.style.background='#2f6a8f';
    friendVisitBtn.textContent='🏡 친구네 집으로 이동';
    wrapEl.appendChild(friendVisitBtn);
    const friendPicker = document.createElement('div');
    friendPicker.id='friendPicker'; friendPicker.className='hidden';
    friendPicker.style.cssText='position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);z-index:9;background:rgba(255,255,255,.97);border:2px solid var(--line);border-radius:16px;padding:14px;width:min(84%,300px);box-shadow:var(--shadow);';
    wrapEl.appendChild(friendPicker);
    function openFriendPicker(){
      friendPicker.innerHTML='<p style="margin:0 0 10px;font-weight:900;text-align:center">🚣 어느 친구네 집으로 갈까요?</p>'+
        COMMUNITY.map(f=>'<button class="secondary-button full-width" data-fv="'+f.n+'" style="margin-bottom:8px">'+f.e+' '+f.n+' 님의 정원</button>').join('')+
        '<button class="secondary-button full-width" data-fv-cancel type="button">닫기</button>';
      friendPicker.classList.remove('hidden');
      friendPicker.querySelectorAll('[data-fv]').forEach(b=>b.addEventListener('click',()=>{ visitFriendGarden(b.dataset.fv); }));
      const cx=friendPicker.querySelector('[data-fv-cancel]'); if(cx) cx.addEventListener('click',()=>friendPicker.classList.add('hidden'));
    }
    friendVisitBtn.addEventListener('click', openFriendPicker);

    // 배치 편집 토글 (req22)
    const editFn=()=>{
      editMode=!editMode; editBtn.classList.toggle('on', editMode);
      touch.active=false; touch.x=0; touch.z=0;
      toast(editMode?'✋ 배치 편집: 나무·밭을 드래그해 옮겨요':'배치 편집 종료');
      if(promptEl) promptEl.classList.add('hidden');
    };
    if(editBtn) editBtn.addEventListener('click', editFn);

    const onResize=()=>{ const w=container.clientWidth, h=container.clientHeight; if(!w||!h) return; camera.aspect=w/h; camera.updateProjectionMatrix(); renderer.setSize(w,h); };
    window.addEventListener('resize', onResize);

    const housePos=new THREE.Vector3(-6.5,0,-7);
    let raf=0, t=0, stopped=false, gustT=0;
    const tmp=new THREE.Vector3(), fwd=new THREE.Vector3();
    // 제3자(관찰자) 시점 카메라 — 캐릭터를 비스듬히 위·뒤에서 내려다보며 정원 전체가 보임 (요구사항6-1)
    const CAM_DIST=9.0, CAM_HEIGHT=6.0, CAM_SIDE=1.15;  // CAM_SIDE: 정면 기준 옆으로 튼 각도(rad) → 얼굴이 보이는 3/4 시점
    function loop(){
      if(stopped) return;
      raf=requestAnimationFrame(loop); t+=0.016;

      if(sailing){
        sailElapsed += 0.016; // 항해 경과(초)
        // req4,6: 배가 15초에 한 바퀴씩 집(정원) 주위를 계속 돎 — 집으로 복귀하지 않음(req5)
        const ORBIT_R=22, PERIOD=15; // 15초에 한 바퀴
        sailAngle = sailStartAngle + (sailElapsed/PERIOD)*Math.PI*2;
        boat.position.x = Math.sin(sailAngle)*ORBIT_R;
        boat.position.z = Math.cos(sailAngle)*ORBIT_R;
        boat.position.y = -0.45 + Math.sin(t*1.4)*0.12;             // 물결 위 상하 흔들림
        const tang = sailAngle + Math.PI/2;                         // 진행(접선) 방향
        boat.rotation.set(Math.sin(t*1.1)*0.03, tang, Math.sin(t*0.9)*0.045);
        // req3: 캐릭터가 배 위에 타고 노를 저으며 여행
        player.visible=true;
        player.position.set(boat.position.x, boat.position.y+0.55, boat.position.z);
        player.rotation.y = tang;
        const row = Math.sin(sailElapsed*4.2);                      // 노 젓기 리듬
        built.armL.rotation.x = -0.6 + row*0.7; built.armR.rotation.x = -0.6 + row*0.7;
        built.legL.rotation.x = -0.5; built.legR.rotation.x = -0.5; // 앉은 자세로 다리 굽힘
        oars.forEach(o=>{ o.rotation.x = row*0.5; });               // 노도 함께 저어짐
        // 카메라: 배 바깥·위에서 배와 그 너머 정원/집을 함께 보여줌 (다양한 제주 풍경 감상)
        const camPos=tmp.set(Math.sin(sailAngle)*(ORBIT_R+8), 5.2, Math.cos(sailAngle)*(ORBIT_R+8));
        camera.position.lerp(camPos,0.06);
        camera.lookAt(boat.position.x*0.5, 1.0, boat.position.z*0.5); // 배와 섬 중앙 사이
        // req7: 항해 10초 이후 '친구네 집 이동' 버튼 노출
        if(sailElapsed>=10 && friendVisitBtn) friendVisitBtn.classList.remove('hidden');
        if(windmillBlades) windmillBlades.rotation.z += 0.015;
        swayers.forEach(s=>{ s.obj.rotation.z = Math.sin(t*1.2 + s.ph)*s.amp; });
        if(portalTags.length) portalTags.forEach(tg=>tg.quaternion.copy(camera.quaternion)); // req10: 항해 중에도 섬 이름표가 보이게
        renderer.render(scene,camera); return;
      }

      // ── 내 기준(상대) 이동·회전 + PC 클릭 이동 (req2,3,9) ──
      const spd=0.13;
      let turn=0, fb=0;
      if(!editMode){
        if(keys.left) turn+=1; if(keys.right) turn-=1;    // 좌/우 = 회전 방향
        if(keys.up) fb+=1; if(keys.down) fb-=1;            // 위/아래 = 앞/뒤
        // req4,5,6: 좌우 방향키는 '제자리 회전'이 아니라 왼쪽/오른쪽으로 돌면서 앞으로 이동
        if((keys.left||keys.right) && !keys.down) fb+=1;
        if(touch.active){ turn+=-touch.x; fb+=-touch.z; }  // 모바일: 좌우 드래그=회전, 상하=앞뒤
      }
      const manualInput = (Math.abs(turn)+Math.abs(fb))>0.08;
      if(manualInput) moveTarget=null; // 수동 조작 시 클릭 이동 취소
      if(Math.abs(turn)>0.001) heading += turn*0.05;
      let autoFwd=0;
      if(moveTarget){
        const dxT=moveTarget.x-player.position.x, dzT=moveTarget.z-player.position.z, distT=Math.hypot(dxT,dzT);
        if(distT>0.35){ heading=Math.atan2(dxT,dzT); autoFwd=1; } else moveTarget=null;
      }
      const drive=clamp(fb+autoFwd,-1,1);
      const moving=Math.abs(drive)>0.05;
      fwd.set(Math.sin(heading),0,Math.cos(heading));
      player.rotation.y=heading;   // 3D 캐릭터가 진행 방향을 바라봄
      if(moving){
        player.position.x=clamp(player.position.x+fwd.x*spd*drive,-14.5,14.5);
        player.position.z=clamp(player.position.z+fwd.z*spd*drive,-14.5,14.5);
        walkPhase+=0.28;
        // 3D 걷기: 팔·다리 스윙 + 살짝 위아래 홉
        const sw=Math.sin(walkPhase);
        built.legL.rotation.x= sw*0.5; built.legR.rotation.x=-sw*0.5;
        built.armL.rotation.x=-sw*0.5; built.armR.rotation.x= sw*0.5;
        player.position.y=Math.abs(sw)*0.06;
        if(sw*Math.sin(walkPhase-0.28)<0) Sound.step();
      } else {
        walkPhase=0; player.position.y=0;
        built.legL.rotation.x=0; built.legR.rotation.x=0; built.armL.rotation.x=0; built.armR.rotation.x=0;
      }

      // ── 반려동물 이동 (req13: 동행은 주인 옆을 따라다니고, req15: 나머지는 자유롭게 배회) ──
      if(gardenPets.length){
        const activeIds = state.pet.active||[];
        gardenPets.forEach(pet=>{
          const slot = activeIds.indexOf(pet.id);
          if(slot>=0){
            // 동행: 주인 뒤·옆으로 따라옴 (2마리는 좌우로)
            const side = slot===0? -1:1;
            const tx = player.position.x + Math.sin(heading+Math.PI)*1.5 + Math.cos(heading)*side*0.9;
            const tz = player.position.z + Math.cos(heading+Math.PI)*1.5 - Math.sin(heading)*side*0.9;
            const dx=tx-pet.group.position.x, dz=tz-pet.group.position.z, d=Math.hypot(dx,dz);
            pet.group.position.x += dx*0.12; pet.group.position.z += dz*0.12;
            if(d>0.06) pet.group.rotation.y = Math.atan2(dx,dz);
            pet.moving = d>0.12;
          } else {
            // 자유 배회 (집안 포함, 경계 제한 없음)
            const dx=pet.tgt.x-pet.group.position.x, dz=pet.tgt.z-pet.group.position.z, d=Math.hypot(dx,dz);
            if(d<0.5){ pet.tgt=randPetTarget(); pet.moving=false; }
            else { pet.group.position.x += dx/d*0.035; pet.group.position.z += dz/d*0.035; pet.group.rotation.y=Math.atan2(dx,dz); pet.moving=true; }
          }
          // 걷는 홉 애니메이션
          if(pet.moving){ pet.phase+=0.2; pet.group.position.y=Math.abs(Math.sin(pet.phase))*0.06; }
          else { pet.group.position.y += (0-pet.group.position.y)*0.2; }
        });
      }

      // 비스듬한 앞·옆(3/4) 시점: 캐릭터 앞·옆에서 바라봐 걷는 중에도 얼굴이 보이게 (얼굴 표시 요청)
      fwd.set(Math.sin(heading),0,Math.cos(heading));
      const camYaw = heading + CAM_SIDE;   // 캐릭터가 바라보는 방향 기준 옆으로 튼 각도
      tmp.set(
        player.position.x + Math.sin(camYaw)*CAM_DIST,
        player.position.y + CAM_HEIGHT,
        player.position.z + Math.cos(camYaw)*CAM_DIST
      );
      camera.position.lerp(tmp, editMode?0.05:0.1);
      camera.lookAt(player.position.x, player.position.y+1.9, player.position.z);  // 상반신·얼굴을 향해

      // req7: 카메라와 캐릭터 사이를 가리는 나무는 반투명 처리해 시야를 확보
      if(treeGroups.length){
        const ax=camera.position.x, az=camera.position.z, bx=player.position.x, bz=player.position.z;
        const abx=bx-ax, abz=bz-az; const seg2=(abx*abx+abz*abz)||1;
        treeGroups.forEach(tg=>{
          let tp=((tg.position.x-ax)*abx+(tg.position.z-az)*abz)/seg2; tp=clamp(tp,0,1);
          const dx=tg.position.x-(ax+abx*tp), dz=tg.position.z-(az+abz*tp);
          const blocking = tp>0.05 && tp<0.98 && Math.hypot(dx,dz)<2.2;
          const target = blocking?0.18:1;
          tg.traverse(o=>{ if(o.material){ o.material.opacity += (target-o.material.opacity)*0.2; } });
        });
      }
      if(windmillBlades) windmillBlades.rotation.z += 0.015; // req8: 풍차 날개 회전

      const gust = 0.6 + 0.4*Math.sin(t*0.5);
      swayers.forEach(s=>{ s.obj.rotation.z = Math.sin(t*1.2 + s.ph)*s.amp*gust; });
      gustT+=0.016; if(gustT>3){ gustT=0; Sound.windGust(gust); }
      if(friendTags.length) friendTags.forEach(tg=>tg.quaternion.copy(camera.quaternion)); // 이름표 빌보드 (req15)
      if(portalTags.length) portalTags.forEach(tg=>tg.quaternion.copy(camera.quaternion)); // 섬 이름표 빌보드 (req10)

      if(!editMode){
        let cand=null, best=3.0;
        plots.forEach(pl=>{ const d=pl.pos.distanceTo(player.position); if(d<best){best=d; cand={type:'plot',idx:pl.idx};} });
        const dh=housePos.distanceTo(player.position); if(dh<3.2 && dh<best){ best=dh; cand={type:'house'}; }
        const db=boatPos.distanceTo(player.position); if(db<3.6 && db<best){ best=db; cand={type:'boat'}; }
        const changed = JSON.stringify(cand)!==JSON.stringify(near);
        if(changed){
          near=cand;
          if(promptEl){
            if(near&&near.type==='plot'){ promptEl.textContent='🌱 '+CROPS[near.idx].name+' 키우기'; promptEl.classList.remove('hidden'); }
            else if(near&&near.type==='house'){ promptEl.textContent='🏠 집 들어가기'; promptEl.classList.remove('hidden'); }
            else if(near&&near.type==='boat'){ promptEl.textContent='🚣 나룻배 타기'; promptEl.classList.remove('hidden'); }
            else promptEl.classList.add('hidden');
          }
        }
      } else if(promptEl){ promptEl.classList.add('hidden'); }

      renderer.render(scene,camera);
    }
    // 밭 작물 갱신 API — 성장/수확 시 3D 밭도 함께 성장 (req5)
    function rebuildField(i){
      const pl=plots[i]; if(!pl) return; const old=pl.group; const px=old.position.x, pz=old.position.z;
      scene.remove(old);
      old.traverse(o=>{ if(o.geometry) o.geometry.dispose(); if(o.material){ if(o.material.map) o.material.map.dispose(); o.material.dispose(); } });
      const g=makeField(i); g.position.set(px,0,pz); g.userData.dragKey='f'+i; scene.add(g);
      pl.group=g; pl.pos=g.position;
      const di=draggables.findIndex(d=>d.group===old); if(di>=0) draggables[di]={group:g};
    }
    villageApi = { rebuildField };

    loop();
    setTimeout(onResize,60);

    return function cleanup(){
      stopped=true; cancelAnimationFrame(raf);
      clearTimeout(sailBannerTimer);
      villageApi = null;
      Sound.windStop(); Sound.seaMusicStop();
      window.removeEventListener('keydown',kd); window.removeEventListener('keyup',ku);
      window.removeEventListener('resize',onResize);
      cvEl.removeEventListener('pointerdown',tStart); cvEl.removeEventListener('pointermove',tMove);
      cvEl.removeEventListener('pointerup',tEnd); cvEl.removeEventListener('pointercancel',tEnd);
      if(actBtn) actBtn.removeEventListener('click',micFn);
      if(promptEl) promptEl.removeEventListener('click',doContext);
      if(disembarkBtn) disembarkBtn.removeEventListener('click',disembarkFn);
      if(editBtn) editBtn.removeEventListener('click',editFn);
      renderer.dispose();
      if(renderer.domElement.parentElement) renderer.domElement.parentElement.removeChild(renderer.domElement);
    };
  }

  /* ============================================================
     스마트팜 실시간 작물 모달 (요구사항 6)
     ============================================================ */
  const farmDialog = $('#farmDialog');
  let farmRaf=0, farmIdx=0, farmT=0, waterAnim=0;
  const STAGE_STORY = ['🌰 씨앗 단계','🌱 새싹이 돋았어요','🍃 잎이 무성해져요','🌸 꽃과 열매가 맺혔어요','🧺 수확 준비 완료!'];

  // ── 작물 성장 렌더러 (성장 스토리 + 물주기 모션 공용, req10,11,12,14,15) ──
  // 작물 종류별로 실제 자라는 모습이 다르게: 옥수수(줄기+긴잎+자루), 수박(덩굴+줄무늬 열매) (req14)
  function drawCropScene(ctx,w,h,idx,tt,anim){
    const crop=CROPS[idx], plot=state.farm[idx];
    const soilH=Math.max(30, h*0.13), baseY=h-soilH;
    // 흙(이랑 밭 느낌) — 흰 배경에서도 잘 보이는 흙색
    ctx.fillStyle='#7a5230'; ctx.fillRect(0,baseY,w,soilH);
    ctx.fillStyle='#8a5f38'; for(let r=0;r<w;r+=Math.max(24,w/8)){ ctx.beginPath(); ctx.ellipse(r+12,baseY+8,14,5,0,0,Math.PI*2); ctx.fill(); }
    // 성장도 = 단계 + 현재 영양분 비율 (부드러운 성장 스토리)
    const g=clamp((plot.stage + (plot.water||0)/100)/4, 0, 1);
    const sway=Math.sin(tt*0.05);
    if(crop.key==='corn')       drawCorn(ctx,w,h,baseY,g,plot,tt,sway);
    else if(crop.key==='melon') drawMelon(ctx,w,h,baseY,g,plot,tt,sway);
    else                        drawLeafy(ctx,w,h,baseY,g,plot,tt,sway,crop);
    // 물주기 시각 모션: 물뿌리개 + 낙하하는 물방울 (req10)
    if(anim>0){
      ctx.font=Math.round(w*0.11)+'px sans-serif'; ctx.fillText('🪴', w*0.06, h*0.2);
      ctx.font=Math.round(w*0.13)+'px sans-serif'; ctx.fillText('💦', w*0.14, h*0.16);
      ctx.fillStyle='rgba(70,160,230,.85)';
      for(let d=0;d<10;d++){
        const dx=w*0.22+((d*37)%(w*0.55));
        const dy=((h*0.2)+((tt*7+d*33)%(baseY-h*0.2)));
        ctx.beginPath(); ctx.ellipse(dx,dy,2.5,6,0,0,Math.PI*2); ctx.fill();
      }
    }
  }

  // 옥수수: 두꺼운 대 + 마디마다 길게 휘는 잎 + 초록 껍질의 노란 옥수수 자루 + 수꽃(태슬) (req14)
  function drawCorn(ctx,w,h,baseY,g,plot,tt){
    for(let c=0;c<3;c++){
      const cx=w*(0.26+0.24*c);
      const stalkH=(baseY*0.10)+g*(h*0.72);
      const topY=baseY-stalkH;
      const bend=Math.sin(tt*0.05)*8*g*(c===1?1.1:0.8);
      // 옥수수대(줄기)
      ctx.strokeStyle='#5aa53a'; ctx.lineWidth=Math.max(5,w*0.022); ctx.lineCap='round';
      ctx.beginPath(); ctx.moveTo(cx,baseY); ctx.quadraticCurveTo(cx+bend*0.5,baseY-stalkH*0.5,cx+bend,topY); ctx.stroke();
      // 마디마다 뻗는 길고 휘어진 잎
      const nLeaves=Math.max(2, plot.stage+2);
      for(let k=0;k<nLeaves;k++){
        const t=(k+1)/(nLeaves+1);
        const ny=baseY-stalkH*t, nx=cx+bend*t;
        const side=k%2?1:-1;
        const leafLen=(w*0.17)*(0.6+g*0.9);
        const wob=Math.sin(tt*0.05+k)*4;
        ctx.strokeStyle= k%2?'#4d9d3a':'#57ab42'; ctx.lineWidth=Math.max(3,w*0.015); ctx.lineCap='round';
        ctx.beginPath(); ctx.moveTo(nx,ny);
        ctx.quadraticCurveTo(nx+side*leafLen*0.6, ny-leafLen*0.12+wob, nx+side*leafLen, ny+leafLen*0.55+wob);
        ctx.stroke();
      }
      // 옥수수 자루: stage>=3부터 열림
      if(plot.stage>=3){
        const ears=plot.stage>=4?2:1;
        for(let e=0;e<ears;e++){
          const ey=baseY-stalkH*(0.4+e*0.2), ex=cx+bend*(0.4+e*0.2)+(e%2?1:-1)*w*0.035;
          const ew=w*0.05, eh=h*(plot.stage>=4?0.07:0.055);
          // 초록 껍질
          ctx.fillStyle='#4f9d3a'; ctx.beginPath(); ctx.ellipse(ex,ey,ew*1.3,eh*0.62,0.3,0,Math.PI*2); ctx.fill();
          // 노란 몸통
          ctx.fillStyle= plot.stage>=4?'#f2c200':'#d7d06a'; ctx.beginPath(); ctx.ellipse(ex,ey,ew,eh*0.5,0.25,0,Math.PI*2); ctx.fill();
          // 알갱이
          ctx.fillStyle= plot.stage>=4?'#e0ad00':'#c6be55';
          for(let gy=-2;gy<=2;gy++) for(let gx=-1;gx<=1;gx++){ ctx.beginPath(); ctx.arc(ex+gx*ew*0.42, ey+gy*eh*0.16, ew*0.13,0,Math.PI*2); ctx.fill(); }
          // 옥수수 수염
          ctx.strokeStyle='#caa24a'; ctx.lineWidth=1.4;
          for(let s=0;s<5;s++){ ctx.beginPath(); ctx.moveTo(ex+ew*0.7,ey-eh*0.4); ctx.lineTo(ex+ew*1.1+s*2, ey-eh*0.75-s); ctx.stroke(); }
        }
      }
      // 수꽃(태슬): 다 자라면 줄기 끝에
      if(plot.stage>=4){
        ctx.strokeStyle='#d8c56a'; ctx.lineWidth=2;
        for(let s=-2;s<=2;s++){ ctx.beginPath(); ctx.moveTo(cx+bend,topY); ctx.lineTo(cx+bend+s*w*0.022, topY-h*0.05); ctx.stroke(); }
      }
    }
  }

  // 수박: 바닥을 기는 덩굴 + 둥근 잎 + 초록 줄무늬 열매 (req12,14)
  function drawMelon(ctx,w,h,baseY,g,plot,tt){
    const vineY=baseY-6;
    ctx.strokeStyle='#4d9d3a'; ctx.lineWidth=Math.max(3,w*0.013); ctx.lineCap='round';
    ctx.beginPath(); ctx.moveTo(w*0.12,vineY);
    ctx.bezierCurveTo(w*0.35,vineY-20*g, w*0.6,vineY+8, w*0.9,vineY-14*g); ctx.stroke();
    // 잎
    const nLeaves=Math.max(3, plot.stage+3);
    ctx.fillStyle='#4fa33f';
    for(let k=0;k<nLeaves;k++){
      const t=k/(nLeaves-0.999);
      const lx=w*(0.14+0.72*t), ly=vineY-8-Math.sin(t*Math.PI)*12*g+Math.sin(tt*0.05+k)*2;
      const lw=(w*0.065)*(0.6+g*0.8);
      ctx.save(); ctx.translate(lx,ly); ctx.rotate(Math.sin(k)*0.3);
      ctx.beginPath(); ctx.moveTo(0,0);
      ctx.quadraticCurveTo(lw,-lw*0.9,0,-lw*1.4);
      ctx.quadraticCurveTo(-lw,-lw*0.9,0,0); ctx.fill(); ctx.restore();
    }
    // 수박 열매: stage>=3
    if(plot.stage>=3){
      const n=plot.stage>=4?2:1;
      for(let f=0;f<n;f++){
        const r=(plot.stage>=4?w*0.15:w*0.10);
        const mx=w*(0.34+0.34*f), my=baseY-r*0.65;
        ctx.fillStyle='#3a9d3a'; ctx.beginPath(); ctx.arc(mx,my,r,0,Math.PI*2); ctx.fill();
        ctx.save(); ctx.beginPath(); ctx.arc(mx,my,r,0,Math.PI*2); ctx.clip();
        ctx.strokeStyle='#2c7a2c'; ctx.lineWidth=Math.max(2,r*0.11);
        for(let s=-2;s<=2;s++){ const off=s*r*0.42; ctx.beginPath(); ctx.moveTo(mx+off*0.5,my-r*1.1); ctx.quadraticCurveTo(mx+off,my,mx+off*0.5,my+r*1.1); ctx.stroke(); }
        ctx.restore();
        ctx.fillStyle='rgba(255,255,255,.25)'; ctx.beginPath(); ctx.ellipse(mx-r*0.35,my-r*0.4,r*0.25,r*0.14,-0.5,0,Math.PI*2); ctx.fill();
      }
    }
  }

  // 잎채소/토마토 등 일반 작물 (기존 방식)
  function drawLeafy(ctx,w,h,baseY,g,plot,tt,sway,crop){
    const swayPx=sway*6*g;
    for(let c=0;c<3;c++){
      const cx=w*(0.28+0.22*c);
      const stemH=(baseY*0.06)+g*(h*0.62);
      ctx.strokeStyle='#3f8a3a'; ctx.lineWidth=Math.max(4,w*0.016); ctx.lineCap='round';
      ctx.beginPath(); ctx.moveTo(cx,baseY);
      const sw=swayPx*(c===1?1.2:0.8);
      ctx.quadraticCurveTo(cx+sw/2,baseY-stemH/2,cx+sw,baseY-stemH); ctx.stroke();
      const leaves=1+plot.stage+(plot.water>=50?1:0);
      ctx.fillStyle='#57a83f';
      for(let k=1;k<=leaves;k++){ const ly=baseY-stemH*(k/(leaves+1)); const side=k%2?1:-1;
        ctx.save(); ctx.translate(cx,ly); ctx.rotate(side*0.5+Math.sin(tt*0.05)*0.05);
        const lw=Math.max(12,w*0.045); ctx.beginPath(); ctx.ellipse(side*lw*0.9,0,lw,lw*0.4,0,0,Math.PI*2); ctx.fill(); ctx.restore(); }
      if(plot.stage>=3){ ctx.fillStyle=crop.color; const n=plot.stage>=4?3:2;
        for(let f=0;f<n;f++){ const fx=cx+sw+Math.cos(f*2.1)*(w*0.05), fy=baseY-stemH+18+Math.sin(f*1.7)*14;
          ctx.beginPath(); ctx.arc(fx,fy,plot.stage>=4?w*0.03:w*0.022,0,Math.PI*2); ctx.fill(); } }
    }
  }

  function openFarm(idx){
    farmIdx=idx; farmT=0; waterAnim=0;
    const crop=CROPS[idx];
    $('#farmTitle').textContent = crop.emoji+' '+crop.name+' · 식물 키우기';
    updateFarmUI();
    if (typeof farmDialog.showModal==='function') farmDialog.showModal();
    drawFarmLoop();
    completeRoutine('farm'); save();
  }
  function updateFarmUI(){
    const plot=state.farm[farmIdx];
    const pct=Math.round((plot.stage/4)*100);
    $('#farmStage').textContent='성장 '+pct+'%';
    $('#growStory').textContent = STAGE_STORY[Math.min(4,plot.stage)];
    const wp = plot.stage>=4 ? 100 : Math.round(plot.water||0);
    $('#waterPct').textContent = plot.stage>=4 ? '다 자랐어요' : ('영양분 '+wp+'%');
    $('#waterFill').style.setProperty('--progress', wp+'%');
    const temp=(22+Math.sin(farmT*0.05)*2).toFixed(1);
    const hum=(64+Math.cos(farmT*0.04)*6).toFixed(0);
    const soil=(40+(plot.water||0)*0.4+Math.sin(farmT*0.06)*3).toFixed(0);
    // 온도·습도·토양수분만 표시 (조도 삭제, req6)
    $('#sensorGrid').innerHTML =
      sensor('🌡️ 온도', temp+'°C')+sensor('💧 습도', hum+'%')+
      sensor('🌱 토양수분', soil+'%');
    $('#farmHarvest').disabled = plot.stage < 4;
  }
  const sensor=(l,v)=>'<div class="sensor"><small>'+l+'</small><strong>'+v+'</strong></div>';

  function drawFarmLoop(){
    const cv=$('#farmFeed'); if(!cv){ return; }
    const ctx=cv.getContext('2d'); const w=cv.width,h=cv.height;
    function frame(){
      farmT++; if(waterAnim>0) waterAnim--;
      // 밝은 흰색 하늘 배경 (req15)
      const sky=ctx.createLinearGradient(0,0,0,h);
      sky.addColorStop(0,'#dff0ff'); sky.addColorStop(0.55,'#f5fbff'); sky.addColorStop(1,'#ffffff');
      ctx.fillStyle=sky; ctx.fillRect(0,0,w,h);
      // 은은한 햇살
      ctx.fillStyle='rgba(255,238,180,.4)'; ctx.beginPath(); ctx.arc(w*0.8,h*0.12,w*0.14,0,Math.PI*2); ctx.fill();
      drawCropScene(ctx,w,h,farmIdx,farmT,waterAnim);
      // LIVE/REC 등 라이브 표시 제거 (req7)
      farmRaf=requestAnimationFrame(frame);
    }
    cancelAnimationFrame(farmRaf); frame();
  }
  $('#farmWater').addEventListener('click', ()=>{
    const plot=state.farm[farmIdx];
    if(plot.stage>=4){ toast('이미 다 자랐어요 · 수확하세요'); return; }
    if(state.coins<10){ toast('코인이 부족해요'); return; }
    addCoins(-10); Sound.water(); waterAnim=48; // 물주기 모션
    plot.water = Math.min(100, (plot.water||0) + 5); // 영양분 한 번에 5% 상승 (req8)
    if(plot.water>=100 && plot.stage<4){ plot.stage++; plot.water=0; Sound.coin(); toast('🌱 '+STAGE_STORY[Math.min(4,plot.stage)]); if(villageApi) villageApi.rebuildField(farmIdx); }
    else toast('영양분을 줬어요 💧 (+5%)');
    state.coop.myContribField++; bumpDaily('water');
    save(); updateFarmUI();
  });
  $('#farmHarvest').addEventListener('click', ()=>{
    const plot=state.farm[farmIdx];
    if(plot.stage<4) return;
    const crop=CROPS[farmIdx];
    addCoins(70); plot.stage=0; plot.water=0; Sound.harvest();
    // 수확한 작물을 가방에 담기 (req17,18)
    if(!Array.isArray(state.harvested)) state.harvested=[];
    state.harvested.push({ key:crop.key, name:crop.name, emoji:crop.emoji });
    completeRoutine('family');
    save(); updateFarmUI();
    const cnt=state.harvested.length;
    toast('수확 완료! '+crop.emoji+' '+crop.name+' 가방에 담았어요 · 총 '+cnt+'개'+(cnt>=5?' 🎁 작물받기 가능!':''));
    farmDialog.close();
    if(villageApi) villageApi.rebuildField(farmIdx); // 밭 작물 동반 갱신 (req5)
    syncBagBadge();
  });

  /* ── 집안 꾸미기 (req3) ── */
  const houseDialog = $('#houseDialog');
  function openHouse(){ renderRoom(); if(typeof houseDialog.showModal==='function') houseDialog.showModal(); }
  function renderRoom(){
    const room=$('#room'); if(!room) return;
    // 구버전 저장 데이터 마이그레이션 (owned/pos/size 보강)
    if(!state.house.owned) state.house.owned = (state.house.items||[]).slice();
    if(!state.house.pos) state.house.pos = {};
    if(!state.house.size) state.house.size = {};
    const owned=state.house.owned, placed=state.house.items||[];
    const sizer=$('#furnSizer'), sizeRange=$('#furnSizeRange'), sizeLabel=$('#furnSizerLabel');
    let selected=null;
    // 방 안: 러그 + 내 캐릭터(req16,10) + 배치된(구매한) 가구만(req15) — 드래그 이동(req17)·클릭 크기변형(req11)
    room.innerHTML='<div class="rug"></div>'+
      '<div class="room-char">'+avatarSvg(false)+'</div>'+
      FURNITURE.filter(f=>placed.includes(f.id)&&owned.includes(f.id)).map(f=>{
        const p=state.house.pos[f.id]||{x:f.x,y:f.y}; const sz=state.house.size[f.id]||40;
        return '<span class="furn" data-furn-move="'+f.id+'" style="left:'+p.x+'%;top:'+p.y+'%;font-size:'+sz+'px">'+f.e+'</span>';
      }).join('');
    if(sizer) sizer.style.display='none';
    const tray=$('#furnTray');
    // 상점: 구매/배치 토글. 미구매는 코인으로 구매, 구매한 것만 방에 놓기 가능
    tray.innerHTML=FURNITURE.map(f=>{
      const own=owned.includes(f.id), on=placed.includes(f.id);
      const label = !own ? (f.price+'🪙 구매') : (on?'놓음 ✓':'놓기');
      return '<button class="furn-chip '+(on?'on':'')+(own?'':' buy')+'" data-furn="'+f.id+'">'+f.e+'<div style="font-size:10px;font-weight:700">'+f.name+' · '+label+'</div></button>';
    }).join('');
    tray.querySelectorAll('[data-furn]').forEach(b=>b.addEventListener('click',()=>{
      const f=FURNITURE.find(x=>x.id===b.dataset.furn);
      if(!state.house.owned.includes(f.id)){
        if(state.coins<f.price){ toast('코인이 부족해요'); return; }
        addCoins(-f.price); state.house.owned.push(f.id); state.house.items.push(f.id); Sound.coin(); save(); toast(f.name+' 구매 완료! 방에 놓았어요 '+f.e); renderRoom(); return;
      }
      const i=state.house.items.indexOf(f.id);
      if(i>=0){ state.house.items.splice(i,1); } else { state.house.items.push(f.id); }
      Sound.tap(); save(); renderRoom();
    }));
    // 가구 선택(크기변형 req11) + 드래그(이동 req17)
    function selectFurn(id, el){
      selected=id; room.querySelectorAll('.furn').forEach(x=>x.classList.remove('sel')); el.classList.add('sel');
      if(sizer){ sizer.style.display='block'; sizeLabel.textContent=(FURNITURE.find(f=>f.id===id)||{}).name+' 크기'; sizeRange.value=state.house.size[id]||40; }
    }
    if(sizeRange){ sizeRange.oninput=()=>{ if(!selected) return; const v=Number(sizeRange.value); state.house.size[selected]=v; const el=room.querySelector('[data-furn-move="'+selected+'"]'); if(el) el.style.fontSize=v+'px'; save(); }; }
    // req5: 선택한(내가 산) 가구 삭제 버튼
    const delBtn=$('#furnDeleteBtn');
    if(delBtn){ delBtn.onclick=()=>{
      if(!selected){ toast('삭제할 가구를 먼저 선택하세요'); return; }
      const id=selected; const nm=(FURNITURE.find(f=>f.id===id)||{}).name||'가구';
      ['owned','items'].forEach(k=>{ const arr=state.house[k]; if(arr){ const i=arr.indexOf(id); if(i>=0) arr.splice(i,1); } });
      if(state.house.pos) delete state.house.pos[id];
      if(state.house.size) delete state.house.size[id];
      selected=null; Sound.tap(); save(); toast('🗑 '+nm+'를 삭제했어요'); renderRoom();
    }; }
    room.querySelectorAll('[data-furn-move]').forEach(el=>{
      const id=el.dataset.furnMove;
      el.addEventListener('pointerdown',(ev)=>{
        ev.preventDefault(); const rect=room.getBoundingClientRect(); const sx=ev.clientX, sy=ev.clientY; let didMove=false;
        el.setPointerCapture&&el.setPointerCapture(ev.pointerId);
        const move=(e)=>{
          if(Math.abs(e.clientX-sx)+Math.abs(e.clientY-sy)>5) didMove=true;
          const x=clamp((e.clientX-rect.left)/rect.width*100,4,96), y=clamp((e.clientY-rect.top)/rect.height*100,10,92);
          el.style.left=x+'%'; el.style.top=y+'%'; state.house.pos[id]={x:Math.round(x),y:Math.round(y)};
        };
        const up=()=>{ el.removeEventListener('pointermove',move); el.removeEventListener('pointerup',up);
          if(didMove){ save(); } else { selectFurn(id, el); } };
        el.addEventListener('pointermove',move); el.addEventListener('pointerup',up);
      });
    });
  }

  /* ── 오늘의 나의 미션 모달 (req6) ── */
  const missionDialog = $('#missionDialog');
  function openMission(){ renderMissionList(); if(typeof missionDialog.showModal==='function') missionDialog.showModal(); }
  function renderMissionList(){
    const list=$('#missionList'); if(!list) return;
    const done=state.routines.filter(r=>r.done).length, total=state.routines.length;
    $('#missionFill').style.setProperty('--progress', Math.round(done/total*100)+'%');
    list.innerHTML = state.routines.map(r=>
      '<button class="mission-item '+(r.done?'done':'')+'" data-mission="'+r.id+'">'+
        '<span class="mi-ico" style="background:'+r.color+'">'+routineIcon(r.icon)+'</span>'+
        '<span><h4>'+esc(r.title)+'</h4><p>'+esc(r.desc)+(r.done?'':' · +10 코인')+'</p></span>'+
        '<span class="mi-check '+(r.done?'on':'')+'">'+(r.done?'✓':'')+'</span>'+
      '</button>').join('');
    list.querySelectorAll('[data-mission]').forEach(b=>b.addEventListener('click',()=>{
      const id=b.dataset.mission; const r=state.routines.find(x=>x.id===id);
      if(r.done){ toast('이미 완료한 미션이에요'); return; }
      completeRoutine(id); Sound.coin();
      if(id==='game') bumpDaily('game');
      if(id==='walk'){ state.steps+=1000; }
      save(); toast('🎉 미션 완료! +10 코인'); renderMissionList();
    }));
  }

  /* ============================================================
     작물 가방 · 배송 (req17~24)
     ============================================================ */
  const backpackDialog = $('#backpackDialog');
  let deliveryStage = 'list';

  // 정원 HUD의 가방 버튼 뱃지(수확 개수) 동기화
  function syncBagBadge(){
    const b=document.getElementById('bagBtn'); if(!b) return;
    const badge=b.querySelector('.bag-badge'); if(badge) badge.textContent=(state.harvested||[]).length;
  }

  function openBackpack(stage){
    deliveryStage = stage || 'list';
    if(deliveryStage!=='list' && (state.harvested||[]).length<5) deliveryStage='list';
    renderBackpack();
    if(typeof backpackDialog.showModal==='function' && !backpackDialog.open) backpackDialog.showModal();
  }

  function renderBackpack(){
    const body=$('#backpackBody'); if(!body) return;
    const items=state.harvested||[];
    if(deliveryStage==='list'){
      // req17: 가방을 누르면 그동안 재배(수확)한 작물을 보여줌
      $('#backpackTitle').textContent='🎒 나의 작물 가방';
      const grid = items.length
        ? '<div class="harvest-grid">'+items.map(c=>'<div class="harvest-item"><div class="hi-e">'+c.emoji+'</div><small>'+esc(c.name)+'</small></div>').join('')+'</div>'
        : '<div class="empty">아직 수확한 작물이 없어요.<br>마을에서 작물을 키워 🧺 수확해 보세요 🌱</div>';
      body.innerHTML =
        '<p class="tiny" style="margin:0 0 4px">그동안 수확한 작물이에요. <b>5개</b>를 모으면 실제 작물을 집으로 배송받을 수 있어요!</p>'+
        grid+
        '<p class="tiny" style="margin:6px 0 10px">수확한 작물 <b>'+items.length+' / 5</b>개</p>'+
        // req18: 5개가 모이면 '작물받기' 버튼 노출
        (items.length>=5
          ? '<button class="primary-button full-width" id="claimCropBtn">🎁 작물 받기</button>'
          : '<button class="secondary-button full-width" disabled>작물 5개를 모으면 받을 수 있어요</button>');
      const cb=$('#claimCropBtn'); if(cb) cb.addEventListener('click',()=>{ Sound.tap(); deliveryStage='address'; renderBackpack(); }); // req19
    }
    else if(deliveryStage==='address'){
      // req19: 작물받기를 누르면 주소창이 뜸
      $('#backpackTitle').textContent='🚚 작물 배송 신청';
      body.innerHTML =
        '<p class="tiny" style="margin:0 0 6px">배송받을 <b>주소</b>를 입력해 주세요. 주소를 입력하면 <b>작물 배송 받기</b>가 활성화돼요.</p>'+
        '<input class="addr-field" id="addrName" placeholder="받는 분 성함" value="'+esc(state.delivery.name||'')+'">'+
        '<input class="addr-field" id="addrPhone" placeholder="연락처 (선택)" value="'+esc(state.delivery.phone||'')+'">'+
        '<textarea class="addr-field" id="addrText" placeholder="배송 주소를 입력하세요 (예: 제주시 …)">'+esc(state.delivery.addr||'')+'</textarea>'+
        (Voice.supported?'<button class="mic-btn" id="deliverMic" title="음성으로 배송 진행"><svg viewBox="0 0 24 24"><path d="M12 15a3 3 0 0 0 3-3V6a3 3 0 0 0-6 0v6a3 3 0 0 0 3 3Zm5-3a5 5 0 0 1-10 0H5a7 7 0 0 0 6 6.9V21h2v-2.1A7 7 0 0 0 19 12h-2Z"/></svg></button><p class="heard" id="deliverHeard"></p>':'')+
        '<button class="primary-button full-width" id="deliverBtn" disabled>주소를 입력하세요</button>';
      const addr=$('#addrText'), btn=$('#deliverBtn');
      const refresh=()=>{ const has=addr.value.trim().length>0; btn.disabled=!has; btn.textContent = has ? '🚚 작물 배송 받기' : '주소를 입력하세요'; }; // req20
      addr.addEventListener('input', refresh); refresh();
      btn.addEventListener('click', submitDelivery); // req20 → req21
      // req23,24: 배송 버튼도 음성인식 · 배송 관련 발화는 작물배송으로 연결
      const mic=$('#deliverMic'), heard=$('#deliverHeard');
      if(mic){ mic.addEventListener('click',()=>{
        if(Voice.isActive()){ Voice.stop(); mic.classList.remove('listening'); return; }
        Sound.resume(); heard.textContent='듣는 중… (예: "배송", "작물 배송해줘")'; mic.classList.add('listening');
        Voice.start((alts)=>{
          const s=alts.join(' '); heard.textContent='"'+alts[0]+'"';
          if(/배송|보내|받기|택배|주소|작물/.test(s)){
            if(addr.value.trim()) submitDelivery();
            else heard.textContent='주소를 먼저 입력해 주세요';
          } else heard.textContent='"배송"이라고 말하면 배송이 진행돼요';
        }, ()=>{ mic.classList.remove('listening'); });
      }); }
    }
    else if(deliveryStage==='shipping'){
      // req21: 작물 배송 받기 안내가 뜰 때 선물 박스가 보임
      $('#backpackTitle').textContent='🎁 작물 배송 접수 완료';
      body.innerHTML =
        '<div class="deliver-note">'+
          '<div class="gift-box">🎁</div>'+
          '<h3 style="margin:10px 0 4px">작물 배송을 접수했어요!</h3>'+
          '<p class="tiny">신선하게 수확한 작물 '+(state.harvested||[]).length+'개를<br>입력하신 주소로 정성껏 보내드릴게요.</p>'+
          '<p class="tiny" style="color:var(--ink);font-weight:700">📍 '+esc(state.delivery.addr||'')+'</p>'+
          '<button class="primary-button full-width" id="finishDeliverBtn" style="margin-top:12px">📦 배송 완료 · 메인으로</button>'+
        '</div>';
      $('#finishDeliverBtn').addEventListener('click', finishDelivery); // req22
    }
  }

  function submitDelivery(){
    const name=$('#addrName'), phone=$('#addrPhone'), addr=$('#addrText');
    if(!addr || !addr.value.trim()){ toast('주소를 입력해 주세요'); return; }
    Voice.stop();
    state.delivery.name=name?name.value.trim():'';
    state.delivery.phone=phone?phone.value.trim():'';
    state.delivery.addr=addr.value.trim();
    save(); Sound.coin();
    deliveryStage='shipping'; renderBackpack(); // req21
  }

  function finishDelivery(){
    // req22: 배송 완료 → 가방 비우고 메인(정원)으로 이동
    state.delivery.done=true; state.delivery.addr=''; state.delivery.name=''; state.delivery.phone='';
    state.harvested=[]; save(); syncBagBadge();
    if(backpackDialog.open) backpackDialog.close();
    toast('📦 작물 배송이 완료되었어요! 메인으로 돌아갈게요');
    setTab('village');
  }

  /* ============================================================
     2) 마이페이지 (기존 홈 → 대시보드+루틴+활동+리포트)
     ============================================================ */
  function renderMy(){
    const done=state.routines.filter(r=>r.done).length, total=state.routines.length;
    const pct=Math.round(done/total*100);
    const stepsPct=Math.min(100,Math.round(state.steps/state.stepGoal*100));

    const routineCards=state.routines.map(r=>
      '<button class="routine-card" data-routine="'+r.id+'">'+
        '<span class="routine-icon" style="background:'+r.color+'">'+routineIcon(r.icon)+'</span>'+
        '<span><h4>'+esc(r.title)+'</h4><p>'+esc(r.desc)+'</p></span>'+
        '<span class="status-pill '+(r.done?'done':'')+'">'+(r.done?'완료':'+10')+'</span>'+
      '</button>').join('');

    const bars=AREAS.map(a=>{
      const v=state.scores[a.id];
      return '<div class="bar-row"><span>'+a.name+'</span><div class="bar"><i style="--score:'+v+'%;--bar-color:'+a.color+'"></i></div><strong>'+v+'</strong></div>';
    }).join('');

    app.innerHTML =
      '<section class="hero">'+
        '<div class="hero-copy"><h2>우*수</h2><p>오늘의 컨디션과 루틴을 한눈에<br>마을에서 활동한 기록이 여기 보여요</p></div>'+
        '<button class="avatar-scene" id="myAvatarBtn" type="button" title="아바타 꾸미러 가기" style="cursor:pointer;border:1px solid var(--line);padding:0">'+avatarSvg(false)+'<span class="ava-hint">👗 아바타</span></button>'+
      '</section>'+
      '<div class="stats-row">'+
        '<div class="stat"><strong>'+brainAge()+'세</strong><span>두뇌 나이</span></div>'+
        '<div class="stat"><strong>'+nf(state.coins)+'</strong><span>보유 코인</span></div>'+
        '<div class="stat"><strong>'+state.streak+'일</strong><span>연속 루틴</span></div>'+
      '</div>'+
      '<div class="panel"><h3 style="margin-bottom:8px">오늘의 루틴</h3>'+
        '<div class="progress-track"><div class="progress-fill" style="--progress:'+pct+'%"></div></div>'+
        '<p class="tiny" style="margin:8px 0 0">'+done+' / '+total+'개 완료</p></div>'+
      '<div class="routine-list" style="margin-top:10px">'+routineCards+'</div>'+
      '<div class="section-title"><h3>걷기 활동</h3><span>시뮬레이션</span></div>'+
      '<div class="panel">'+
        '<div class="big-number"><strong>'+nf(state.steps)+'</strong><span>/ '+nf(state.stepGoal)+' 걸음</span></div>'+
        '<div class="progress-track"><div class="progress-fill" style="--progress:'+stepsPct+'%"></div></div>'+
        '<div class="button-row"><button class="secondary-button" data-walk="1000">+1,000</button><button class="secondary-button" data-walk="3000">+3,000</button></div>'+
        '<button class="primary-button full-width" data-claim style="margin-top:8px" '+(state.steps>=state.stepGoal?'':'disabled')+'>'+
          (state.steps>=state.stepGoal?'목표 달성 보상 (+30)':'목표까지 '+nf(state.stepGoal-state.steps)+'걸음')+'</button>'+
      '</div>'+
      '<div class="section-title"><h3>주간 인지 리포트</h3><span class="badge-pill">종합 '+avgScore()+'</span></div>'+
      '<div class="panel"><div class="report-grid">'+bars+'</div></div>'+
      // AI 건강·활동 리포트 (req13)
      '<div class="section-title"><h3>🤖 AI 건강·활동 리포트</h3><span class="badge-pill">AI 분석</span></div>'+
      '<div class="panel" style="border-color:var(--teal)">'+aiHealthReport()+
        '<button class="secondary-button full-width" data-report style="margin-top:10px">리포트 새로고침</button></div>'+
      '<div class="panel" style="margin-top:12px;border-color:var(--teal)"><span class="badge-pill">PREMIUM</span>'+
        '<h3 style="margin:8px 0 6px">AI 맞춤 루틴 · 실물 스마트팜</h3>'+
        '<p>AI 자동 루틴 설계와 실물 스마트팜 구획은 프리미엄에서 제공됩니다.</p>'+
        '<button class="primary-button full-width" data-sub>프리미엄 보기</button></div>';

    app.querySelectorAll('[data-routine]').forEach(b=>b.addEventListener('click',()=>{
      const id=b.dataset.routine;
      if(id==='game') return setTab('brain');
      if(id==='farm') return setTab('village');
      const r=state.routines.find(x=>x.id===id);
      if(r.done){ toast('이미 완료했어요'); return; }
      completeRoutine(id); save(); toast('루틴 완료! +10'); renderMy();
    }));
    app.querySelectorAll('[data-walk]').forEach(b=>b.addEventListener('click',()=>{
      state.steps+=Number(b.dataset.walk); completeRoutine('walk'); if(state.steps>=6000) bumpDaily('walk'); save(); toast('걷기 기록 추가!'); renderMy();
    }));
    const claim=$('[data-claim]',app); if(claim) claim.addEventListener('click',()=>{
      if(state.steps<state.stepGoal) return; addCoins(30); state.steps=0; completeRoutine('walk'); save(); toast('+30 코인!'); renderMy();
    });
    $('[data-sub]',app).addEventListener('click',()=>toast('구독 전환 데모 화면'));
    const rpt=$('[data-report]',app); if(rpt) rpt.addEventListener('click',()=>{ toast('AI가 최신 데이터로 다시 분석했어요'); renderMy(); });
    // 캐릭터(아바타) 클릭 → 아바타 페이지 연동 (req3)
    const avaBtn=$('#myAvatarBtn',app); if(avaBtn) avaBtn.addEventListener('click',()=>{ Sound.tap(); setTab('avatar'); });
  }

  /* ============================================================
     리워드 상점 (독립 카테고리, req4)
     ============================================================ */
  function renderReward(){
    // 꾸미기 상점 — 카테고리별 아이템 (요구사항11-9): 건강식품·이벤트 박스 '위로' 배치
    const shopSection = SHOP_CATS.map(cat=>{
      const items=SHOP_ITEMS.filter(s=>s.cat===cat);
      return '<div class="section-title" style="margin-top:14px"><h3>🎨 '+cat+' 사기</h3><span class="badge-pill">코인 구매</span></div>'+
        '<div class="reward-grid">'+items.map(s=>{
          const owned=state.shopOwned.includes(s.id), can=state.coins>=s.price;
          const btn = owned
            ? '<button class="secondary-button" disabled>보유 중 ✓</button>'
            : '<button class="'+(can?'primary-button':'secondary-button')+'" data-shop="'+s.id+'" '+(can?'':'disabled')+'>'+(can?'구매하기':'코인 부족')+'</button>';
          return '<div class="reward-card"><div class="rc-emoji">'+s.emoji+'</div><strong>'+esc(s.name)+'</strong>'+
            '<span class="rc-cost">'+nf(s.price)+' 🪙</span>'+btn+'</div>';
        }).join('')+'</div>';
    }).join('');

    app.innerHTML =
      '<div class="section-title"><h3>🎁 리워드 상점</h3><span class="badge-pill">'+nf(state.coins)+' P</span></div>'+
      '<div class="panel" style="margin-bottom:12px"><p class="tiny" style="margin:0">코인으로 캐릭터와 정원을 꾸미고, 모은 포인트로 작물 씨앗·리워드를 교환하세요. 교환권은 아래에 발급돼요.</p></div>'+
      // req9: 옷·악세서리·신발·정원 디자인 등 꾸미기 상점 (건강식품·이벤트 박스 위)
      shopSection+
      '<div class="section-title" style="margin-top:16px"><h3>🌱 포인트 교환</h3><span class="badge-pill">'+nf(state.coins)+' P</span></div>'+
      '<div class="reward-grid">'+REWARDS.map(r=>{
        const can=state.coins>=r.cost;
        return '<div class="reward-card"><div class="rc-emoji">'+r.emoji+'</div><strong>'+esc(r.name)+'</strong>'+
          '<span class="rc-cost">'+nf(r.cost)+' P</span>'+
          '<button class="'+(can?'primary-button':'secondary-button')+'" data-reward="'+r.id+'" '+(can?'':'disabled')+'>'+(can?'교환하기':'포인트 부족')+'</button></div>';
      }).join('')+'</div>'+
      // req10: 보유 교환권 이미지 (수박·옥수수 등 작물 씨앗 교환권)
      (state.rewardsOwned.length?'<div class="panel" style="margin-top:12px"><h3 style="margin-bottom:6px">🎟️ 보유 교환권</h3><div style="font-size:30px">'+state.rewardsOwned.map(id=>{const r=REWARDS.find(x=>x.id===id);return r?r.emoji:'🍉';}).join(' ')+'</div></div>':'')+
      (state.shopOwned.length?'<div class="panel" style="margin-top:12px"><h3 style="margin-bottom:6px">🛍️ 보유 꾸미기 아이템</h3><div style="font-size:28px">'+state.shopOwned.map(id=>{const s=SHOP_ITEMS.find(x=>x.id===id);return s?s.emoji:'';}).join(' ')+'</div></div>':'');
    app.querySelectorAll('[data-reward]').forEach(b=>b.addEventListener('click',()=>{
      const r=REWARDS.find(x=>x.id===b.dataset.reward);
      if(state.coins<r.cost){ toast('포인트가 부족해요'); return; }
      if(!confirm(r.emoji+' '+r.name+' 을(를) '+nf(r.cost)+'P로 교환할까요?')) return;
      addCoins(-r.cost); state.rewardsOwned.push(r.id); Sound.coin(); save();
      toast('🎉 '+r.name+' 교환 완료! 교환권이 발급됐어요'); renderReward();
    }));
    // req9: 꾸미기 아이템 구매
    app.querySelectorAll('[data-shop]').forEach(b=>b.addEventListener('click',()=>{
      const s=SHOP_ITEMS.find(x=>x.id===b.dataset.shop);
      if(state.shopOwned.includes(s.id)){ toast('이미 보유한 아이템이에요'); return; }
      if(state.coins<s.price){ toast('코인이 부족해요'); return; }
      addCoins(-s.price); state.shopOwned.push(s.id); Sound.coin(); save();
      toast('🛍️ '+s.name+' 구매 완료!'); renderReward();
    }));
  }
  const topArea=()=>AREAS.slice().sort((a,b)=>state.scores[b.id]-state.scores[a.id])[0];
  const lowArea=()=>AREAS.slice().sort((a,b)=>state.scores[a.id]-state.scores[b.id])[0];

  /* ---------- AI 건강·활동 리포트 생성 (req13) ---------- */
  function aiHealthReport(){
    const avg=avgScore(), age=brainAge(), top=topArea(), low=lowArea();
    const stepsPct=Math.round(state.steps/state.stepGoal*100);
    const done=state.routines.filter(r=>r.done).length;
    let grade = avg>=75?'매우 우수':avg>=60?'양호':avg>=45?'보통':'주의';
    let intro = '두뇌 나이는 <b>'+age+'세</b>, 인지 종합 점수는 <b>'+avg+'점('+grade+')</b>이에요.';
    const tips=[];
    tips.push('강점 영역은 <b>'+top.name+'</b>, 더 키우면 좋을 영역은 <b>'+low.name+'</b>예요. 두뇌 탭에서 '+low.name+' 훈련을 추천해요.');
    if(stepsPct>=100) tips.push('오늘 걷기 목표를 <b>달성</b>했어요! 유산소 활동이 뇌 혈류를 도와요. 👏');
    else tips.push('오늘 걸음 수는 목표의 <b>'+stepsPct+'%</b>예요. 10분 더 걸으면 기억력 향상에 도움이 돼요.');
    if(state.streak>=3) tips.push('<b>'+state.streak+'일 연속</b> 활동 중! 규칙적인 습관이 인지 건강의 핵심이에요.');
    tips.push('오늘 루틴을 '+done+'/'+state.routines.length+'개 완료했어요. 수분 섭취와 충분한 수면도 잊지 마세요.');
    return '<p style="margin:0 0 8px;color:var(--ink)">'+intro+'</p>'+
      '<ul style="margin:0;padding-left:18px;color:var(--muted);font-size:13px;line-height:1.7">'+
      tips.map(t=>'<li>'+t+'</li>').join('')+'</ul>';
  }

  /* ============================================================
     7+8) 두뇌 챌린지 (다양화 + 난이도 + 적응형 자동조정)
     ============================================================ */
  const brain={ active:false, area:null, q:null, index:0, correct:0, size:5, answered:false };
  const ARROWS={ left:'◀', right:'▶', up:'▲', down:'▼' };

  function recentAcc(area){
    const arr=state.brain.stats[area]||[]; const r=arr.slice(-15);
    if(r.length<5) return null;
    return r.filter(Boolean).length/r.length;
  }
  function autoAdjust(area){
    const acc=recentAcc(area); if(acc==null) return null;
    const cur=state.brain.level[area]; let next=cur;
    if(acc>=0.85){ next = cur==='easy'?'normal':(cur==='normal'?'hard':'hard'); }
    else if(acc<=0.5){ next = cur==='hard'?'normal':(cur==='normal'?'easy':'easy'); }
    if(next!==cur){ state.brain.level[area]=next; state.brain.stats[area]=[]; return {from:cur,to:next,acc}; }
    return {from:cur,to:cur,acc};
  }

  // 문제 생성기: 영역별 여러 게임 타입, 난이도 파라미터 반영
  const QGEN={
    attention(D){
      if(rand(2)===0){ // 플랭커
        const dirSet = D.dirs===4?['left','right','up','down']:['left','right'];
        const center=dirSet[rand(dirSet.length)]; const flank=dirSet[rand(dirSet.length)];
        const row=Array(D.flankers).fill(flank); row.splice(Math.floor(D.flankers/2),0,center);
        const names={left:'왼쪽',right:'오른쪽',up:'위',down:'아래'};
        const choices=shuffle(dirSet.map(d=>({t:names[d],ok:d===center})));
        return { prompt:'가운데 화살표 방향은?', stimulus:row.map(d=>ARROWS[d]).join(' '), choices };
      } else { // 스트룹
        const cols=[['빨강','#e0453e'],['파랑','#2f6bd6'],['초록','#3f9d3a'],['노랑','#d9a521']];
        const word=cols[rand(cols.length)], ink=cols[rand(cols.length)];
        const choices=shuffle(cols.map(c=>({t:c[0],ok:c[0]===ink[0]}))).slice(0,D.choices);
        if(!choices.some(c=>c.ok)) choices[0]={t:ink[0],ok:true};
        return { prompt:'글자의 <b>색깔</b>을 고르세요', stimulusHtml:'<span style="color:'+ink[1]+'">'+word[0]+'</span>', choices };
      }
    },
    memory(D){
      const len=D.seqLen; let d=''; for(let i=0;i<len;i++) d+=rand(10);
      const wrongs=new Set();
      while(wrongs.size<D.choices-1){ const s=shiftDigit(d); if(s!==d) wrongs.add(s); }
      const choices=shuffle([{t:d,ok:true}].concat([...wrongs].map(t=>({t,ok:false}))));
      return { prompt:'방금 본 숫자 열을 고르세요', stimulus:d, hideAfter:D.hideMs, choices };
    },
    language(D){
      const syn=[
        {w:'기쁘다',s:'즐겁다',d:['슬프다','지루하다','피곤하다','답답하다']},
        {w:'빠르다',s:'신속하다',d:['느리다','무겁다','조용하다','약하다']},
        {w:'똑똑하다',s:'영리하다',d:['둔하다','게으르다','어둡다','흐리다']},
        {w:'튼튼하다',s:'견고하다',d:['약하다','무르다','얇다','가늘다']},
        {w:'아름답다',s:'고운',d:['추한','거친','차가운','메마른']},
      ];
      const ant=[
        {w:'높다',s:'낮다',d:['깊다','넓다','밝다','길다']},
        {w:'무겁다',s:'가볍다',d:['크다','뜨겁다','굵다','단단하다']},
        {w:'시작',s:'끝',d:['중간','과정','준비','계획']},
      ];
      if(rand(2)===0){
        const p=syn[rand(syn.length)];
        const choices=shuffle([{t:p.s,ok:true}].concat(p.d.slice(0,D.choices-1).map(t=>({t,ok:false}))));
        return { prompt:'‘'+p.w+'’와 뜻이 비슷한 낱말은?', choices };
      } else {
        const p=ant[rand(ant.length)];
        const choices=shuffle([{t:p.s,ok:true}].concat(p.d.slice(0,D.choices-1).map(t=>({t,ok:false}))));
        return { prompt:'‘'+p.w+'’의 반대말은?', choices };
      }
    },
    visuospatial(D){
      const dirs=['up','right','down','left'];
      const start=rand(4), steps=1+rand(D.dirs===4?3:2);
      const end=dirs[(start+steps)%4];
      const names={up:'↑ 위',right:'→ 오른쪽',down:'↓ 아래',left:'← 왼쪽'};
      const choices=shuffle(dirs.map(d=>({t:names[d],ok:d===end}))).slice(0,D.choices);
      if(!choices.some(c=>c.ok)) choices[0]={t:names[end],ok:true};
      return { prompt:'이 화살표를 시계방향으로 '+steps+'칸(90°) 돌리면?', stimulus:ARROWS[dirs[start]], choices };
    },
    executive(D){
      if(rand(2)===0){ // 수열
        const s=2+rand(6), st=D.step+rand(3);
        const seq=[s,s+st,s+st*2,s+st*3], ans=s+st*4;
        const opts=shuffle([ans,ans+st,ans-1,ans+2].slice(0,D.choices)).map(n=>({t:String(n),ok:n===ans}));
        if(!opts.some(o=>o.ok)) opts[0]={t:String(ans),ok:true};
        return { prompt:'다음에 올 수는?', stimulus:seq.join(', ')+', ?', choices:opts };
      } else { // 계산
        const a=rand(D.numMax)+1, b=rand(D.numMax)+1, op=rand(2);
        const ans=op?a*Math.max(1,Math.round(b/8)+1):a+b;
        const q=op? a+' × '+(Math.max(1,Math.round(b/8)+1)) : a+' + '+b;
        const wr=new Set(); while(wr.size<D.choices-1){ const w=ans+(rand(9)-4); if(w!==ans&&w>0) wr.add(w); }
        const opts=shuffle([{t:String(ans),ok:true}].concat([...wr].map(t=>({t:String(t),ok:false}))));
        return { prompt:'계산해 보세요', stimulus:q+' = ?', choices:opts };
      }
    },
  };
  function shiftDigit(s){ const a=s.split(''); const i=rand(a.length); a[i]=String((Number(a[i])+1)%10); return a.join(''); }

  function renderBrain(){
    if(brain.active){ renderBrainQuestion(); return; }
    const tiles=AREAS.map(a=>{
      const lv=state.brain.level[a.id]; const acc=recentAcc(a.id);
      return '<div class="area-tile">'+
        '<div class="cat-ico" style="background:'+a.tile+'">'+a.emoji+'</div>'+
        '<span class="area-badge">'+a.name+'</span>'+
        '<strong>점수 '+state.scores[a.id]+' · '+LEVELS[lv]+'</strong>'+
        '<small>'+(acc==null?'데이터 수집 중':'최근 정답률 '+Math.round(acc*100)+'%')+'</small>'+
        '<button class="primary-button" data-area="'+a.id+'" style="min-height:40px">훈련 시작</button>'+
      '</div>';
    }).join('');
    app.innerHTML =
      '<div class="section-title"><h3>두뇌 챌린지</h3><span>인지 5개 영역</span></div>'+
      '<div class="brain-intro-coach"><div class="coach-face">'+coachFace('idle')+'</div>'+
        '<div><p>오늘도 함께 두뇌 운동해요!</p><small>영역을 골라 훈련을 시작해 보세요 🌱</small></div></div>'+
      '<div class="panel" style="margin-bottom:12px"><h3 style="margin-bottom:6px">🤖 적응형 난이도</h3>'+
        '<p class="tiny" style="margin:0">정답률·오답률을 분석해 <strong>쉬움 · 보통 · 어려움</strong>을 자동 조정합니다. '+
        '최근 정답률이 85%↑면 상향, 50%↓면 하향돼요. 게임 종류도 매번 바뀝니다.</p></div>'+
      '<div class="area-grid">'+tiles+'</div>'+
      '<div class="panel" style="margin-top:14px"><h3 style="margin-bottom:6px">추천 훈련</h3>'+
        '<p>가장 낮은 <strong>'+lowArea().name+'</strong>부터 시작해 보세요.</p>'+
        '<button class="primary-button full-width" data-area="'+lowArea().id+'">추천 영역 시작</button></div>';
    app.querySelectorAll('[data-area]').forEach(b=>b.addEventListener('click',()=>startBrain(b.dataset.area)));
  }

  function startBrain(area){ brain.active=true; brain.area=area; brain.index=0; brain.correct=0; brain.usedVoice=false; nextQ(); }
  function nextQ(){ const D=DIFF[state.brain.level[brain.area]]; brain.q=QGEN[brain.area](D); brain.answered=false; renderBrainQuestion(); }

  function renderBrainQuestion(){
    const area=AREAS.find(a=>a.id===brain.area); const q=brain.q;
    const lv=state.brain.level[brain.area];
    let stim='';
    if(q.stimulusHtml) stim='<div class="stimulus">'+q.stimulusHtml+'</div>';
    else if(q.stimulus!=null) stim='<div class="stimulus" id="stim">'+esc(q.stimulus)+'</div>';
    const choices=q.choices.map((c,i)=>'<button class="choice-button" data-choice="'+i+'">'+esc(c.t)+'</button>').join('');
    // 마이크(음성) + 버튼 두 방식 (req10)
    const micBlock = Voice.supported
      ? '<button class="mic-btn" id="micBtn" title="음성으로 답하기"><svg viewBox="0 0 24 24"><path d="M12 15a3 3 0 0 0 3-3V6a3 3 0 0 0-6 0v6a3 3 0 0 0 3 3Zm5-3a5 5 0 0 1-10 0H5a7 7 0 0 0 6 6.9V21h2v-2.1A7 7 0 0 0 19 12h-2Z"/></svg></button>'+
        '<p class="mode-note">🎙️ 마이크를 누르고 답을 말하거나, 아래 버튼을 눌러 진행하세요</p><p class="heard" id="heard"></p>'
      : '<p class="mode-note">🔘 버튼을 눌러 답을 선택하세요 (이 브라우저는 음성인식 미지원)</p>';
    const qpPct = Math.round(brain.index / brain.size * 100);
    app.innerHTML =
      '<div class="game-stage">'+
        '<div class="q-progress"><i style="--qp:'+qpPct+'%"></i></div>'+
        '<div class="game-meta"><span>'+area.name+' · '+LEVELS[lv]+'</span><span class="gm-score">'+(brain.index+1)+'/'+brain.size+' · 정답 '+brain.correct+'</span></div>'+
        '<div class="coach" id="coach"><div class="coach-face" id="coachFace">'+coachFace('think')+'</div><div class="speech" id="speech">천천히 잘 보고 골라 보세요 😊</div></div>'+
        '<div class="game-card"><span class="area-badge">'+area.name+'</span>'+stim+'<p class="prompt">'+q.prompt+'</p><div class="choice-grid">'+choices+'</div>'+micBlock+'</div>'+
        '<button class="secondary-button full-width" data-quit>그만두기</button>'+
      '</div>';
    if(q.hideAfter){
      const stimEl=$('#stim',app), grid=$('.choice-grid',app), pr=$('.prompt',app);
      const orig=pr.innerHTML; pr.textContent='숫자를 외우세요…'; grid.style.visibility='hidden';
      setTimeout(()=>{ if(!brain.active) return; if(stimEl) stimEl.textContent='？ ？ ？'; pr.innerHTML=orig; grid.style.visibility='visible'; }, q.hideAfter);
    }
    app.querySelectorAll('[data-choice]').forEach(b=>b.addEventListener('click',()=>{ Sound.resume(); answerQ(Number(b.dataset.choice)); }));
    $('[data-quit]',app).addEventListener('click',()=>{ Voice.stop(); brain.active=false; renderBrain(); });
    // 음성 인식 버튼
    const micBtn=$('#micBtn',app), heard=$('#heard',app);
    if(micBtn){
      micBtn.addEventListener('click',()=>{
        if(Voice.isActive()){ Voice.stop(); micBtn.classList.remove('listening'); return; }
        Sound.resume();
        heard.textContent='듣는 중…'; micBtn.classList.add('listening');
        const ok=Voice.start(
          (alts)=>{
            heard.textContent='"'+alts[0]+'"';
            const idx=matchChoice(alts, q.choices);
            if(idx>=0){ brain.usedVoice=true; answerQ(idx); }
            else heard.textContent='못 알아들었어요, 다시 말하거나 버튼을 눌러요';
          },
          ()=>{ micBtn.classList.remove('listening'); }
        );
        if(!ok){ heard.textContent='음성인식을 시작할 수 없어요'; micBtn.classList.remove('listening'); }
      });
    }
  }

  function answerQ(i){
    if(brain.answered) return; brain.answered=true; Voice.stop();
    const mb=$('#micBtn',app); if(mb) mb.classList.remove('listening');
    const q=brain.q, ok=q.choices[i].ok;
    app.querySelectorAll('[data-choice]').forEach((b,idx)=>{ b.disabled=true; if(q.choices[idx].ok) b.classList.add('correct'); if(idx===i&&!ok) b.classList.add('wrong'); });
    state.brain.stats[brain.area].push(ok);
    if(state.brain.stats[brain.area].length>30) state.brain.stats[brain.area].shift();
    // 코치 캐릭터 반응 (얼굴 표정 + 말풍선)
    const coach=$('#coach',app), face=$('#coachFace',app), speech=$('#speech',app);
    if(face) face.innerHTML = coachFace(ok?'correct':'wrong');
    if(coach){ coach.classList.remove('react'); void coach.offsetWidth; coach.classList.add('react'); }
    if(speech){
      speech.classList.remove('correct','wrong');
      speech.classList.add(ok?'correct':'wrong');
      speech.textContent = ok ? COACH_OK[brain.correct % COACH_OK.length] : '괜찮아요, 다음 문제 함께 도전해요 💪';
    }
    if(ok){ brain.correct++; Sound.correct(); toast('정답!'); } else { Sound.wrong(); toast('아쉬워요'); }
    setTimeout(()=>{ brain.index++; if(brain.index>=brain.size) finishBrain(); else nextQ(); }, 800);
  }

  function finishBrain(){
    const area=AREAS.find(a=>a.id===brain.area);
    const D=DIFF[state.brain.level[brain.area]];
    const reward=brain.correct*D.coin; addCoins(reward);
    bumpScore(brain.area, Math.round(brain.correct/brain.size*6)-1);
    completeRoutine('game');
    // 함께하기 단체 미션 기여
    state.coop.myContribGame++;
    if(reward>0) Sound.coin();
    bumpDaily('game'); if(brain.usedVoice) bumpDaily('voice');
    const adj=autoAdjust(brain.area);
    brain.active=false; save();
    let adjMsg='';
    if(adj && adj.from!==adj.to) adjMsg='<div class="banner-reward"><strong>난이도 자동 조정</strong><br>최근 정답률 '+Math.round(adj.acc*100)+'% → '+LEVELS[adj.from]+' → <b>'+LEVELS[adj.to]+'</b></div>';
    else if(adj) adjMsg='<p class="tiny">최근 정답률 '+Math.round(adj.acc*100)+'% · 난이도 유지('+LEVELS[adj.to]+')</p>';
    app.innerHTML =
      adjMsg+
      '<div class="panel" style="text-align:center"><span class="area-badge">'+area.name+'</span>'+
        '<h2 style="margin:12px 0 4px">'+brain.correct+' / '+brain.size+' 정답</h2>'+
        '<p>+'+reward+' 코인 획득 · '+area.name+' 점수 '+state.scores[brain.area]+'</p>'+
        '<div class="button-row"><button class="secondary-button" data-again>한 번 더</button><button class="primary-button" data-list>영역 목록</button></div>'+
      '</div>';
    $('[data-again]',app).addEventListener('click',()=>startBrain(area.id));
    $('[data-list]',app).addEventListener('click',renderBrain);
  }

  /* ============================================================
     반려동물 — 몸통·꼬리·다리 SVG + 키우기/성장/리워드 (요구사항11-11,16~25)
     ============================================================ */
  // 몸통·꼬리·다리·귀를 갖춘 2D 반려동물 (req11) — 단계가 오를수록 커짐(req22)
  function petBodySvg(type, stage){
    const p=PETS.find(x=>x.type===type)||PETS[0];
    const b=p.body, e=p.ear, belly=p.belly;
    const sc=(0.78+(Math.min(5,stage||1)-1)*0.09).toFixed(2);
    let ears='', tail='', extra='', legs='', body='', head='';
    if(type==='bird'){
      body='<ellipse cx="66" cy="52" rx="26" ry="20" fill="'+b+'"/><ellipse cx="66" cy="58" rx="16" ry="11" fill="'+belly+'"/>';
      head='<circle cx="90" cy="40" r="14" fill="'+b+'"/><circle cx="88" cy="38" r="2.4" fill="#222"/><circle cx="95" cy="38" r="2.4" fill="#222"/>';
      extra='<path d="M102 40 l12 4 -12 4 Z" fill="#e6a23c"/>';
      tail='<path d="M40 50 l-20 -6 6 12 Z" fill="'+e+'"/>';
      legs='<rect x="60" y="70" width="3" height="14" fill="#e6a23c"/><rect x="72" y="70" width="3" height="14" fill="#e6a23c"/>';
      ears='<path d="M62 48 q-8 4 -2 12" stroke="'+e+'" stroke-width="8" fill="none" stroke-linecap="round"/>';
    } else {
      tail = type==='rabbit'
        ? '<circle cx="24" cy="50" r="9" fill="#ffffff"/>'
        : (type==='cat'
          ? '<path d="M30 52 q-18 0 -16 -20" stroke="'+b+'" stroke-width="7" fill="none" stroke-linecap="round"/>'
          : '<path d="M30 50 q-14 -4 -10 -20" stroke="'+b+'" stroke-width="8" fill="none" stroke-linecap="round"/>');
      legs='<rect x="42" y="60" width="8" height="22" rx="3" fill="'+b+'"/><rect x="55" y="62" width="8" height="22" rx="3" fill="'+b+'"/><rect x="72" y="62" width="8" height="22" rx="3" fill="'+b+'"/><rect x="85" y="60" width="8" height="22" rx="3" fill="'+b+'"/>';
      body='<ellipse cx="62" cy="54" rx="34" ry="20" fill="'+b+'"/><ellipse cx="62" cy="62" rx="24" ry="12" fill="'+belly+'"/>';
      head='<circle cx="96" cy="44" r="16" fill="'+b+'"/>'+
        '<circle cx="92" cy="42" r="2.6" fill="#222"/><circle cx="101" cy="42" r="2.6" fill="#222"/>'+
        '<circle cx="96.5" cy="49" r="2.6" fill="#5a3a2a"/>'+
        '<path d="M92 52 q4.5 4 9 0" stroke="#5a3a2a" stroke-width="1.6" fill="none" stroke-linecap="round"/>';
      ears = type==='dog'
        ? '<ellipse cx="88" cy="34" rx="6" ry="12" fill="'+e+'"/><ellipse cx="104" cy="34" rx="6" ry="12" fill="'+e+'"/>'
        : (type==='cat'
          ? '<path d="M86 32 l-3 -15 12 8 Z" fill="'+e+'"/><path d="M106 32 l3 -15 -12 8 Z" fill="'+e+'"/>'
          : '<ellipse cx="90" cy="20" rx="5" ry="17" fill="'+e+'"/><ellipse cx="103" cy="20" rx="5" ry="17" fill="'+e+'"/>');
    }
    return '<svg viewBox="0 0 120 90" class="pet-svg"><g transform="translate(60 45) scale('+sc+') translate(-60 -45)">'+tail+legs+body+ears+head+extra+'</g></svg>';
  }

  const petCareDialog = $('#petCareDialog');
  let carePetId = null;
  function getPet(id){ return (state.pet.adopted||[]).find(p=>p.id===id); }

  // 동행 토글 — 최대 2마리 (req14)
  function toggleActive(id){
    if(!Array.isArray(state.pet.active)) state.pet.active=[];
    const arr=state.pet.active, i=arr.indexOf(id);
    if(i>=0){ arr.splice(i,1); toast('동행을 해제했어요'); }
    else { if(arr.length>=2){ toast('동행은 최대 2마리까지예요'); return; } arr.push(id); toast('🐾 동행 반려동물로 설정했어요'); }
    save();
  }

  // req16: 반려동물 키우기 창
  function openPetCare(id){
    carePetId=id; renderPetCare();
    if(typeof petCareDialog.showModal==='function' && !petCareDialog.open) petCareDialog.showModal();
  }
  function renderPetCare(){
    const pd=getPet(carePetId); if(!pd){ if(petCareDialog.open) petCareDialog.close(); return; }
    const info=PETS.find(x=>x.type===pd.type)||PETS[0];
    const isActive=(state.pet.active||[]).includes(pd.id);
    $('#petCareTitle').textContent = info.emoji+' '+info.name+' 키우기';
    const dots=[1,2,3,4,5].map(n=>'<i class="'+(n<=pd.stage?'on':'')+'"></i>').join('');
    const stageLabel = pd.complete ? '완전체 🏆 (5단계)' : (pd.stage+'단계 · '+PET_STAGE_NAMES[Math.min(4,pd.stage-1)]);
    $('#petCareBody').innerHTML =
      '<div class="pet-stage" id="petStage">'+petBodySvg(pd.type, pd.stage)+'</div>'+
      '<div class="pet-stage-dots">'+dots+'</div>'+
      '<p class="tiny" style="text-align:center;margin:2px 0 8px">성장 단계: <b>'+stageLabel+'</b></p>'+
      '<div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:4px"><small class="tiny">💕 교감도</small><small class="tiny">'+Math.round(pd.affection)+'%</small></div>'+
      '<div class="progress-track"><div class="progress-fill" style="--progress:'+Math.round(pd.affection)+'%"></div></div>'+
      // req17: 놀아주기/밥주기/목욕하기/산책하기
      (pd.complete
        ? (pd.rewarded
            ? '<p class="tiny" style="text-align:center;margin-top:12px">🏆 완전체로 성장 완료! 리워드를 받았어요.</p>'
            : '<button class="primary-button full-width" id="petRewardBtn" style="margin-top:12px">🎁 성장 완료 리워드 받기</button>') // req25
        : '<div class="care-actions">'+
            '<button class="secondary-button" data-care="play">🎾 놀아주기</button>'+
            '<button class="secondary-button" data-care="feed">🍚 밥주기</button>'+
            '<button class="secondary-button" data-care="bath">🚿 목욕하기</button>'+
            '<button class="secondary-button" data-care="walk">🦮 산책하기</button>'+
          '</div>')+
      '<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:10px">'+
        '<button class="chip '+(isActive?'on':'')+'" id="petCareActive">'+(isActive?'동행 중 ✓':'동행하기')+'</button>'+
        '<button class="chip" id="petCareClose2">닫기</button>'+
      '</div>';
    $('#petCareBody').querySelectorAll('[data-care]').forEach(b=>b.addEventListener('click',()=>doCareAction(b.dataset.care)));
    const rb=$('#petRewardBtn'); if(rb) rb.addEventListener('click', claimPetReward);
    const ab=$('#petCareActive'); if(ab) ab.addEventListener('click',()=>{ toggleActive(pd.id); renderPetCare(); });
    const cb=$('#petCareClose2'); if(cb) cb.addEventListener('click',()=>petCareDialog.close());
  }
  // req18~21: 각 돌봄 동작의 시각 연출 + 교감도 상승
  function doCareAction(kind){
    const pd=getPet(carePetId); if(!pd || pd.complete) return;
    if(pd._busy) return; pd._busy=true;
    const stage=$('#petStage'); const petSvg=stage?stage.querySelector('.pet-svg'):null;
    const prop=document.createElement('div'); prop.className='care-prop '+kind;
    if(kind==='play'){ prop.textContent='🎾'; if(petSvg) petSvg.classList.add('bounce'); Sound.tap(); }       // req18: 장난감 공
    else if(kind==='feed'){ prop.textContent='🥣'; const food=document.createElement('div'); food.className='care-prop food'; food.textContent='🍚'; if(stage) stage.appendChild(food); setTimeout(()=>food.remove(),1200); Sound.tap(); } // req19: 사료그릇+사료
    else if(kind==='bath'){ prop.textContent='🚿'; if(stage) stage.classList.add('bathing'); Sound.water(); }  // req20: 물주기
    else if(kind==='walk'){ prop.textContent='🦮'; if(petSvg) petSvg.classList.add('walking'); Sound.step(); } // req21: 산책줄
    if(stage) stage.appendChild(prop);
    document.querySelectorAll('[data-care]').forEach(b=>b.disabled=true);
    setTimeout(()=>{
      prop.remove(); if(petSvg) petSvg.classList.remove('bounce','walking'); if(stage) stage.classList.remove('bathing');
      pd._busy=false;
      addAffection(pd, 25, {play:'놀이',feed:'식사',bath:'목욕',walk:'산책'}[kind]);
      bumpDaily('pet'); save(); renderPetCare();
    }, 1300);
  }
  // req22,23,24: 교감 100% → 한 단계 성장 (5단계=완전체)
  function addAffection(pd, amt, label){
    const info=PETS.find(x=>x.type===pd.type)||PETS[0];
    pd.affection += amt;
    if(pd.affection>=100){
      if(pd.stage<5){
        pd.stage++; pd.affection=0; Sound.coin();
        if(pd.stage>=5){ pd.complete=true; toast('🏆 '+info.name+' 완전체 달성! 리워드를 받으세요'); }
        else toast('🎉 '+info.name+' 성장! '+pd.stage+'단계가 되었어요');
      } else { pd.affection=100; }
    } else {
      toast('💕 '+label+' 완료 · 교감도 +'+amt+'%');
    }
  }
  // req25: 성장 완료 리워드
  function claimPetReward(){
    const pd=getPet(carePetId); if(!pd || !pd.complete || pd.rewarded) return;
    pd.rewarded=true; addCoins(200); Sound.harvest();
    save(); toast('🎁 성장 완료 리워드 +200 코인 획득!'); renderPetCare();
  }

  /* ============================================================
     3) 아바타 · 반려동물 (꾸미기 게임)
     ============================================================ */
  function renderAvatar(){
    const a=state.avatar;
    const skinSw=SKINS.map(c=>'<button class="swatch '+(a.skin===c?'on':'')+'" data-skin="'+c+'" style="background:'+c+'"></button>').join('');
    const outSw=OUTFITS.map(c=>'<button class="swatch '+(a.outfit===c?'on':'')+'" data-outfit="'+c+'" style="background:'+c+'"></button>').join('');
    const hairSw=HAIRS.map(c=>'<button class="swatch '+((a.hair||HAIRS[0])===c?'on':'')+'" data-hair="'+c+'" style="background:'+c+'"></button>').join('');
    const hatCh=HATS.map(h=>'<button class="chip '+(a.hat===h.id?'on':'')+'" data-hat="'+h.id+'">'+h.label+'</button>').join('');

    // 분양소 (마리수 제한 없이, req12) — 같은 종류도 여러 번 분양 가능
    const adoptCards=PETS.map(p=>
      '<div class="pet-card">'+
        '<div class="pet-emoji">'+p.emoji+'</div><strong>'+p.name+'</strong>'+
        '<button class="chip" data-adopt="'+p.type+'">분양 '+p.price+'🪙</button>'+
      '</div>').join('');
    // 내 반려동물 목록 (동행 최대 2마리, 키우기 창 연결)
    const activeIds=state.pet.active||[];
    const myPetList=(state.pet.adopted||[]).length
      ? (state.pet.adopted).map(pd=>{
          const info=PETS.find(x=>x.type===pd.type)||PETS[0];
          const isActive=activeIds.includes(pd.id);
          const stageTxt=pd.complete?'완전체 🏆':(pd.stage+'단계');
          return '<div class="pet-list-card '+(isActive?'on':'')+'">'+
            '<div class="plc-ico">'+petBodySvg(pd.type, pd.stage)+'</div>'+
            '<div><strong>'+info.name+'</strong> '+(pd.complete?'<span class="pet-badge-done">완전체</span>':'')+
              '<div class="aff-track" style="margin:5px 0 3px"><i style="--aff:'+Math.round(pd.affection)+'%"></i></div>'+
              '<small class="tiny">'+stageTxt+' · 교감 '+Math.round(pd.affection)+'%</small></div>'+
            '<div style="display:grid;gap:4px">'+
              '<button class="chip '+(isActive?'on':'')+'" data-petactive="'+pd.id+'">'+(isActive?'동행중':'동행')+'</button>'+
              '<button class="chip" data-petcare="'+pd.id+'">키우기</button>'+
            '</div>'+
          '</div>';
        }).join('')
      : '<div class="empty">아직 분양받은 반려동물이 없어요. 위에서 분양받아 보세요 🐾</div>';

    app.innerHTML =
      '<div class="section-title"><h3>아바타 꾸미기</h3><span>나만의 캐릭터</span></div>'+
      '<div class="avatar-big" id="avaPreview">'+avatarSvg(true)+'</div>'+
      // 성별 선택 (req2)
      '<div class="panel" style="margin-top:12px"><h3 style="margin-bottom:8px">성별</h3>'+
        '<div class="opt-row">'+
          '<button class="chip '+(a.gender!=='female'?'on':'')+'" data-gender="male">👨 남자</button>'+
          '<button class="chip '+(a.gender==='female'?'on':'')+'" data-gender="female">👩 여자</button>'+
        '</div>'+
        '<h3 style="margin:14px 0 8px">피부색</h3><div class="swatches">'+skinSw+'</div>'+
        '<h3 style="margin:14px 0 8px">머리카락 색</h3><div class="swatches">'+hairSw+'</div>'+
        '<h3 style="margin:14px 0 8px">옷(스웨터) 색</h3><div class="swatches">'+outSw+'</div>'+
        '<h3 style="margin:14px 0 8px">모자·장식</h3><div class="opt-row">'+hatCh+'</div>'+
        '<h3 style="margin:14px 0 8px">악세사리</h3><div class="opt-row">'+
          '<button class="chip '+(a.glasses?'on':'')+'" data-glasses="1">👓 안경 '+(a.glasses?'착용':'벗기')+'</button>'+
        '</div></div>'+
      '<div class="section-title"><h3>반려동물 분양소</h3><span>마리수 제한 없이</span></div>'+
      '<div class="pet-grid">'+adoptCards+'</div>'+
      '<div class="section-title"><h3>내 반려동물</h3><span>동행 최대 2마리</span></div>'+
      myPetList+
      '<p class="tiny" style="margin-top:12px">분양받은 반려동물은 <b>정원에서 자유롭게</b> 돌아다녀요. <b>동행</b>으로 설정하면 주인을 따라다니고, <b>키우기</b>로 놀아주면 성장해요(5단계 완전체까지!).</p>';

    app.querySelectorAll('[data-gender]').forEach(b=>b.addEventListener('click',()=>{ applyGenderLook(state.avatar, b.dataset.gender); Sound.tap(); save(); renderAvatar(); }));
    app.querySelectorAll('[data-glasses]').forEach(b=>b.addEventListener('click',()=>{ state.avatar.glasses=!state.avatar.glasses; Sound.tap(); save(); renderAvatar(); }));
    app.querySelectorAll('[data-skin]').forEach(b=>b.addEventListener('click',()=>{ state.avatar.skin=b.dataset.skin; save(); renderAvatar(); }));
    app.querySelectorAll('[data-hair]').forEach(b=>b.addEventListener('click',()=>{ state.avatar.hair=b.dataset.hair; save(); renderAvatar(); }));
    app.querySelectorAll('[data-outfit]').forEach(b=>b.addEventListener('click',()=>{ state.avatar.outfit=b.dataset.outfit; save(); renderAvatar(); }));
    app.querySelectorAll('[data-hat]').forEach(b=>b.addEventListener('click',()=>{ state.avatar.hat=b.dataset.hat; save(); renderAvatar(); }));
    // 분양 (req12: 마리수 제한 없이, 같은 종류도 여러 번)
    app.querySelectorAll('[data-adopt]').forEach(b=>b.addEventListener('click',()=>{
      const p=PETS.find(x=>x.type===b.dataset.adopt);
      if(state.coins<p.price){ toast('코인이 부족해요'); return; }
      addCoins(-p.price);
      const id='p'+(++state.pet.seq);
      state.pet.adopted.push({ id, type:p.type, affection:20, stage:1, complete:false, rewarded:false });
      if((state.pet.active||[]).length<2) state.pet.active.push(id); // 동행 여유가 있으면 자동 동행
      Sound.coin(); save(); toast(p.name+'를 분양받았어요! 🎉 정원에서 만나요'); renderAvatar();
    }));
    // 동행 토글 (req14, 최대 2마리)
    app.querySelectorAll('[data-petactive]').forEach(b=>b.addEventListener('click',()=>{ toggleActive(b.dataset.petactive); renderAvatar(); }));
    // 키우기 창 열기 (req16)
    app.querySelectorAll('[data-petcare]').forEach(b=>b.addEventListener('click',()=>{ Sound.tap(); openPetCare(b.dataset.petcare); }));
  }

  /* ============================================================
     4) 함께하기 (연동형 · 단체 미션 · 공동 작물 · 세상 꾸미기)
     ============================================================ */
  const FRIENDS=[
    {n:'복순',c:'#3a72b8',e:'👵'},{n:'영호',c:'#5b8d3a',e:'👴'},{n:'미자',c:'#d7644f',e:'👵'},
    {n:'상철',c:'#d99a25',e:'👴'},{n:'정순',c:'#7a4fd7',e:'👵'},
  ];
  const DECOS=[ {id:'bench',e:'🪑',name:'벤치',price:30}, {id:'fountain',e:'⛲',name:'분수',price:60}, {id:'lamp',e:'🏮',name:'가로등',price:20}, {id:'flower',e:'🌷',name:'꽃밭',price:15}, {id:'bridge',e:'🌉',name:'다리',price:80} ];

  function renderCoop(){
    ensureDaily();
    const ch=todayChallenge();
    const c=state.coop;
    const missionNow=Math.min(c.mission.goal, c.mission.base + c.myContribGame*1);
    const missionPct=Math.round(missionNow/c.mission.goal*100);
    const fieldNow=Math.min(c.field.goal, c.field.base + c.myContribField*2);
    const fieldPct=Math.round(fieldNow/c.field.goal*100);

    const friendStrip=FRIENDS.map(f=>'<div class="friend-ava"><div class="fa-face" style="background:'+f.c+'">'+f.e+'</div><small>'+f.n+'</small></div>').join('')+
      '<div class="friend-ava"><div class="fa-face" style="background:var(--teal)">🙂</div><small>나</small></div>';

    const decoOwned=c.decos.map(id=>{ const d=DECOS.find(x=>x.id===id); return d?d.e:''; }).join(' ')||'아직 없음';
    const decoBtns=DECOS.map(d=>{
      const owned=c.decos.includes(d.id);
      return '<button class="chip '+(owned?'on':'')+'" data-deco="'+d.id+'">'+d.e+' '+d.name+(owned?' ✓':' '+d.price+'🪙')+'</button>';
    }).join('');

    // 커뮤니티 피드 (req14)
    const feed=COMMUNITY.map((f,i)=>{
      const cheered=state.cheers['c'+i];
      return '<div class="feed-item"><div class="feed-face" style="background:'+f.c+'">'+f.e+'</div>'+
        '<div><p><b>'+f.n+'</b> · '+esc(f.t)+'</p><small>방금 전</small><br>'+
        '<button class="cheer-btn" data-cheer="'+i+'">'+(cheered?'💚 응원함':'👏 응원하기')+'</button></div></div>';
    }).join('');

    app.innerHTML =
      '<div class="section-title"><h3>함께하는 마을 친구들</h3><span>온라인 '+ (FRIENDS.length+1) +'명</span></div>'+
      '<div class="panel"><div class="friend-strip">'+friendStrip+'</div></div>'+

      // 오늘의 도전과제 (req14)
      '<div class="section-title"><h3>🗓️ 오늘의 도전과제</h3><span>'+(state.daily.done?'완료 ✓':'+'+ch.reward+'P')+'</span></div>'+
      '<div class="challenge"><div class="ch-emoji">'+ch.emoji+'</div>'+
        '<div><strong>'+esc(ch.title)+'</strong><p class="tiny" style="margin:2px 0 0">매일 자정에 새로운 도전과제로 바뀌어요</p></div>'+
        '<span class="status-pill '+(state.daily.done?'done':'')+'">'+(state.daily.done?'완료':'+'+ch.reward)+'</span></div>'+

      '<div class="section-title"><h3>🎯 단체 미션</h3><span>'+missionPct+'%</span></div>'+
      '<div class="panel"><p style="margin:0 0 8px;color:var(--ink);font-weight:700">'+esc(c.mission.title)+'</p>'+
        '<div class="progress-track"><div class="progress-fill" style="--progress:'+missionPct+'%"></div></div>'+
        '<p class="tiny" style="margin:8px 0 0">'+missionNow+' / '+c.mission.goal+'판 · 내 기여 '+c.myContribGame+'판</p>'+
        '<button class="primary-button full-width" data-mgo style="margin-top:10px">두뇌 게임으로 기여하기</button>'+
        (missionPct>=100?'<div class="banner-reward" style="margin-top:10px"><strong>단체 미션 달성! 🎉</strong><br>참여 보상 +100 코인을 받으세요.<br><button class="secondary-button full-width" data-mreward style="margin-top:8px;color:#2b3d6b">보상 받기</button></div>':'')+
      '</div>'+

      '<div class="section-title"><h3>🌾 공동 작물 밭</h3><span>'+fieldPct+'%</span></div>'+
      '<div class="panel"><p class="tiny" style="margin:0 0 8px">마을 친구들과 함께 키우는 공동 밭이에요. 다 자라면 모두 코인을 나눠 가져요.</p>'+
        '<div class="progress-track"><div class="progress-fill" style="--progress:'+fieldPct+'%"></div></div>'+
        '<p class="tiny" style="margin:8px 0 0">내 물주기 기여 '+c.myContribField+'회</p>'+
        '<button class="secondary-button full-width" data-fgo style="margin-top:10px">💧 공동 밭에 물주기 (-8)</button>'+
        (fieldPct>=100?'<button class="primary-button full-width" data-freward style="margin-top:8px">🧺 공동 수확 나눔 받기 (+90)</button>':'')+
      '</div>'+

      '<div class="section-title"><h3>🏘️ 우리 마을</h3><span>공용 마을</span></div>'+
      '<div class="panel"><div class="avatar-big" style="min-height:110px;display:grid;place-items:center;font-size:44px">🏘️🌳🧑‍🌾</div>'+
        '<p class="tiny" style="margin:10px 0">마을 친구들과 함께 모여 <b>나의 정원처럼 같이 꾸미고</b>, <b>단체로 게임</b>할 수 있는 공용 마을이에요.</p>'+
        '<button class="primary-button full-width" data-village-enter>🏘️ 마을 들어가기</button></div>'+

      // 커뮤니티 (req14)
      '<div class="section-title"><h3>💬 마을 커뮤니티</h3><span>이웃 소식</span></div>'+
      '<div class="panel">'+feed+'</div>';

    $('[data-mgo]',app).addEventListener('click',()=>setTab('brain'));
    app.querySelectorAll('[data-cheer]').forEach(b=>b.addEventListener('click',()=>{
      const k='c'+b.dataset.cheer;
      if(state.cheers[k]){ toast('이미 응원했어요'); return; }
      state.cheers[k]=true; addCoins(2); Sound.tap(); bumpDaily('cheer'); save();
      toast('👏 이웃을 응원했어요! +2'); renderCoop();
    }));
    const mr=$('[data-mreward]',app); if(mr) mr.addEventListener('click',()=>{ addCoins(100); c.mission.base=c.mission.goal; save(); toast('단체 미션 보상 +100!'); renderCoop(); });
    $('[data-fgo]',app).addEventListener('click',()=>{ if(state.coins<8){toast('코인이 부족해요');return;} addCoins(-8); c.myContribField++; save(); toast('공동 밭에 물을 줬어요 💧'); renderCoop(); });
    const fr=$('[data-freward]',app); if(fr) fr.addEventListener('click',()=>{ addCoins(90); c.field.base=0; c.myContribField=0; save(); toast('공동 수확 나눔 +90!'); renderCoop(); });
    const ve=$('[data-village-enter]',app); if(ve) ve.addEventListener('click',()=>enterCommonVillage());
  }

  /* ── 공용 마을 (마을 들어가기, req15) ── */
  function enterCommonVillage(){
    if (villageCleanup){ villageCleanup(); villageCleanup=null; }
    if(!state.coop.layout) state.coop.layout={};
    app.classList.add('flush');
    $('#topTitle').textContent='우리 마을 (공용)';
    app.innerHTML =
      '<div class="village-wrap">'+
        '<div id="villageCanvas"></div>'+
        '<div class="vil-hud">'+
          '<span class="vil-tag">🏘️ 우리 마을 · 친구 4명</span>'+
          '<span class="vil-tag">🪙 '+nf(state.coins)+'</span>'+
        '</div>'+
        '<div class="sail-banner" id="sailBanner">⛵ 항해 중 · 제주 바다에서 한라산 풍경을 둘러보세요</div>'+
        '<div class="vil-prompt hidden" id="vilPrompt">🌱 도착!</div>'+
        '<div class="move-hint" id="moveHint">🎮 PC: 방향키/클릭 이동 · 📱 모바일: 화면을 밀어 이동 · ✋배치로 함께 꾸며요</div>'+
        '<button class="edit-btn" id="editBtn" type="button" title="배치 편집">✋ 배치</button>'+
        '<button class="disembark-btn hidden" id="disembarkBtn" type="button">🚣 배에서 내리기</button>'+
        '<button class="act-btn" id="actBtn" title="음성"><svg viewBox="0 0 24 24"><path d="M12 15a3 3 0 0 0 3-3V6a3 3 0 0 0-6 0v6a3 3 0 0 0 3 3Zm5-3a5 5 0 0 1-10 0H5a7 7 0 0 0 6 6.9V21h2v-2.1A7 7 0 0 0 19 12h-2Z"/></svg><span>음성</span></button>'+
        // 공용 마을 전용: 나가기 + 단체 게임
        '<button class="common-exit" id="commonExit" type="button">← 마을 나가기</button>'+
        '<button class="common-game" id="commonGame" type="button">🧠 단체 게임 시작</button>'+
      '</div>';
    const container = $('#villageCanvas');
    const ex=$('#commonExit'); if(ex) ex.addEventListener('click',()=>{ Sound.tap(); setTab('coop'); });
    const gm=$('#commonGame'); if(gm) gm.addEventListener('click',()=>{ toast('🧠 마을 단체 게임 시작! 함께 점수를 모아요'); setTab('brain'); });
    initVillage(container, { communal:true, layout: state.coop.layout }).then(cleanup => { villageCleanup = cleanup; });
    setTimeout(()=>{ const h=$('#moveHint'); if(h) h.style.display='none'; }, 6000);
  }

  /* ============================================================
     5) 랭킹 (친구 경쟁)
     ============================================================ */
  function myRankScore(){ return avgScore()*10 + state.coins + state.streak*20 + state.brain.stats.attention.length*3; }
  const RIVALS=[
    {n:'복순 여사',base:940,e:'👵'},{n:'영호 형님',base:880,e:'👴'},{n:'미자 언니',base:1010,e:'👵'},
    {n:'상철 아재',base:790,e:'👴'},{n:'정순 이모',base:1120,e:'👵'},{n:'광수 삼촌',base:700,e:'👴'},{n:'순자 할매',base:1180,e:'👵'},
  ];
  function renderRank(){
    const me={ n:'나', e:'🙂', score: myRankScore(), me:true };
    const list=RIVALS.map(r=>({ n:r.n, e:r.e, score: r.base + (state.streak*3) })).concat(me)
      .sort((a,b)=>b.score-a.score);
    const myPos=list.findIndex(x=>x.me)+1;
    const [p1,p2,p3]=list;

    const rows=list.map((x,i)=>
      '<div class="rank-row '+(x.me?'me':'')+'"><div class="rank-no">'+(i+1)+'</div>'+
        '<div>'+x.e+' '+esc(x.n)+'</div><strong>'+nf(x.score)+'점</strong></div>').join('');

    app.innerHTML =
      '<div class="section-title"><h3>주간 랭킹</h3><span>친구 '+RIVALS.length+'명과 경쟁</span></div>'+
      '<div class="panel"><div class="podium">'+
        '<div class="pod p2"><div class="medal">🥈</div><div class="pn">'+esc(p2.n)+'</div><div class="ps">'+nf(p2.score)+'</div></div>'+
        '<div class="pod p1"><div class="medal">🥇</div><div class="pn">'+esc(p1.n)+'</div><div class="ps">'+nf(p1.score)+'</div></div>'+
        '<div class="pod p3"><div class="medal">🥉</div><div class="pn">'+esc(p3.n)+'</div><div class="ps">'+nf(p3.score)+'</div></div>'+
      '</div>'+
      '<div class="banner-reward" style="margin:0"><strong>내 순위 '+myPos+'위 / '+list.length+'명</strong><br>'+
        (myPos<=3?'대단해요! 상위권을 지키고 있어요 🏆':'게임·루틴·연속출석으로 점수를 올려 순위를 높여보세요!')+'</div>'+
      '</div>'+
      '<div class="panel" style="margin-top:12px"><h3 style="margin-bottom:6px">전체 순위표</h3>'+rows+'</div>'+
      '<div class="panel" style="margin-top:12px"><h3 style="margin-bottom:6px">점수 올리는 법</h3>'+
        '<p class="tiny" style="margin:0">인지 점수 ×10 + 보유 코인 + 연속 출석 ×20 + 두뇌 게임 참여도로 랭킹 점수가 계산돼요. 두뇌 탭과 마을 활동을 꾸준히!</p></div>';
  }

  /* ============================================================
     8-b) 취침모드 + 수면 미션 (요구사항 1)
     ============================================================ */
  const sleepOverlay=$('#sleepOverlay');
  function nowHour(){ return state.forceNight ? 23 : new Date().getHours(); }
  function isSleepTime(){ if(state.sleepOff) return false; const h=nowHour(); return h>=23 || h<6; } // 일시중지 시 취침모드 진입 안 함
  function showSleep(){
    sleepOverlay.classList.add('show');
    const stars=$('#stars');
    if(!stars.dataset.filled){ let s=''; for(let i=0;i<40;i++){ s+='<i style="left:'+rand(100)+'%;top:'+rand(100)+'%;animation-delay:'+(rand(25)/10)+'s"></i>'; } stars.innerHTML=s; stars.dataset.filled='1'; }
    const h=nowHour();
    $('#sleepClock').textContent='현재 '+String(h).padStart(2,'0')+':00 · 아침 6시에 다시 열려요';
  }
  function hideSleep(){ sleepOverlay.classList.remove('show'); }
  function checkSleep(){ if(isSleepTime()) showSleep(); else hideSleep(); }

  function todayStr(){ const d=new Date(); return d.getFullYear()+'-'+(d.getMonth()+1)+'-'+d.getDate(); }
  function checkSleepMission(){
    const now=Date.now();
    if(state.lastPlayTs){
      const gapH=(now-state.lastPlayTs)/3600000;
      if(gapH>=8 && state.sleepClaimedDate!==todayStr()){
        grantSleepMission(gapH);
      }
    }
  }
  function grantSleepMission(gapH){
    state.sleepClaimedDate=todayStr(); addCoins(50); save();
    setTimeout(()=>{
      if(activeTab && RENDER[activeTab]){ /* 배너는 토스트로 */ }
      toast('🌙 취침 미션 완료! 푹 주무셨네요 · +50 코인');
    }, 400);
  }
  function touchPlay(){ state.lastPlayTs=Date.now(); save(); }

  /* ============================================================
     설정 다이얼로그 / 초기화 / 공통
     ============================================================ */
  const menuDialog=$('#menuDialog');
  // 개발 모드 칩 상태 동기화 (취침모드 일시중지 / 코인 무제한)
  function syncDevChips(){
    const s=$('#sleepOffToggle'); if(s){ s.classList.toggle('on', !!state.sleepOff); s.textContent = state.sleepOff ? '🌙 취침모드 중지됨' : '🌙 취침모드 일시중지'; }
    const c=$('#coinUnlimitedToggle'); if(c){ c.classList.toggle('on', !!state.unlimitedCoins); c.textContent = state.unlimitedCoins ? '🪙 코인 무제한 (켜짐)' : '🪙 코인 무제한'; }
  }
  $('#menuButton').addEventListener('click',()=>{
    $('#nightToggle').classList.toggle('on', state.forceNight);
    $('#nightToggle').textContent = state.forceNight ? '🌙 밤 시뮬레이션 (켜짐)' : '🌙 밤 시뮬레이션';
    syncDevChips();
    if(typeof menuDialog.showModal==='function') menuDialog.showModal();
  });
  $('#sleepOffToggle').addEventListener('click',()=>{
    state.sleepOff=!state.sleepOff; save(); syncDevChips(); checkSleep();
    toast(state.sleepOff ? '🌙 취침모드를 일시중지했어요 (다시 켤 때까지 취침 안 함)' : '🌙 취침모드를 다시 켰어요');
  });
  $('#coinUnlimitedToggle').addEventListener('click',()=>{
    state.unlimitedCoins=!state.unlimitedCoins;
    if(state.unlimitedCoins) state.coins=9999999;
    save(); syncDevChips(); syncCoins();
    toast(state.unlimitedCoins ? '🪙 코인 무제한 켜짐' : '🪙 코인 무제한 끔');
  });
  $('#nightToggle').addEventListener('click',()=>{
    state.forceNight=!state.forceNight; save();
    $('#nightToggle').classList.toggle('on', state.forceNight);
    $('#nightToggle').textContent = state.forceNight ? '🌙 밤 시뮬레이션 (켜짐)' : '🌙 밤 시뮬레이션';
    menuDialog.close(); checkSleep();
    if(state.forceNight) toast('밤 시뮬레이션 켜짐 · 취침모드');
    else { toast('낮으로 전환'); }
  });
  $('#sleepTestBtn').addEventListener('click',()=>{
    menuDialog.close();
    state.lastPlayTs = Date.now() - 9*3600000; state.sleepClaimedDate=null; save();
    checkSleepMission();
  });

  // 음소거 칩 (코인 옆, req8)
  function syncMute(){ const m=$('#muteChip'); if(!m) return; m.classList.toggle('off', state.muted); m.firstChild.textContent = state.muted?'🔇 ':'🔊 '; $('#muteLabel').textContent = state.muted?'음소거':'소리'; }
  $('#muteChip').addEventListener('click',()=>{
    Sound.muteAll(!state.muted); save(); syncMute();
    if(!state.muted){ Sound.resume(); if(activeTab==='village') Sound.windStart(); }
    toast(state.muted?'효과음 껐어요':'효과음 켰어요');
  });

  document.querySelectorAll('[data-close]').forEach(b=>b.addEventListener('click',()=>{ b.closest('dialog').close(); }));
  farmDialog.addEventListener('close',()=>{ cancelAnimationFrame(farmRaf); });

  $('#resetButton').addEventListener('click',()=>{
    if(!confirm('모든 진행 데이터를 초기화할까요?')) return;
    state=defaultState(); save(); toast('초기화했어요'); syncCoins(); setTab('village');
  });

  // 주기적 취침 체크
  setInterval(checkSleep, 60000);
  window.addEventListener('beforeunload', ()=>{ state.lastPlayTs=Date.now(); save(); });

  // 첫 사용자 상호작용 시 오디오 컨텍스트 활성화 (브라우저 자동재생 정책, req19)
  const armAudio=()=>{ Sound.resume(); if(!state.muted) Sound.windStart(); window.removeEventListener('pointerdown',armAudio); window.removeEventListener('keydown',armAudio); };
  window.addEventListener('pointerdown',armAudio); window.addEventListener('keydown',armAudio);

  /* ============================================================
     시작
     ============================================================ */
  syncCoins();
  syncMute();
  ensureDaily();
  checkSleepMission();
  checkSleep();
  setTab('village');

  // 로딩 스플래시 6초 후 정원으로 (요구사항11-27)
  setTimeout(()=>{
    const s=$('#splash');
    if(s){ s.classList.add('hide'); setTimeout(()=>{ if(s.parentElement) s.remove(); }, 650); }
  }, 6000);
  </script>
</body>
</html>

[index (3).html](https://github.com/user-attachments/files/28263847/index.3.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="SafetyMS">
<link rel="apple-touch-icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><rect width='100' height='100' rx='20' fill='%2300d4a0'/><text y='.9em' font-size='72' x='12' fill='black' font-weight='900'>S</text></svg>">
<meta name="theme-color" content="#0f1117">
<meta name="description" content="Occupational Safety Management System">
<title>Safety System</title>
<link rel="manifest" href="#" id="pwa-manifest">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.2/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.8.2/jspdf.plugin.autotable.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
<style>
:root{
  --bg:#0f1117;--bg2:#161b25;--bg3:#1e2535;--bg4:#252d40;
  --border:#2a3350;--border2:#3a4560;
  --text:#e8eaf0;--text2:#8b92a8;--text3:#4a5270;
  --teal:#00d4a0;--teal2:#00a87d;--tealb:rgba(0,212,160,.12);
  --red:#ff4d6d;--red2:#cc3355;--redb:rgba(255,77,109,.12);
  --amber:#ffaa00;--amberb:rgba(255,170,0,.12);
  --blue:#4d9fff;--blueb:rgba(77,159,255,.12);
  --purple:#9d7dff;--purpleb:rgba(157,125,255,.12);
  --r:8px;--r2:12px;--r3:18px;
  --sidebar:220px;
}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html{height:100%}
body{background:var(--bg);color:var(--text);font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',system-ui,sans-serif;min-height:100%;display:flex;font-size:14px;overflow-x:hidden}
::-webkit-scrollbar{width:4px;height:4px}
::-webkit-scrollbar-thumb{background:var(--border2);border-radius:2px}

/* ── LOGIN ── */
#login-screen{position:fixed;inset:0;background:var(--bg);z-index:9000;display:flex;align-items:center;justify-content:center;padding:20px;overflow-y:auto}
#login-screen.hidden{display:none}
.ll-wrap{width:100%;max-width:400px;margin:auto}
.ll-logo{display:flex;align-items:center;gap:12px;justify-content:center;margin-bottom:28px}
.ll-icon{width:48px;height:48px;border-radius:14px;background:var(--teal);display:flex;align-items:center;justify-content:center;font-size:22px;font-weight:900;color:#000;flex-shrink:0}
.ll-name{font-size:20px;font-weight:800;color:var(--text)}
.ll-sub{font-size:11px;color:var(--text3);margin-top:1px}
.ll-card{background:var(--bg2);border:1px solid var(--border);border-radius:20px;padding:24px}
.ll-title{font-size:18px;font-weight:700;margin-bottom:4px}
.ll-subtitle{font-size:12px;color:var(--text2);margin-bottom:20px}
.lf{margin-bottom:13px}
.lf-lbl{font-size:10px;font-weight:700;color:var(--text2);text-transform:uppercase;letter-spacing:.06em;margin-bottom:5px;display:flex;justify-content:space-between;align-items:center}
.lf-inp,.lf-sel{width:100%;background:var(--bg3);border:1.5px solid var(--border);border-radius:var(--r);padding:11px 13px;font-size:14px;color:var(--text);font-family:inherit;transition:border-color .18s;-webkit-appearance:none;appearance:none}
.lf-inp:focus,.lf-sel:focus{outline:none;border-color:var(--teal);background:var(--bg4)}
.lf-inp.err{border-color:var(--red)!important;animation:shake .3s}
@keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-6px)}75%{transform:translateX(6px)}}
.lf-sel{cursor:pointer}
.ll-btn{width:100%;padding:13px;background:var(--teal);color:#000;font-size:14px;font-weight:700;border:none;border-radius:var(--r);cursor:pointer;transition:all .15s;margin-top:4px}
.ll-btn:hover{background:var(--teal2)}
.ll-btn:active{transform:scale(.98)}
.ll-err{background:var(--redb);border:1px solid rgba(255,77,109,.3);border-radius:var(--r);padding:10px 13px;font-size:12px;color:var(--red);margin-top:10px;display:none;align-items:center;gap:7px}
.ll-err.show{display:flex}
.ll-quick{margin-top:18px;border-top:1px solid var(--border);padding-top:14px}
.ll-quick-title{font-size:9px;font-weight:700;color:var(--text3);text-transform:uppercase;letter-spacing:.08em;margin-bottom:8px}
.qu{display:flex;align-items:center;gap:9px;width:100%;padding:8px 11px;background:var(--bg3);border:1px solid var(--border);border-radius:var(--r);cursor:pointer;transition:all .14s;margin-bottom:5px;text-align:left}
.qu:hover,.qu:active{border-color:var(--teal);background:var(--bg4)}
.qu-av{width:28px;height:28px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:800;flex-shrink:0}
.qu-name{font-size:12px;font-weight:600;color:var(--text)}
.qu-role{font-size:10px;color:var(--text3)}
.qu-badge{margin-left:auto;font-size:9px;font-weight:700;padding:2px 6px;border-radius:8px}

/* ── LAYOUT ── */
#app{display:none;width:100%;min-height:100vh;position:relative}
#app.visible{display:flex}

/* ── SIDEBAR ── */
#sidebar{width:var(--sidebar);min-height:100vh;background:var(--bg2);border-right:1px solid var(--border);display:flex;flex-direction:column;flex-shrink:0;position:sticky;top:0;height:100vh;overflow-y:auto;z-index:200;transition:transform .3s}
.logo-area{padding:16px 14px 12px;border-bottom:1px solid var(--border);display:flex;align-items:center;gap:9px}
.logo-ic{width:32px;height:32px;border-radius:9px;background:var(--teal);display:flex;align-items:center;justify-content:center;font-size:16px;font-weight:900;color:#000;flex-shrink:0}
.logo-nm{font-size:12px;font-weight:700;color:var(--text);line-height:1.2}
.logo-vr{font-size:10px;color:var(--text3)}
.s-sec{padding:10px 12px 4px;font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.1em;color:var(--text3)}
.ni{display:flex;align-items:center;gap:8px;padding:8px 11px;border-radius:var(--r);margin:1px 5px;cursor:pointer;color:var(--text2);font-size:12px;font-weight:500;transition:all .13s;user-select:none;position:relative}
.ni:hover{background:var(--bg3);color:var(--text)}
.ni.active{background:var(--tealb);color:var(--teal);border:1px solid rgba(0,212,160,.2)}
.ni-ic{font-size:15px;flex-shrink:0;width:18px;text-align:center}
.ni-badge{margin-left:auto;background:var(--red);color:#fff;font-size:9px;font-weight:700;padding:1px 5px;border-radius:20px;min-width:16px;text-align:center}
.sb-bot{margin-top:auto;padding:10px;border-top:1px solid var(--border)}
.user-pill{display:flex;align-items:center;gap:8px;padding:8px 10px;background:var(--bg3);border-radius:var(--r);cursor:pointer;margin-bottom:6px;transition:background .13s}
.user-pill:hover{background:var(--bg4)}
.ua{width:28px;height:28px;border-radius:50%;font-size:10px;font-weight:800;display:flex;align-items:center;justify-content:center;flex-shrink:0;color:#000}
.un{font-size:11px;font-weight:600;color:var(--text)}
.ur{font-size:10px;color:var(--text3)}

/* ── MOBILE HEADER ── */
#mob-header{display:none;position:sticky;top:0;z-index:150;background:var(--bg2);border-bottom:1px solid var(--border);padding:10px 14px;align-items:center;gap:10px}
#mob-menu-btn{width:36px;height:36px;border-radius:var(--r);background:var(--bg3);border:1px solid var(--border);display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:16px;flex-shrink:0}
#mob-title{font-size:14px;font-weight:700;color:var(--text);flex:1}
#mob-user-btn{width:32px;height:32px;border-radius:50%;font-size:11px;font-weight:800;display:flex;align-items:center;justify-content:center;cursor:pointer;flex-shrink:0;color:#000}
#mob-overlay{display:none;position:fixed;inset:0;background:rgba(0,0,0,.6);z-index:190}
#mob-overlay.show{display:block}

/* ── MAIN ── */
#main{flex:1;overflow-y:auto;background:var(--bg);min-width:0}
.page{display:none;padding:20px 22px 40px}
.page.active{display:block}
.ph{margin-bottom:18px;display:flex;align-items:flex-start;justify-content:space-between;gap:10px;flex-wrap:wrap}
.pt{font-size:20px;font-weight:700;letter-spacing:-.3px}
.ps{font-size:11.5px;color:var(--text2);margin-top:3px}
.top-row{display:flex;align-items:center;gap:6px;flex-wrap:wrap}

/* ── KPI CARDS ── */
.kgrid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;margin-bottom:14px}
.kc{background:var(--bg2);border:1px solid var(--border);border-radius:var(--r2);padding:13px 15px;position:relative;overflow:hidden}
.kc::after{content:'';position:absolute;bottom:0;left:0;right:0;height:3px}
.kc.r::after{background:var(--red)}.kc.t::after{background:var(--teal)}
.kc.a::after{background:var(--amber)}.kc.b::after{background:var(--blue)}
.kl{font-size:9.5px;color:var(--text3);text-transform:uppercase;letter-spacing:.07em;font-weight:700;margin-bottom:5px}
.kv{font-size:22px;font-weight:700;line-height:1;margin-bottom:3px}
.kc.r .kv{color:var(--red)}.kc.t .kv{color:var(--teal)}
.kc.a .kv{color:var(--amber)}.kc.b .kv{color:var(--blue)}
.kd{font-size:10px;color:var(--text3)}

/* ── CHARTS ── */
.cgrid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:14px}
.cgrid3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:14px}
.cc{background:var(--bg2);border:1px solid var(--border);border-radius:var(--r2);padding:13px 15px}
.ct{font-size:12px;font-weight:700;color:var(--text);margin-bottom:2px}
.cs{font-size:10px;color:var(--text3);margin-bottom:8px}

/* ── TABLES ── */
.tw{border:1px solid var(--border);border-radius:var(--r2);overflow:hidden;margin-bottom:12px;overflow-x:auto}
.tw table{width:100%;border-collapse:collapse;min-width:400px}
.tw th{background:var(--bg3);padding:8px 11px;text-align:left;font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.06em;color:var(--text3);border-bottom:1px solid var(--border);white-space:nowrap}
.tw td{padding:8px 11px;font-size:12px;color:var(--text);border-bottom:1px solid var(--border);vertical-align:middle}
.tw tr:last-child td{border-bottom:none}
.tw tr:hover td{background:rgba(255,255,255,.02)}

/* ── BADGE ── */
.badge{font-size:9.5px;font-weight:700;padding:2px 7px;border-radius:20px;white-space:nowrap;display:inline-block}
.badge.r{background:var(--redb);color:var(--red);border:1px solid rgba(255,77,109,.25)}
.badge.t{background:var(--tealb);color:var(--teal);border:1px solid rgba(0,212,160,.25)}
.badge.a{background:var(--amberb);color:var(--amber);border:1px solid rgba(255,170,0,.25)}
.badge.b{background:var(--blueb);color:var(--blue);border:1px solid rgba(77,159,255,.25)}
.badge.p{background:var(--purpleb);color:var(--purple);border:1px solid rgba(157,125,255,.25)}

/* ── ALERTS ── */
.ai{background:var(--bg2);border:1px solid var(--border);border-left:3px solid transparent;border-radius:var(--r2);padding:11px 13px;display:flex;align-items:center;gap:10px;margin-bottom:7px}
.ai.crit{border-left-color:var(--red)}.ai.warn{border-left-color:var(--amber)}
.ai-ic{width:34px;height:34px;border-radius:8px;display:flex;align-items:center;justify-content:center;font-size:15px;flex-shrink:0}
.ai-ic.r{background:var(--redb)}.ai-ic.a{background:var(--amberb)}
.ai-body{flex:1;min-width:0}
.ai-title{font-size:12px;font-weight:700;color:var(--text)}
.ai-sub{font-size:11px;color:var(--text3);line-height:1.4}

/* ── PROGRESS ── */
.pw{display:flex;align-items:center;gap:6px}
.pb{flex:1;height:5px;background:var(--bg4);border-radius:3px;overflow:hidden;min-width:40px}
.pf{height:100%;border-radius:3px;transition:width .5s}

/* ── FORMS ── */
.fg{display:grid;grid-template-columns:1fr 1fr;gap:11px}
.fgr{display:flex;flex-direction:column;gap:4px}
.fgr.full{grid-column:1/-1}
.flbl{font-size:10px;font-weight:700;color:var(--text2);text-transform:uppercase;letter-spacing:.05em}
.fi,.fs,.ft{background:var(--bg3);border:1.5px solid var(--border);border-radius:var(--r);padding:9px 11px;font-size:13px;color:var(--text);font-family:inherit;width:100%;transition:border-color .15s;-webkit-appearance:none}
.fi:focus,.fs:focus,.ft:focus{outline:none;border-color:var(--teal);background:var(--bg4)}
.ft{min-height:70px;resize:vertical;line-height:1.5}
.fi::placeholder,.ft::placeholder{color:var(--text3)}

/* ── BUTTONS ── */
.btn{display:inline-flex;align-items:center;gap:5px;padding:8px 14px;border-radius:var(--r);font-size:12px;font-weight:600;cursor:pointer;border:none;transition:all .13s;white-space:nowrap;font-family:inherit}
.btn:active{transform:scale(.97)}
.btn-p{background:var(--teal);color:#000}.btn-p:hover{background:var(--teal2)}
.btn-r{background:var(--red);color:#fff}.btn-r:hover{background:var(--red2)}
.btn-a{background:var(--amber);color:#000}
.btn-g{background:var(--bg3);color:var(--text);border:1px solid var(--border)}.btn-g:hover{border-color:var(--border2);background:var(--bg4)}
.btn-sm{padding:5px 10px;font-size:11px}
.btn-icon{padding:6px;border-radius:var(--r);background:var(--bg3);border:1px solid var(--border);cursor:pointer;color:var(--text2);transition:all .13s}
.btn-icon:hover{color:var(--teal);border-color:var(--teal)}

/* ── MODAL ── */
.mo{display:none;position:fixed;inset:0;background:rgba(0,0,0,.75);z-index:2000;align-items:center;justify-content:center;padding:16px}
.mo.open{display:flex}
.md{background:var(--bg2);border:1px solid var(--border);border-radius:var(--r3);padding:22px;width:100%;max-width:540px;max-height:92vh;overflow-y:auto;animation:fu .2s ease}
.md.wide{max-width:660px}
@keyframes fu{from{transform:translateY(10px);opacity:0}to{transform:translateY(0);opacity:1}}
.md-title{font-size:14px;font-weight:700;color:var(--text);margin-bottom:16px;display:flex;align-items:center;gap:8px}
.md-close{margin-left:auto;cursor:pointer;color:var(--text3);font-size:18px;background:none;border:none;line-height:1;padding:2px;flex-shrink:0}
.md-close:hover{color:var(--text)}
.md-footer{display:flex;gap:8px;justify-content:flex-end;margin-top:16px;padding-top:14px;border-top:1px solid var(--border)}

/* ── TABS ── */
.tabs{display:flex;gap:2px;border-bottom:1px solid var(--border);margin-bottom:14px;overflow-x:auto;-webkit-overflow-scrolling:touch}
.tab{padding:7px 12px;font-size:12px;font-weight:600;cursor:pointer;color:var(--text2);border-bottom:2.5px solid transparent;margin-bottom:-1px;transition:all .13s;white-space:nowrap;flex-shrink:0}
.tab:hover{color:var(--text)}
.tab.active{color:var(--teal);border-bottom-color:var(--teal)}

/* ── MISC ── */
.card{background:var(--bg2);border:1px solid var(--border);border-radius:var(--r2);padding:15px 17px}
.card-sm{background:var(--bg3);border-radius:var(--r);padding:10px 12px}
.st{font-size:12px;font-weight:700;color:var(--text);margin:14px 0 8px}
.srch{background:var(--bg3);border:1.5px solid var(--border);border-radius:var(--r);padding:8px 11px;font-size:12px;color:var(--text);transition:border-color .15s;-webkit-appearance:none}
.srch:focus{outline:none;border-color:var(--teal)}
.sig-box{background:var(--bg3);border:1.5px dashed var(--border2);border-radius:var(--r);height:62px;display:flex;align-items:center;justify-content:center;cursor:pointer;color:var(--text3);font-size:12px;gap:5px;transition:all .18s}
.sig-box:hover,.sig-box:active{border-color:var(--teal);color:var(--teal)}
.sig-box.signed{border-color:var(--teal);background:var(--tealb);color:var(--teal);font-size:11px}
.tl{border-left:2px solid var(--border);padding-left:14px;margin-left:4px}
.tl-item{position:relative;padding-bottom:14px}
.tl-dot{width:9px;height:9px;border-radius:50%;position:absolute;left:-20px;top:3px;border:2px solid var(--bg2)}
.tl-title{font-size:12px;font-weight:700;color:var(--text);margin-bottom:1px}
.tl-sub{font-size:11px;color:var(--text3);line-height:1.4}
.log-item{display:grid;grid-template-columns:70px 7px 1fr;gap:6px;padding:6px 0;border-bottom:1px solid var(--border);align-items:flex-start}
.log-item:last-child{border-bottom:none}
.log-t{color:var(--text3);font-size:10px;font-family:monospace;padding-top:2px}
.log-d{width:5px;height:5px;border-radius:50%;margin-top:4px;flex-shrink:0}
.log-m{font-size:11px;color:var(--text2);line-height:1.5}
.log-m b{color:var(--text)}
.set-row{display:flex;align-items:center;justify-content:space-between;padding:8px 0;border-bottom:1px solid var(--border)}
.set-row:last-child{border-bottom:none}
.toggle{width:38px;height:21px;background:var(--bg4);border-radius:11px;cursor:pointer;position:relative;transition:background .2s;border:1px solid var(--border2);flex-shrink:0}
.toggle.on{background:var(--teal)}
.toggle::after{content:'';position:absolute;top:2px;left:2px;width:15px;height:15px;border-radius:50%;background:#fff;transition:left .2s}
.toggle.on::after{left:19px}
.um-row{display:flex;align-items:center;gap:9px;padding:8px 0;border-bottom:1px solid var(--border)}
.um-row:last-child{border-bottom:none}
.po-info{background:var(--amberb);border:1px solid rgba(255,170,0,.3);border-radius:var(--r);padding:10px 13px;font-size:11px;color:var(--amber);line-height:1.6;margin-bottom:12px}
/* permissions */
body:not(.is-admin):not(.is-operator) .edit-guard{display:none!important}
body:not(.is-admin) .admin-only{display:none!important}
/* Admin-only delete buttons — non-admin see "Request deletion" instead */
body:not(.is-admin) .delete-admin-only{display:none!important}
body.is-admin .delete-request-btn{display:none!important}

/* ── EMPLOYEE PICKER ── */
.ep-wrap{position:relative}
.ep-input{width:100%;background:var(--bg3);border:1.5px solid var(--border);border-radius:var(--r);padding:9px 11px;font-size:13px;color:var(--text);font-family:inherit;transition:border-color .15s;cursor:text}
.ep-input:focus{outline:none;border-color:var(--teal);background:var(--bg4)}
.ep-dropdown{display:none;position:absolute;top:100%;left:0;right:0;background:var(--bg2);border:1.5px solid var(--teal);border-top:none;border-radius:0 0 var(--r) var(--r);z-index:500;max-height:220px;overflow-y:auto;box-shadow:0 8px 24px rgba(0,0,0,.5)}
.ep-dropdown.open{display:block}
.ep-filter-bar{display:flex;gap:6px;padding:7px 8px;border-bottom:1px solid var(--border);background:var(--bg3);position:sticky;top:0}
.ep-search{flex:1;background:var(--bg4);border:1px solid var(--border);border-radius:6px;padding:5px 9px;font-size:12px;color:var(--text);font-family:inherit}
.ep-search:focus{outline:none;border-color:var(--teal)}
.ep-pos-sel{background:var(--bg4);border:1px solid var(--border);border-radius:6px;padding:4px 7px;font-size:11px;color:var(--text);max-width:130px}
.ep-item{padding:8px 12px;font-size:12px;color:var(--text);cursor:pointer;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;gap:8px;transition:background .1s}
.ep-item:last-child{border-bottom:none}
.ep-item:hover,.ep-item.focused{background:var(--tealb);color:var(--teal)}
.ep-item-name{font-weight:600}
.ep-item-pos{font-size:10px;color:var(--text3)}
.ep-empty{padding:12px;text-align:center;color:var(--text3);font-size:12px}

/* ── TOAST ── */
#toast{position:fixed;bottom:20px;right:20px;background:var(--bg3);border:1px solid var(--border);color:var(--text);padding:10px 14px;border-radius:var(--r);font-size:12px;font-weight:600;transform:translateY(70px);opacity:0;transition:all .27s;z-index:9999;max-width:280px;display:flex;align-items:center;gap:7px;box-shadow:0 4px 20px rgba(0,0,0,.5)}

/* ── INSTALL BANNER ── */
#install-banner{display:none;position:fixed;bottom:70px;left:50%;transform:translateX(-50%);background:var(--bg3);border:1px solid var(--teal);border-radius:var(--r2);padding:12px 16px;font-size:12px;color:var(--text);z-index:500;box-shadow:0 4px 20px rgba(0,0,0,.5);white-space:nowrap;display:flex;align-items:center;gap:10px}
#install-banner.show{display:flex}

/* ── RESPONSIVE ── */
@media(max-width:768px){
  :root{--sidebar:0px}
  body{flex-direction:column}
  #sidebar{position:fixed;left:0;top:0;width:260px;height:100%;transform:translateX(-100%);z-index:300}
  #sidebar.open{transform:translateX(0)}
  #app.visible{flex-direction:column}
  #mob-header{display:flex}
  #main{flex:1}
  .page{padding:14px 14px 30px}
  .kgrid{grid-template-columns:repeat(2,1fr)}
  .cgrid,.cgrid3{grid-template-columns:1fr}
  .fg{grid-template-columns:1fr}
  .fgr.full,.fg .fgr{grid-column:auto}
  .md{margin:0;border-radius:var(--r3) var(--r3) 0 0;max-height:85vh;position:fixed;bottom:0;left:0;right:0;width:100%;max-width:100%}
  .md.wide{max-width:100%}
  .mo{align-items:flex-end;padding:0}
  .tw{border-radius:var(--r)}
  .ph{gap:8px}
  .pt{font-size:17px}
  .top-row{width:100%}
  .tabs{flex-wrap:nowrap;overflow-x:auto;-webkit-overflow-scrolling:touch;padding-bottom:2px}
  .tab{font-size:11px;padding:6px 10px}
  .btn{padding:7px 11px;font-size:11px}
  .tw table{min-width:auto}
  .tw th,.tw td{padding:6px 8px;font-size:11px}
  .srch{font-size:12px;min-width:0!important}
  .card-sm{padding:7px 9px}
}
@media(max-width:480px){
  .kgrid{grid-template-columns:1fr 1fr}
  .top-row{gap:5px}
  .btn{padding:7px 11px;font-size:11px}
  .ph{flex-direction:column;align-items:flex-start}
  .md-footer{flex-wrap:wrap}
  .md-footer .btn{flex:1;min-width:80px;justify-content:center}
  #page-audit .card>div:first-child{grid-template-columns:1fr!important}
  #activity-log-list>div{grid-template-columns:1fr!important;gap:4px!important}
}
/* ── Sync overlay ── */
@keyframes spin{to{transform:rotate(360deg)}}
#sync-overlay{position:fixed;inset:0;background:var(--bg);z-index:9100;display:none;flex-direction:column;align-items:center;justify-content:center;gap:14px}
#sync-overlay .so-spinner{width:44px;height:44px;border:3px solid var(--border2);border-top-color:var(--teal);border-radius:50%;animation:spin .7s linear infinite}
#sync-overlay .so-msg{font-size:13px;color:var(--text2)}
#sync-overlay .so-sub{font-size:11px;color:var(--text3)}
/* ── Mobile PWA banner ── */
#mobile-pwa-bar{display:none;background:var(--bg3);border:1px solid var(--teal);border-radius:var(--r);padding:10px 14px;margin-top:14px;font-size:11px;color:var(--text2);line-height:1.6;text-align:center}
@media(max-width:600px){#mobile-pwa-bar{display:block}}
.ios-hint{display:none}
@supports(-webkit-touch-callout:none){.ios-hint{display:block}.android-hint{display:none}}
</style>
<script>
// Inline PWA manifest
const manifest = {
  name: "Safety Management System",
  short_name: "SafetyMS",
  description: "Occupational Safety Management System",
  start_url: window.location.origin + '/',
  scope: window.location.origin + '/',
  display: "standalone",
  background_color: "#0f1117",
  theme_color: "#0f1117",
  orientation: "any",
  icons: [
    { src: "data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><rect width='100' height='100' rx='20' fill='%2300d4a0'/><text y='.9em' font-size='72' x='12' fill='black' font-weight='900'>S</text></svg>", sizes: "192x192", type: "image/svg+xml" }
  ]
};
const blob = new Blob([JSON.stringify(manifest)], {type:'application/json'});
const manifestURL = URL.createObjectURL(blob);
document.getElementById('pwa-manifest').href = manifestURL;
</script>
</head>
<body>

<!-- LOGIN -->
<div id="login-screen">
  <div class="ll-wrap">
    <div class="ll-logo">
      <div class="ll-icon" id="ll-icon">S</div>
      <div><div class="ll-name" id="ll-name">Safety System</div><div class="ll-sub">Occupational Safety Management</div></div>
    </div>
    <div class="ll-card">
      <div class="ll-title">Welcome back</div>
      <div class="ll-subtitle">Sign in to access the system</div>
      <div class="lf">
        <div class="lf-lbl">Username</div>
        <input class="lf-inp" id="login-user" placeholder="Enter your username" autocomplete="username" autocapitalize="none" spellcheck="false"
          onkeydown="if(event.key==='Enter')document.getElementById('login-pass').focus()">
      </div>
      <div class="lf">
        <div class="lf-lbl"><span>Password</span><span style="font-size:10px;color:var(--teal);cursor:pointer;font-weight:600" onclick="togglePass()">👁 show</span></div>
        <input class="lf-inp" id="login-pass" type="password" placeholder="••••••••" autocomplete="current-password"
          onkeydown="if(event.key==='Enter')doLogin()">
      </div>
      <button class="ll-btn" onclick="doLogin()">Sign in</button>
      <div class="ll-err" id="login-error"><span>⚠</span><span id="ll-err-msg">Invalid username or password.</span></div>
      <div class="ll-quick" id="ll-quick" style="display:none">
        <div class="ll-quick-title">Quick access — Admin only</div>
        <div id="quick-users"></div>
      </div>
      <!-- Dica de instalação no celular -->
      <div id="mobile-pwa-bar">
        <div class="ios-hint">📱 <b>Instalar no iPhone:</b> toque em <b>Compartilhar</b> (⬆) → <b>Adicionar à Tela de Início</b></div>
        <div class="android-hint">📱 <b>Instalar no Android:</b> toque no menu do Chrome (⋮) → <b>Adicionar à tela inicial</b></div>
        <div style="margin-top:6px;color:var(--text3);font-size:10px">Funciona offline após instalado • Dados sincronizados em tempo real</div>
      </div>
    </div>
  </div>
</div>

<div class="so-msg">Conectando ao servidor...</div>
  <div class="so-sub">Sincronizando dados. Aguarde um momento.</div>
</div>

<!-- APP -->
<div id="app">
  <!-- Mobile header -->
  <div id="mob-header">
    <div id="mob-menu-btn" onclick="toggleMobMenu()">☰</div>
    <div id="mob-title">Dashboard</div>
    <div id="mob-user-btn" class="ua" onclick="openMo('mo-user-menu')">AD</div>
  </div>
  <div id="mob-overlay" onclick="closeMobMenu()"></div>

  <!-- Sidebar -->
  <nav id="sidebar">
    <div class="logo-area">
      <div class="logo-ic" id="s-logo">S</div>
      <div>
        <div class="logo-nm" id="s-company">Safety System</div>
        <div style="display:flex;align-items:center;gap:4px;margin-top:1px">
          <span class="logo-vr">v8.0</span>
          <span id="sync-dot" style="width:6px;height:6px;border-radius:50%;background:var(--text3);display:inline-block" title="Sync status"></span>
          <span id="sync-label" style="font-size:9px;color:var(--text3)">local</span>
        </div>
      </div>
    </div>
    <div class="s-sec">Main</div>
    <div class="ni active" onclick="goPage('dashboard',this)"><span class="ni-ic">▣</span><span>Dashboard</span><span class="ni-badge" id="bdg-alerts" style="display:none">0</span></div>
    <div class="s-sec">Modules</div>
    <div class="ni" id="nav-ppe" onclick="goPage('ppe',this)"><span class="ni-ic">🛡</span><span>PPE Management</span></div>
    <div class="ni" id="nav-inc" onclick="goPage('incidents',this)"><span class="ni-ic">⚠</span><span>Incidents</span><span class="ni-badge" id="bdg-inc" style="display:none">0</span></div>
    <div class="ni" id="nav-perf" onclick="goPage('performance',this)"><span class="ni-ic">◉</span><span>Performance</span></div>
    <div class="ni" id="nav-emp" onclick="goPage('employees',this)"><span class="ni-ic">👥</span><span>Employees</span></div>
    <div class="s-sec">System</div>
    <div class="ni" id="nav-loc" onclick="goPage('locations',this)"><span class="ni-ic">📍</span><span>Locations</span></div>
    <div class="ni" id="nav-rep" onclick="goPage('reports',this)"><span class="ni-ic">📄</span><span>Reports</span></div>
    <div class="ni" id="nav-set" onclick="goPage('settings',this)"><span class="ni-ic">⚙</span><span>Settings</span></div>
    <div class="ni admin-only" id="nav-del-req" onclick="openMo('mo-del-admin');renderDeleteRequests()"><span class="ni-ic">🗑</span><span>Delete requests</span><span class="ni-badge" id="bdg-del-req" style="display:none">0</span></div>
    <div class="ni" id="nav-audit" onclick="goPage('audit',this)"><span class="ni-ic">📋</span><span>Activity log</span></div>
    <div class="sb-bot">
      <div class="user-pill" onclick="openMo('mo-user-menu')">
        <div class="ua" id="ua-av">AD</div>
        <div><div class="un" id="ua-name">Administrator</div><div class="ur" id="ua-role">Admin</div></div>
      </div>
      <button class="btn btn-g btn-sm" style="width:100%;justify-content:center" onclick="doLogout()">↩ Sign out</button>
    </div>
  </nav>

  <!-- MAIN -->
  <main id="main">

<!-- DASHBOARD -->
<div id="page-dashboard" class="page active">
  <div class="ph">
    <div><div class="pt">Executive Dashboard</div><div class="ps" id="dash-date"></div></div>
    <div class="top-row">
      <button class="btn btn-g btn-sm period-btn active" onclick="setPeriod('6m',this)">6M</button>
      <button class="btn btn-g btn-sm period-btn" onclick="setPeriod('3m',this)">3M</button>
      <button class="btn btn-g btn-sm period-btn" onclick="setPeriod('1m',this)">1M</button>
      <button class="btn btn-r btn-sm" onclick="simDeviation()">⚡ Simulate</button>
    </div>
  </div>
  <div class="kgrid">
    <div class="kc r"><div class="kl">Incidents</div><div class="kv" id="kv-inc">26</div><div class="kd" id="kd-inc">↑ above target</div></div>
    <div class="kc a"><div class="kl">PPE Deviations</div><div class="kv" id="kv-ppe">18</div><div class="kd">action required</div></div>
    <div class="kc b"><div class="kl">Expired Training</div><div class="kv" id="kv-train">14</div><div class="kd">recertification needed</div></div>
    <div class="kc t"><div class="kl">Compliance</div><div class="kv" id="kv-conf">74%</div><div class="kd">target: 90%</div></div>
  </div>
  <div class="cgrid">
    <div class="cc"><div class="ct">Incidents per month</div><div class="cs">Max target: 4/month</div><div style="height:140px;position:relative"><canvas id="c-inc"></canvas></div></div>
    <div class="cc"><div class="ct">Compliance by module</div><div class="cs">Current vs 90% target</div><div style="height:140px;position:relative"><canvas id="c-comp"></canvas></div></div>
  </div>
  <div class="cgrid3">
    <div class="cc"><div class="ct">PPE by category</div><div class="cs">Stock status</div><div style="height:120px;position:relative"><canvas id="c-ppe-kpi"></canvas></div></div>
    <div class="cc"><div class="ct">Training status</div><div class="cs">Certifications</div><div style="height:120px;position:relative"><canvas id="c-train-kpi"></canvas></div></div>
    <div class="cc"><div class="ct">Performance dist.</div><div class="cs">Score bands</div><div style="height:120px;position:relative"><canvas id="c-perf-kpi"></canvas></div></div>
  </div>
  <div class="cgrid">
    <div class="cc"><div class="ct">Incidents by location</div><div class="cs">Distribution</div><div style="display:grid;grid-template-columns:1fr auto;gap:8px;align-items:center"><div style="height:120px;position:relative"><canvas id="c-areas"></canvas></div><div id="areas-legend" style="font-size:10px;display:flex;flex-direction:column;gap:3px"></div></div></div>
    <div class="cc"><div class="ct">Frequency × Severity rate</div><div class="cs">×10⁶h worked</div><div style="height:120px;position:relative"><canvas id="c-rates"></canvas></div></div>
  </div>
  <div class="card" style="margin-bottom:14px">
    <div class="ct" style="margin-bottom:10px">📡 Deviation monitor</div>
    <div id="dev-monitor"></div>
  </div>
  <div class="st">🔔 Active alerts</div>
  <div id="alert-list"></div>
  <div class="st" style="margin-top:16px">⏱ Action log</div>
  <div class="card"><div id="auto-log"></div></div>
</div>

<!-- PPE -->
<div id="page-ppe" class="page">
  <div class="ph">
    <div><div class="pt">PPE Management</div><div class="ps">Stock, deliveries and purchase requests</div></div>
    <div class="top-row edit-guard">
      <button class="btn btn-p btn-sm" onclick="openMo('mo-delivery')">+ New delivery</button>
      <button class="btn btn-g btn-sm" onclick="openMo('mo-item')">+ Add item</button>
    </div>
  </div>
  <div class="kgrid">
    <div class="kc t"><div class="kl">Total stock</div><div class="kv" id="kv-ppe-stock">0</div><div class="kd">items</div></div>
    <div class="kc r"><div class="kl">Below minimum</div><div class="kv" id="kv-ppe-low">0</div><div class="kd">action required</div></div>
    <div class="kc a"><div class="kl">Open requests</div><div class="kv" id="kv-ppe-po">0</div><div class="kd">awaiting approval</div></div>
    <div class="kc b"><div class="kl">Deliveries / month</div><div class="kv" id="kv-ppe-del">0</div><div class="kd">this period</div></div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab('ppe-tab',0,this)">📦 Stock</div>
    <div class="tab" onclick="switchTab('ppe-tab',1,this)">🚚 Deliveries</div>
    <div class="tab" onclick="switchTab('ppe-tab',2,this)">🛒 Purchase requests</div>
    <div class="tab" onclick="switchTab('ppe-tab',3,this)">📊 By employee</div>
  </div>
  <div id="ppe-tab-0">
    <div style="display:flex;gap:7px;margin-bottom:9px;flex-wrap:wrap">
      <input class="srch" style="flex:1;min-width:140px" placeholder="Search PPE..." oninput="filterTbl('tbl-ppe',this.value)">
      <select class="fs" id="ppe-cat-filter" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)" onchange="renderPpe()">
        <option value="">All categories</option>
        <option>Head</option><option>Hands</option><option>Feet</option>
        <option>Vision</option><option>Respiratory</option><option>Hearing</option><option>Fall</option>
      </select>
      <select class="fs" id="ppe-loc-filter" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)" onchange="renderPpe()">
        <option value="">All locations</option>
      </select>
    </div>
    <div class="tw"><table id="tbl-ppe"><thead><tr><th>Item</th><th>Location</th><th>Category</th><th>Sizes</th><th>Stock</th><th>Min</th><th>Status</th><th class="edit-guard"></th></tr></thead><tbody id="ppe-tbody"></tbody></table></div>
  </div>
  <div id="ppe-tab-1" style="display:none">
    <div class="tw"><table><thead><tr><th>Employee</th><th>Item</th><th>Qty</th><th>Clothing size</th><th>Shoe size</th><th>PO Ref.</th><th>Date</th><th>Status</th><th></th></tr></thead><tbody id="del-tbody"></tbody></table></div>
  </div>
  <div id="ppe-tab-2" style="display:none">
    <div class="po-info">⚠ Requests are <b>generated automatically</b> when stock falls below minimum. Approval is only allowed after stock is updated, invoice number and supplier are filled. PO number is mandatory.</div>
    <div style="margin-bottom:10px" class="edit-guard"><button class="btn btn-g btn-sm" onclick="openMo('mo-new-po')">+ New manual request</button></div>
    <div class="tw"><table><thead><tr><th>PO Number</th><th>Item</th><th>Req. qty</th><th>Supplier</th><th>Invoice</th><th>Stock</th><th>Status</th><th class="edit-guard"></th></tr></thead><tbody id="po-tbody"></tbody></table></div>
  </div>
  <div id="ppe-tab-3" style="display:none">
    <div class="cgrid">
      <div class="cc"><div class="ct">Deliveries by employee (top 15)</div><div class="cs">Total units received</div><div style="height:220px;position:relative"><canvas id="c-del-by-emp"></canvas></div></div>
      <div class="cc"><div class="ct">Deliveries by location</div><div class="cs">Total by site</div><div style="height:220px;position:relative"><canvas id="c-del-by-loc"></canvas></div></div>
    </div>
    <div class="cc" style="margin-top:12px"><div class="ct">History by item type</div><div class="cs">Deliveries per PPE category</div><div style="height:160px;position:relative"><canvas id="c-del-by-item"></canvas></div></div>
  </div>
</div>

<!-- INCIDENTS -->
<div id="page-incidents" class="page">
  <div class="ph">
    <div><div class="pt">Incidents</div><div class="ps">View all locations · Report and edit restricted to your location</div></div>
    <div class="top-row"><button class="btn btn-r btn-sm" id="btn-report-inc" onclick="openMo('mo-incident')">⚠ Report incident</button></div>
  </div>
  <div class="kgrid">
    <div class="kc r"><div class="kl">Open</div><div class="kv" id="kv-inc-open">0</div><div class="kd">awaiting action</div></div>
    <div class="kc a"><div class="kl">Investigating</div><div class="kv" id="kv-inc-inv">0</div><div class="kd">in progress</div></div>
    <div class="kc t"><div class="kl">Closed this month</div><div class="kv" id="kv-inc-closed">0</div></div>
    <div class="kc b"><div class="kl">Freq. rate (TF)</div><div class="kv" id="kv-inc-tf">2.3</div><div class="kd">×10⁶h</div></div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab('inc-tab',0,this)">All incidents</div>
    <div class="tab" onclick="switchTab('inc-tab',1,this)">Investigating</div>
    <div class="tab" onclick="switchTab('inc-tab',2,this)">Corrective actions</div>
  </div>
  <div id="inc-tab-0">
    <div style="display:flex;gap:7px;margin-bottom:9px;flex-wrap:wrap">
      <input class="srch" style="flex:1;min-width:140px" placeholder="Search..." oninput="filterTbl('tbl-inc',this.value)">
      <select class="fs" id="inc-status-filter" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)" onchange="renderIncidents()">
        <option value="">All statuses</option>
        <option>Open</option><option>Investigating</option><option>Pending Report</option><option>Corrective Action</option><option>Closed</option>
      </select>
    </div>
    <div class="tw"><table id="tbl-inc"><thead><tr><th>Code</th><th>Type</th><th>Location</th><th>Severity</th><th>Status</th><th>Date</th><th></th></tr></thead><tbody id="inc-tbody"></tbody></table></div>
  </div>
  <div id="inc-tab-1" style="display:none"><div id="inv-list"></div></div>
  <div id="inc-tab-2" style="display:none">
    <div class="card" style="margin-bottom:14px;border-left:3px solid var(--amber)">
      <div style="font-size:12.5px;font-weight:700;margin-bottom:10px">➕ Add corrective action</div>
      <div class="fg">
        <div class="fgr"><div class="flbl">Incident code</div>
          <select class="fs" id="ca-inc"><option value="">Select incident...</option></select>
        </div>
        <div class="fgr"><div class="flbl">Responsible</div><input class="fi" id="ca-resp" placeholder="Name or department"></div>
        <div class="fgr"><div class="flbl">Due date</div><input class="fi" type="date" id="ca-due"></div>
        <div class="fgr"><div class="flbl">Status</div>
          <select class="fs" id="ca-status">
            <option>Pending</option><option>In progress</option><option>Completed</option><option>Overdue</option>
          </select>
        </div>
        <div class="fgr full"><div class="flbl">Action description</div>
          <input class="fi" id="ca-action" placeholder="Describe the corrective action to take...">
        </div>
      </div>
      <div style="margin-top:10px;display:flex;justify-content:flex-end">
        <button class="btn btn-p btn-sm" onclick="saveCorrAction()">Add corrective action</button>
      </div>
    </div>
    <div class="tw"><table><thead><tr><th>Incident</th><th>Action</th><th>Responsible</th><th>Due</th><th>Status</th><th></th></tr></thead><tbody id="actions-tbody"></tbody></table></div>
  </div>
</div>

<!-- PERFORMANCE -->
<div id="page-performance" class="page">
  <div class="ph">
    <div><div class="pt">Performance</div><div class="ps">Individual KPIs, regional results, warnings and training</div></div>
    <div class="top-row edit-guard"><button class="btn btn-p btn-sm" onclick="openMo('mo-eval')">+ New evaluation</button></div>
  </div>
  <div class="kgrid">
    <div class="kc b"><div class="kl">Evaluations</div><div class="kv" id="kv-evals">0</div></div>
    <div class="kc t"><div class="kl">Team avg</div><div class="kv" id="kv-goal">—</div></div>
    <div class="kc a"><div class="kl">Warnings</div><div class="kv" id="kv-warn">0</div></div>
    <div class="kc r"><div class="kl">Expired training</div><div class="kv" id="kv-texp">0</div></div>
  </div>
  <div class="tabs">
    <div class="tab active" onclick="switchTab('perf-tab',0,this)">Individual KPIs</div>
    <div class="tab" onclick="switchTab('perf-tab',1,this)">Regional Analyst</div>
    <div class="tab" onclick="switchTab('perf-tab',2,this)">Warnings</div>
    <div class="tab" onclick="switchTab('perf-tab',3,this)">Training</div>
    <div class="tab" onclick="switchTab('perf-tab',4,this)">Workflow</div>
  </div>
  <div id="perf-tab-0">
    <div style="display:flex;gap:7px;margin-bottom:9px;flex-wrap:wrap;align-items:center">
      <input class="srch" style="flex:1;min-width:140px" placeholder="Search employee..." oninput="filterTbl('tbl-eval',this.value)">
      <select class="fs" id="eval-loc-filter" onchange="renderEvaluations()" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)">
        <option value="">All locations</option>
      </select>
    </div>
    <div class="tw"><table id="tbl-eval"><thead><tr><th>Employee</th><th>Location</th><th>Score</th><th>Progress</th><th>Period</th><th>Status</th><th></th></tr></thead><tbody id="eval-tbody"></tbody></table></div>
  </div>
  <div id="perf-tab-1" style="display:none">
    <div class="card" style="margin-bottom:14px">
      <div style="font-size:13px;font-weight:700;color:var(--text);margin-bottom:4px">Regional Safety Analyst — score based on team results</div>
      <div style="font-size:11px;color:var(--text2)">Score calculated automatically as weighted average of all Safety Analysts under supervision. Monthly and quarterly separated.</div>
    </div>
    <div class="cgrid" style="margin-bottom:14px">
      <div class="cc"><div class="ct" style="margin-bottom:8px">Monthly evolution</div><div style="height:150px;position:relative"><canvas id="c-regional-monthly"></canvas></div></div>
      <div class="cc"><div class="ct" style="margin-bottom:8px">Quarterly score</div><div style="height:150px;position:relative"><canvas id="c-regional-quarterly"></canvas></div></div>
    </div>
    <div class="st">Results by Safety Analyst</div>
    <div class="tw"><table><thead><tr><th>Analyst</th><th>Location</th><th>Monthly</th><th>Quarterly</th><th>Status</th></tr></thead><tbody id="regional-tbody"></tbody></table></div>
  </div>
  <div id="perf-tab-2" style="display:none">
    <div style="margin-bottom:9px" class="edit-guard"><button class="btn btn-a btn-sm" onclick="openMo('mo-warning')">+ New warning</button></div>
    <div class="tw"><table><thead><tr><th>Employee</th><th>Type</th><th>Reason</th><th>Date</th><th>Status</th><th></th></tr></thead><tbody id="warn-tbody"></tbody></table></div>
  </div>
  <div id="perf-tab-3" style="display:none">
    <div style="margin-bottom:9px"><button class="btn btn-p btn-sm" onclick="openMo('mo-training')">+ Add training record</button></div>
    <div class="tw"><table><thead><tr><th>Employee</th><th>Training</th><th>Standard</th><th>Expiry</th><th>Status</th><th></th></tr></thead><tbody id="train-tbody"></tbody></table></div>
  </div>
  <div id="perf-tab-4" style="display:none">
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;flex-wrap:wrap">
      <div class="card">
        <div style="font-size:13px;font-weight:700;margin-bottom:12px">Evaluation workflow</div>
        <div class="tl">
          <div class="tl-item"><div class="tl-dot" style="background:var(--blue)"></div><div class="tl-title">Draft</div><div class="tl-sub">Manager fills KPIs and feedback</div></div>
          <div class="tl-item"><div class="tl-dot" style="background:var(--amber)"></div><div class="tl-title">Employee review</div><div class="tl-sub">Employee reads and signs</div></div>
          <div class="tl-item"><div class="tl-dot" style="background:var(--blue)"></div><div class="tl-title">Approval</div><div class="tl-sub">Manager validates</div></div>
          <div class="tl-item"><div class="tl-dot" style="background:var(--teal)"></div><div class="tl-title">Archived</div><div class="tl-sub">Next cycle goals set</div></div>
        </div>
      </div>
      <div class="card">
        <div style="font-size:13px;font-weight:700;margin-bottom:6px">Auto actions (ISO 45001 / ILO-OSH 2001)</div>
        <div style="font-size:10px;color:var(--text3);margin-bottom:10px">Based on international standards — <button class="btn btn-g btn-sm edit-guard" onclick="openMo('mo-auto-actions')" style="font-size:10px;padding:3px 8px">✏ Edit</button></div>
        <div id="auto-actions-preview"></div>
      </div>
    </div>
  </div>
</div>

<!-- EMPLOYEES -->
<div id="page-employees" class="page">
  <div class="ph">
    <div><div class="pt">Employees</div><div class="ps" id="emp-count">Loading...</div></div>
    <div class="top-row edit-guard"><button class="btn btn-p btn-sm" onclick="openMo('mo-employee')">+ New employee</button></div>
  </div>
  <div style="display:flex;gap:7px;margin-bottom:12px;flex-wrap:wrap">
    <input class="srch" style="flex:1;min-width:160px" placeholder="Search by name, ID, position..." oninput="filterTbl('tbl-emp',this.value)">
    <select class="fs" id="emp-loc-filter" onchange="renderEmployees()" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)"><option value="">All locations</option></select>
    <select class="fs" id="emp-dept-filter" onchange="renderEmployees()" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)"><option value="">All departments</option></select>
    <select class="fs" id="emp-status-filter" onchange="renderEmployees()" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)"><option value="">All statuses</option><option>Active</option><option>Vacation</option><option>Other</option></select>
  </div>
  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:14px;margin-bottom:14px">
    <div class="cc"><div class="ct">Employees by location</div><div class="cs">Headcount per site</div><div style="height:200px;position:relative"><canvas id="c-emp-by-loc"></canvas></div></div>
    <div class="cc"><div class="ct">Employees by region</div><div class="cs">Distribution overview</div><div style="height:200px;position:relative"><canvas id="c-emp-by-region"></canvas></div></div>
  </div>
  <div class="tw"><table id="tbl-emp"><thead><tr><th>#</th><th>Name</th><th>Position</th><th>Location</th><th>Region</th><th>Dept</th><th>Status</th><th></th></tr></thead><tbody id="emp-tbody"></tbody></table></div>
</div>

<!-- LOCATIONS -->
<div id="page-locations" class="page">
  <div class="ph">
    <div><div class="pt">Locations</div><div class="ps">Manage all company sites and countries</div></div>
    <div class="top-row admin-only"><button class="btn btn-p btn-sm" onclick="openMo('mo-location')">+ Add location</button></div>
  </div>
  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:14px">
    <div>
      <div class="st">Active locations</div>
      <div class="card" id="loc-list-box" style="padding:8px 12px"></div>
    </div>
    <div>
      <div class="st">Employees by location</div>
      <div class="cc"><div style="height:200px;position:relative"><canvas id="c-loc-emp"></canvas></div></div>
    </div>
  </div>
</div>

<!-- REPORTS -->
<div id="page-reports" class="page">
  <div class="ph"><div class="pt">Reports</div><div class="ps">Export safety reports to PDF or Excel</div></div>
  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px" id="reports-grid"></div>
</div>

<!-- SETTINGS -->
<div id="page-settings" class="page">
  <div class="ph"><div class="pt">Settings</div><div class="ps">System configuration and data management</div></div>
  <div class="card" style="margin-bottom:12px">
    <div style="font-size:13px;font-weight:700;margin-bottom:14px">🏢 Company information</div>
    <div class="fg">
      <div class="fgr"><div class="flbl">Company name</div><input class="fi" id="cfg-company" oninput="saveCfg()"></div>
      <div class="fgr"><div class="flbl">Department</div><input class="fi" id="cfg-dept" oninput="saveCfg()"></div>
      <div class="fgr"><div class="flbl">Admin name</div><input class="fi" id="cfg-admin" oninput="saveCfg()"></div>
      <div class="fgr"><div class="flbl">Logo icon</div><input class="fi" id="cfg-logo" maxlength="3" oninput="saveCfg()"></div>
    </div>
  </div>
  <div class="card" style="margin-bottom:12px">
    <div style="font-size:13px;font-weight:700;margin-bottom:14px">🎯 Thresholds</div>
    <div class="fg">
      <div class="fgr"><div class="flbl">Max incidents/month</div><input class="fi" id="cfg-max-inc" type="number" oninput="saveCfg()"></div>
      <div class="fgr"><div class="flbl">Min compliance (%)</div><input class="fi" id="cfg-min-comp" type="number" oninput="saveCfg()"></div>
      <div class="fgr"><div class="flbl">Min performance score</div><input class="fi" id="cfg-min-score" type="number" step="0.1" oninput="saveCfg()"></div>
      <div class="fgr"><div class="flbl">Alert days before expiry</div><input class="fi" id="cfg-alert-days" type="number" oninput="saveCfg()"></div>
    </div>
  </div>
  <div class="card">
    <div style="font-size:13px;font-weight:700;margin-bottom:14px">🗄 Data</div>
    <div class="set-row"><div><div style="font-size:12px">Export backup</div><div style="font-size:10px;color:var(--text3)">JSON file</div></div><button class="btn btn-g btn-sm" onclick="exportData()">Export</button></div>
    <div class="set-row"><div><div style="font-size:12px">Import backup</div><div style="font-size:10px;color:var(--text3)">Restore from JSON</div></div><button class="btn btn-g btn-sm" onclick="importData()">Import</button></div>
    <div class="set-row"><div><div style="font-size:12px;color:var(--red)">Reset all data</div><div style="font-size:10px;color:var(--text3)">Irreversible</div></div><button class="btn btn-r btn-sm" onclick="if(confirm('Reset all data?'))resetData()">Reset</button></div>
  </div>

  <!-- ═══ SYNC SETTINGS ═══ -->
  <div class="card" style="margin-top:12px">
    <div style="font-size:13px;font-weight:700;margin-bottom:4px;display:flex;align-items:center;gap:8px">
      🔄 Live sync — online &amp; cross-device
      <span id="sync-dot-s" style="width:9px;height:9px;border-radius:50%;background:var(--text3);display:inline-block;transition:background .4s"></span>
      <span id="sync-label-s" style="font-size:10px;color:var(--text3)">local only</span>
    </div>
    <div style="font-size:11px;color:var(--text2);margin-bottom:14px;line-height:1.8">
      <b>Same-device sync is always automatic</b> (multiple tabs/windows). For multiple computers, phones and tablets seeing the same data in real time, connect a cloud backend below.
    </div>

    <!-- Backend selector -->
    <div class="fgr" style="margin-bottom:14px">
      <div class="flbl">Cloud backend</div>
      <select class="fs" id="cfg-sync-backend" onchange="syncBackendChanged()">
        <option value="">⬜ Local only — no cloud sync</option>
        <option value="firebase">🔥 Firebase Realtime DB — 1GB free, real-time</option>
        <option value="sharepoint">🏢 SharePoint Lists (Microsoft 365)</option>
        <option value="jsonbin">🌐 JSONBin.io — free, no server needed</option>
        <option value="custom">⚙ Custom REST endpoint</option>
      </select>
    </div>

    <!-- SharePoint config -->
    <div id="sp-config" style="display:none;margin-bottom:14px">
      <div style="background:rgba(77,159,255,.1);border:1px solid rgba(77,159,255,.3);border-radius:var(--r);padding:13px;margin-bottom:12px;font-size:11px;color:var(--text2);line-height:1.9">
        <b style="color:var(--blue);font-size:12px">🏢 SharePoint — setup once (~5 min)</b><br>
        <b>1.</b> Go to your SharePoint site → <b>Site contents → New → List</b> → name: <code style="background:var(--bg4);padding:1px 6px;border-radius:3px">SafetyAppData</code><br>
        <b>2.</b> Add column: <b>Multiple lines of text</b> → name: <code style="background:var(--bg4);padding:1px 6px;border-radius:3px">payload</code><br>
        <b>3.</b> Add column: <b>Number</b> → name: <code style="background:var(--bg4);padding:1px 6px;border-radius:3px">ts</code><br>
        <b>4.</b> Upload this HTML file to a <b>Document Library</b> on the same site<br>
        <b>5.</b> Open from SharePoint — Microsoft login is automatic (no extra passwords)<br>
        <b>6.</b> Paste site URL below and click <b>⬆ Push now</b>
      </div>
      <div class="fg">
        <div class="fgr full"><div class="flbl">SharePoint site URL</div><input class="fi" id="cfg-sp-site" placeholder="https://company.sharepoint.com/sites/Safety" oninput="saveCfg()"></div>
        <div class="fgr"><div class="flbl">List name</div><input class="fi" id="cfg-sp-list" placeholder="SafetyAppData" oninput="saveCfg()"></div>
      </div>
    </div>

    <!-- Firebase config -->
    <div id="firebase-config" style="display:none;margin-bottom:14px">
      <div style="background:rgba(255,170,0,.1);border:1px solid rgba(255,170,0,.3);border-radius:var(--r);padding:13px;margin-bottom:12px;font-size:11px;color:var(--text2);line-height:2">
        <b style="color:var(--amber);font-size:12px">🔥 Firebase Realtime DB — setup (~3 min, 100% free, no card)</b><br>
        <b>1.</b> Go to <a href="https://console.firebase.google.com" target="_blank" style="color:var(--amber)">console.firebase.google.com</a> → sign in with Google<br>
        <b>2.</b> Add project → name <code style="background:var(--bg4);padding:1px 6px;border-radius:3px">SafetySystem</code> → disable Analytics → Create<br>
        <b>3.</b> Left menu → <b>Build → Realtime Database → Create database</b><br>
        <b>4.</b> Region → <b>Start in test mode</b> → Enable<br>
        <b>5.</b> Copy the URL shown: <code style="background:var(--bg4);padding:1px 6px;border-radius:3px">https://safetysystem-xxxxx-default-rtdb.firebaseio.com</code><br>
        <b>6.</b> Paste below → click <b>⬆ Push now</b>
      </div>
      <div class="fg">
        <div class="fgr full"><div class="flbl">Firebase Database URL</div>
          <input class="fi" id="cfg-firebase-url" placeholder="https://your-project-default-rtdb.firebaseio.com" oninput="saveCfg()">
        </div>
        <div class="fgr full"><div class="flbl">Secret key (leave blank for test mode)</div>
          <input class="fi" type="password" id="cfg-firebase-key" placeholder="Leave blank" oninput="saveCfg()">
        </div>
      </div>
    </div>

    <!-- JSONBin config -->
    <div id="jsonbin-config" style="display:none;margin-bottom:14px">
      <div style="background:rgba(0,212,160,.1);border:1px solid rgba(0,212,160,.3);border-radius:var(--r);padding:13px;margin-bottom:12px;font-size:11px;color:var(--text2);line-height:1.9">
        <b style="color:var(--teal);font-size:12px">🌐 JSONBin.io — free, works from any network</b><br>
        <b>1.</b> Go to <a href="https://jsonbin.io" target="_blank" style="color:var(--teal)">jsonbin.io</a> → create free account<br>
        <b>2.</b> Click <b>+ Create Bin</b> → paste <code style="background:var(--bg4);padding:1px 5px;border-radius:3px">{}</code> → Save<br>
        <b>3.</b> Copy the <b>Bin ID</b> from the URL bar<br>
        <b>4.</b> In Account → <b>API Keys</b> → copy your <b>Master Key</b><br>
        <b>5.</b> Paste both below and click <b>⬆ Push now</b> — done!
      </div>
      <div class="fg">
        <div class="fgr"><div class="flbl">Bin ID</div><input class="fi" id="cfg-jsonbin-id" placeholder="64abc..." oninput="saveCfg()"></div>
        <div class="fgr"><div class="flbl">Master Key</div><input class="fi" type="password" id="cfg-jsonbin-key" placeholder="$2a$10$..." oninput="saveCfg()"></div>
      </div>
    </div>

    <!-- Custom endpoint config -->
    <div id="custom-config" style="display:none;margin-bottom:14px">
      <div class="fg">
        <div class="fgr full"><div class="flbl">Endpoint URL (GET /get · POST /set)</div><input class="fi" id="cfg-sync-url" placeholder="https://your-api.com" oninput="saveCfg()"></div>
        <div class="fgr"><div class="flbl">Access key</div><input class="fi" type="password" id="cfg-sync-key" placeholder="API key" oninput="saveCfg()"></div>
      </div>
    </div>

    <!-- Action buttons -->
    <div style="display:flex;gap:8px;flex-wrap:wrap;align-items:center">
      <button class="btn btn-p btn-sm" onclick="pushToRemote().then(()=>toast('✓ Pushed!')).catch(e=>toast('Push error: '+e.message,'err'))">⬆ Push now</button>
      <button class="btn btn-g btn-sm" onclick="pullFromRemote().then(()=>toast('✓ Pulled!')).catch(e=>toast('Pull error: '+e.message,'err'))">⬇ Pull now</button>
      <button class="btn btn-g btn-sm" onclick="startRemoteSync();toast('Auto-sync active (every 15s) ✓')">🔄 Auto-sync</button>
      <div style="margin-left:auto;font-size:11px;color:var(--text3)">Updates every 15 seconds when active</div>
    </div>
  </div>

</div>

<!-- AUDIT PAGE -->
<div id="page-audit" class="page">
  <div class="ph">
    <div>
      <div class="pt">Activity Log</div>
      <div class="ps">Audit trail — edits, creations, deletions, approvals</div>
    </div>
    <div class="top-row">
      <select class="fs" id="audit-filter-action" onchange="filterAuditLog()" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)">
        <option value="">All actions</option>
        <option value="CREATE">Create</option>
        <option value="EDIT">Edit</option>
        <option value="DELETE">Delete</option>
        <option value="DELETE_REQUEST">Delete request</option>
        <option value="DELETE_APPROVED">Delete approved</option>
        <option value="DELETE_REJECTED">Delete rejected</option>
        <option value="APPROVE">Approve</option>
        <option value="SECURITY">Security</option>
        <option value="LOGIN">Login</option>
      </select>
      <select class="fs" id="audit-filter-user" onchange="filterAuditLog()" style="font-size:11px;padding:5px 9px;background:var(--bg3);border:1.5px solid var(--border);color:var(--text);border-radius:var(--r)">
        <option value="">All users</option>
      </select>
      <button class="btn btn-g btn-sm" onclick="exportAuditLog()">📥 Export CSV</button>
    </div>
  </div>
  <div class="card" style="padding:0;overflow:hidden">
    <div style="display:grid;grid-template-columns:120px 90px 1fr;gap:0;padding:8px 14px;background:var(--bg3);border-bottom:1px solid var(--border)">
      <div style="font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.06em;color:var(--text3)">Action · Time</div>
      <div style="font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.06em;color:var(--text3)">User</div>
      <div style="font-size:9px;font-weight:700;text-transform:uppercase;letter-spacing:.06em;color:var(--text3)">Detail</div>
    </div>
    <div id="activity-log-list" style="padding:0 14px;max-height:70vh;overflow-y:auto"></div>
  </div>
</div>

  </main>
</div>

<!-- MODALS -->
<div class="mo" id="mo-user-menu">
  <div class="md" style="max-width:320px">
    <div class="md-title">👤 My account<button class="md-close" onclick="closeMo('mo-user-menu')">✕</button></div>
    <div style="background:var(--bg3);border-radius:var(--r2);padding:14px;text-align:center;margin-bottom:14px">
      <div id="um-av" style="width:48px;height:48px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:17px;font-weight:800;margin:0 auto 8px"></div>
      <div id="um-name" style="font-size:14px;font-weight:700"></div>
      <div id="um-role" style="font-size:11px;color:var(--text3);margin-top:2px"></div>
    </div>
    <div style="display:flex;flex-direction:column;gap:7px;margin-bottom:14px">
      <button class="btn btn-g" style="justify-content:flex-start;gap:9px" onclick="closeMo('mo-user-menu');openMo('mo-change-pass')">🔑 Change my password</button>
      <button class="btn btn-g admin-only" style="justify-content:flex-start;gap:9px" onclick="closeMo('mo-user-menu');openMo('mo-user-mgr')">👥 Manage users</button>
    </div>
    <button class="btn btn-r" style="width:100%;justify-content:center" onclick="doLogout()">↩ Sign out</button>
  </div>
</div>

<div class="mo" id="mo-change-pass">
  <div class="md" style="max-width:360px">
    <div class="md-title">🔑 Change password<button class="md-close" onclick="closeMo('mo-change-pass')">✕</button></div>
    <div id="cp-info" style="background:var(--bg3);border-radius:var(--r);padding:9px 12px;margin-bottom:14px;font-size:12px;color:var(--text2)"></div>
    <div class="fg">
      <div class="fgr full" id="cp-cur-wrap"><div class="flbl">Current password</div><input class="fi" type="password" id="cp-current"></div>
      <div class="fgr full"><div class="flbl">New password (min 4)</div><input class="fi" type="password" id="cp-new"></div>
      <div class="fgr full"><div class="flbl">Confirm new password</div><input class="fi" type="password" id="cp-confirm"></div>
    </div>
    <div class="ll-err" id="cp-err" style="margin-top:8px"><span>⚠</span><span id="cp-err-msg"></span></div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-change-pass')">Cancel</button><button class="btn btn-p" onclick="doChangePass()">Change password</button></div>
  </div>
</div>

<div class="mo" id="mo-user-mgr">
  <div class="md wide">
    <div class="md-title">👥 User Management<button class="md-close" onclick="closeMo('mo-user-mgr')">✕</button></div>

    <!-- Tab bar -->
    <div class="tabs" style="margin-bottom:14px">
      <div class="tab active" onclick="switchTab('umgr-tab',0,this)">👥 Users list</div>
      <div class="tab" onclick="switchTab('umgr-tab',1,this)">➕ Add user</div>
    </div>

    <!-- TAB 0: User list -->
    <div id="umgr-tab-0">
      <div id="user-mgr-list"></div>
    </div>

    <!-- TAB 1: Add user -->
    <div id="umgr-tab-1" style="display:none">
      <div class="fg">
        <div class="fgr"><div class="flbl">Username <span style="color:var(--red)">*</span></div><input class="fi" id="nu-user" placeholder="john.doe" autocapitalize="none" spellcheck="false"></div>
        <div class="fgr"><div class="flbl">Display name <span style="color:var(--red)">*</span></div><input class="fi" id="nu-display" placeholder="Full name"></div>
        <div class="fgr"><div class="flbl">Email</div><input class="fi" type="email" id="nu-email" placeholder="user@company.com"></div>
        <div class="fgr"><div class="flbl">Password <span style="color:var(--red)">*</span> (min 4)</div><input class="fi" type="password" id="nu-pass" placeholder="Temporary password"></div>
        <div class="fgr"><div class="flbl">Profile / Role</div>
          <select class="fs" id="nu-role">
            <option value="admin">Administrator</option>
            <option value="regional_safety">Regional Safety Analyst</option>
            <option value="safety_analyst" selected>Safety Analyst</option>
            <option value="operator">Operator</option>
            <option value="viewer">Viewer</option>
          </select>
        </div>
        <div class="fgr"><div class="flbl">Department</div><input class="fi" id="nu-dept" placeholder="e.g. SESMT"></div>
        <div class="fgr full"><div class="flbl">Location access</div>
          <select class="fs" id="nu-loc"><option value="all">All locations</option></select>
        </div>
      </div>
      <div style="background:var(--amberb);border:1px solid rgba(255,170,0,.3);border-radius:var(--r);padding:9px 13px;font-size:11px;color:var(--amber);margin-top:10px;line-height:1.6">
        ⚠ The password is stored in plain text and converted to a hash on first login. Share the temporary password securely with the user.
      </div>
      <button class="btn btn-p" style="width:100%;justify-content:center;margin-top:12px" onclick="addUser()">+ Create user</button>
    </div>

    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-user-mgr')">Close</button></div>
  </div>
</div>

<!-- Edit user modal -->
<div class="mo" id="mo-edit-user">
  <div class="md" style="max-width:480px">
    <div class="md-title">✏ Edit user — <span id="edit-user-title"></span><button class="md-close" onclick="closeMo('mo-edit-user')">✕</button></div>
    <input type="hidden" id="edit-user-idx">
    <div class="fg">
      <div class="fgr"><div class="flbl">Username</div><input class="fi" id="eu-user" autocapitalize="none" spellcheck="false"></div>
      <div class="fgr"><div class="flbl">Display name</div><input class="fi" id="eu-display"></div>
      <div class="fgr"><div class="flbl">Email</div><input class="fi" type="email" id="eu-email"></div>
      <div class="fgr"><div class="flbl">Department</div><input class="fi" id="eu-dept"></div>
      <div class="fgr"><div class="flbl">Profile / Role</div>
        <select class="fs" id="eu-role">
          <option value="admin">Administrator</option>
          <option value="regional_safety">Regional Safety Analyst</option>
          <option value="safety_analyst">Safety Analyst</option>
          <option value="operator">Operator</option>
          <option value="viewer">Viewer</option>
        </select>
      </div>
      <div class="fgr"><div class="flbl">Location access</div>
        <select class="fs" id="eu-loc"><option value="all">All locations</option></select>
      </div>
      <div class="fgr"><div class="flbl">Status</div>
        <select class="fs" id="eu-status">
          <option value="active">Active</option>
          <option value="suspended">Suspended (cannot login)</option>
        </select>
      </div>
      <div class="fgr full">
        <div class="flbl">Reset password (leave blank to keep current)</div>
        <input class="fi" type="password" id="eu-pass" placeholder="New password (min 4 chars)">
      </div>
      <div class="fgr full" id="eu-info-row" style="background:var(--bg3);border-radius:var(--r);padding:9px 12px;font-size:11px;color:var(--text3)"></div>
    </div>
    <div class="md-footer">
      <button class="btn btn-r btn-sm" onclick="deleteUserFromEdit()">🗑 Delete user</button>
      <button class="btn btn-g" onclick="closeMo('mo-edit-user')">Cancel</button>
      <button class="btn btn-p" onclick="saveEditUser()">💾 Save changes</button>
    </div>
  </div>
</div>

<div class="mo" id="mo-delivery">
  <div class="md wide">
    <div class="md-title">🛡 New PPE delivery<button class="md-close" onclick="closeMo('mo-delivery')">✕</button></div>
    <div class="fg">
            <div class="fgr full">
        <div class="flbl">Employee</div>
        <div class="ep-wrap" id="ep-wrap-del-emp">
          <input class="ep-input" id="ep-input-del-emp" 
            placeholder="🔍 Type to search employee..."
            autocomplete="off"
            oninput="epFilter('del-emp',this.value)"
            onfocus="epOpen('del-emp')"
            onkeydown="epKey(event,'del-emp')">
          <input type="hidden" id="del-emp" name="del-emp">
          <div class="ep-dropdown" id="ep-drop-del-emp">
            <div class="ep-filter-bar">
              <input class="ep-search" id="ep-srch-del-emp" placeholder="Search name..." 
                oninput="epFilter('del-emp',this.value)" autocomplete="off">
              <select class="ep-pos-sel" id="ep-pos-del-emp" onchange="epFilterPos('del-emp',this.value)">
                <option value="">All positions</option>
              </select>
            </div>
            <div id="ep-list-del-emp"></div>
          </div>
        </div>
      </div>
      <div class="fgr"><div class="flbl">PPE item</div><select class="fs" id="del-item"></select></div>
      <div class="fgr"><div class="flbl">Quantity</div><input class="fi" type="number" id="del-qty" value="1" min="1"></div>
      <div class="fgr"><div class="flbl">Clothing size</div><select class="fs" id="del-size"><option>XS</option><option>S</option><option selected>M</option><option>L</option><option>XL</option><option>XXL</option><option>N/A</option></select></div>
      <div class="fgr"><div class="flbl">Shoe/boot size</div><select class="fs" id="del-shoe-size"><option value="">N/A</option><option>34</option><option>35</option><option>36</option><option>37</option><option>38</option><option>39</option><option>40</option><option>41</option><option>42</option><option>43</option><option>44</option><option>45</option><option>46</option><option>47</option></select></div>
      <div class="fgr"><div class="flbl">Delivery location <span style="color:var(--red)">*</span></div>
        <select class="fs" id="del-location">
          <option value="">-- Select location --</option>
        </select>
      </div>
      <div class="fgr"><div class="flbl">PO Reference</div><input class="fi" id="del-po-ref" placeholder="e.g. PO-2025-042"></div>
      <div class="fgr"><div class="flbl">Notes</div><input class="fi" id="del-notes" placeholder="Optional notes..."></div>
      <div class="fgr full"><div class="flbl">Digital signature</div><div class="sig-box" id="del-sig" onclick="signBox('del-sig','del-signed')">✍ Click to sign digitally</div><input type="hidden" id="del-signed" value="0"></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-delivery')">Cancel</button><button class="btn btn-p" onclick="saveDelivery()">✓ Confirm delivery</button></div>
  </div>
</div>

<div class="mo" id="mo-item">
  <div class="md">
    <div class="md-title">+ Add PPE item<button class="md-close" onclick="closeMo('mo-item')">✕</button></div>
    <div class="fg">
      <div class="fgr full"><div class="flbl">Item name</div><input class="fi" id="item-name" placeholder="e.g. Safety helmet ABS"></div>
      <div class="fgr"><div class="flbl">Location / Site <span style="color:var(--red)">*</span></div>
        <select class="fs" id="item-location">
          <option value="">-- Select location --</option>
        </select>
      </div>
      <div class="fgr"><div class="flbl">Category</div><select class="fs" id="item-cat"><option>Head</option><option>Hands</option><option>Feet</option><option>Vision</option><option>Respiratory</option><option>Hearing</option><option>Fall</option><option>Body</option></select></div>
      <div class="fgr"><div class="flbl">Unit</div><select class="fs" id="item-unit"><option>Unit</option><option>Pair</option><option>Box</option></select></div>
      <div class="fgr"><div class="flbl">Current stock</div><input class="fi" type="number" id="item-stock" value="0" min="0"></div>
      <div class="fgr"><div class="flbl">Minimum stock</div><input class="fi" type="number" id="item-min" value="10" min="0"></div>
      <div class="fgr"><div class="flbl">Clothing sizes available</div><input class="fi" id="item-clothing-sizes" placeholder="e.g. S, M, L, XL"></div>
      <div class="fgr"><div class="flbl">Shoe/boot sizes available</div><input class="fi" id="item-shoe-sizes" placeholder="e.g. 38, 39, 40, 41, 42"></div>
      <div class="fgr"><div class="flbl">Validity (months)</div><input class="fi" type="number" id="item-exp" value="12" min="1"></div>
      <div class="fgr"><div class="flbl">Invoice No. (on receipt)</div><input class="fi" id="item-invoice" placeholder="e.g. INV-2025-042"></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-item')">Cancel</button><button class="btn btn-p" onclick="savePpeItem()">Save item</button></div>
  </div>
</div>

<div class="mo" id="mo-new-po">
  <div class="md">
    <div class="md-title">🛒 New purchase request<button class="md-close" onclick="closeMo('mo-new-po')">✕</button></div>
    <div class="fg">
      <div class="fgr full"><div class="flbl">PPE item</div><select class="fs" id="po-item"></select></div>
      <div class="fgr full">
        <div class="flbl">Destination location (stock-in) <span style="color:var(--red)">*</span></div>
        <select class="fs" id="po-location">
          <option value="">-- Select location --</option>
        </select>
      </div>
      <div class="fgr"><div class="flbl">Requested quantity</div><input class="fi" type="number" id="po-qty" value="50" min="1"></div>
      <div class="fgr"><div class="flbl">Sizes needed</div><input class="fi" id="po-sizes" placeholder="e.g. M, L, XL or 40, 41, 42"></div>
      <div class="fgr"><div class="flbl">Supplier</div><input class="fi" id="po-supplier" placeholder="Supplier name"></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-new-po')">Cancel</button><button class="btn btn-p" onclick="saveNewPO()">Create request</button></div>
  </div>
</div>

<div class="mo" id="mo-incident">
  <div class="md wide">
    <div class="md-title">⚠ Report incident<button class="md-close" onclick="closeMo('mo-incident')">✕</button></div>
    <div class="fg">
      <div class="fgr"><div class="flbl">Type</div>
        <select class="fs" id="inc-type"><option>Typical accident</option><option>Near miss</option><option>Unsafe condition</option><option>Unsafe act</option><option>Occupational disease</option></select></div>
      <div class="fgr"><div class="flbl">Severity</div>
        <select class="fs" id="inc-sev"><option>Low</option><option>Medium</option><option>High</option><option>Critical</option></select></div>
      <div class="fgr"><div class="flbl">Date and time</div><input class="fi" type="datetime-local" id="inc-date"></div>
      <div class="fgr"><div class="flbl">Location</div><select class="fs" id="inc-loc"></select></div>
      <div class="fgr"><div class="flbl">Status</div>
        <select class="fs" id="inc-status-sel">
          <option value="Open">Open — awaiting investigation</option>
          <option value="Investigating">Under investigation</option>
          <option value="Pending Report">Awaiting report</option>
          <option value="Corrective Action">Corrective action in progress</option>
          <option value="Closed">Closed</option>
        </select>
      </div>
      <div class="fgr full"><div class="flbl">Exact location</div><input class="fi" id="inc-exact" placeholder="e.g. Production line B, sector 3"></div>
      <div class="fgr full"><div class="flbl">Description</div><textarea class="ft" id="inc-desc" placeholder="Describe what happened..."></textarea></div>
      <div class="fgr full"><div class="flbl">Involved employees</div><input class="fi" id="inc-inv" placeholder="Names (comma separated)"></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-incident')">Cancel</button><button class="btn btn-r" onclick="saveIncident()">⚠ Register</button></div>
  </div>
</div>

<div class="mo" id="mo-eval">
  <div class="md">
    <div class="md-title">◉ New evaluation<button class="md-close" onclick="closeMo('mo-eval')">✕</button></div>
    <div class="fg" style="margin-bottom:10px">
            <div class="fgr full">
        <div class="flbl">Employee</div>
        <div class="ep-wrap" id="ep-wrap-eval-emp">
          <input class="ep-input" id="ep-input-eval-emp" 
            placeholder="🔍 Type to search employee..."
            autocomplete="off"
            oninput="epFilter('eval-emp',this.value)"
            onfocus="epOpen('eval-emp')"
            onkeydown="epKey(event,'eval-emp')">
          <input type="hidden" id="eval-emp" name="eval-emp">
          <div class="ep-dropdown" id="ep-drop-eval-emp">
            <div class="ep-filter-bar">
              <input class="ep-search" id="ep-srch-eval-emp" placeholder="Search name..." 
                oninput="epFilter('eval-emp',this.value)" autocomplete="off">
              <select class="ep-pos-sel" id="ep-pos-eval-emp" onchange="epFilterPos('eval-emp',this.value)">
                <option value="">All positions</option>
              </select>
            </div>
            <div id="ep-list-eval-emp"></div>
          </div>
        </div>
      </div>
      <div class="fgr"><div class="flbl">Period</div><input class="fi" id="eval-period" placeholder="e.g. 2025-Q2 or 2025-Jun"></div>
    </div>
    <div style="font-size:10px;font-weight:700;color:var(--text2);text-transform:uppercase;letter-spacing:.05em;margin-bottom:9px">Scores per criterion (0–10)</div>
    <div class="fg">
      <div class="fgr"><div class="flbl">Productivity</div><input class="fi" type="number" min="0" max="10" step="0.1" value="8" oninput="calcScore()"></div>
      <div class="fgr"><div class="flbl">Quality</div><input class="fi" type="number" min="0" max="10" step="0.1" value="8.5" oninput="calcScore()"></div>
      <div class="fgr"><div class="flbl">Safety compliance</div><input class="fi" type="number" min="0" max="10" step="0.1" value="9" oninput="calcScore()"></div>
      <div class="fgr"><div class="flbl">Punctuality</div><input class="fi" type="number" min="0" max="10" step="0.1" value="7.5" oninput="calcScore()"></div>
      <div class="fgr"><div class="flbl">Teamwork</div><input class="fi" type="number" min="0" max="10" step="0.1" value="9" oninput="calcScore()"></div>
      <div class="fgr" style="display:flex;flex-direction:column;justify-content:flex-end">
        <div style="background:var(--bg3);border-radius:var(--r);padding:10px;text-align:center;border:1px solid var(--border)">
          <div style="font-size:9px;color:var(--text3);text-transform:uppercase;margin-bottom:2px">Average</div>
          <div id="avg-score" style="font-size:22px;font-weight:700;color:var(--teal)">8.4</div>
        </div>
      </div>
      <div class="fgr full"><div class="flbl">Feedback</div><textarea class="ft" id="eval-fb" placeholder="Strengths, areas of improvement..."></textarea></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-eval')">Cancel</button><button class="btn btn-p" onclick="saveEval()">Submit</button></div>
  </div>
</div>

<div class="mo" id="mo-warning">
  <div class="md">
    <div class="md-title">⚠ New warning<button class="md-close" onclick="closeMo('mo-warning')">✕</button></div>
    <div class="fg">
            <div class="fgr full">
        <div class="flbl">Employee</div>
        <div class="ep-wrap" id="ep-wrap-warn-emp">
          <input class="ep-input" id="ep-input-warn-emp" 
            placeholder="🔍 Type to search employee..."
            autocomplete="off"
            oninput="epFilter('warn-emp',this.value)"
            onfocus="epOpen('warn-emp')"
            onkeydown="epKey(event,'warn-emp')">
          <input type="hidden" id="warn-emp" name="warn-emp">
          <div class="ep-dropdown" id="ep-drop-warn-emp">
            <div class="ep-filter-bar">
              <input class="ep-search" id="ep-srch-warn-emp" placeholder="Search name..." 
                oninput="epFilter('warn-emp',this.value)" autocomplete="off">
              <select class="ep-pos-sel" id="ep-pos-warn-emp" onchange="epFilterPos('warn-emp',this.value)">
                <option value="">All positions</option>
              </select>
            </div>
            <div id="ep-list-warn-emp"></div>
          </div>
        </div>
      </div>
      <div class="fgr"><div class="flbl">Type</div><select class="fs" id="warn-type"><option>Verbal</option><option>Written</option><option>Suspension</option></select></div>
      <div class="fgr full"><div class="flbl">Reason</div><input class="fi" id="warn-reason" placeholder="Reason for warning..."></div>
      <div class="fgr full"><div class="flbl">Description</div><textarea class="ft" id="warn-desc" placeholder="Describe the facts..."></textarea></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-warning')">Cancel</button><button class="btn btn-a" onclick="saveWarning()">Issue warning</button></div>
  </div>
</div>

<div class="mo" id="mo-employee">
  <div class="md wide">
    <div class="md-title">👤 New employee<button class="md-close" onclick="closeMo('mo-employee')">✕</button></div>
    <div class="fg">
      <div class="fgr full"><div class="flbl">Full name</div><input class="fi" id="emp-name" placeholder="Full name"></div>
      <div class="fgr"><div class="flbl">Employee #</div><input class="fi" id="emp-num" placeholder="e.g. 123"></div>
      <div class="fgr"><div class="flbl">Position</div><input class="fi" id="emp-pos" placeholder="e.g. DRIVER"></div>
      <div class="fgr"><div class="flbl">Location</div><select class="fs" id="emp-loc-sel" onchange="var l=D.locations.find(x=>x.id===this.value);if(l)document.getElementById('emp-region').value=l.region||'';"></select></div>
      <div class="fgr"><div class="flbl">Region</div><input class="fi" id="emp-region" placeholder="e.g. Gauteng, North West..."></div>
      <div class="fgr"><div class="flbl">Department</div><input class="fi" id="emp-dept" placeholder="e.g. Operations"></div>
      <div class="fgr"><div class="flbl">Gender</div><select class="fs" id="emp-gender"><option>Male</option><option>Female</option></select></div>
      <div class="fgr"><div class="flbl">Status</div><select class="fs" id="emp-status"><option>Active</option><option>Vacation</option><option>Other</option><option>Maternity Leave</option></select></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-employee')">Cancel</button><button class="btn btn-p" onclick="saveEmployee()">Register</button></div>
  </div>
</div>

<div class="mo" id="mo-location">
  <div class="md" style="max-width:420px">
    <div class="md-title">📍 Add location<button class="md-close" onclick="closeMo('mo-location')">✕</button></div>
    <div class="fg">
      <div class="fgr"><div class="flbl">Location name</div><input class="fi" id="loc-name-inp" placeholder="e.g. Durban North"></div>
      <div class="fgr"><div class="flbl">Country</div><input class="fi" id="loc-country-inp" value="South Africa"></div>
      <div class="fgr"><div class="flbl">Region / Province</div><input class="fi" id="loc-region-inp" placeholder="e.g. Gauteng"></div>
      <div class="fgr"><div class="flbl">Manager</div><input class="fi" id="loc-manager-inp" placeholder="Manager name"></div>
    </div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-location')">Cancel</button><button class="btn btn-p" onclick="saveLocation()">Add location</button></div>
  </div>
</div>

<div class="mo" id="mo-auto-actions">
  <div class="md wide">
    <div class="md-title">⚙ Edit automatic actions<button class="md-close" onclick="closeMo('mo-auto-actions')">✕</button></div>
    <div style="font-size:11px;color:var(--text2);margin-bottom:14px">Based on <b style="color:var(--teal)">ISO 45001:2018</b>, <b style="color:var(--teal)">ILO-OSH 2001</b> and <b style="color:var(--teal)">OHSAS 18001</b></div>
    <div id="edit-actions-list"></div>
    <button class="btn btn-g btn-sm" style="margin-top:10px" onclick="addAutoAction()">+ Add action</button>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-auto-actions')">Cancel</button><button class="btn btn-p" onclick="saveAutoActions()">💾 Save actions</button></div>
  </div>
</div>

<div class="mo" id="mo-eval-detail">
  <div class="md">
    <div class="md-title">◉ <span id="eval-det-title">Evaluation</span><button class="md-close" onclick="closeMo('mo-eval-detail')">✕</button></div>
    <div id="eval-det-body"></div>
    <div class="md-footer">
      <button class="btn btn-r btn-sm edit-guard" onclick="deleteCurrentEval()">🗑 Delete</button>
      <button class="btn btn-g" onclick="closeMo('mo-eval-detail')">Close</button>
      <button class="btn btn-p btn-sm edit-guard" onclick="saveEvalDetail()">💾 Save</button>
    </div>
  </div>
</div>

<div class="mo" id="mo-training">
  <div class="md">
    <div class="md-title">📋 Add training record<button class="md-close" onclick="closeMo('mo-training')">✕</button></div>
    <div class="fg">
      <div class="fgr full">
        <div class="flbl">Employee</div>
        <div class="ep-wrap" id="ep-wrap-train-emp">
          <input class="ep-input" id="ep-input-train-emp" 
            placeholder="🔍 Type to search employee..."
            autocomplete="off"
            oninput="epFilter('train-emp',this.value)"
            onfocus="epOpen('train-emp')"
            onkeydown="epKey(event,'train-emp')">
          <input type="hidden" id="train-emp" name="train-emp">
          <div class="ep-dropdown" id="ep-drop-train-emp">
            <div class="ep-filter-bar">
              <input class="ep-search" id="ep-srch-train-emp" placeholder="Search name..." 
                oninput="epFilter('train-emp',this.value)" autocomplete="off">
              <select class="ep-pos-sel" id="ep-pos-train-emp" onchange="epFilterPos('train-emp',this.value)">
                <option value="">All positions</option>
              </select>
            </div>
            <div id="ep-list-train-emp"></div>
          </div>
        </div>
      </div>
      <div class="fgr full"><div class="flbl">Training name</div><input class="fi" id="train-name" placeholder="e.g. Working at height NR-35"></div>
      <div class="fgr"><div class="flbl">Standard / Regulation</div><input class="fi" id="train-nr" placeholder="e.g. NR-35"></div>
      <div class="fgr"><div class="flbl">Expiry date</div><input class="fi" type="date" id="train-exp"></div>
      <div class="fgr"><div class="flbl">Status</div>
        <select class="fs" id="train-status">
          <option>Valid</option><option>Expiring 30d</option><option>Expired</option>
        </select>
      </div>
    </div>
    <div class="md-footer">
      <button class="btn btn-g" onclick="closeMo('mo-training')">Cancel</button>
      <button class="btn btn-p" onclick="saveTraining()">Add record</button>
    </div>
  </div>
</div>

<div class="mo" id="mo-del-request">
  <div class="md" style="max-width:460px">
    <div class="md-title">🗑 Request deletion approval<button class="md-close" onclick="closeMo('mo-del-request')">✕</button></div>
    <div style="background:rgba(255,170,0,.1);border:1px solid rgba(255,170,0,.3);border-radius:var(--r);padding:10px 13px;margin-bottom:14px;font-size:11px;color:var(--amber);line-height:1.6">
      ⚠ Only administrators can permanently delete records. Your request — including who you are, your location, and your reason — will be recorded in the audit log and sent to the administrator.
    </div>
    <div style="background:var(--amberb);border:1px solid rgba(255,170,0,.3);border-radius:var(--r);padding:10px 13px;font-size:12px;color:var(--amber);margin-bottom:14px">
      ⚠ Only administrators can permanently delete records. Your request will be sent to the admin for approval.
    </div>
    <input type="hidden" id="del-req-type">
    <input type="hidden" id="del-req-id">
    <div class="fgr" style="margin-bottom:12px">
      <div class="flbl">Item to delete</div>
      <div id="del-req-item" style="background:var(--bg3);border-radius:var(--r);padding:9px 12px;font-size:12px;color:var(--text)"></div>
    </div>
    <div class="fgr">
      <div class="flbl">Reason for deletion</div>
      <textarea class="ft" id="del-req-reason" placeholder="Explain why this record should be deleted..."></textarea>
    </div>
    <div class="md-footer">
      <button class="btn btn-g" onclick="closeMo('mo-del-request')">Cancel</button>
      <button class="btn btn-a" onclick="submitDeleteRequest()">Send request to Admin</button>
    </div>
  </div>
</div>

<div class="mo" id="mo-del-admin">
  <div class="md wide">
    <div class="md-title">🗑 Pending deletion requests<button class="md-close" onclick="closeMo('mo-del-admin')">✕</button></div>
    <div id="del-admin-list"></div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-del-admin')">Close</button></div>
  </div>
</div>

<div class="mo" id="mo-edit-record">
  <div class="md wide">
    <div class="md-title">✏ Edit record<button class="md-close" onclick="closeMo('mo-edit-record')">✕</button></div>
    <div id="edit-record-body"></div>
    <div class="md-footer">
      <button class="btn btn-g" onclick="closeMo('mo-edit-record')">Cancel</button>
      <button class="btn btn-p" onclick="saveEditRecord()">💾 Save changes</button>
    </div>
  </div>
</div>

<div class="mo" id="mo-ppe-detail">
  <div class="md wide">
    <div class="md-title">🛡 PPE Item Detail<button class="md-close" onclick="closeMo('mo-ppe-detail')">✕</button></div>
    <div id="ppe-detail-body"></div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-ppe-detail')">Close</button></div>
  </div>
</div>

<div class="mo" id="mo-record-detail">
  <div class="md wide">
    <div class="md-title"><span id="record-detail-title">Record Detail</span><button class="md-close" onclick="closeMo('mo-record-detail')">✕</button></div>
    <div id="record-detail-body"></div>
    <div class="md-footer"><button class="btn btn-g" onclick="closeMo('mo-record-detail')">Close</button></div>
  </div>
</div>

<div id="toast"></div>
<div id="install-banner" style="display:none">
  📱 Install app: <button class="btn btn-p btn-sm" onclick="installApp()">Install</button>
  <button class="btn-icon" onclick="document.getElementById('install-banner').style.display='none'">✕</button>
</div>

<script>
// No auto-server — using Firebase or local mode
// ═══════════════════════════════════════════════════
// CONSTANTS & DATA
// ═══════════════════════════════════════════════════
const SK = 'sms_v8';       // v8 — fresh key clears all old data
const SES_K = 'sms_ses_v8';

const ROLE_LABELS = {admin:'Administrator',regional_safety:'Regional Safety Analyst',safety_analyst:'Safety Analyst',operator:'Operator',viewer:'Viewer'};
const ROLE_COLORS = {admin:'#00d4a0',regional_safety:'#4d9fff',safety_analyst:'#9d7dff',operator:'#ffaa00',viewer:'#ff4d6d'};
const ROLE_PAGES = {
  admin:['dashboard','ppe','incidents','performance','employees','locations','reports','settings','audit'],
  regional_safety:['dashboard','ppe','incidents','performance','employees','locations','reports','audit'],
  safety_analyst:['dashboard','ppe','incidents','performance','employees','locations','reports','audit'],
  operator:['dashboard','ppe','incidents','performance','employees','locations','reports','audit'],
  viewer:['dashboard','ppe','incidents','performance','employees','locations','reports','audit'],
};
// regional_safety can see Regional Analyst KPI tab; others cannot
const CAN_SEE_REGIONAL_KPI = ['admin','regional_safety'];
const CAN_EDIT = ['admin','regional_safety','safety_analyst','operator'];
const NEEDS_LOC = ['safety_analyst','operator','viewer']; // must pick location on login

function defaultData() { return {
  cfg:{company:'Safety System',dept:'SESMT',admin:'Administrator',email:'admin@company.com',logo:'S',maxInc:4,minComp:90,minScore:7.0,alertDays:30},
  locations:[
    {id:'HEAD_OFFICE',name:'HEAD OFFICE',country:'South Africa',region:'Gauteng'},
    {id:'ALRODE_T1_BREWERY',name:'ALRODE T1 BREWERY',country:'South Africa',region:'Gauteng'},
    {id:'ALRODE_BREWERY',name:'ALRODE BREWERY',country:'South Africa',region:'Gauteng'},
    {id:'BARAGWANATH',name:'BARAGWANATH',country:'South Africa',region:'Gauteng'},
    {id:'RUSTENBURG',name:'RUSTENBURG',country:'South Africa',region:'North West'},
    {id:'MAFIKENG',name:'MAFIKENG',country:'South Africa',region:'North West'},
    {id:'POTCHEFSTROOM',name:'POTCHEFSTROOM',country:'South Africa',region:'North West'},
    {id:'WELKOM',name:'WELKOM',country:'South Africa',region:'Free State'},
    {id:'KIMBERLEY',name:'KIMBERLEY',country:'South Africa',region:'Northern Cape'},
    {id:'HARTSWATER',name:'HARTSWATER',country:'South Africa',region:'Northern Cape'},
    {id:'NWL_SERVICE',name:'NWL SERVICE',country:'South Africa',region:'Gauteng'},
  ],
  users:[
    {username:'admin',display:'Administrator',password:'admin123',role:'admin',dept:'SESMT',locationAccess:'all',color:'#00d4a0'},
    {username:'regional',display:'Regional Safety Analyst',password:'regional123',role:'regional_safety',dept:'SESMT',locationAccess:'all',color:'#4d9fff'},
    {username:'analyst.alrode',display:'Safety Analyst Alrode',password:'analyst123',role:'safety_analyst',dept:'Operations',locationAccess:'ALRODE_T1_BREWERY',color:'#9d7dff'},
    {username:'analyst.bara',display:'Safety Analyst Bara',password:'analyst123',role:'safety_analyst',dept:'Operations',locationAccess:'BARAGWANATH',color:'#ffaa00'},
    {username:'manager',display:'Operations Manager',password:'manager123',role:'operator',dept:'Operations',locationAccess:'all',color:'#ff4d6d'},
    {username:'viewer',display:'HR Viewer',password:'viewer123',role:'viewer',dept:'HR',locationAccess:'all',color:'#7f77dd'},
  ],
  kpis:{inc:0,ppe:0,train:0,conf:0},
  ppeItems:[],
  deliveries:[],
  purchaseOrders:[],
  incidents:[],
  corrActions:[],
  evaluations:[],
  warnings:[],
  trainings:[],
  autoActions:[
    {trigger:'Score < 7.0',action:'Formal notification to direct manager (ISO 45001 cl. 9.1)',norm:'ISO 45001:2018 §9.1.1',color:'var(--amber)',active:true},
    {trigger:'Score < 5.0 (2nd cycle)',action:'Performance review meeting within 48h (ILO-OSH §3.16)',norm:'ILO-OSH 2001 §3.16',color:'var(--red)',active:true},
    {trigger:'Incidents > target/month',action:'Mandatory root cause investigation — bow-tie method (ISO 45001 cl. 10.2)',norm:'ISO 45001:2018 §10.2',color:'var(--red)',active:true},
    {trigger:'PPE below minimum',action:'Purchase request generated and manager notified (OHSAS 18001 cl. 4.4.6)',norm:'OHSAS 18001 §4.4.6',color:'var(--amber)',active:true},
    {trigger:'Training expired',action:'Area access blocked and recertification scheduled (ISO 45001 §7.2)',norm:'ISO 45001:2018 §7.2',color:'var(--red)',active:true},
    {trigger:'Serious/fatal accident',action:'Regulatory authority notification within 24h (ILO C155 / ISO 45001 §10.2)',norm:'ILO C155 / ISO 45001 §10.2',color:'var(--red)',active:true},
  ],
  alerts:[],
  logEntries:[],
  incidentChart:{
    '6m':{labels:['Jan','Feb','Mar','Apr','May','Jun'],data:[0,0,0,0,0,0]},
    '3m':{labels:['Apr','May','Jun'],data:[0,0,0]},
    '1m':{labels:['W1','W2','W3','W4'],data:[0,0,0,0]}
  },
  areas:[],
  simCount:0,
  employees:[
    {num:'1',name:'Habiba Yasmin Maconha',pos:'ACCOUNTING COORDINATOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'2',name:'Ricardo George Barbosa Valongo',pos:'REGIONAL MANAGER',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'4',name:'Alfred Lulu Shabangu',pos:'FLEET ANALYST',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'5',name:'Serge Kurt Nelson',pos:'BUYER JUNIOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'6',name:'Sheba Nudas Mathebula',pos:'BUYER',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'8',name:'Bongani Sibusiso Tshabalala',pos:'OPERATIONS COORDINATOR',status:'Other',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'11',name:'Sanky Vander Novela',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'12',name:'Jabulile Mokele',pos:'FINANCIAL ANALYST',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'14',name:'Londiwe Mseleku',pos:'HR ANALYST',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'19',name:'Naphtal Mphendukeni Zwane',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'20',name:'Jeff Makhuvele',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'21',name:'Themba Clifford Mtuze',pos:'FLEET ANALYST',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'22',name:'Marcio Jose Ribeiro Dos Santos',pos:'DIRECTOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'23',name:'Vanessa Carlos De Brito Fegueiredo',pos:'HR COORDINATOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'24',name:'Brenda Ortiz Leandro Ricardo',pos:'HR SUPERVISOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'26',name:'Joseph Mkhabela',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'27',name:'Lindani Katleho Nicholas Khumalo',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'28',name:'Mbedzi Ramaano Zacharia',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'31',name:'Sbusiso Shadrack Ndhlangamandla',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'34',name:'Vutomi Ben Masinge',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'35',name:'Sipho Cyphrian Ndumo',pos:'SHUNTER- DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'37',name:'Bongani Freddy Buthelezi',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'38',name:'Bongani Jeffrey Shabalala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'39',name:'Francisco Lucas Matsinho',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'40',name:'Hendry Manganyi',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'41',name:'John Khoza',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'42',name:'Leabuwa Joseph Raisa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'44',name:'Mandla Williams',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'45',name:'Msingathi Vellem',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'47',name:'Robert Mphumeleli Mtshali',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'48',name:'Sifiso Mahlalela',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'49',name:'Sihle Nsibande',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'51',name:'Siyabonga Masango',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'52',name:'Nkululeko Vincent Zulu',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'53',name:'Vusimuzi France Nkosi',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'54',name:'Lucky Lehlohonolo Motsie',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'55',name:'Byron Yulin Van Wyk',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'56',name:'Cliff Hlulani Hlungwani',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'58',name:'Moshe Frans Selatola',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'60',name:'Jack Kgorometja Lepogo',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'61',name:'Sihle Boavactura Jacob',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'62',name:'Makhado Warning Mukwevho',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'63',name:'Mbavhalelo Edmond Ramabulana',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'64',name:'Moses Mangana Segooa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'65',name:'Motsamai Frank Makheta',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'66',name:'Nkosinathi Mkhwela',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'69',name:'Oscar Nkosi',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'77',name:'Aluwani David Sadiki',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'80',name:'Bongani Philmon Khoza',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'83',name:'Bushelezana Jerry Mabizela',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'84',name:'Cebolenkosi Mafuya',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'85',name:'Emmanuel Mosele Matimela',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'86',name:'Emmanuel Mzikabani Xaba',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'87',name:'Fenias Tomas Chauke',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'89',name:'Hasani Thomas Maceke',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'90',name:'Ignitious Rikhotso',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'92',name:'Joao Sebastiao Muguambe',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'93',name:'Khuduwane Clarence Malatjie',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'97',name:'Muziwakhe Markos Mazibuko',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'98',name:'Mvumeni Samuel Mdlalose',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'99',name:'Mzonke Eliiot Fusa',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'100',name:'Neo Motlafi',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'103',name:'Patrik Malope',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'105',name:'Sipho Meshack Mudzindiko',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'106',name:'Siyabonga Nama',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'108',name:'Trevor William Baloyi',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'110',name:'Veli Amos Ngwenya',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'111',name:'Vukani Welcome Mbambo',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'112',name:'Thabo Welcome Mofokeng',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'113',name:'Tshepo Benett Hlongwane',pos:'SHUNTER- DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'114',name:'Musawenkosi Erasmus Mavundla',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'115',name:'Khanyisile Baleni',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'116',name:'Mphekwa Maisela',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'117',name:'Lucky Johannes Dlamini',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'118',name:'Fufu Masina',pos:'SHUNTER- DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'121',name:'Sipho Dan Ndlovu',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'122',name:'Phakani Sithole',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'123',name:'Bhekinkosi Walter Gcabashe',pos:'FINANCIAL ANALYST',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'124',name:'Ugan Govenden',pos:'BRANCH MANAGER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'125',name:'Siyabonga Sithole',pos:'MECHANIC',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'126',name:'Moeketsi Petrus Moloi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'128',name:'Kgalalelo Shereen Molobi',pos:'HR ANALYST',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'129',name:'Tshiamo Morweng',pos:'BRANCH MANAGER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'135',name:'Bam Binifatius',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'136',name:'Costa Moyo',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'137',name:'Edwin Nthabiseng Letlhogonolo Mosekwane',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'138',name:'Edwin Sebatleng Masoko',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'139',name:'Isaac Kagiso Mogwera',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'140',name:'Kefilwe Daniel Tsele',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'141',name:'Lebogang Maswabi',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'144',name:'Joseph Lepogo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'145',name:'Veronica Veronica Mabote',pos:'OPERATIONS COORDINATOR',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'146',name:'Gopolang Andrew Ndaba',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'148',name:'Dineo Debra Madisa',pos:'FLEET ASSISTANT',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'150',name:'Mooketsi Trevor Bodigelo',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'151',name:'Peter Ogopoleng Mmusi',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'152',name:'Phuthego Jury Matsosa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'153',name:'Pontsho Sibasa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'155',name:'Tshepiso Stoffol Mafora',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'158',name:'Abednego Modisaotile Phatshwane',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'160',name:'Boineelo Vincent Gabe',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'162',name:'France Monnapula Mogorosi',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'163',name:'Johannes Toko Matshogo',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'166',name:'Lawrence Nkgape Sefako',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'167',name:'Marumo Sonnyboy Sedombu',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'168',name:'Mothusi Shilombe',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'169',name:'Papa Sithole',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'170',name:'Paseka Goitsemodimo Tlhowe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'172',name:'Sello Jack Nkwana',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'173',name:'Shadrack Morudi',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'174',name:'Tebogo Wellem Disipi',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'176',name:'Thapelo Odacius Moabi',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'177',name:'Tlabo Donald Madiope',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'178',name:'Tlotliso Edward Motloung',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'179',name:'Tumelo Phillip Mothoagae',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'180',name:'Tyelo Karel Mothobi',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'181',name:'Wilfred Molefe Mokhine',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'182',name:'Kgalalelo Matshediso',pos:'SAFETY ANALYST',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Female'},
    {num:'183',name:'Vhutshilo Justice Makekeba',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'184',name:'Mathews Lesiba Tladi',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'187',name:'Mahlathini Thulani Ndlovu',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'188',name:'Bafana Welcome Mjijwa',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'192',name:'Thabang Cavin Mokati',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'194',name:'Serame Aaron Senna',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'195',name:'Nomvula Mavis Nkosi',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'196',name:'Melokwakhe Siphelele Mavundla',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'197',name:'Khayelihle Mbatha',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'198',name:'Lesedi Tshwane',pos:'FINANCIAL ANALYST',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'199',name:'Mandla Zingeni',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'202',name:'Thabang Joseph Mashinini',pos:'MECHANIC',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'205',name:'Maripana Kgoboko',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'207',name:'Kebakile Macdonald Baraganye',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'212',name:'Bongani Promise Xulu',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'215',name:'Alice Andiswa Sophi',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'216',name:'Bolishevic Kopano Thobejane',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'220',name:'Bulelani Hamilton Tuswa',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'225',name:'Khotsofalang Mohlauli',pos:'FORKLIFT DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'227',name:'Modisaotsile Elias Modibetsane',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'230',name:'Ditiro Joseph Diseko',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'231',name:'Khanyile Joseph Somzila',pos:'HELPER LEADER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'236',name:'Thando Sanele Thawala',pos:'HELPER LEADER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'237',name:'Jafta Nyaku Makgato',pos:'HELPER LEADER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'239',name:'Thalles Mateus Santos Soares',pos:'OCCUPATIONAL SAFETY SUPERVISOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'241',name:'Cesar Willian Pereira',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'242',name:'Alessandra Dos Santos Pereira',pos:'FLEET SUPERVISOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'243',name:'Samuel Molapo Kaise',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'245',name:'Lindokuhle Lerato Koloba',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'246',name:'Rebaona Kelly Moswane',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'247',name:'Ditiro Michael Jama',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'248',name:'Dumisani Matthews Malaza',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'250',name:'Abel Itumeleng Masibi',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'251',name:'Puso Mokopanele',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'252',name:'Tshepo Andrew Tsubane',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'254',name:'Lefu Freedom Ndaba',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'255',name:'Odirile Helman Setlhatloso',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'256',name:'James Slaai',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'258',name:'Katlego Precious Kokozela',pos:'FINANCIAL ANALYST',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'259',name:'Muhle Progress Sifunda',pos:'SAFETY ANALYST',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'260',name:'Thabo George Leburu',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'261',name:'Moagisi Yule Molamu',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'262',name:'Aobakwe Ivan Mankuroane',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'263',name:'Modisenyane William Balaoleng',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'264',name:'Kagiso Kegopotswe',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'266',name:'Thutego Sylvester Bosele',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'267',name:'John Sizane Khalipa',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'268',name:'Mosimanegape Ishmael Mess',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'270',name:'Nelson Tiragalo Moses',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'271',name:'Sipho Simon Ramoba',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'272',name:'Thabo Patrick Mokoto',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'273',name:'Bethuel Petsola Mokawane',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'276',name:'Molefi Gaddafi Moseki',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'277',name:'Christopher Fikile Thebeeng',pos:'SHUNTER- DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'278',name:'Lesego William Monnapula',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'279',name:'Modirakgotla Ernest Diphoko',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'280',name:'Kantoro April Mafokeng',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'281',name:'Evidence Thembani Mosia',pos:'HELPER LEADER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'283',name:'Thabang Letsomo',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'284',name:'Phello Solomon Phallo',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'285',name:'Abel Motsamai Modisadife',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'286',name:'Sabelo Valentino Mabhena',pos:'FLEET ANALYST',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'287',name:'Peter Ranko Simelane',pos:'FLEET SUPERVISOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'288',name:'Rethabile Sehemo',pos:'OPERATIONS ASSISTANT',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Female'},
    {num:'290',name:'Johannes Sekobo Thobakgale',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'292',name:'Gugulethu Millecent Mkhonto',pos:'FINANCIAL ANALYST',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Female'},
    {num:'294',name:'Tshepiso Meshack Letshabo',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'295',name:'James Molete',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'297',name:'Tshepang Thembani Mangena',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'298',name:'Thabiso Ernest Sechele',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'301',name:'Tshibvumo Eddie Mauba',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'302',name:'Valson Thulane Tshabalala',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'303',name:'William Luckyboy Miles',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'304',name:'Bulelani Tengwa',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'305',name:'Lebogang Collen Nthutang',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'309',name:'Lebohang Vincent Thobela',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'311',name:'Mangaliso Daniel Moss',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'312',name:'Lloyd Thamsanqa Mahlangu',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'314',name:'Cliffort Ikaneng Sereo',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'318',name:'Kamogelo James Dinake',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'319',name:'Hloniphani Mbambela',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'320',name:'Wayne Lwazi Mabena',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'321',name:'Thapelo Patrick Stona',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'324',name:'Tumelo Joel Telekoa',pos:'SHUNTER- DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'325',name:'Daphney Madavha',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'326',name:'Tshawe Monwabisi Mali',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'328',name:'Ofentse Lernart Tshabalala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'329',name:'Zama Majola',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'330',name:'Asinike Nkonyanebomvu',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'333',name:'Molefi Solomon Serame',pos:'DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'335',name:'Molelekwa Petrus Serame',pos:'DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'336',name:'Lesang Nicholas Matlhoko',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'337',name:'Keolebogile Edward Osiang',pos:'DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'338',name:'Ntshabele Josiah Ntsimane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'340',name:'Tsaone Christopher Sapeloeng',pos:'DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'341',name:'Ntsokolo Mackson Kaekema',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'342',name:'Selego Isaac Pholoana',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'344',name:'Velaphi Allen Tshabangu',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'345',name:'Young Maliwa',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'348',name:'Mzwandile Patric Siko',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'349',name:'Thabo Sam Senohe',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'350',name:'Sylvester Tiisetso Ramosie',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'351',name:'Simon Mandisi Jordaan',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'352',name:'Thato Andries Maphisa',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'353',name:'Malefetsane Harmans Sebatana',pos:'SHUNTER- DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'355',name:'Tumelo Jonas Mosese',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'356',name:'Sibusiso Goda',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'357',name:'Boitumelo Shadrack Molale',pos:'DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'359',name:'John Silas Kale',pos:'DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'360',name:'Olebogeng John Peme',pos:'DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'362',name:'Ompolokile Vincent Mere',pos:'DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'363',name:'Tumisang Thomson Mojela',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'365',name:'Lebogang Gabriel Moremane',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'366',name:'Tshenolo Mathews Piterson',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'371',name:'Kaelo Simon Seokwang',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'372',name:'Boitumelo Collin Moabi',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'374',name:'Gift Fadzai Kaguda',pos:'SHUNTER- DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'376',name:'Buti Ernest Letlooa',pos:'MECHANIC',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'381',name:'Khetho Phinda',pos:'FLEET ANALYST',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'382',name:'Zodwa Monyepao',pos:'OPERATIONS SUPERVISOR',status:'Other',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Female'},
    {num:'387',name:'Sello Aubrey Moloi',pos:'BRANCH MANAGER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'388',name:'Gerrit Joubert',pos:'T1 OPERATIONS COORDINATOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'390',name:'Jeneffer Komba',pos:'HR SUPERVISOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'391',name:'Thabo William Mampe',pos:'BRANCH MANAGER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'392',name:'Kopano Dimpho Lepedi',pos:'OPERATIONS ASSISTANT',status:'Maternity Leave',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'396',name:'Phuti Provia Kgomo',pos:'SAFETY ANALYST',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'397',name:'Refiloe Lillian Moshoeu',pos:'HR ANALYST',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Female'},
    {num:'399',name:'Celane Plaatjies',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'400',name:'Tshepiso Relebogile Modise',pos:'HR ANALYST',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'402',name:'Anathi Ntlabathi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'405',name:'Bulelani Brian Ntlabathi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'406',name:'Charles Mondjezi Malema',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'407',name:'Enerst Nkuna',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'408',name:'Fele Makamole',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'409',name:'Masinda Jacisa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'410',name:'Ketseletso Aron Moshoeshoe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'411',name:'Lehlohonolo John Moloi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'412',name:'Lesodi Soldaat Mbele',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'413',name:'Masilo Obed Moila',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'414',name:'Mcebo Chiyi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'415',name:'Melusi Ottoh Hlatswayo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'416',name:'Mjabulisi Alfred Ngobese',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'417',name:'Moeketsi Joseph Maleho',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'418',name:'Mxolisi David Mthanti',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'419',name:'Mveleli Mavuso',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'420',name:'Nkosinkhona Lindokuhle Mabaso',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'421',name:'Olwethu Makaula',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'422',name:'Sipho Lindelani Menyoka',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'423',name:'Sipho Moses Buthelezi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'424',name:'Siyabulela Gusha',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'425',name:'Tshepo Jacob Sindane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'427',name:'Henry Bongani Theledi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'428',name:'Aaron Mkhulu Mahlangu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'430',name:'Witness Maluleke',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'431',name:'Avuyile Mbengo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'432',name:'Luleko O\'Brian Mbhele',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'473',name:'Mduduzi Joseph Twala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'474',name:'Mqwalaseli Mthwesi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'475',name:'Sandile Sydwell Mango',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'476',name:'Sandisiwe Sanele Maphasa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'477',name:'Khwahla Thomas Gqozo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'479',name:'Tebogo Lucky Nkau',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'482',name:'Nkululeko Nkomentaba',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'483',name:'Bonisile Mashiqa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'484',name:'Mohlabi William Letsoalo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'485',name:'Chaveni Daniel Mhlanga',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'486',name:'Thulasizwe Promise Zikhali',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'487',name:'Thulani Mphakameleni Masondo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'488',name:'Peron Banele Nkosi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'489',name:'Mxolisi Situma',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'490',name:'Matimba Given Mongwe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'491',name:'Mohale Felix Mathedimosa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'492',name:'Lungani Praiseworth Zwane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'493',name:'Mthobisi Victor Nyandeni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'497',name:'Luyanda Mgibanyoni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'498',name:'Mfanafuthi Mathiesen Ntuli',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'499',name:'Philemon Ndodomzi Njova',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'500',name:'Mduduzi Nkosinathi Skosana',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'501',name:'Livhuwani Tshamaano',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'502',name:'Ofentse Ignatious Ranape',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'503',name:'Sifiso Savy Tembe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'504',name:'Gaodihelwe Godfrey Selaledi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'505',name:'Bongani Desmond Thanjekwayo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'506',name:'Sandile Sphiwe Zondi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'507',name:'Tumelo James Mokgele',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'509',name:'Winners Khumbuza',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'510',name:'Thandisizwe Clemence Mashiya',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'511',name:'Thulang Clement Motloung',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'512',name:'Mthembeni Physical Dlephu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'513',name:'Ntobeko Loqo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'514',name:'Thokozani Emmanuel Gladman Hlongwane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'515',name:'Bheki Amos Mhlungu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'516',name:'Simon Mokoena',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'517',name:'Lucas Semonyo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'518',name:'Willies Ngobeni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'519',name:'Soza Given Maluleke',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'520',name:'Sanele Big-Boy Mbatha',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'521',name:'Tshilisanani Tshilingani',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'522',name:'Cleopas Phiwokwakhe Ntombela',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'523',name:'Moalosi Paul Makhalanyane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'524',name:'Lebogang Lesley Nkuna',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'526',name:'Nkosindiphile Gcali',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'527',name:'Nkosikhona Mpofu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'528',name:'Sipho Ephraim Nsibanyoni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'529',name:'Menzi S\'Bonelo Nxumalo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'530',name:'Sibongiseni Praisewell Sikhosana',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'531',name:'Bongani Ndandani',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'532',name:'John Mojakgomo Matsealepoo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'533',name:'Mokibelo Linken Nare',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'534',name:'Tankiso James Letlala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'535',name:'Freedom Fortune Kgene',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'536',name:'Dennis Jonas Maomela',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'537',name:'Mangaliso Alfred Majolo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'538',name:'Anele Ntanjana',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'540',name:'Gift Mpho Mokoena',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'541',name:'Mzukiseni Sizwe Katywa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'542',name:'Ndikho Malindi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'543',name:'Nkululeko Amos Marumole',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'544',name:'Sibusiso Wellington Mazibuko',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'546',name:'Arnold Ndobela',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'547',name:'Patrick Sbongiseni Nene',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'548',name:'Amukelani Ezrome Chauke',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'549',name:'Mokete David Moloi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'550',name:'Sandile Mcebiseni Buthelezi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'551',name:'Luthando Donald Somtsewu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'552',name:'Calvin Candru Mashele',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'553',name:'Excellent Samkelo Mduduzi Mlambo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'554',name:'Nkateko Nichold Khoza',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'555',name:'Themba Jim Ngoma',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'556',name:'Jabu John Ntshangase',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'557',name:'Sifiso Malevu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'558',name:'Mondli Hendrick Shezi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'559',name:'Tello David Rakaki',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'560',name:'Prayer Lamola',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'561',name:'Celenkosini Praise-God Muntuwokubongwa Ndlovu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'562',name:'Lawrence Mashinini',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'563',name:'Unathi Masixole Mnyamana',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'564',name:'Sibusiso Nobomvu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'566',name:'Raputshe Abram Thibile',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'567',name:'Katleho Lenyora',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'568',name:'Jacob Linda',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'569',name:'Thapelo Phahlane Molema',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'570',name:'Asah Jabu Nkosi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'571',name:'Andrew Visser',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'572',name:'Sonwabile Jaho',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'573',name:'Halalisani Sibonakaliso Mkhize',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'574',name:'Ndiphile Bolitye',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'575',name:'Thabiso Lesly Maphopha',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'576',name:'Vusimuzi Cecil Masuku',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'577',name:'Syvion Delani Mbanjwa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'578',name:'Lethu Ndabeni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'579',name:'Themba Given Tlou',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'580',name:'Hlalele Thakali',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'581',name:'Sibusiso Joseph Tsotetsi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'582',name:'Kgaugelo Elvis Mashego',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'583',name:'Dumisani Artwell Mbatha',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'584',name:'Absalom Mandla Mashinini',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'585',name:'Mthetheleli Jobe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'586',name:'Mkhululi Mazula',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'587',name:'Sefiso Alfonso Nkosi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'588',name:'Mzothini Petros Khumalo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'589',name:'Tshepo Petrus Sebola',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'590',name:'Khayalethu Mseleni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'592',name:'Sizwe Nqanawe Shange',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'593',name:'Thamsanqa Fortune Ntshalintshali',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'594',name:'Simphiwe Zondi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'595',name:'Mfanafuthi Sydwell Mokoena',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'597',name:'Nthokoleng Mathaba',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'598',name:'Hasani Aubrey Mitileni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'599',name:'Siphokuhle Secretary Shabalala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'600',name:'Bonga Makhitshi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'601',name:'Makhosonke Lawrence Ngcobo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'602',name:'Jan Maletsi Molifi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'603',name:'Risimati Lucky Mashele',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'604',name:'Matshisele Lesley Sadiki',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'605',name:'Amukelani Mavunda',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'606',name:'Louis Chuma',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'607',name:'Sibusiso Thomas Khoza',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'608',name:'Cingile Tintelo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'609',name:'Lucky Thulani Khumalo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'610',name:'Justice Siwele',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'611',name:'Mokgwadi Charles Mabane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'612',name:'Mashile Cleopus Mogashoa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'613',name:'Ernest Mosupulogo Matsoga',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'614',name:'Johannes Sphiwe Shabalala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'618',name:'Humphry Xolisa Ludidi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'619',name:'Daliwonga Maqungu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'620',name:'Latif Mahomed',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'621',name:'Paballo Kgabantloane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'622',name:'Frank Phillip Ngobeni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'623',name:'Alungile Sydwell Madolo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'625',name:'Thokozani Francis Mthembu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'626',name:'William Themba Kekana',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'628',name:'Tumisang Lazarus Morake',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'629',name:'Ndade Eric Melamu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'631',name:'Morris Collen Maswanganye',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'632',name:'Khotso Khotso Menyatswe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'633',name:'Nokuthula Angelinah Vumisa',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'634',name:'Nkululeko Nkululeko Shandu',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'635',name:'Tekoetsi David Sibi',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'636',name:'Dineo Zondo',pos:'FINANCIAL ANALYST',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'638',name:'Matiwane Jeffrey Marareni',pos:'MECHANIC',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'640',name:'Jabulani Makhoba',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'641',name:'David Shuping',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'642',name:'Ophelia Offentse Kapari',pos:'FLEET ASSISTANT',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'643',name:'Luis Manual Cordeiro',pos:'BRANCH MANAGER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'645',name:'Torrance Sizwe Khoza',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'646',name:'Mandla Mhlongo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'647',name:'Makgoba Freddy Frans Malatjie',pos:'MECHANIC',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'648',name:'Millicent Tears Morare',pos:'HR ANALYST',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'649',name:'Mahlomola Patrick Mocwane',pos:'DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'652',name:'Samuel Ohentse Morobane',pos:'DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'655',name:'Thato Brandon Modisadife',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'657',name:'Tshepo Lawrence Dinale',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'658',name:'Thato Edwin Moraloki',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'660',name:'Matshediso Alphius Marope',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'661',name:'Itumeleng Menong',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'662',name:'Kabelo Abram Molelekwa',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'664',name:'Lebogang Christopher Korope',pos:'SHUNTER- DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'665',name:'Taki Andries Moacwiemang',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'669',name:'Johannes Esterhuizen',pos:'BRANCH MANAGER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'671',name:'Rose-Anne Sibongile Mabuza',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'673',name:'Moreumane Bassanio Letsau',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'674',name:'Khothatso Wiseman Tolo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'675',name:'Mcdonald Dimakatso Ramalapa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'676',name:'Simon Mpho Ntoka',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'677',name:'Siyabonga Praisegod Mabaso',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'678',name:'Franklin Mavela Dhludhla',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'679',name:'Mzwandile Johannes Jama',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'681',name:'Thabo Prosper Ngwenya',pos:'MECHANIC',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'683',name:'Johan Christiaan Lodewikus Lombard',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'684',name:'Othusitse Joseph Khumalo',pos:'DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'686',name:'Thabo Sylvester Motsitsi',pos:'FORKLIFT DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'687',name:'Sebastian Jacobs Alphonso',pos:'HELPER LEADER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'690',name:'Mcebisi Mbanga Matheus',pos:'GENERAL WORKER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'692',name:'Moses Molefi Thabisho',pos:'GENERAL WORKER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'693',name:'Baamogetswe Bertha Dikeletsane Madisa',pos:'FINANCIAL ANALYST',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Female'},
    {num:'695',name:'Siphiwekuhle Ndlovu',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'696',name:'Vusimuzi Bernardo Mtolo',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'698',name:'Emmanuel Mfanampela Nhlabathi',pos:'MECHANIC',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'699',name:'Mancoba Gift Shongwe',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'702',name:'Sasha Lecheye Arends',pos:'FINANCIAL ANALYST',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'704',name:'Thembinkosi Patrick Mlambo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'706',name:'Njabulo Nhlanhla Wellington Nkosi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'707',name:'Michael Ramasepela',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'708',name:'Josiah Ramokgalagadi Moalosi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'709',name:'Daniel Fortunate Mkansie',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'710',name:'Welcome Sbusiso Skosana',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'711',name:'Siphesihle Goodwill Mdletshe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'712',name:'Senzo Sunjohn Miya',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'713',name:'Thabo Christopher Nonyane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'714',name:'Sandile Khonzuyise Mazibuko',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'715',name:'Oswell Abednigo Ngoveni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'716',name:'Hulisani Trevor Mukondeleli',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'717',name:'Mbongiseni Derick Kunene',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'718',name:'Minister Mongwe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'719',name:'Petros Mzukiseni Monakali',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'722',name:'Mpikeleli Jeremia Radebe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'723',name:'Molefi Nefthaly Mokhethi',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'724',name:'Good-Man Sandulela Myataza',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'725',name:'Angela Thabile Mothupi',pos:'FLEET ANALYST',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'727',name:'Lerato Priscilla Motsepa',pos:'FLEET ASSISTANT',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'728',name:'Gerald Victor Smith',pos:'GENERAL WORKER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'730',name:'Bongani Musa Mavimbela',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'731',name:'Olebogeng Tsatsinyane',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'733',name:'Moeketsi Modise',pos:'GENERAL WORKER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'735',name:'Keleabetswe Dorothy Gadise',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'736',name:'Alex Simango',pos:'FORKLIFT DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'737',name:'Wendel Agostinho -Guilhem',pos:'REGIONAL MANAGER',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'738',name:'Akthar Raza Khan',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'741',name:'Analo Magaulana',pos:'FLEET ASSISTANT',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'742',name:'Zwivhuya Mukhavhuli',pos:'FLEET ANALYST',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'743',name:'Sibonelo James Myaka',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'745',name:'Godiramang Samson Mothobi',pos:'SHUNTER- DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'747',name:'Thabang Edwin Modutwane',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'750',name:'Anathi September',pos:'GENERAL WORKER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'756',name:'Teboho Mpatane',pos:'GENERAL WORKER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'757',name:'Kamohelo Tsokolibane',pos:'GENERAL WORKER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'759',name:'Asakhe Siga',pos:'GENERAL WORKER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'760',name:'Joshua Tsatsi Mogorosi',pos:'HELPER LEADER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'762',name:'Goitsemodimo Frans Racodi',pos:'GENERAL WORKER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'763',name:'Paballo Nicolus Tiralo',pos:'GENERAL WORKER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'764',name:'Thato Johannes Moroane',pos:'GENERAL WORKER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'765',name:'Thabo David Mofo',pos:'HELPER LEADER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'768',name:'Asanda Innocent Dikwelane',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'769',name:'Malefetsane John Mofokeng',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'774',name:'Xiluvelo Manganyi',pos:'FLEET ANALYST',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'775',name:'Justin Luke Harle',pos:'SAFETY ANALYST',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'776',name:'Bhekani Matthews Mazibuko',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'777',name:'Charit Mathebula',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'778',name:'Bishop Mosoma',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'779',name:'Leche Kortjaas',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'780',name:'Mzimkhulu Skans Mlangeni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'781',name:'Sikhumbuzo Zamokwakhe Shandu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'782',name:'Oscar Jonfaith Moyane',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'783',name:'Luvuyo Nicholas Mpothulo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'784',name:'Vukane Petrus Mabhena',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'785',name:'Kwanele Listen Shabangu',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'786',name:'Maupi Petros Semenya',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'788',name:'Tebogo Shadrack Tingana',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'790',name:'Israel Mokete Mmolaeng',pos:'HELPER LEADER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'791',name:'Obakeng Isak Rooibaadjie',pos:'GENERAL WORKER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'795',name:'Sulphy Mpho Mayisa',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'797',name:'Themba Harry Mophiring',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'798',name:'Boitshoko Oratile Metswamere',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'800',name:'Phillip Boitsoko Leburwane',pos:'DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'801',name:'Lungelo Duma',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'802',name:'John Makonyana Motaung',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'803',name:'Lerato Johannes Mpholo',pos:'DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'806',name:'Wanderson Da Silva Franca',pos:'FLEET COORDINATOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'807',name:'Xolo Ntuthuko Nqoubuka',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'808',name:'Paulus Thithi Mokebe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'809',name:'Sekgwele Isabel Moabelo',pos:'FINANCE ASSISTANT',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'812',name:'Abenezear Job Muri',pos:'GENERAL WORKER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'823',name:'Tsireletso Ralekuku',pos:'SAFETY ANALYST',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'824',name:'Leornard Ngobeni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'832',name:'Kelebogile Jacqueline Mabilo',pos:'FINANCIAL ANALYST',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'835',name:'Teressa Joanna Da Silva',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'836',name:'Thuso Thuso Morokane',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'838',name:'Olebile Hamilton Olebile Moilwa',pos:'DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'839',name:'Rebaone Surprise Rebaone Mosiedi',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'840',name:'Abram Lelhlohonolo Lehlohonolo Selai',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'841',name:'Micheal Michael Saul',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'844',name:'Kealeboga Khodumo',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Female'},
    {num:'845',name:'Mojalefa Mogorosi',pos:'DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'846',name:'Jabulani Tshoba',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'847',name:'Nicole De Almeida Mogne',pos:'FINANCIAL ANALYST',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'855',name:'Lefa Percy Lengana',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'856',name:'Andrias Moleko',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'857',name:'David Tifo Mokhehle',pos:'DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'858',name:'Kgatliso Kgole',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'860',name:'Isaac Seun Mandu',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'864',name:'Rhulani Mzamani',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'865',name:'Frans Magabi Moilwa',pos:'DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'866',name:'Andile Cebisile Jiyana',pos:'SAFETY ANALYST',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'875',name:'Solomon Solomon Nku',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'876',name:'Ronald Reagan Mkhari',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'877',name:'Abram Motloung',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'878',name:'Benjamin Kgololo Lencwe',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'879',name:'Bongumenzi Zwelakhe Xulu',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'881',name:'Tiisetso Simon Motsei',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'882',name:'Tebogo Makgale',pos:'BRANCH MANAGER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'883',name:'Mzwandile Felix Matoko',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'891',name:'Trishana Kishori',pos:'FINANCE ASSISTANT',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'892',name:'Comfort Gabonwe Mokgadi',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'893',name:'Itumeleng Rejoice Molokoane',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'894',name:'Siphesihle Douglas Nkosi',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'896',name:'Tuelo Vincent Kegakilwe',pos:'DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'898',name:'Nomthandazo Sophy Masemola',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'899',name:'Thamsanqa Terrence Ntakakaze',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'901',name:'Richard Smyth',pos:'SENIOR FLEET ANALYST',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'902',name:'Nokhukhanya Gcinile Khumalo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'903',name:'Mzwandile Artwell Duma',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'904',name:'Engetani Winston Ngobeni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'905',name:'Katlego Isaac Nkitseng',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'906',name:'Boye Frans Matjila',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'907',name:'Carnox Mandla Mposha',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'908',name:'Aphelele Nkebe',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'909',name:'Siyabonga Duma',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'910',name:'Thomas Matlala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'911',name:'Raymond Tebogo Phalafala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'912',name:'Njabulo Senzo Mtungwa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'913',name:'Masekou Bessel Mothokwa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'914',name:'Simon Gezane Mngomezulu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'915',name:'Nicholas Anda Mqikela',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'916',name:'Siyabonga Collen Sithole',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'917',name:'Themba Nkabinde Mdumiseni',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'918',name:'Mhlanganisi Welcome Ndlovu',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'919',name:'Motsamai Petrus Mokoakoa',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'920',name:'Sifiso Mvelase',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'922',name:'Jane Judith Ndlala',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'924',name:'Sifiso Vincent Mdlalose',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'925',name:'Bakang Irvin Ditlhobolo',pos:'DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'926',name:'Boitshwarelo Moleme',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'927',name:'Aletta Themba',pos:'SAFETY ANALYST',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'929',name:'Bonginkosi Nkazimulo Xulu',pos:'DRIVER-HELPER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'930',name:'Sbongiseni Victor Nene',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'932',name:'Letlhogonolo George Duiker',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'933',name:'Itumeleng Bernard Modisapudi',pos:'DRIVER-HELPER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'934',name:'Boitshoko Gabriel Ndusu',pos:'GENERAL WORKER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'935',name:'Aminy Ngobeni',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'938',name:'Mthandazo Nilliton Dube',pos:'MECHANIC',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'939',name:'Mbongeni Hector Mahlangu',pos:'FLEET ASSISTANT',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'945',name:'Clifford Sising',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'946',name:'Karabo David Morake',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'947',name:'Siphiwe Sabelo Mlambo',pos:'GENERAL WORKER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'948',name:'Keamogetswe Ruth Mosime',pos:'SAFETY ANALYST',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'956',name:'Elijah Masiteng',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'958',name:'Lebogang David Mmopelwa',pos:'DRIVER-HELPER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'961',name:'Moeketsi Doctor Tsie',pos:'FORKLIFT DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'963',name:'Thabang Mabele',pos:'GENERAL WORKER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'964',name:'Jabulani Alfred Mahlangu',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'966',name:'Zwele Patrick Landu',pos:'DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'968',name:'Mpho Andrew Mofama',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'969',name:'Gomolemo Anthony Legodu',pos:'GENERAL WORKER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'970',name:'Tlhokomelo Jack Baleng',pos:'GENERAL WORKER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'971',name:'Boitumelo Nelson Nkgashu',pos:'GENERAL WORKER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'973',name:'Mzonakele Jazzman Wittes',pos:'DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'978',name:'Mncedisi Mpulo',pos:'DRIVER',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'979',name:'Masego Mabote',pos:'OPERATIONAL ASSISTANT',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'980',name:'Keorapetse Rearabetswe Galeng',pos:'HR ANALYST',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'981',name:'Hlabathini Mofokeng',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'982',name:'Una Belinda Britz',pos:'FLEET ASSISTANT',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'983',name:'Jonathan Ferguson',pos:'REGIONAL SAFETY  ANALYST',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Male'},
    {num:'985',name:'Kagiso Patrick Phakalatsane',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'986',name:'Kabelo Giveness Kwadibane',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'987',name:'Mosimanegape Solomon Peteke',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'988',name:'Adrienne Elton John Adolph',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'989',name:'Antony Mogohlwana',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'993',name:'Charissa-Ann Koegelenberg',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1001',name:'Happy Nkosana Tsoari',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1003',name:'Karabo Joseph Makgopela',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1004',name:'Kgotso Tobalete',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1005',name:'Zama Khetha Gwala',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1006',name:'Lisakanya Madolo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1007',name:'Mandla Talent Sambo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1008',name:'Matsobane Mokgethoa Galane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1010',name:'Musa Leonard Mahomani',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1012',name:'Mushe Hlungwane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1013',name:'Ndumiso Sthembiso Khumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1016',name:'Nkosivumile Senzo Senzo Galo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1017',name:'Pheaha Moffat Magokare',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1019',name:'Ramatshwele Daniel Thabana',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1020',name:'Rufus Sylvester Arends',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1021',name:'Samkelo Masikane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1022',name:'Samkelo Ntshangase',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1024',name:'Sibonelo Knowledge Hlatshwayo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1025',name:'Siyabonga Fortune Mkhize',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1026',name:'Sophia Rorisang Gloria Ngiba',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1027',name:'Thabelo Elijah Ramikosi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1029',name:'Vuma William Shaun Nzuza',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1030',name:'Tumelo Conrad Molapisi',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1031',name:'Mzamo Thamsanqa Mathenjwa',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1032',name:'Busisiwe Letseka',pos:'HR ANALYST',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Female'},
    {num:'1037',name:'Kamohelo Dinakane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1039',name:'Bonga Sbonda Ntshangase',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1040',name:'Mashudu Tshikhudo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1041',name:'Mlungisi Zamokuhle Sibiya',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1042',name:'Zwane Mthunzi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1043',name:'Neo Lennox Sehoshe',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1044',name:'Olwethu Sithandiwe Mdleleni',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1045',name:'Irvin Namane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1046',name:'Simeon Baloyi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1047',name:'Thembelani Zacharia Ntshinga',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1048',name:'Dankie Sandiso Mabanga',pos:'WAREHOUSE SAFETY',status:'Active',unit:'NWL SERVICE',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1049',name:'Pertunia Keatlaretse Segwele',pos:'WAREHOUSE SUPERVISOR',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1051',name:'Madidimalo Bephley Mangweta',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1052',name:'Mzwakhe David Mthembu',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1053',name:'Noel Jacob Hlabane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1054',name:'Nompumelelo Innocent  Paulina Mnyakeni',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1055',name:'Siphelele Laqwela',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1056',name:'Thabang Mosia',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1058',name:'Thembisile Sophie Motankisi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1059',name:'Celimpilo Derrick Gabela',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1060',name:'Dumisani Lucas Thabede',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1065',name:'Zama Khumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1066',name:'Mzoxolo Ngcobelo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1067',name:'Sboniso Freedom Mlambo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1068',name:'David Tebogo Senosha',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1069',name:'Thubalethu Mordecay Nxumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1070',name:'Norman Smangaliso Dlamini',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1071',name:'Lusanda Plan Msimango',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1072',name:'Jonas Mokoena',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1073',name:'Zinhle Genrah Dladla',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1074',name:'Athenkosi Solomon',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1075',name:'Banenge Jemis Radebe',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1076',name:'Lungisani Emmanuel Mdluli',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1077',name:'Mpho Molovhedzi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1078',name:'Phindile Xoshe',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1079',name:'Sgcino Mbhekiseni Zondo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1080',name:'Tenza Mtshizane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1081',name:'Thabo Mdluli',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1082',name:'Khulekani Dubula',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1083',name:'Lebohang James Khanye',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1084',name:'Lunga Ezrom Dlamini',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1085',name:'Lwando Mpetsheni',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1086',name:'Mkhuseli Mini',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1087',name:'Reathaba David Mohoto',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1088',name:'Thembela Bambiso',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1090',name:'Aubrey Selepe',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1091',name:'Sebilaro Ernest Phala',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1092',name:'Fezile Mathews Somaxhama',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1094',name:'Johannes Kgahliso Khanye',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1095',name:'Daniel Fourie',pos:'WAREHOUSE SUPERVISOR',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1096',name:'Lifa Blessing Sibiya',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1097',name:'Riveshin Chetty',pos:'HR ANALYST',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1098',name:'Siphephelo Vukani Khumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1100',name:'Thato Maleka',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1101',name:'Thulani Ngcobo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1102',name:'Bongimpilo Mncube',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1103',name:'Mzuvulile Comfort Miya',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1104',name:'Khumbo Kazeze Tshabalala',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1107',name:'Nkosibonile Radebe',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1108',name:'Freeman Nxumalo',pos:'DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1109',name:'Thabang Christopher Mofokeng',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1110',name:'Cornelius Mthembu',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1111',name:'Ndivhuwo Aubrey Malange',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1113',name:'Liza Marie Strauss',pos:'HR ANALYST',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'1114',name:'Charity Jenel Haigh',pos:'BUYER JUNIOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'1117',name:'Bongani Walter Majalamba',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1118',name:'Pankie Lawrence Senoamali',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1119',name:'Frans Matsobane Sekele',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1120',name:'Tinyiko Vincent Hlabangwane',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1121',name:'Vuyisile Postulate Madolo',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1122',name:'Tebogo Ofentse Moremong',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1123',name:'Rudzani Silas Khaphathe',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1124',name:'Bayanda Michael Myaka',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1125',name:'Miehleketo Maluleke',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1126',name:'Sicelokuhle Goodenough Mdlalose',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1127',name:'Itumeleng More',pos:'HELPER LEADER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1129',name:'Kabelo Johannes Khumalo',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1130',name:'Basha Monareng Bogatsu',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1131',name:'Lindani Sithembile',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1132',name:'Dennis Gaopalelwe Motshabi',pos:'FORKLIFT DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1133',name:'Ofentse Henry Lefora',pos:'FORKLIFT DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1134',name:'Isaac Hlasoa Lehloo',pos:'FORKLIFT DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1136',name:'Benjamin Loedewyk Swartz',pos:'FORKLIFT DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1137',name:'Diau Petrus Molapo',pos:'FORKLIFT DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1138',name:'Masonti Daniel Radebe',pos:'FORKLIFT DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1139',name:'Nkosinathi Aurthur Khefi',pos:'FORKLIFT DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1140',name:'Thabiso Eugene Moholo',pos:'FORKLIFT DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1141',name:'Teboho Stephans Phallo',pos:'FORKLIFT DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1142',name:'Teko Williem Monoto',pos:'FORKLIFT DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1147',name:'Sydney Tshepang Modikoe',pos:'FORKLIFT DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1148',name:'Siphenathi Vava',pos:'FORKLIFT DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1149',name:'Othusitse Lucas Ganakgomo',pos:'FORKLIFT DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1150',name:'Lehlohonolo Hlompho Khalapa',pos:'GENERAL WORKER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1151',name:'Donald Olebogeng Korasi',pos:'FORKLIFT DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1152',name:'Orateng Felix Malekanyo',pos:'FORKLIFT DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1153',name:'Thabo William Nthako',pos:'FORKLIFT DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1154',name:'Phetogo Gaetshele',pos:'FORKLIFT DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1156',name:'Morake Daniel Moopela',pos:'FORKLIFT DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1157',name:'Mogorotshi Richard Paul',pos:'FORKLIFT DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1158',name:'Itumeleng Albert Kgoa',pos:'FORKLIFT DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1161',name:'Mhlengi Ndumiso Ntshangase',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1163',name:'Leonard Sydney Mathebula',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1164',name:'Siyabonga Yekela',pos:'FORKLIFT DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1165',name:'Moiloa Sebesho',pos:'FORKLIFT DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1166',name:'Mashilo Phillemon Mashola',pos:'FLEET ASSISTANT',status:'Active',unit:'ALRODE T1 BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1167',name:'Muntu Gerald Pheto',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1169',name:'Sekopyane Alfred Mokalapa',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1170',name:'Karabo Molapo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1171',name:'Bongani Victor Mbuyisa',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1172',name:'Themba Meshack Mthembu',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1174',name:'Sibusiso Maseko',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1175',name:'Themba Phumlani Ndlovana',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1176',name:'Seiso Grant Nkosi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1177',name:'Sanele Moloi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1178',name:'Simphiweyinkosi Khumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1179',name:'Xolani Alfred Tshabalala',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1180',name:'Sizwe Siphamandla Zulu',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1181',name:'Celimpilo Nhlakanipho Buthelezi',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1182',name:'Wanda Sibawu',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1183',name:'Phezile Magadla',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1185',name:'Sifiso Joshua Ngwenya',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1187',name:'Lucky Seboya',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1188',name:'Madodenzane Richard Nxumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1189',name:'Siyabonga Sandile Hadebe',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1190',name:'Inkosiyazi Khumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1191',name:'Siyanda Masondo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1192',name:'Petros Mhlongo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1193',name:'Luyanda Khanyile Prince',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1194',name:'Sello Tshepo Dhlamini',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1199',name:'Keababetswe Abegnog Tsomele',pos:'DRIVER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1200',name:'Oratile Igzebear Mhlanga',pos:'DRIVER-HELPER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1201',name:'Omphile Lylian Thebeyagae',pos:'FINANCE ASSISTANT',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Female'},
    {num:'1204',name:'Kabelo Moagaesi',pos:'GENERAL WORKER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1206',name:'Dakalo Mafhungo-Nedawayila',pos:'HR ANALYST',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Female'},
    {num:'1207',name:'Thato Benjamin Mogorosi',pos:'FLEET ANALYST',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1208',name:'Keenan Vries',pos:'FLEET ANALYST',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'1213',name:'Brett Scorgie',pos:'FLEET ANALYST',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1216',name:'Botshelo Mogale',pos:'FORKLIFT DRIVER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1218',name:'Simon Mosa Nyamakela',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1221',name:'Takalani Glen Nangani',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1222',name:'Cyprian Zithulele Ntsimbi',pos:'FORKLIFT DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1223',name:'Siphamandla Excellent Ngwenya',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1225',name:'Theko Simon Masiu',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1226',name:'Themba Obed Mosetlho',pos:'OPERATIONS SUPERVISOR',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1227',name:'Malapane William Mothudi',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1228',name:'Tshamano Lucas Phaswana',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1229',name:'Wandile Nelson Thobela',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1231',name:'Luyanda Luther Xasa',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1232',name:'Jeffrey Mzondeni Sithole',pos:'DRIVER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1233',name:'Michael Sloane',pos:'FLEET ANALYST',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1234',name:'Goboletseng David Molatole',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1235',name:'Tshepang Rakgwale',pos:'GENERAL WORKER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1236',name:'Gobusamang Ronald Gaonathebe',pos:'FORKLIFT DRIVER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1237',name:'Roelof Jacobus Els',pos:'WAREHOUSE SUPERVISOR',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1239',name:'Thabo Peter Makhalanyane',pos:'FORKLIFT DRIVER',status:'Active',unit:'HARTSWATER',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1240',name:'Magetsi Donald Goitsemodimo',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1241',name:'Phathisizwe Mbatha',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1243',name:'Sandile Praise-God Zwane',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1244',name:'Siyabonga Mchunu',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1245',name:'Nokulunga Sinkwana',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1246',name:'Sibusile Ntshangase',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Female'},
    {num:'1247',name:'Zamani Nxumalo',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1248',name:'Xola Dlokweni',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1249',name:'Zonke Mbatha',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1250',name:'Sifiso Given Ngonyama',pos:'FORKLIFT DRIVER',status:'Active',unit:'ALRODE BREWERY',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1251',name:'Manghena Wiseman Chauke',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1252',name:'Sipho Mbongeleni Mkhize',pos:'GENERAL WORKER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1253',name:'Bongani Kubheka',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1254',name:'Itumeleng Adam Makoloi',pos:'DRIVER-HELPER',status:'Active',unit:'KIMBERLEY',dept:'Operation',region:'Northern Cape',gender:'Male'},
    {num:'1255',name:'Sam Sipho Nkonyanebomvu',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1256',name:'Lebohang Godfrey Mphunngoa',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1257',name:'Onalenna Benny Morebodi',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1258',name:'Selemogo Modise Soldia',pos:'DRIVER-HELPER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1259',name:'Tobekile Sogexe',pos:'DRIVER',status:'Active',unit:'POTCHEFSTROOM',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1261',name:'Hopewell Sibonelo Langa',pos:'DRIVER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1262',name:'Fisokuhle Khanyeza',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1263',name:'Khayelihle Smethembile Dlamini',pos:'DRIVER-HELPER',status:'Active',unit:'BARAGWANATH',dept:'Operation',region:'Gauteng',gender:'Male'},
    {num:'1264',name:'Elmar Siphe Gixela',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1265',name:'Ntsikelelo Benjamine Nkumla',pos:'DRIVER-HELPER',status:'Active',unit:'WELKOM',dept:'Operation',region:'Free State',gender:'Male'},
    {num:'1266',name:'Maruping Moses Gaje',pos:'GENERAL WORKER',status:'Active',unit:'MAFIKENG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1268',name:'Tebano Frederick Kgopyane',pos:'BRANCH MANAGER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1269',name:'Mojalefa Gregory Sojane',pos:'GENERAL WORKER',status:'Active',unit:'RUSTENBURG',dept:'Operation',region:'North West',gender:'Male'},
    {num:'1270',name:'Lindy Raynard',pos:'PEOPLE MANAGEMENT COORDINATOR',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'},
    {num:'1271',name:'Yolanda Bernadette Rossouw',pos:'SENIOR HR ANALYST',status:'Active',unit:'HEAD OFFICE',dept:'Management',region:'Gauteng',gender:'Female'}
  ],
  deleteRequests:[],
  activityLog:[]
}; }

let D = (() => { try { const s=localStorage.getItem(SK); return s ? JSON.parse(s) : defaultData(); } catch(e) { return defaultData(); } })();

// Migration v3: mark as done (superseded by v4)
D._migrated_v2 = true;
D._migrated_v3 = true;

// Migration v4: update locations, normalize units, restore employees, standardize PPE
(function migrateV4() {
  if (D._migrated_v4) return;

  const UNIT_NORM = {
    'alrode t1':'ALRODE T1 BREWERY','alrode t1 brewery':'ALRODE T1 BREWERY',
    'alrode nwl t1':'ALRODE BREWERY','alrode nwl':'ALRODE BREWERY',
    'alrode brewery':'ALRODE BREWERY','alrode':'ALRODE BREWERY',
    'head office':'HEAD OFFICE','baragwanath':'BARAGWANATH',
    'rustenburg':'RUSTENBURG','mafikeng':'MAFIKENG',
    'potchefstroom':'POTCHEFSTROOM','welkom':'WELKOM',
    'kimberley':'KIMBERLEY','hartswater':'HARTSWATER',
    'nwl service':'NWL SERVICE',
    'alrode_t1':'ALRODE T1 BREWERY','alrode_t1_brewery':'ALRODE T1 BREWERY',
    'alrode_nwl_t1':'ALRODE BREWERY','alrode_brewery':'ALRODE BREWERY',
    'head_office':'HEAD OFFICE','nwl_service':'NWL SERVICE',
  };
  function normUnit(v) {
    if (!v) return v;
    const k = v.toLowerCase().replace(/_/g,' ').replace(/\s+/g,' ').trim();
    return UNIT_NORM[k] || v;
  }

  D.locations = defaultData().locations;

  D.users = (D.users||[]).map(u => {
    if (u.locationAccess && u.locationAccess !== 'all') {
      const nla = u.locationAccess.toLowerCase().replace(/_/g,' ').trim();
      const match = D.locations.find(l => l.name.toLowerCase() === (UNIT_NORM[nla]||'').toLowerCase());
      if (match) u.locationAccess = match.id;
    }
    return u;
  });

  (D.employees||[]).forEach(e => { if (e.unit) e.unit = normUnit(e.unit); });
  (D.incidents||[]).forEach(r => { if (r.loc) r.loc = normUnit(r.loc); });
  (D.evaluations||[]).forEach(r => { if (r.loc) r.loc = normUnit(r.loc); });
  (D.deliveries||[]).forEach(r => { if (r.loc) r.loc = normUnit(r.loc); if (r.location) r.location = normUnit(r.location); });
  (D.warnings||[]).forEach(r => { if (r.unit) r.unit = normUnit(r.unit); if (r.loc) r.loc = normUnit(r.loc); });
  (D.trainings||[]).forEach(r => { if (r.unit) r.unit = normUnit(r.unit); if (r.loc) r.loc = normUnit(r.loc); });
  (D.purchaseOrders||[]).forEach(r => { if (r.loc) r.loc = normUnit(r.loc); if (r.location) r.location = normUnit(r.location); });
  (D.corrActions||[]).forEach(r => { if (r.loc) r.loc = normUnit(r.loc); if (r.unit) r.unit = normUnit(r.unit); });
  (D.ppeItems||[]).forEach(r => { if (r.location) r.location = normUnit(r.location); if (r.loc) r.loc = normUnit(r.loc); });

  const existing = new Set((D.employees||[]).map(e => String(e.num)));
  const toRestore = defaultData().employees.filter(e => !existing.has(String(e.num)));
  if (toRestore.length) D.employees = (D.employees||[]).concat(toRestore);

  const locNames = D.locations.map(l => l.name);
  const ppeTemplates = {};
  (D.ppeItems||[]).forEach(item => {
    if (!ppeTemplates[item.name] || (item.stock||0) > 0) {
      ppeTemplates[item.name] = {name:item.name, cat:item.cat, min:item.min||0, exp:item.exp||12, clothingSizes:item.clothingSizes||'', shoeSizes:item.shoeSizes||''};
    }
  });
  const existingPpeKeys = new Set((D.ppeItems||[]).map(i => i.name + '|' + (i.location||'')));
  Object.values(ppeTemplates).forEach(tmpl => {
    locNames.forEach(loc => {
      const key = tmpl.name + '|' + loc;
      if (!existingPpeKeys.has(key)) {
        D.ppeItems.push({name:tmpl.name, cat:tmpl.cat, stock:0, min:tmpl.min, exp:tmpl.exp, location:loc, clothingSizes:tmpl.clothingSizes, shoeSizes:tmpl.shoeSizes});
        existingPpeKeys.add(key);
      }
    });
  });

  D._migrated_v4 = true;
  try { localStorage.setItem(SK, JSON.stringify(D)); } catch(e) {}
})();
function _saveLocal() {
  try {
    localStorage.setItem(SK, JSON.stringify(D));
    showSyncStatus('synced');
  } catch(e) { console.warn('Save error:',e); }
}

function save() {
  D._ts = Date.now(); // timestamp every save
  _saveLocal();
  // Broadcast to same-browser tabs
  const payload = JSON.stringify(D);
  const hash = payload.length + '_' + D._ts;
  lastSyncHash = hash;
  if (typeof syncChannel !== 'undefined' && syncChannel) {
    syncChannel.postMessage({ type:'DATA_UPDATE', payload, hash });
  }
  // Push to cloud backend (non-blocking)
  if (D.cfg?.syncBackend) {
    pushToRemote().catch(e => console.warn('Auto-push failed:', e.message));
  }
  showSyncStatus(D.cfg?.syncBackend ? 'synced' : 'local');
}

// ═══════════════════════════════════════════════════
// AUTH
// ═══════════════════════════════════════════════════
let SESSION = null;

function hp(p) { let h=0; for(let i=0;i<p.length;i++){h=((h<<5)-h)+p.charCodeAt(i);h|=0;} return 'h'+Math.abs(h).toString(36); }
function checkPass(u,input) {
  if(!u||!u.password||!input) return false;
  // 1. Plain text match (new users, reset passwords)
  if(u.password===input) return true;
  // 2. Hashed match (users who logged in before and got upgraded)
  if(u.password===hp(input)) return true;
  return false;
  // NOTE: we no longer auto-upgrade plain→hash to avoid cross-device issues
  // Passwords stay as plain text until admin explicitly resets them
}
function isAdmin(){return SESSION&&SESSION.role==='admin';}
function canEdit(){return SESSION&&CAN_EDIT.includes(SESSION.role);}

// canEditItem: checks if user can edit a specific item based on its location
function canEditItem(item, locKey='loc') {
  if (!canEdit()) return false;
  if (isAdmin() || locAccess()==='all') return true;
  const itemLoc = item[locKey] || item.loc || item.unit || '';
  return matchesLoc(itemLoc, locAccess());
}

// Guard for actions that write data — validates location ownership
function assertCanEditLocation(locVal) {
  if (isAdmin() || locAccess() === 'all') return true;
  if (!matchesLoc(locVal, locAccess())) {
    toast('You do not have permission to modify data outside your location', 'err');
    logActivity('SECURITY', 'access_violation', locVal,
      `Attempted to edit data outside assigned location (${locAccess()})`);
    return false;
  }
  return true;
}
function locAccess(){
  if(!SESSION) return 'all'; // no session = show nothing sensitive (filtered elsewhere)
  return SESSION.locationAccess || 'all';
}

// canViewLocation: checks if user can access data for a given location string
function canViewLocation(locVal) {
  const la = locAccess();
  if (la === 'all' || la === 'none') return la === 'all';
  return matchesLoc(locVal, la);
}
function canAccessPage(p){return SESSION&&(ROLE_PAGES[SESSION.role]||[]).includes(p);}

function doLogin() {
  const uname = (document.getElementById('login-user').value||'').trim().toLowerCase();
  const pass  = document.getElementById('login-pass').value||'';
  const errEl = document.getElementById('login-error');
  const msgEl = document.getElementById('ll-err-msg');
  if(errEl) errEl.classList.remove('show');

  // Basic validation
  if (!uname||!pass) {
    if(msgEl) msgEl.textContent='Please enter username and password.';
    if(errEl) errEl.classList.add('show');
    return;
  }

  // Find user (case-insensitive)
  if(!D||!D.users||!Array.isArray(D.users)) {
    if(msgEl) msgEl.textContent='System error: user data not loaded. Refresh the page.';
    if(errEl) errEl.classList.add('show');
    return;
  }

  const user = D.users.find(u=>(u.username||'').toLowerCase()===uname);
  if (!user) {
    if(msgEl) msgEl.textContent='User not found. Check username.';
    if(errEl) errEl.classList.add('show');
    return;
  }

  // Check if suspended
  if (user.status==='suspended') {
    if(msgEl) msgEl.textContent='This account has been suspended. Contact the administrator.';
    if(errEl) errEl.classList.add('show');
    return;
  }

  if (!checkPass(user,pass)) {
    if(msgEl) msgEl.textContent='Incorrect password. Please try again.';
    if(errEl) errEl.classList.add('show');
    const pi=document.getElementById('login-pass');
    if(pi){pi.classList.add('err');setTimeout(()=>pi.classList.remove('err'),800);pi.value='';}
    return;
  }

  // Location selection (required for NEEDS_LOC roles)
  const locSel = document.getElementById('login-loc-sel');
  const chosenLoc = locSel ? locSel.value : '';
  if (NEEDS_LOC.includes(user.role) && !chosenLoc && user.locationAccess==='all') {
    if(msgEl) msgEl.textContent='Please select your location to continue.';
    if(errEl) errEl.classList.add('show');
    return;
  }

  // Assign session location
  if (chosenLoc) {
    user._sessionLoc = chosenLoc;
  } else if (user.locationAccess && user.locationAccess !== 'all') {
    user._sessionLoc = user.locationAccess;
  } else {
    delete user._sessionLoc;
  }

  startSession(user);
}

function startSession(user) {
  // 1. Set SESSION first — everything else depends on it
  SESSION = {
    username: user.username,
    display:  user.display,
    role:     user.role,
    dept:     user.dept||'',
    locationAccess: user._sessionLoc || user.locationAccess || 'all',
    color:    user.color || '#00d4a0',
  };
  try{ sessionStorage.setItem(SES_K, JSON.stringify(SESSION)); } catch(e){}

  // 2. Show app
  const ls = document.getElementById('login-screen');
  if(ls) ls.classList.add('hidden');
  const app = document.getElementById('app');
  if(app) app.classList.add('visible');

  // 3. Apply body classes AFTER SESSION is set
  document.body.classList.toggle('is-admin', isAdmin());
  document.body.classList.toggle('is-operator', canEdit());

  // 4. Nav visibility
  const navMap={ppe:'nav-ppe',incidents:'nav-inc',performance:'nav-perf',
                employees:'nav-emp',locations:'nav-loc',reports:'nav-rep',
                settings:'nav-set',audit:'nav-audit'};
  Object.entries(navMap).forEach(([pg,id])=>{
    const el=document.getElementById(id);
    if(el) el.style.display=canAccessPage(pg)?'flex':'none';
  });

  // 5. Update UI & render
  updateSessionUI();
  try { renderAll(); } catch(e) { console.warn('renderAll error:', e); }

  // 6. Post-render UI tweaks
  const regTab = document.querySelector('#page-performance .tab:nth-child(2)');
  if(regTab) regTab.style.display = CAN_SEE_REGIONAL_KPI.includes(user.role)?'':'none';
  const reportBtn = document.getElementById('btn-report-inc');
  if(reportBtn) reportBtn.style.display = canEdit()?'flex':'none';

  // 7. Record last login (local only, no remote push)
  const loginUser = D.users.find(u=>u.username===user.username);
  if(loginUser){
    loginUser.lastLogin = new Date().toLocaleString('en-ZA');
    try { localStorage.setItem(SK, JSON.stringify(D)); } catch(e) {}
  }

  // 8. Log activity
  try { logActivity('LOGIN','session',user.display,
    `${ROLE_LABELS[user.role]||user.role} · ${SESSION.locationAccess}`); } catch(e){}

  toast(`Welcome, ${user.display}!`);
}

function doLogout() {
  SESSION=null;
  try{sessionStorage.removeItem(SES_K);}catch(e){}
  document.body.classList.remove('is-admin','is-operator');
  document.getElementById('login-screen').classList.remove('hidden');
  document.getElementById('app').classList.remove('visible');
  document.getElementById('login-user').value='';
  document.getElementById('login-pass').value='';
  document.getElementById('login-error').classList.remove('show');
  closeMobMenu();
}

let cpTarget=null;
function doChangePass() {
  const cur=document.getElementById('cp-current').value;
  const nw=document.getElementById('cp-new').value;
  const cf=document.getElementById('cp-confirm').value;
  const err=document.getElementById('cp-err');
  const msg=document.getElementById('cp-err-msg');
  err.classList.remove('show');
  const u=D.users.find(x=>x.username===(cpTarget||SESSION.username));
  if(!u)return;
  const skip=(isAdmin()&&cpTarget&&cpTarget!==SESSION.username);
  if(!skip&&!checkPass(u,cur)){msg.textContent='Current password incorrect.';err.classList.add('show');return;}
  if(nw.length<4){msg.textContent='New password must be at least 4 characters.';err.classList.add('show');return;}
  if(nw!==cf){msg.textContent='Passwords do not match.';err.classList.add('show');return;}
  u.password=hp(nw);save();closeMo('mo-change-pass');toast('Password changed! 🔑');cpTarget=null;
}

// ═══════════════════════════════════════════════════
// NAV
// ═══════════════════════════════════════════════════
function goPage(id,el) {
  if(!canAccessPage(id)){toast('Access denied for your profile','warn');return;}
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.ni').forEach(n=>n.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  el.classList.add('active');
  document.getElementById('mob-title').textContent=el.querySelector('span:not(.ni-ic):not(.ni-badge)')?.textContent||id;
  closeMobMenu();
  if(id==='locations')renderLocPage();
  if(id==='employees')renderEmployees();
  if(id==='audit'){
    renderActivityLog();
    filterAuditLog();
    // Populate user filter
    const uf = document.getElementById('audit-filter-user');
    if(uf && isAdmin()){
      const users = [...new Set((D.activityLog||[]).map(e=>e.user).filter(Boolean))].sort();
      uf.innerHTML = '<option value="">All users</option>' + users.map(u=>`<option>${u}</option>`).join('');
    }
  }
  if(id==='performance')buildRegionalCharts();
  if(id==='settings')renderSettings();
  if(id==='reports')renderReports();
}

function toggleMobMenu(){
  document.getElementById('sidebar').classList.toggle('open');
  document.getElementById('mob-overlay').classList.toggle('show');
}
function closeMobMenu(){
  document.getElementById('sidebar').classList.remove('open');
  document.getElementById('mob-overlay').classList.remove('show');
}

function switchTab(prefix,idx,el){
  el.closest('.page,.md').querySelectorAll('.tab').forEach(t=>t.classList.remove('active'));
  el.classList.add('active');
  let i=0,f;
  while((f=document.getElementById(prefix+'-'+i))){f.style.display=i===idx?'block':'none';i++;}
  if(prefix==='ppe-tab'&&idx===3) requestAnimationFrame(buildDeliveryCharts);
}

// ═══════════════════════════════════════════════════
// MODALS
// ═══════════════════════════════════════════════════
function openMo(id){
  const el=document.getElementById(id);if(!el)return;
  el.classList.add('open');
  if(id==='mo-user-menu')updateSessionUI();
  if(id==='mo-user-mgr')renderUserMgr();
  if(id==='mo-auto-actions')renderEditActions();
  if(['mo-delivery','mo-incident','mo-eval','mo-warning','mo-employee','mo-new-po','mo-training'].includes(id))populateSelects();
  if(id==='mo-training'){
    setTimeout(()=>epInit('train-emp'),50);
  }
}
function closeMo(id){const el=document.getElementById(id);if(el)el.classList.remove('open');}
document.addEventListener('click',e=>{if(e.target.classList.contains('mo'))e.target.classList.remove('open');});

// ── EMPLOYEE PICKER COMPONENT ─────────────────────────
// Uses a custom dropdown with real-time search + position filter
// Properly works on all browsers (no option.style.display hack)
let _epData = {}; // stores {empId: [{name, pos, unit}]}

function epInit(selId) {
  const locEmps = filterByLoc(D.employees,'unit').sort((a,b)=>a.name.localeCompare(b.name));
  const positions = [...new Set(locEmps.map(e=>e.pos||'').filter(Boolean))].sort();
  _epData[selId] = locEmps;
  // Populate position filter
  const posEl = document.getElementById('ep-pos-'+selId);
  if (posEl) {
    posEl.innerHTML = '<option value="">All positions</option>' + positions.map(p=>`<option>${p}</option>`).join('');
  }
  epRender(selId, '', '');
}

function epRender(selId, query, pos) {
  const list = document.getElementById('ep-list-'+selId);
  if (!list) return;
  const emps = (_epData[selId] || []).filter(e => {
    const q = query.toLowerCase();
    const matchName = !q || e.name.toLowerCase().includes(q) || (e.pos||'').toLowerCase().includes(q);
    const matchPos = !pos || e.pos === pos;
    return matchName && matchPos;
  });
  if (!emps.length) {
    list.innerHTML = '<div class="ep-empty">No employees found</div>';
    return;
  }
  list.innerHTML = emps.map((e,i) => 
    `<div class="ep-item" data-name="${e.name}" data-pos="${e.pos||''}" 
      onclick="epSelect('${selId}','${e.name.replace(/'/g,"\'")}','${(e.pos||'').replace(/'/g,"\'")}')">
      <span class="ep-item-name">${e.name}</span>
      <span class="ep-item-pos">${e.pos||''} · ${e.unit||''}</span>
    </div>`
  ).join('');
}

function epFilter(selId, query) {
  const posEl = document.getElementById('ep-pos-'+selId);
  const pos = posEl ? posEl.value : '';
  // Sync both search inputs
  const main = document.getElementById('ep-input-'+selId);
  const inner = document.getElementById('ep-srch-'+selId);
  if (main && document.activeElement !== main) main.value = query;
  if (inner && document.activeElement !== inner) inner.value = query;
  epRender(selId, query, pos);
  epOpen(selId);
}

function epFilterPos(selId, pos) {
  const srch = document.getElementById('ep-srch-'+selId);
  const query = srch ? srch.value : '';
  epRender(selId, query, pos);
}

function epSelect(selId, name, pos) {
  // Set the display input
  const inp = document.getElementById('ep-input-'+selId);
  if (inp) inp.value = name;
  // Set the hidden value input
  const hid = document.getElementById(selId);
  if (hid) hid.value = name;
  // Close dropdown
  epClose(selId);
  // Visual feedback
  const wrap = document.getElementById('ep-wrap-'+selId);
  if (wrap) { wrap.style.borderColor='var(--teal)'; setTimeout(()=>wrap.style.borderColor='',1000); }
}

function epOpen(selId) {
  const drop = document.getElementById('ep-drop-'+selId);
  if (drop) {
    drop.classList.add('open');
    // Focus the search input inside
    const inner = document.getElementById('ep-srch-'+selId);
    if (inner) setTimeout(()=>inner.focus(), 50);
  }
  // Close other pickers
  document.querySelectorAll('.ep-dropdown.open').forEach(d => {
    if (d.id !== 'ep-drop-'+selId) d.classList.remove('open');
  });
}

function epClose(selId) {
  const drop = document.getElementById('ep-drop-'+selId);
  if (drop) drop.classList.remove('open');
}

function epKey(e, selId) {
  if (e.key === 'Escape') epClose(selId);
  if (e.key === 'Enter' || e.key === 'ArrowDown') { e.preventDefault(); epOpen(selId); }
}

// Close pickers when clicking outside
document.addEventListener('click', e => {
  if (!e.target.closest('.ep-wrap')) {
    document.querySelectorAll('.ep-dropdown.open').forEach(d => d.classList.remove('open'));
  }
});

function populateSelects(){
  // Init employee pickers
  ['del-emp','eval-emp','warn-emp','train-emp'].forEach(id => {
    const wrap = document.getElementById('ep-wrap-'+id);
    if (wrap) epInit(id);
  });

  // PPE items: only show items matching user's location (or all for admin/regional)
  const visiblePpe = filterByLoc(D.ppeItems, 'location');
  const di=document.getElementById('del-item');
  if(di) di.innerHTML=visiblePpe.map(i=>`<option value="${i.name}" data-loc="${i.location||''}">${i.name}${i.location?' ['+i.location+']':''}</option>`).join('');
  const pi=document.getElementById('po-item');
  if(pi) pi.innerHTML=visiblePpe.map(i=>`<option value="${i.name}">${i.name}${i.location?' ['+i.location+']':''}</option>`).join('');

  // Location dropdowns — only show accessible locations
  const la = locAccess();
  const accessibleLocs = la==='all'
    ? D.locations
    : D.locations.filter(l => matchesLoc(l.name, la) || matchesLoc(l.id, la));

  const locOptions = '<option value="">-- Select location --</option>' +
    accessibleLocs.map(l=>`<option value="${l.id}">${l.name}</option>`).join('');

  // Delivery location
  const dl=document.getElementById('del-location');
  if(dl){ dl.innerHTML=locOptions; if(la!=='all'){ dl.value=la; } }

  // Add item location
  const il2=document.getElementById('item-location');
  if(il2){ il2.innerHTML=locOptions; if(la!=='all'){ il2.value=la; } }

  // PO stock-in location
  const pl=document.getElementById('po-location');
  if(pl){ pl.innerHTML=locOptions; if(la!=='all'){ pl.value=la; } }

  // Incident location
  const il=document.getElementById('inc-loc');
  if(il)il.innerHTML=D.locations.map(l=>`<option value="${l.id}">${l.name}</option>`).join('');

  // Employee location selector
  const el=document.getElementById('emp-loc-sel');
  if(el)el.innerHTML=D.locations.map(l=>`<option value="${l.id}">${l.name}</option>`).join('');
}

// ═══════════════════════════════════════════════════
// LOCATION FILTER HELPERS
// ═══════════════════════════════════════════════════
// Normalize location string — removes underscores, lowercases, trims
function normLoc(s){ return (s||'').toLowerCase().replace(/_/g,' ').trim(); }

function matchesLoc(val, la){
  if(!la||la==='all') return true;
  const nv=normLoc(val), nla=normLoc(la);
  if(!nv) return false;
  return nv===nla;
}

// Filter array by current user's location access
// key = field name on items that holds location (default 'loc')
// For employees: key='unit'. For trainings/warnings: use 'unit' or lookup emp.unit
function filterByLoc(arr, key='loc'){
  const la=locAccess();
  if(la==='all') return arr;
  return arr.filter(i=>{
    const val = i[key] || i.loc || i.unit || '';
    if(matchesLoc(val, la)) return true;
    // Lookup via employee name
    if(i.emp||i.name){
      const ename = i.emp||i.name;
      const emp = D.employees.find(e=>e.name===ename);
      if(emp && matchesLoc(emp.unit, la)) return true;
    }
    return false;
  });
}

function locFilter(item, key='loc'){
  const la=locAccess();
  if(la==='all') return true;
  const val = item[key] || item.loc || item.unit || '';
  if(matchesLoc(val, la)) return true;
  if(item.emp||item.name){
    const ename = item.emp||item.name;
    const emp=D.employees.find(e=>e.name===ename);
    if(emp && matchesLoc(emp.unit, la)) return true;
  }
  return false;
}

// ═══════════════════════════════════════════════════
// BADGE HELPERS
// ═══════════════════════════════════════════════════
function bSev(s){const sl=(s||'').toLowerCase();if(sl.includes('high')||sl.includes('critical'))return`<span class="badge r">${s}</span>`;if(sl.includes('med'))return`<span class="badge a">${s}</span>`;if(sl.includes('low'))return`<span class="badge t">${s}</span>`;return`<span class="badge b">${s}</span>`;}
function bSt(s){const sl=(s||'').toLowerCase();if(['approved','valid','signed','completed','active','closed'].some(x=>sl.includes(x)))return`<span class="badge t">${s}</span>`;if(['open','overdue','expired','critical','below','out'].some(x=>sl.includes(x)))return`<span class="badge r">${s}</span>`;if(['pending','investigating','review','expiring','awaiting','vacation','progress'].some(x=>sl.includes(x)))return`<span class="badge a">${s}</span>`;return`<span class="badge b">${s}</span>`;}

// ═══════════════════════════════════════════════════
// TABLE FILTER
// ═══════════════════════════════════════════════════
function filterTbl(id,q){const rows=document.querySelectorAll('#'+id+' tbody tr');const l=q.toLowerCase();rows.forEach(r=>{r.style.display=(!q||r.textContent.toLowerCase().includes(l))?'':'none';});}

// ═══════════════════════════════════════════════════
// TOAST & SIGNATURE
// ═══════════════════════════════════════════════════
function toast(msg,type='ok'){const c={ok:'var(--teal)',warn:'var(--amber)',err:'var(--red)'};const i={ok:'✓',warn:'⚠',err:'✕'};const el=document.getElementById('toast');el.innerHTML=`<span style="color:${c[type]};font-size:15px">${i[type]}</span> ${msg}`;el.style.borderColor=c[type];el.style.transform='translateY(0)';el.style.opacity='1';clearTimeout(el._t);el._t=setTimeout(()=>{el.style.transform='translateY(70px)';el.style.opacity='0';},3200);}
function signBox(boxId,hidId){const el=document.getElementById(boxId);if(!el)return;el.classList.add('signed');el.textContent='✓ Signed — '+new Date().toLocaleString('en-ZA');if(hidId){const h=document.getElementById(hidId);if(h)h.value='1';}}

// ═══════════════════════════════════════════════════
// SESSION UI
// ═══════════════════════════════════════════════════
function updateSessionUI(){
  if(!SESSION)return;
  const init=SESSION.display.split(' ').map(w=>w[0]).join('').substring(0,2).toUpperCase();
  const col=SESSION.color||'var(--teal)';
  const rl=ROLE_LABELS[SESSION.role]||SESSION.role;
  ['ua-av','mob-user-btn','um-av'].forEach(id=>{const el=document.getElementById(id);if(el){el.textContent=init;el.style.background=col;}});
  const un=document.getElementById('ua-name');if(un)un.textContent=SESSION.display;
  const ur=document.getElementById('ua-role');if(ur)ur.textContent=rl;
  const mn=document.getElementById('um-name');if(mn)mn.textContent=SESSION.display;
  const mr=document.getElementById('um-role');if(mr)mr.textContent=rl+' · @'+SESSION.username;
  const ci=document.getElementById('cp-info');if(ci)ci.textContent='Changing password for: '+SESSION.display;
  document.getElementById('s-logo').textContent=D.cfg.logo||'S';
  document.getElementById('s-company').textContent=D.cfg.company||'Safety System';
  document.getElementById('ll-icon').textContent=D.cfg.logo||'S';
  document.getElementById('ll-name').textContent=D.cfg.company||'Safety System';
}

// ═══════════════════════════════════════════════════
// QUICK USERS (admin only)
// ═══════════════════════════════════════════════════
function renderQuickUsers(){
  const c=document.getElementById('quick-users');if(!c)return;
  c.innerHTML=D.users.filter(u=>u.role==='admin').map(u=>`<div class="qu" onclick="quickLogin('${u.username}')">
    <div class="qu-av" style="background:${u.color||'#00d4a0'};color:#000">${u.display.split(' ').map(w=>w[0]).join('').substring(0,2).toUpperCase()}</div>
    <div><div class="qu-name">${u.display}</div><div class="qu-role">@${u.username}</div></div>
    <span class="qu-badge" style="background:${u.color||'#00d4a0'}22;color:${u.color||'#00d4a0'}">Admin</span>
  </div>`).join('');
}
function quickLogin(u){document.getElementById('login-user').value=u;document.getElementById('login-pass').focus();}
function togglePass(){const i=document.getElementById('login-pass');i.type=i.type==='password'?'text':'password';}

// ═══════════════════════════════════════════════════
// USER MANAGER
// ═══════════════════════════════════════════════════
function renderUserMgr(){
  const list=document.getElementById('user-mgr-list');if(!list)return;
  list.innerHTML=D.users.map((u,i)=>{
    const init=u.display.split(' ').map(w=>w[0]).join('').substring(0,2).toUpperCase();
    const suspended = u.status==='suspended';
    return `<div class="um-row" style="${suspended?'opacity:.5':''}">
      <div class="ua" style="background:${u.color||'#888'};width:36px;height:36px;font-size:12px;flex-shrink:0">${init}</div>
      <div style="flex:1;min-width:0">
        <div style="font-size:12.5px;font-weight:600;color:var(--text)">${u.display}
          <span class="badge ${u.role==='admin'?'t':u.role==='regional_safety'?'b':'p'}">${ROLE_LABELS[u.role]||u.role}</span>
          ${suspended?'<span class="badge r">Suspended</span>':''}
        </div>
        <div style="font-size:10.5px;color:var(--text3);margin-top:1px">
          @${u.username}
          ${u.email?'· '+u.email:''}
          · ${u.dept||'--'}
          · <b style="color:var(--text2)">${u.locationAccess==='all'?'All locations':u.locationAccess.replace(/_/g,' ')}</b>
          ${u.createdAt?`<br>Created ${u.createdAt}${u.createdBy?' by '+u.createdBy:''}` : ''}
        </div>
      </div>
      <div style="display:flex;gap:5px;flex-shrink:0">
        <button class="btn btn-g btn-sm" onclick="openEditUser(${i})" title="Edit user">✏ Edit</button>
      </div>
    </div>`;
  }).join('');
  // Populate location dropdowns
  const locOpts='<option value="all">All locations</option>'+D.locations.map(l=>`<option value="${l.id}">${l.name}</option>`).join('');
  const ls=document.getElementById('nu-loc');if(ls)ls.innerHTML=locOpts;
  const el=document.getElementById('eu-loc');if(el)el.innerHTML=locOpts;
}

function openEditUser(i) {
  const u = D.users[i];
  if (!u) return;
  document.getElementById('edit-user-idx').value = i;
  document.getElementById('edit-user-title').textContent = u.display + ' (@' + u.username + ')';
  document.getElementById('eu-user').value    = u.username;
  document.getElementById('eu-display').value = u.display;
  document.getElementById('eu-email').value   = u.email || '';
  document.getElementById('eu-dept').value    = u.dept || '';
  document.getElementById('eu-pass').value    = '';
  document.getElementById('eu-role').value    = u.role || 'viewer';
  document.getElementById('eu-status').value  = u.status || 'active';
  // Location
  const euLoc = document.getElementById('eu-loc');
  if (euLoc) {
    euLoc.innerHTML = '<option value="all">All locations</option>' +
      D.locations.map(l=>`<option value="${l.id}">${l.name}</option>`).join('');
    euLoc.value = u.locationAccess || 'all';
  }
  // Info row
  const info = document.getElementById('eu-info-row');
  if (info) {
    info.innerHTML = `
      Created: ${u.createdAt||'--'} ${u.createdBy?'by '+u.createdBy:''}<br>
      Last login: ${u.lastLogin||'Never recorded'}<br>
      Password: ${u.password?.startsWith('h')?'Hashed (secure)':'Plain text (will hash on login)'}
    `;
  }
  closeMo('mo-user-mgr');
  openMo('mo-edit-user');
}

function saveEditUser() {
  const i = parseInt(document.getElementById('edit-user-idx').value);
  const u = D.users[i];
  if (!u) return;
  const newUser = document.getElementById('eu-user').value.trim().toLowerCase();
  const newPass = document.getElementById('eu-pass').value;

  // Check username conflict (only if changed)
  if (newUser !== u.username && D.users.find((x,xi)=>xi!==i&&x.username===newUser)) {
    toast('Username already exists','warn'); return;
  }
  if (newPass && newPass.length < 4) { toast('Min password: 4 chars','warn'); return; }

  u.username      = newUser || u.username;
  u.display       = document.getElementById('eu-display').value.trim() || u.display;
  u.email         = document.getElementById('eu-email').value.trim();
  u.dept          = document.getElementById('eu-dept').value.trim();
  u.role          = document.getElementById('eu-role').value;
  u.locationAccess= document.getElementById('eu-loc').value;
  u.status        = document.getElementById('eu-status').value;
  u.updatedAt     = new Date().toLocaleString('en-ZA');
  u.updatedBy     = SESSION?.display || 'Admin';

  if (newPass) {
    u.password = newPass; // always store plain — works on all browsers/devices
  }

  save();
  if (D.cfg?.syncBackend || D.cfg?.syncUrl) {
    pushToRemote().then(()=>toast('User updated and synced! ✓')).catch(()=>toast('User updated (sync pending)'));
  } else {
    toast('User updated! ✓');
  }
  closeMo('mo-edit-user');
  openMo('mo-user-mgr');
  renderUserMgr();
  renderQuickUsers();
}

function deleteUserFromEdit() {
  const i = parseInt(document.getElementById('edit-user-idx').value);
  const u = D.users[i];
  if (!u) return;
  if (u.username === 'admin') { toast('Cannot delete admin user','warn'); return; }
  if (!confirm('Delete user ' + u.display + ' (@' + u.username + ')? This cannot be undone.')) return;
  D.users.splice(i, 1);
  save();
  if (D.cfg?.syncBackend || D.cfg?.syncUrl) pushToRemote().catch(()=>{});
  toast('User deleted');
  closeMo('mo-edit-user');
  openMo('mo-user-mgr');
  renderUserMgr();
  renderQuickUsers();
}
function addUser(){
  const un=document.getElementById('nu-user').value.trim().toLowerCase();
  const dn=document.getElementById('nu-display').value.trim();
  const pw=document.getElementById('nu-pass').value;
  const ro=document.getElementById('nu-role').value;
  const de=document.getElementById('nu-dept').value.trim();
  const lo=document.getElementById('nu-loc').value;
  const em=document.getElementById('nu-email')?.value?.trim()||'';
  if(!un||!dn||!pw){toast('Fill all required fields','warn');return;}
  if(pw.length<4){toast('Min password: 4 chars','warn');return;}
  if(D.users.find(u=>u.username===un)){toast('Username already exists','warn');return;}
  const cols=['#00d4a0','#4d9fff','#9d7dff','#ffaa00','#ff4d6d'];
  // Store password as PLAIN TEXT — checkPass upgrades on first login
  // This avoids hash mismatch between devices/browsers
  D.users.push({
    username:un, display:dn,
    password:pw,  // plain text — each device upgrades on first login
    role:ro, dept:de, locationAccess:lo,
    email:em,
    color:cols[D.users.length%cols.length],
    createdAt:new Date().toLocaleString('en-ZA'),
    createdBy:SESSION?.display||'Admin',
  });
  save();
  // Push to remote immediately so other devices get the new user
  if(D.cfg?.syncBackend || D.cfg?.syncUrl) {
    pushToRemote().then(()=>toast(`User @${un} created and synced! ✓`)).catch(()=>toast(`User @${un} created (sync pending)`));
  } else {
    toast(`User @${un} created! ✓`);
  }
  ['nu-user','nu-display','nu-pass','nu-dept','nu-email'].forEach(id=>{const el=document.getElementById(id);if(el)el.value='';});
  renderUserMgr();renderQuickUsers();
}
function removeUser(i){if(!confirm('Remove user '+D.users[i].display+'?'))return;D.users.splice(i,1);save();renderUserMgr();toast('User removed');}
function openChangePassFor(username){cpTarget=username;const u=D.users.find(x=>x.username===username);const ci=document.getElementById('cp-info');if(ci&&u)ci.textContent='Changing password for: '+u.display+' (@'+u.username+')';const wrap=document.getElementById('cp-cur-wrap');if(wrap)wrap.style.display=isAdmin()&&username!==SESSION.username?'none':'';['cp-current','cp-new','cp-confirm'].forEach(id=>{const el=document.getElementById(id);if(el)el.value='';});document.getElementById('cp-err').classList.remove('show');closeMo('mo-user-mgr');openMo('mo-change-pass');}

// ═══════════════════════════════════════════════════
// RENDER FUNCTIONS
// ═══════════════════════════════════════════════════
function renderKpis(){
  // ALWAYS filter by location — every user sees only their own location data
  const locInc    = filterByLoc(D.incidents,'loc');
  const locEval   = filterByLoc(D.evaluations,'loc');
  const locTrain  = filterByLoc(D.trainings,'unit');
  const locDel    = filterByLoc(D.deliveries,'unit');
  const locWarn   = filterByLoc(D.warnings,'unit');
  const locPPE    = filterByLoc(D.ppeItems, 'location'); // filtered by user's location

  const lo        = locPPE.filter(i=>i.stock<=i.min).length;
  const openPO    = (D.purchaseOrders||[]).filter(p=>{
    if(locAccess()==='all') return p.status!=='Approved'&&p.status!=='Completed';
    return (p.status!=='Approved'&&p.status!=='Completed') && matchesLoc(p.locationName||p.location||'', locAccess());
  }).length;
  const locScores = locEval.map(e=>e.score);
  const avgScore  = locScores.length ? (locScores.reduce((a,b)=>a+b,0)/locScores.length).toFixed(1) : '--';

  // Dashboard KPIs
  document.getElementById('kv-inc').textContent  = locInc.length;
  document.getElementById('kv-ppe').textContent   = lo;
  document.getElementById('kv-train').textContent = locTrain.filter(t=>t.status==='Expired').length;
  document.getElementById('kv-conf').textContent  = locInc.length===0 ? '100%' :
    Math.max(0,Math.round((1-locInc.filter(i=>i.status==='Open').length/Math.max(locInc.length,1))*100))+'%';

  // PPE KPIs
  document.getElementById('kv-ppe-stock').textContent = locPPE.reduce((a,i)=>a+(i.stock||0),0);
  document.getElementById('kv-ppe-low').textContent   = lo;
  document.getElementById('kv-ppe-po').textContent    = openPO;
  document.getElementById('kv-ppe-del').textContent   = locDel.length;

  // Incidents KPIs
  document.getElementById('kv-inc-open').textContent   = locInc.filter(i=>i.status==='Open').length;
  document.getElementById('kv-inc-inv').textContent    = locInc.filter(i=>i.status==='Investigating').length;
  document.getElementById('kv-inc-closed').textContent = locInc.filter(i=>i.status==='Closed').length;

  // Performance KPIs
  document.getElementById('kv-evals').textContent = locEval.length;
  document.getElementById('kv-goal').textContent  = avgScore;
  document.getElementById('kv-warn').textContent  = locWarn.length;
  document.getElementById('kv-texp').textContent  = locTrain.filter(t=>t.status==='Expired').length;

  // Badges
  const al=document.getElementById('bdg-alerts');
  const ac=D.alerts.length; if(al){al.textContent=ac;al.style.display=ac?'block':'none';}
  const dr=document.getElementById('bdg-del-req');
  if(dr){const dc=(D.deleteRequests||[]).filter(r=>r.status==='Pending').length;dr.textContent=dc;dr.style.display=dc?'block':'none';}
  const bi=document.getElementById('bdg-inc');
  const oi=locInc.filter(i=>i.status==='Open').length; if(bi){bi.textContent=oi;bi.style.display=oi?'block':'none';}

  // Date + location label
  const locName = locAccess()==='all' ? 'All locations' :
    D.locations.find(l=>l.id===locAccess())?.name || locAccess().replace(/_/g,' ');
  const dateEl = document.getElementById('dash-date');
  if(dateEl) dateEl.textContent = new Date().toLocaleDateString('en-ZA',
    {weekday:'long',day:'2-digit',month:'long',year:'numeric'}) + ' · ' + locName;
}

function renderPpe(){
  const catF=(document.getElementById('ppe-cat-filter')||{}).value||'';
  const locF=(document.getElementById('ppe-loc-filter')||{}).value||'';
  const filteredPpe=D.ppeItems.filter(i=>{
    if(catF&&i.cat!==catF)return false;
    if(locF&&!matchesLoc(i.location||i.locationName||'',locF))return false;
    if(locAccess()!=='all'&&!matchesLoc(i.location||i.locationName||'',locAccess()))return false;
    return true;
  });
  const ppeHtml=filteredPpe.length?filteredPpe.map((i)=>{const idx=D.ppeItems.indexOf(i);
    const st=i.stock<=0?'<span class="badge r">Out</span>':i.stock<=i.min?'<span class="badge r">Low</span>':i.stock<=i.min*1.5?'<span class="badge a">Attention</span>':'<span class="badge t">OK</span>';
    const req=i.stock<=i.min?`<button class="btn btn-a btn-sm" onclick="createAutoPO(${idx})" style="font-size:10px;padding:3px 8px">Request</button>`:'';
    const inv=i.invoice?`<span style="font-family:monospace;font-size:10px;color:var(--text3)">${i.invoice}</span>`:'';
    const sizes=[];
    if(i.clothingSizes) sizes.push(i.clothingSizes);
    if(i.shoeSizes) sizes.push('Boot: '+i.shoeSizes);
    const sizeStr=sizes.length?sizes.join(' | '):'--';
    return `<tr data-search="${i.name.toLowerCase()} ${(i.cat||'').toLowerCase()} ${(i.locationName||'').toLowerCase()}">
      <td><a href="#" onclick="event.preventDefault();openPpeDetail(${idx})" style="color:var(--teal);text-decoration:none;cursor:pointer"><b>${i.name}</b></a>${inv?'<br>'+inv:''}</td><td style="font-size:11px">${i.locationName||i.location||'--'}</td><td>${i.cat}</td><td style="font-size:10px">${sizeStr}</td><td>${i.stock}</td><td>${i.min}</td><td>${st}</td>
      <td style="display:flex;gap:4px;flex-wrap:wrap">
        <button class="btn-icon" title="View details" onclick="openPpeDetail(${idx})" style="font-size:11px;padding:4px 7px">👁</button>
        ${req}
        <button class="btn-icon edit-guard" title="Edit" onclick="requestEdit('ppeItem',${idx},null)" style="font-size:11px;padding:4px 7px">✏</button>
        <button class="btn-icon edit-guard" title="Delete" onclick="requestDelete('ppeItem',${idx},'${i.name.replace(/'/g,"\'")}')" style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>
      </td>
    </tr>`;
  }).join(''):'<tr><td colspan="8" style="text-align:center;color:var(--text3);padding:20px">No PPE items registered yet. Click + Add item to start.</td></tr>';
  document.getElementById('ppe-tbody').innerHTML=ppeHtml;
  // Deliveries filtered by user's location
  const locDeliveries = filterByLoc(D.deliveries, 'unit');
  document.getElementById('del-tbody').innerHTML=locDeliveries.map((d,idx)=>{const ridx=D.deliveries.indexOf(d);return`<tr>
    <td>${d.emp}</td><td>${d.item}</td><td>${d.qty||1}</td>
    <td style="font-size:11px">${d.clothingSize||d.size||'--'}</td>
    <td style="font-size:11px">${d.shoeSize||'--'}</td>
    <td style="font-size:11px;color:var(--text3)">${d.poRef||'--'}</td>
    <td>${d.date}</td><td>${bSt(d.status)}</td>
    <td style="display:flex;gap:4px">
      <button class="btn-icon" onclick="openRecordDetail('delivery',${ridx})" style="font-size:11px;padding:4px 7px">👁</button>
      <button class="btn-icon edit-guard" onclick="requestEdit('delivery',${ridx},null)" style="font-size:11px;padding:4px 7px">✏</button>
      <button class="btn-icon edit-guard" onclick="requestDelete('delivery',${ridx},'Delivery: ${(d.emp||'').replace(/'/g,"\\'")} / ${(d.item||'').replace(/'/g,"\\'")}') " style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>
    </td>
  </tr>`;}).join('') || '<tr><td colspan="9" style="text-align:center;color:var(--text3);padding:16px">No deliveries for this location</td></tr>';
  renderPOTable();
}

function renderPOTable(){
  // Filter POs by user's location
  const locPOs = (D.purchaseOrders||[]).filter((p,i)=>{
    if(locAccess()==='all') return true;
    return matchesLoc(p.locationName||p.location||'', locAccess());
  });
  document.getElementById('po-tbody').innerHTML=locPOs.map((p)=>{
    const i=D.purchaseOrders.indexOf(p);
    const ready=p.stockUpdated&&p.supplier&&p.invoice;
    const appBtn=ready?`<button class="btn btn-p btn-sm admin-only" onclick="approvePO(${i})">✓ Approve</button>`:`<button class="btn btn-g btn-sm admin-only" style="opacity:.5;cursor:not-allowed;font-size:10px" title="Update stock, supplier and invoice first">🔒 Blocked</button>`;
    const locTag=p.locationName?`<span style="font-size:9px;background:var(--bg4);color:var(--text3);padding:1px 5px;border-radius:4px">📍${p.locationName}</span>`:'';
    return `<tr>
      <td style="font-family:monospace;font-size:11px;font-weight:700;color:var(--teal)">${p.po}</td>
      <td>${p.item}<br>${locTag}</td><td>${p.qty}</td>
      <td><input style="background:transparent;border:none;color:var(--text);font-size:11px;width:100px" value="${p.supplier||''}" placeholder="Supplier" onchange="D.purchaseOrders[${i}].supplier=this.value;save()"></td>
      <td><input style="background:transparent;border:none;color:var(--text);font-size:11px;width:110px" value="${p.invoice||''}" placeholder="Invoice no." onchange="D.purchaseOrders[${i}].invoice=this.value;save()"></td>
      <td><label style="display:flex;align-items:center;gap:4px;cursor:pointer"><input type="checkbox" ${p.stockUpdated?'checked':''} onchange="D.purchaseOrders[${i}].stockUpdated=this.checked;save();renderPOTable()"> <span style="font-size:11px">Updated</span></label></td>
      <td>${bSt(p.status)}</td>
      <td class="edit-guard" style="display:flex;gap:4px">${p.status!=='Approved'?appBtn:''} ${p.status!=='Approved'?`<button class="btn btn-r btn-sm" style="font-size:10px;padding:3px 7px" onclick="removePO(${i})">✕</button>`:''}</td>
    </tr>`;
  }).join('') || '<tr><td colspan="8" style="text-align:center;color:var(--text3);padding:16px">No purchase requests for your location</td></tr>';
}

function createAutoPO(itemIdx){
  const item=D.ppeItems[itemIdx];if(!item)return;
  if(!D.purchaseOrders)D.purchaseOrders=[];
  if(D.purchaseOrders.find(p=>p.item===item.name&&p.status!=='Approved')){toast('A request already exists for this item','warn');return;}
  const n=D.purchaseOrders.length+1;
  const po={po:`PO-${new Date().getFullYear()}-${String(n).padStart(3,'0')}`,item:item.name,qty:item.min*3,supplier:'',invoice:'',stockUpdated:false,status:'Awaiting approval',location:item.location||'',locationName:item.locationName||''};
  D.purchaseOrders.unshift(po);
  logActivity('CREATE','purchaseOrder',po.po,`Auto-generated — Item: ${item.name} × ${po.qty} — Stock: ${item.stock}/${item.min}`);
  D.logEntries.unshift({time:'Now',color:'var(--amber)',msg:`<b>Purchase request</b> created · ${item.name} × ${po.qty} units · ${po.po}`});
  save();renderPpe();switchTab('ppe-tab',2,document.querySelector('#page-ppe .tab:nth-child(3)'));toast(`${po.po} created!`);
}

function approvePO(i){
  if(!isAdmin()){toast('Only administrators can approve purchase orders','warn');return;}
  const p=D.purchaseOrders[i];
  if(!p.stockUpdated){toast('Update stock before approving','warn');return;}
  if(!p.supplier){toast('Enter supplier before approving','warn');return;}
  if(!p.invoice){toast('Enter invoice number before approving','warn');return;}
  p.status='Approved';
  p.approvedBy=SESSION?.display||'Admin';
  p.approvedAt=new Date().toLocaleString('en-ZA');
  logActivity('APPROVE','purchaseOrder',p.po,`Approved by ${SESSION?.display||'Admin'} — Item: ${p.item} × ${p.qty} — Supplier: ${p.supplier} — Invoice: ${p.invoice}`);
  D.logEntries.unshift({time:'Now',color:'var(--teal)',msg:`<b>PO Approved</b> · ${p.po} · ${p.item} · Supplier: ${p.supplier} · Invoice: ${p.invoice}`});
  save();renderPOTable();toast(`${p.po} approved!`);
}

function saveNewPO(){
  const item=document.getElementById('po-item').value;
  const qty=parseInt(document.getElementById('po-qty').value)||50;
  const poLocation=document.getElementById('po-location')?.value||'';
  const sizes=document.getElementById('po-sizes')?.value?.trim()||'';
  const supplier=document.getElementById('po-supplier').value.trim();
  if(!poLocation){toast('Select the destination location for this stock','warn');return;}
  if(!assertCanEditLocation(poLocation)){return;}
  const invoice=document.getElementById('po-invoice')?.value?.trim()||'';
  if(!item){toast('Select an item','warn');return;}
  if(!D.purchaseOrders)D.purchaseOrders=[];
  const n=D.purchaseOrders.length+1;
  const locName=D.locations.find(l=>l.id===poLocation)?.name||poLocation;
  D.purchaseOrders.unshift({po:`PO-${new Date().getFullYear()}-${String(n).padStart(3,'0')}`,item,qty,supplier,invoice,stockUpdated:false,status:'Awaiting approval',location:poLocation,locationName:locName,sizes});
  logActivity('CREATE','purchaseOrder',`PO for ${item}`,`Qty: ${qty} | Location: ${locName} | Sizes: ${sizes||'N/A'}`);
  save();closeMo('mo-new-po');renderPpe();toast('Purchase request created!');
}

function removePO(i){
  const p=D.purchaseOrders[i];
  if(!p)return;
  requestDelete('po',i,'PO: '+p.po+' — '+p.item);
}

function renderIncidents(){
  const statusF=(document.getElementById('inc-status-filter')||{}).value||'';
  const items=filterByLoc(D.incidents,'loc').filter(i=>!statusF||i.status===statusF);
  // ALL incidents visible, but edit/delete only for own location
  const allIncs = D.incidents.filter(i=>!statusF||i.status===statusF);
  document.getElementById('inc-tbody').innerHTML=allIncs.map(i=>{const ridx=D.incidents.indexOf(i);
    const canEditThis=locAccess()==='all'||locFilter(i,'loc');
    const editBtns=canEditThis&&canEdit()?
      `<button class="btn-icon" onclick="openRecordDetail('incident',${ridx})" style="font-size:11px;padding:4px 7px">👁</button>
       <button class="btn-icon" onclick="requestEdit('incident',${ridx},null)" style="font-size:11px;padding:4px 7px">✏</button>
       <button class="btn-icon" onclick="requestDelete('incident',${ridx},'${i.code}')" style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>`
      :`<button class="btn-icon" onclick="openRecordDetail('incident',${ridx})" style="font-size:11px;padding:4px 7px">👁</button>
        <span style="font-size:10px;color:var(--text3)">view only</span>`;
    return`<tr data-search="${i.code} ${i.type} ${i.loc}">
    <td><b style="font-family:monospace;font-size:11px">${i.code}</b></td><td style="font-size:11px">${i.type}</td>
    <td style="font-size:11px">${i.loc}</td><td>${bSev(i.sev)}</td><td>${bSt(i.status)}</td>
    <td style="font-size:11px;color:var(--text3)">${i.date}</td>
    <td style="display:flex;gap:4px">${editBtns}</td>
  </tr>`;}).join('')||'<tr><td colspan="7" style="text-align:center;color:var(--text3);padding:16px">No incidents</td></tr>';
  document.getElementById('inv-list').innerHTML=D.incidents.filter(i=>i.status==='Investigating').map(i=>`<div class="ai warn"><div class="ai-ic a">🔍</div><div class="ai-body"><div class="ai-title">${i.code} — ${i.type}</div><div class="ai-sub">${i.loc} · ${i.date}</div></div><span class="badge a">Investigating</span></div>`).join('');
  
  // Populate incident dropdown for corrective actions
  const caInc = document.getElementById('ca-inc');
  if(caInc){
    const cur = caInc.value;
    caInc.innerHTML='<option value="">Select incident...</option>'+
      D.incidents.map(i=>`<option value="${i.code}">${i.code} — ${i.type} (${i.loc})</option>`).join('');
    if(cur) caInc.value=cur;
  }

  // Render corrective actions table
  document.getElementById('actions-tbody').innerHTML=(D.corrActions||[]).length ?
    (D.corrActions||[]).map((a,idx)=>`<tr>
      <td style="font-family:monospace;font-size:11px">${a.inc}</td>
      <td>${a.action}</td>
      <td style="font-size:11px">${a.resp}</td>
      <td style="font-size:11px;color:var(--text3)">${a.due}</td>
      <td>${bSt(a.status)}</td>
      <td style="display:flex;gap:4px">
        <button class="btn-icon" onclick="editCorrAction(${idx})" style="font-size:11px;padding:4px 7px">✏</button>
        <button class="btn-icon" onclick="requestDelete('corrAction',${idx},'Action: '+D.corrActions[${idx}].inc)" style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>
      </td>
    </tr>`).join('')
    : '<tr><td colspan="6" style="text-align:center;color:var(--text3);padding:16px">No corrective actions. Add one above.</td></tr>';
}

function renderEvaluations(){
  const locF=(document.getElementById('eval-loc-filter')||{}).value||'';
  // Populate filter
  const lf=document.getElementById('eval-loc-filter');
  if(lf&&lf.options.length<=1){const locs=[...new Set(D.evaluations.map(e=>e.loc||'--'))].sort();locs.forEach(l=>{const o=document.createElement('option');o.value=l;o.textContent=l;lf.appendChild(o);});}
  const filtered=D.evaluations.filter(e=>{
    if(!locFilter(e,'loc'))return false;
    if(locF&&e.loc!==locF)return false;
    return true;
  });
  document.getElementById('eval-tbody').innerHTML=filtered.length?filtered.map((e,i)=>{
    const ri=D.evaluations.indexOf(e);
    const pct=Math.round(e.score*10);
    const col=e.score>=8?'var(--teal)':e.score>=7?'var(--amber)':'var(--red)';
    return `<tr data-search="${(e.name||'').toLowerCase()} ${(e.loc||'').toLowerCase()}">
      <td><b>${e.name}</b></td><td style="font-size:11px">${e.loc||'--'}</td>
      <td><b style="color:${col}">${e.score}</b></td>
      <td><div class="pw"><div class="pb"><div class="pf" style="width:${pct}%;background:${col}"></div></div><span style="font-size:10px;color:var(--text3)">${pct}%</span></div></td>
      <td style="font-size:11px;color:var(--text3)">${e.period||''}</td><td>${bSt(e.status)}</td>
      <td style="display:flex;gap:4px">
        <button class="btn-icon" onclick="openEvalDetail(${ri})" style="font-size:11px;padding:4px 7px">👁</button>
        <button class="btn-icon" onclick="requestEdit('evaluation',${ri},null)" style="font-size:11px;padding:4px 7px">✏</button>
        <button class="btn-icon" onclick="requestDelete('evaluation',${ri},'Eval: ${(e.name||'').replace(/'/g,"\\'")} ${e.period||''}')" style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>
      </td>
    </tr>`;
  }).join(''):'<tr><td colspan="7" style="text-align:center;color:var(--text3);padding:16px">No evaluations for this location</td></tr>';
}

let currentEvalIdx=null;
function openEvalDetail(i){
  currentEvalIdx=i;const e=D.evaluations[i];if(!e)return;
  document.getElementById('eval-det-title').textContent=`${e.name} — ${e.loc||''}`;
  const col=e.score>=8?'var(--teal)':e.score>=7?'var(--amber)':'var(--red)';
  document.getElementById('eval-det-body').innerHTML=`
    <div style="display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:14px">
      <div class="card-sm" style="text-align:center"><div style="font-size:9px;color:var(--text3);margin-bottom:3px">SCORE</div><div style="font-size:26px;font-weight:700;color:${col}">${e.score}</div></div>
      <div class="card-sm" style="text-align:center"><div style="font-size:9px;color:var(--text3);margin-bottom:3px">LOCATION</div><div style="font-size:12px;font-weight:600">${e.loc||'--'}</div></div>
      <div class="card-sm" style="text-align:center"><div style="font-size:9px;color:var(--text3);margin-bottom:3px">STATUS</div><div style="margin-top:4px">${bSt(e.status)}</div></div>
    </div>
    ${e.feedback?`<div class="card-sm" style="margin-bottom:12px;font-size:12px;color:var(--text2);line-height:1.6">${e.feedback}</div>`:''}
    <div class="card-sm">
      <div style="font-size:10px;font-weight:700;color:var(--text2);text-transform:uppercase;margin-bottom:8px">Edit</div>
      <div style="display:flex;gap:8px;align-items:center;flex-wrap:wrap">
        <input class="fi" type="number" id="edet-score" value="${e.score}" min="0" max="10" step="0.1" style="width:80px">
        <select class="fs" id="edet-status" style="flex:1"><option ${e.status==='Approved'?'selected':''}>Approved</option><option ${e.status==='Under review'?'selected':''}>Under review</option><option ${e.status==='Below target'?'selected':''}>Below target</option></select>
      </div>
    </div>`;
  openMo('mo-eval-detail');
}
function saveEvalDetail(){const e=D.evaluations[currentEvalIdx];if(!e)return;const s=parseFloat(document.getElementById('edet-score').value);if(isNaN(s)||s<0||s>10){toast('Invalid score (0-10)','warn');return;}e.score=s;e.status=document.getElementById('edet-status').value;save();renderEvaluations();closeMo('mo-eval-detail');toast('Evaluation updated!');}
function deleteEval(i){if(!confirm('Delete this evaluation?'))return;D.evaluations.splice(i,1);save();renderEvaluations();closeMo('mo-eval-detail');toast('Evaluation deleted');}
function deleteCurrentEval(){
  if(currentEvalIdx!==null){
    const e=D.evaluations[currentEvalIdx];
    if(!e)return;
    requestDelete('evaluation',currentEvalIdx,'Eval: '+e.name+' '+e.period);
    closeMo('mo-eval-detail');
  }
}

function renderWarnings(){
  const warns=filterByLoc(D.warnings,'unit');
  document.getElementById('warn-tbody').innerHTML=warns.length?warns.map(w=>{
    const ridx=D.warnings.indexOf(w);
    return`<tr>
      <td>${w.emp}</td><td>${bSev(w.type)}</td><td>${w.reason}</td>
      <td style="font-size:11px;color:var(--text3)">${w.date}</td><td>${bSt(w.status)}</td>
      <td style="display:flex;gap:4px">
        <button class="btn-icon" onclick="requestEdit('warning',${ridx},null)" style="font-size:11px;padding:4px 7px">✏</button>
        <button class="btn-icon" onclick="requestDelete('warning',${ridx},'Warning: '+D.warnings[${ridx}].emp)" style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>
      </td>
    </tr>`;
  }).join(''):'<tr><td colspan="6" style="text-align:center;color:var(--text3);padding:16px">No warnings for this location</td></tr>';
}
function renderTrainings(){
  const trains=filterByLoc(D.trainings,'unit');
  document.getElementById('train-tbody').innerHTML=trains.length?trains.map(t=>{
    const ridx=D.trainings.indexOf(t);
    return`<tr>
    <td>${t.emp}</td><td>${t.name}</td><td style="font-size:11px">${t.nr}</td>
    <td style="font-size:11px;color:var(--text3)">${t.exp}</td><td>${bSt(t.status)}</td>
    <td style="display:flex;gap:4px">
      <button class="btn-icon" onclick="requestDelete('training',${ridx},'Training: '+D.trainings[${ridx}].emp+' / '+D.trainings[${ridx}].name)" style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>
    </td>
  </tr>`;}).join(''):'<tr><td colspan="6" style="text-align:center;color:var(--text3);padding:16px">No training records for this location</td></tr>';
}

function saveTraining(){
  const emp=document.getElementById('train-emp').value;
  const name=document.getElementById('train-name').value.trim();
  const nr=document.getElementById('train-nr').value.trim();
  const exp=document.getElementById('train-exp').value;
  const status=document.getElementById('train-status').value;
  if(!emp||!name){toast('Fill employee and training name','warn');return;}
  const expFormatted=exp?new Date(exp).toLocaleDateString('en-ZA'):'-';
  const trainEmpObj=D.employees.find(e=>e.name===emp);
  D.trainings.push({emp,name,nr:nr||'-',exp:expFormatted,status,unit:trainEmpObj?.unit||''});
  logActivity('CREATE','training',`${emp} — ${name}`,`Standard: ${nr||'N/A'} | Expiry: ${expFormatted} | Status: ${status}`);
  save();closeMo('mo-training');renderTrainings();toast('Training record added!');
}

function renderEmployees(){
  const lf=document.getElementById('emp-loc-filter');const df=document.getElementById('emp-dept-filter');const sf=document.getElementById('emp-status-filter');
  // Populate filters
  if(lf&&lf.options.length<=1){D.locations.forEach(l=>{const o=document.createElement('option');o.value=l.name;o.textContent=l.name;lf.appendChild(o);});}
  if(df&&df.options.length<=1){const depts=[...new Set(D.employees.map(e=>e.dept||'').filter(Boolean))].sort();depts.forEach(d=>{const o=document.createElement('option');o.value=d;o.textContent=d;df.appendChild(o);});}
  const lv=lf?lf.value:'';const dv=df?df.value:'';const sv=sf?sf.value:'';
  const la=locAccess();
  const filtered=D.employees.filter(e=>{
    // Use normLoc for robust matching (handles underscore vs space)
    if(la!=='all'&&!matchesLoc(e.unit,la))return false;
    if(lv&&!matchesLoc(e.unit,lv))return false;
    if(dv&&e.dept!==dv)return false;
    if(sv&&e.status!==sv)return false;
    return true;
  });
  document.getElementById('emp-count').textContent=`${filtered.length} employee${filtered.length!==1?'s':''} shown${la!=='all'?' at '+la.replace(/_/g,' '):''}`;
  // Build location + region charts for employees page
  buildEmpCharts(filtered);

  document.getElementById('emp-tbody').innerHTML=filtered.map((e)=>{const ri=D.employees.indexOf(e);return`<tr data-search="${(e.name||'').toLowerCase()} ${(e.num||'').toString()} ${(e.pos||'').toLowerCase()} ${(e.unit||'').toLowerCase()}">
    <td style="font-family:monospace;font-size:11px">${e.num||''}</td>
    <td><b>${e.name}</b></td>
    <td style="font-size:11px">${e.pos||''}</td>
    <td style="font-size:11px">${e.unit||''}</td>
    <td style="font-size:11px;color:var(--text3)">${e.region||e.dept||''}</td>
    <td style="font-size:11px;color:var(--text3)">${e.dept||''}</td>
    <td>${bSt(e.status||'Active')}</td>
    <td style="display:flex;gap:4px">
    <button class="btn-icon" onclick="openRecordDetail('employee',${ri})" style="font-size:11px;padding:4px 7px">👁</button>
    <button class="btn-icon edit-guard" onclick="requestEdit('employee',${ri},null)" style="font-size:11px;padding:4px 7px">✏</button>
    <button class="btn-icon edit-guard" onclick="requestDelete('employee',${ri},'${e.name.replace(/'/g,"\\'")}')" style="font-size:11px;padding:4px 7px;color:var(--red)">🗑</button>
  </td>
  </tr>`;}).join('')||'<tr><td colspan="8" style="text-align:center;color:var(--text3);padding:16px">No employees found</td></tr>';
}

function renderLocPage(){
  const box=document.getElementById('loc-list-box');if(!box)return;
  box.innerHTML=D.locations.map((l,i)=>`<div style="display:flex;align-items:center;gap:8px;padding:7px 0;border-bottom:1px solid var(--border)">
    <div style="width:7px;height:7px;border-radius:50%;background:var(--teal);flex-shrink:0"></div>
    <div style="flex:1;font-size:12.5px;font-weight:500">${l.name}</div>
    <div style="font-size:11px;color:var(--text3)">${l.region?l.region+', ':''} ${l.country}</div>
    ${isAdmin()?`<button class="btn-icon" style="font-size:10px;padding:3px 7px;color:var(--red)" onclick="removeLoc(${i})">✕</button>`:''}
  </div>`).join('')||'<div style="color:var(--text3);font-size:12px">No locations registered</div>';
  buildLocChart();
}

function renderAlerts(){
  document.getElementById('alert-list').innerHTML=D.alerts.length?D.alerts.map((a,i)=>`<div class="ai ${a.type}">
    <div class="ai-ic ${a.cls}">${a.icon}</div>
    <div class="ai-body"><div class="ai-title">${a.title}</div><div class="ai-sub">${a.sub}</div></div>
    <span class="badge ${a.badgeCls}">${a.badge}</span>
    <button class="btn btn-g btn-sm" onclick="requestDelete('alert',${i},'Alert: ${(a.title||'').replace(/'/g,"\\'")}')">🗑 Remove</button>
  </div>`).join('') : '<div style="color:var(--text3);font-size:12px;padding:12px;text-align:center">✓ No active alerts</div>';
}

function renderLog(){
  const locLog=(D.logEntries||[]).filter(l=>!l.loc||matchesLoc(l.loc,locAccess()));
  document.getElementById('auto-log').innerHTML=locLog.map(l=>`<div class="log-item"><span class="log-t">${l.time}</span><div class="log-d" style="background:${l.color}"></div><div class="log-m">${l.msg}</div></div>`).join('')||'<div style="color:var(--text3);font-size:12px;padding:10px;text-align:center">No actions logged yet</div>';
}

function renderDevMonitor(){
  const locI=filterByLoc(D.incidents,'loc');
  const locT=filterByLoc(D.trainings,'unit');
  const locE=filterByLoc(D.evaluations,'loc');
  const totalEmp=filterByLoc(D.employees,'unit').length||1;
  const incRate=Math.round((locI.length/Math.max(totalEmp,1))*100);
  const ppeDevPct=Math.round((D.ppeItems.filter(i=>i.stock<=i.min).length/Math.max(D.ppeItems.length,1))*100);
  const trainExpPct=Math.round((locT.filter(t=>t.status==='Expired').length/Math.max(locT.length,1))*100);
  const openPct=locI.length?Math.round((locI.filter(i=>i.status==='Open').length/locI.length)*100):0;
  const scorePct=locE.length?Math.round((locE.reduce((a,e)=>a+e.score,0)/locE.length)*10):0;
  const devs=[
    {label:'Incidents / employees',val:incRate,tgt:D.cfg.maxInc||4,color:'var(--red)'},
    {label:'PPE items below minimum',val:ppeDevPct,tgt:5,color:'var(--amber)'},
    {label:'Expired training (%)',val:trainExpPct,tgt:5,color:'var(--blue)'},
    {label:'Open incidents (%)',val:openPct,tgt:10,rev:false,color:'var(--red)'},
    {label:'Avg performance score',val:scorePct,tgt:70,rev:true,color:'var(--teal)'},
  ];
  document.getElementById('dev-monitor').innerHTML=devs.map(d=>{
    const over=d.rev?d.val<d.tgt:d.val>d.tgt;
    return `<div style="display:flex;align-items:center;gap:8px;padding:6px 0;border-bottom:1px solid var(--border)">
      <div style="font-size:11px;color:var(--text2);min-width:160px">${d.label}</div>
      <div style="flex:1;height:5px;background:var(--bg4);border-radius:3px;overflow:hidden"><div style="width:${Math.min(100,d.val)}%;height:100%;background:${d.color};border-radius:3px"></div></div>
      <div style="font-size:11px;font-weight:700;min-width:35px;text-align:right;color:${over?'var(--red)':'var(--teal)'}">${d.val}%</div>
      <div style="font-size:10px;color:var(--text3);min-width:55px">target: ${d.tgt}%</div>
    </div>`;
  }).join('');
}

function renderAutoActionsPreview(){
  const el=document.getElementById('auto-actions-preview');if(!el)return;
  el.innerHTML=(D.autoActions||[]).filter(a=>a.active).map(a=>`<div style="display:flex;gap:7px;padding:5px 0;border-bottom:1px solid var(--border)">
    <div style="width:6px;height:6px;border-radius:50%;background:${a.color};flex-shrink:0;margin-top:4px"></div>
    <div><div style="font-size:11px;font-weight:600;color:var(--text)">${a.trigger}</div><div style="font-size:10px;color:var(--text3)">${a.action}</div></div>
  </div>`).join('');
}

function renderRegionalTable(){
  const tbody=document.getElementById('regional-tbody');if(!tbody)return;
  const evals=filterByLoc(D.evaluations,'loc');
  if(!evals.length){tbody.innerHTML='<tr><td colspan="5" style="text-align:center;color:var(--text3);padding:16px">No evaluations yet</td></tr>';return;}
  const target=D.cfg.minScore||7;
  const allPeriods=[...new Set(evals.map(e=>e.period||'').filter(Boolean))].sort();
  const lastPeriod=allPeriods[allPeriods.length-1]||'';
  const last4=allPeriods.slice(-4);
  const byLoc={};
  evals.forEach(e=>{const l=e.loc||'--';if(!byLoc[l])byLoc[l]=[];byLoc[l].push(e);});
  const rows=Object.entries(byLoc).map(([loc,le])=>{
    const lp=le.filter(e=>e.period===lastPeriod);
    const monthly=lp.length?Math.round(lp.reduce((s,e)=>s+(e.score||0),0)/lp.length*10)/10:'-';
    const qe=le.filter(e=>last4.includes(e.period));
    const quarterly=qe.length?Math.round(qe.reduce((s,e)=>s+(e.score||0),0)/qe.length*10)/10:'-';
    return{loc,monthly,quarterly};
  }).sort((a,b)=>(b.quarterly||0)-(a.quarterly||0));
  tbody.innerHTML=rows.map(a=>{
    const mc=typeof a.monthly==='number'?(a.monthly>=target?'var(--teal)':a.monthly>=(target*0.9)?'var(--amber)':'var(--red)'):'var(--text3)';
    const qc=typeof a.quarterly==='number'?(a.quarterly>=target?'var(--teal)':a.quarterly>=(target*0.9)?'var(--amber)':'var(--red)'):'var(--text3)';
    const ok=typeof a.monthly==='number'&&a.monthly>=target;
    return`<tr><td><b>${a.loc}</b></td><td>${a.loc}</td><td><b style="color:${mc}">${a.monthly}</b></td><td><b style="color:${qc}">${a.quarterly}</b></td><td>${bSt(ok?'Approved':'Under review')}</td></tr>`;
  }).join('');
}

function renderReports(){
  const reps=[
    {e:'📊',t:'Executive dashboard',d:'KPIs, charts and alerts',key:'executive'},
    {e:'⚠',t:'Incident report',d:'All incidents with causes and actions',key:'incidents'},
    {e:'🛡',t:'PPE compliance',d:'Deliveries and signatures',key:'ppe'},
    {e:'📋',t:'Training status',d:'Certification status by area',key:'training'},
    {e:'◉',t:'Performance evaluations',d:'Individual KPIs and scores',key:'performance'},
    {e:'⚡',t:'Action log',d:'Complete history of alerts',key:'actions'},
  ];
  document.getElementById('reports-grid').innerHTML=reps.map(r=>`<div class="card" style="transition:border-color .18s" onmouseenter="this.style.borderColor='var(--teal)'" onmouseleave="this.style.borderColor='var(--border)'">
    <div style="font-size:22px;margin-bottom:7px">${r.e}</div>
    <div style="font-size:12.5px;font-weight:700;margin-bottom:3px">${r.t}</div>
    <div style="font-size:11px;color:var(--text3);margin-bottom:11px">${r.d}</div>
    <div style="display:flex;gap:6px">
      <button class="btn btn-g btn-sm" style="flex:1" onclick="generatePDF('${r.key}')">📄 PDF</button>
      <button class="btn btn-g btn-sm" style="flex:1" onclick="generateExcel('${r.key}')">📊 Excel</button>
    </div>
  </div>`).join('');
}

function _reportHeader(doc, title) {
  const company = D.cfg.company || 'Safety System';
  const dept = D.cfg.dept || '';
  const now = new Date().toLocaleString('en-ZA');
  doc.setFontSize(18);
  doc.setTextColor(0, 80, 60);
  doc.text(company, 14, 18);
  doc.setFontSize(10);
  doc.setTextColor(100, 100, 100);
  if (dept) doc.text(dept, 14, 25);
  doc.setFontSize(14);
  doc.setTextColor(40, 40, 40);
  doc.text(title, 14, dept ? 34 : 28);
  doc.setFontSize(9);
  doc.setTextColor(130, 130, 130);
  doc.text('Generated: ' + now, 14, dept ? 41 : 35);
  return dept ? 48 : 42;
}

function _getReportData(key) {
  const locIncs = filterByLoc(D.incidents, 'loc');
  const locDelivs = filterByLoc(D.deliveries, 'unit');
  const locEvals = filterByLoc(D.evaluations, 'loc');
  const locTrains = filterByLoc(D.trainings, 'unit');
  const locEmps = filterByLoc(D.employees, 'unit');
  switch (key) {
    case 'executive': {
      const totalInc = locIncs.length;
      const openInc = locIncs.filter(i => i.status !== 'Closed').length;
      const closedInc = locIncs.filter(i => i.status === 'Closed').length;
      const ppeCom = D.ppeItems.length ? Math.round((D.ppeItems.filter(i => i.stock > i.min).length / D.ppeItems.length) * 100) : 100;
      const incCom = locIncs.length ? Math.round((closedInc / locIncs.length) * 100) : 100;
      const avgScore = locEvals.length ? Math.round(locEvals.reduce((s, e) => s + (e.score || 0), 0) / locEvals.length * 10) / 10 : 0;
      return {
        title: 'Executive Dashboard',
        summary: [
          ['Metric', 'Value'],
          ['Total employees', locEmps.length.toString()],
          ['Total incidents', totalInc.toString()],
          ['Open incidents', openInc.toString()],
          ['Closed incidents', closedInc.toString()],
          ['PPE compliance', ppeCom + '%'],
          ['Incident compliance', incCom + '%'],
          ['Avg performance score', avgScore.toString()],
          ['Total deliveries', locDelivs.length.toString()],
          ['Active trainings', locTrains.filter(t => t.status === 'Valid').length.toString()],
          ['Expired trainings', locTrains.filter(t => t.status === 'Expired').length.toString()],
          ['Active alerts', D.alerts.length.toString()],
        ],
        alerts: D.alerts.map(a => [a.title, a.sub, a.badge])
      };
    }
    case 'incidents':
      return {
        title: 'Incident Report',
        headers: ['Code', 'Type', 'Location', 'Severity', 'Status', 'Date'],
        rows: locIncs.map(i => [i.code || '', i.type || '', i.loc || '', i.sev || '', i.status || '', i.date || ''])
      };
    case 'ppe':
      return {
        title: 'PPE Compliance Report',
        headers: ['Employee', 'Item', 'Qty', 'PO Ref', 'Location', 'Date', 'Status', 'Size (Clothing)', 'Size (Shoe)'],
        rows: locDelivs.map(d => [d.emp || '', d.item || '', (d.qty || 1).toString(), d.poRef || '', d.unit || '', d.date || '', d.status || '', d.clothingSize || '', d.shoeSize || ''])
      };
    case 'training':
      return {
        title: 'Training Status Report',
        headers: ['Employee', 'Training', 'Standard', 'Location', 'Expiry', 'Status'],
        rows: locTrains.map(t => [t.emp || '', t.name || '', t.nr || '', t.unit || '', t.exp || '', t.status || ''])
      };
    case 'performance':
      return {
        title: 'Performance Evaluations',
        headers: ['Employee', 'Location', 'Period', 'Score', 'Status'],
        rows: locEvals.map(e => [e.name || '', e.loc || '', e.period || '', (e.score || 0).toString(), e.status || ''])
      };
    case 'actions':
      return {
        title: 'Action Log',
        headers: ['Title', 'Description', 'Type'],
        rows: D.alerts.map(a => [a.title || '', a.sub || '', a.badge || ''])
      };
    default:
      return { title: 'Report', headers: [], rows: [] };
  }
}

function generatePDF(key) {
  try {
    const { jsPDF } = window.jspdf;
    const doc = new jsPDF({ orientation: 'landscape' });
    const data = _getReportData(key);
    let y = _reportHeader(doc, data.title);

    if (key === 'executive') {
      doc.autoTable({
        startY: y,
        head: [['Metric', 'Value']],
        body: data.summary.slice(1),
        theme: 'grid',
        headStyles: { fillColor: [0, 160, 120], fontSize: 10 },
        styles: { fontSize: 9, cellPadding: 3 },
        margin: { left: 14 }
      });
      if (data.alerts.length) {
        doc.autoTable({
          startY: doc.lastAutoTable.finalY + 10,
          head: [['Alert', 'Description', 'Status']],
          body: data.alerts,
          theme: 'grid',
          headStyles: { fillColor: [200, 60, 60], fontSize: 10 },
          styles: { fontSize: 9, cellPadding: 3 },
          margin: { left: 14 }
        });
      }
    } else {
      if (!data.rows.length) {
        doc.setFontSize(11);
        doc.setTextColor(130, 130, 130);
        doc.text('No records found.', 14, y + 10);
      } else {
        doc.autoTable({
          startY: y,
          head: [data.headers],
          body: data.rows,
          theme: 'grid',
          headStyles: { fillColor: [0, 160, 120], fontSize: 9 },
          styles: { fontSize: 8, cellPadding: 2.5 },
          margin: { left: 14 }
        });
      }
    }

    const filename = data.title.toLowerCase().replace(/\s+/g, '-') + '-' + new Date().toISOString().slice(0, 10) + '.pdf';
    doc.save(filename);
    toast(data.title + ' exported as PDF');
  } catch (e) {
    console.error('PDF generation error:', e);
    toast('Error generating PDF', 'err');
  }
}

function generateExcel(key) {
  try {
    const data = _getReportData(key);
    const wb = XLSX.utils.book_new();

    if (key === 'executive') {
      const ws1 = XLSX.utils.aoa_to_sheet(data.summary);
      ws1['!cols'] = [{ wch: 25 }, { wch: 15 }];
      XLSX.utils.book_append_sheet(wb, ws1, 'KPIs');
      if (data.alerts.length) {
        const alertData = [['Alert', 'Description', 'Status'], ...data.alerts];
        const ws2 = XLSX.utils.aoa_to_sheet(alertData);
        ws2['!cols'] = [{ wch: 30 }, { wch: 50 }, { wch: 15 }];
        XLSX.utils.book_append_sheet(wb, ws2, 'Alerts');
      }
    } else {
      const sheetData = [data.headers, ...data.rows];
      const ws = XLSX.utils.aoa_to_sheet(sheetData);
      ws['!cols'] = data.headers.map(() => ({ wch: 18 }));
      XLSX.utils.book_append_sheet(wb, ws, data.title.slice(0, 31));
    }

    const filename = data.title.toLowerCase().replace(/\s+/g, '-') + '-' + new Date().toISOString().slice(0, 10) + '.xlsx';
    XLSX.writeFile(wb, filename);
    toast(data.title + ' exported as Excel');
  } catch (e) {
    console.error('Excel generation error:', e);
    toast('Error generating Excel', 'err');
  }
}

function renderSettings(){
  document.getElementById('cfg-company').value=D.cfg.company||'';
  document.getElementById('cfg-dept').value=D.cfg.dept||'';
  document.getElementById('cfg-admin').value=D.cfg.admin||'';
  document.getElementById('cfg-logo').value=D.cfg.logo||'S';
  document.getElementById('cfg-max-inc').value=D.cfg.maxInc||4;
  document.getElementById('cfg-min-comp').value=D.cfg.minComp||90;
  document.getElementById('cfg-min-score').value=D.cfg.minScore||7.0;
  document.getElementById('cfg-alert-days').value=D.cfg.alertDays||30;
  const su=document.getElementById('cfg-sync-url');if(su)su.value=D.cfg.syncUrl||'';
  const sk=document.getElementById('cfg-sync-key');if(sk)sk.value=D.cfg.syncKey||'';
  // Sync backend fields
  const _b = D.cfg.syncBackend||'';
  const _bsel = document.getElementById('cfg-sync-backend');
  if(_bsel) _bsel.value = _b;
  ['sp-config','jsonbin-config','custom-config'].forEach(id=>{const el=document.getElementById(id);if(el)el.style.display='none';});
  if(_b==='firebase'){const el=document.getElementById('firebase-config');if(el)el.style.display='';}
  if(_b==='sharepoint'){const el=document.getElementById('sp-config');if(el)el.style.display='';}
  if(_b==='jsonbin')   {const el=document.getElementById('jsonbin-config');if(el)el.style.display='';}
  if(_b==='custom')    {const el=document.getElementById('custom-config');if(el)el.style.display='';}
  const _fld=(id,val)=>{const el=document.getElementById(id);if(el)el.value=val||'';};
  _fld('cfg-firebase-url',D.cfg.firebaseUrl);
  _fld('cfg-firebase-key',D.cfg.firebaseKey);
  _fld('cfg-sp-site',D.cfg.spSiteUrl);
  _fld('cfg-sp-list',D.cfg.spListName||'SafetyAppData');
  _fld('cfg-jsonbin-id',D.cfg.jsonbinId);
  _fld('cfg-jsonbin-key',D.cfg.jsonbinKey);
  _fld('cfg-sync-url',D.cfg.syncUrl);
  _fld('cfg-sync-key',D.cfg.syncKey);
  showSyncStatus(_b?'synced':'local');
}

// ═══════════════════════════════════════════════════
// AUTO ACTIONS
// ═══════════════════════════════════════════════════
function renderEditActions(){
  const list=document.getElementById('edit-actions-list');if(!list)return;
  list.innerHTML=(D.autoActions||[]).map((a,i)=>`<div style="background:var(--bg3);border-radius:var(--r);padding:10px;margin-bottom:8px;border:1px solid var(--border)">
    <div style="display:flex;align-items:center;gap:7px;margin-bottom:7px">
      <span class="badge ${a.active?'t':'r'}" style="cursor:pointer" onclick="D.autoActions[${i}].active=!D.autoActions[${i}].active;renderEditActions()">${a.active?'✓ Active':'✕ Inactive'}</span>
      <span style="font-size:9px;color:var(--text3);flex:1">${a.norm}</span>
      <button class="btn btn-r btn-sm" style="font-size:10px;padding:3px 7px" onclick="removeAction(${i})">✕</button>
    </div>
    <div style="display:flex;flex-direction:column;gap:6px">
      <div><div style="font-size:10px;color:var(--text3);margin-bottom:2px">Trigger</div><input class="fi" value="${a.trigger}" onchange="D.autoActions[${i}].trigger=this.value" style="font-size:12px"></div>
      <div><div style="font-size:10px;color:var(--text3);margin-bottom:2px">Action</div><input class="fi" value="${a.action}" onchange="D.autoActions[${i}].action=this.value" style="font-size:12px"></div>
      <div style="display:grid;grid-template-columns:1fr auto;gap:6px">
        <div><div style="font-size:10px;color:var(--text3);margin-bottom:2px">Standard</div><input class="fi" value="${a.norm}" onchange="D.autoActions[${i}].norm=this.value" style="font-size:11px"></div>
        <div><div style="font-size:10px;color:var(--text3);margin-bottom:2px">Color</div>
          <select class="fs" style="font-size:11px" onchange="D.autoActions[${i}].color=this.value">
            <option value="var(--red)" ${a.color==='var(--red)'?'selected':''}>🔴 Critical</option>
            <option value="var(--amber)" ${a.color==='var(--amber)'?'selected':''}>🟡 Warning</option>
            <option value="var(--blue)" ${a.color==='var(--blue)'?'selected':''}>🔵 Info</option>
            <option value="var(--teal)" ${a.color==='var(--teal)'?'selected':''}>🟢 OK</option>
          </select>
        </div>
      </div>
    </div>
  </div>`).join('')||'<div style="color:var(--text3);font-size:12px;padding:10px">No actions. Click + Add action.</div>';
}
function addAutoAction(){if(!D.autoActions)D.autoActions=[];D.autoActions.push({trigger:'New condition',action:'Action to define',norm:'ISO 45001:2018',color:'var(--amber)',active:true});renderEditActions();}
function removeAction(i){if(confirm('Remove this action?')){D.autoActions.splice(i,1);renderEditActions();}}
function saveAutoActions(){save();closeMo('mo-auto-actions');renderAutoActionsPreview();toast('Actions saved!');}

// ═══════════════════════════════════════════════════
// SAVE ACTIONS
// ═══════════════════════════════════════════════════
function saveDelivery(){
  if(!canEdit()){toast('No permission','warn');return;}
  const emp=document.getElementById('del-emp').value;
  const item=document.getElementById('del-item').value;
  const qty=parseInt(document.getElementById('del-qty').value)||1;
  const deliveryLoc=document.getElementById('del-location')?.value||'';
  if(!emp||!item){toast('Fill in employee and item','warn');return;}
  if(!deliveryLoc){toast('Select the delivery location','warn');return;}
  if(!assertCanEditLocation(deliveryLoc)){return;}
  const today=new Date().toLocaleDateString('en-ZA');
  const poRef=document.getElementById('del-po-ref')?.value?.trim()||'';
  const clothingSize=document.getElementById('del-size')?.value||'N/A';
  const shoeSize=document.getElementById('del-shoe-size')?.value||'';
  const delEmpObj=D.employees.find(e=>e.name===emp);
  const locName=D.locations.find(l=>l.id===deliveryLoc)?.name||deliveryLoc;
  D.deliveries.unshift({emp,item,qty,poRef,date:today,status:'Signed',unit:locName,locationId:deliveryLoc,clothingSize,shoeSize,notes:document.getElementById('del-notes')?.value||''});
  const pi=D.ppeItems.find(i=>i.name===item);
  if(pi){
    const prevStock=pi.stock;
    pi.stock=Math.max(0,pi.stock-qty);
    logActivity('STOCK','ppeItem',item,`Stock reduced: ${prevStock} → ${pi.stock} (delivery to ${emp})`);
  }
  logActivity('CREATE','delivery',`${item} → ${emp}`,`Qty: ${qty} | PO: ${poRef||'N/A'} | Clothing: ${clothingSize} | Shoe: ${shoeSize||'N/A'}`);
  D.logEntries.unshift({time:'Now',color:'var(--teal)',msg:`<b>Delivery</b> · ${item} × ${qty} → ${emp}`});
  save();closeMo('mo-delivery');renderAll();toast('Delivery registered!');
}

function savePpeItem(){
  if(!canEdit()){toast('No permission','warn');return;}
  const name=document.getElementById('item-name').value.trim();
  if(!name){toast('Enter item name','warn');return;}
  const itemLocation=document.getElementById('item-location')?.value||'';
  if(!itemLocation){toast('Select the location for this PPE item','warn');return;}
  if(!assertCanEditLocation(itemLocation)){return;}
  const itemInvoice=document.getElementById('item-invoice')?.value?.trim()||'';
  const clothingSizes=document.getElementById('item-clothing-sizes')?.value?.trim()||'';
  const shoeSizes=document.getElementById('item-shoe-sizes')?.value?.trim()||'';
  const locName=D.locations.find(l=>l.id===itemLocation)?.name||itemLocation;
  logActivity('CREATE','ppeItem',name,`New PPE item added — Location: ${locName}`);
  D.ppeItems.push({id:Date.now(),name,cat:document.getElementById('item-cat').value,stock:parseInt(document.getElementById('item-stock').value)||0,min:parseInt(document.getElementById('item-min').value)||10,exp:parseInt(document.getElementById('item-exp').value)||12,unit:document.getElementById('item-unit').value,invoice:itemInvoice,clothingSizes,shoeSizes,location:itemLocation,locationName:locName});
  document.getElementById('item-name').value='';save();closeMo('mo-item');renderAll();toast('Item added!');
}

function saveCorrAction(){
  if(!canEdit()){toast('No permission','warn');return;}
  const inc=document.getElementById('ca-inc').value;
  const action=document.getElementById('ca-action').value.trim();
  const resp=document.getElementById('ca-resp').value.trim();
  const due=document.getElementById('ca-due').value;
  const status=document.getElementById('ca-status').value;
  if(!inc){toast('Select an incident','warn');return;}
  if(!action){toast('Enter the corrective action','warn');return;}
  if(!resp){toast('Enter who is responsible','warn');return;}
  const dueFormatted=due?new Date(due).toLocaleDateString('en-ZA',{day:'2-digit',month:'short'}):'-';
  if(!D.corrActions) D.corrActions=[];
  const idx=D.corrActions.findIndex(a=>a.inc===inc&&a.action===action);
  if(idx>=0){
    D.corrActions[idx]={inc,action,resp,due:dueFormatted,status};
    logActivity('EDIT','corrAction',inc,`Corrective action updated — Resp: ${resp} | Due: ${dueFormatted}`);
    toast('Corrective action updated!');
  } else {
    D.corrActions.push({inc,action,resp,due:dueFormatted,status});
    logActivity('CREATE','corrAction',inc,`New corrective action — Resp: ${resp} | Due: ${dueFormatted} | Action: ${action}`);
    D.logEntries.unshift({time:'Now',color:'var(--blue)',msg:`<b>Corrective action</b> added · ${inc} · ${resp}`});
    toast('Corrective action added!');
  }
  // Clear form
  ['ca-action','ca-resp','ca-due'].forEach(id=>{const el=document.getElementById(id);if(el)el.value='';});
  const caS=document.getElementById('ca-status');if(caS)caS.value='Pending';
  save();
  renderIncidents();
  // Switch to corrective actions tab
  const tab=document.querySelector('#page-incidents .tab:nth-child(3)');
  if(tab) switchTab('inc-tab',2,tab);
}

function editCorrAction(idx){
  const a=D.corrActions[idx];if(!a)return;
  const caInc=document.getElementById('ca-inc');if(caInc)caInc.value=a.inc;
  const caAct=document.getElementById('ca-action');if(caAct)caAct.value=a.action;
  const caResp=document.getElementById('ca-resp');if(caResp)caResp.value=a.resp;
  const caStatus=document.getElementById('ca-status');if(caStatus)caStatus.value=a.status;
  // Switch to tab 2 where form is
  const tab=document.querySelector('#page-incidents .tab:nth-child(3)');
  if(tab) switchTab('inc-tab',2,tab);
  toast('Edit the form above and click Add');
}

function saveIncident(){
  if(!canEdit()){toast('No permission','warn');return;}
  const type=document.getElementById('inc-type').value;
  const sev=document.getElementById('inc-sev').value;
  const loc=document.getElementById('inc-loc').options[document.getElementById('inc-loc').selectedIndex]?.text||'';
  const status=document.getElementById('inc-status-sel').value;
  const desc=document.getElementById('inc-desc').value;
  if(!desc){toast('Fill in description','warn');return;}
  // Validate location — can only report for own location
  if(!canEdit()){toast('No permission to report incidents','warn');return;}
  const locId=document.getElementById('inc-loc').value;
  if(locAccess()!=='all'){
    const userLocName=(D.locations.find(l=>l.id===locAccess())||{}).name||locAccess().replace(/_/g,' ');
    if(loc&&!loc.toUpperCase().includes(userLocName.toUpperCase())&&locAccess()!=='all'){
      toast('You can only report incidents for your location: '+userLocName,'warn');return;
    }
  }
  const id=D.incidents.length+1;
  const code=`INC-${new Date().getFullYear()}-${String(id).padStart(3,'0')}`;
  D.incidents.unshift({id,code,type,loc,sev,status,date:new Date().toLocaleDateString('en-ZA')});
  D.kpis.inc=(D.kpis.inc||0)+1;
  // Always create alert requesting corrective action (manual)
  if(['High','Critical'].includes(sev)){
    D.alerts.unshift({type:'crit',icon:'⚠',cls:'r',
      title:`${code} — ${type} · Corrective action required`,
      sub:`Severity ${sev} · ${loc} · Go to Incidents → Corrective Actions to register the action`,
      badge:'Action needed',badgeCls:'r'});
  } else {
    D.alerts.unshift({type:'warn',icon:'📋',cls:'a',
      title:`${code} — Corrective action recommended`,
      sub:`${type} · ${loc} · Register a corrective action in the Incidents tab`,
      badge:'Recommended',badgeCls:'a'});
  }
  logActivity('CREATE','incident',code,`Severity ${sev} · ${loc} · Status: ${status}`);
  D.logEntries.unshift({time:'Now',color:'var(--red)',msg:`<b>${code}</b> registered · Severity ${sev} · ⚠ Corrective action required`});
  save();closeMo('mo-incident');renderAll();toast('Incident registered!');
}

function saveEval(){
  if(!canEdit()){toast('No permission','warn');return;}
  const emp=document.getElementById('eval-emp').value;
  const period=document.getElementById('eval-period').value;
  const inputs=document.querySelectorAll('#mo-eval .fi[type="number"]');
  let sum=0,cnt=0;inputs.forEach(i=>{const v=parseFloat(i.value);if(!isNaN(v)){sum+=v;cnt++;}});
  const score=cnt?parseFloat((sum/cnt).toFixed(1)):0;
  const empObj=D.employees.find(e=>e.name===emp);
  const loc=empObj?.unit||'--';
  const status=score>=8?'Approved':score>=D.cfg.minScore?'Under review':'Below target';
  D.evaluations.push({name:emp,loc,dept:empObj?.dept||'',score,period:period||'2025-Q2',status,feedback:document.getElementById('eval-fb').value});
  logActivity('CREATE','evaluation',emp,`Score: ${score} | Period: ${period||'N/A'} | Location: ${loc}`);
  if(score<D.cfg.minScore){D.logEntries.unshift({time:'Now',color:'var(--amber)',msg:`<b>Improvement plan</b> generated for ${emp} · Score: ${score}`});}
  save();closeMo('mo-eval');renderAll();toast(`Evaluation for ${emp} submitted!`);
}

function saveWarning(){
  if(!canEdit()){toast('No permission','warn');return;}
  const emp=document.getElementById('warn-emp').value;
  const type=document.getElementById('warn-type').value;
  const reason=document.getElementById('warn-reason').value.trim();
  if(!reason){toast('Fill in reason','warn');return;}
  const warnEmpObj=D.employees.find(e=>e.name===emp);
  D.warnings.push({emp,type,reason,date:new Date().toLocaleDateString('en-ZA'),status:'Pending signature',unit:warnEmpObj?.unit||''});
  logActivity('CREATE','warning',emp,`Type: ${type} | Reason: ${reason}`);
  save();closeMo('mo-warning');renderAll();toast(`Warning issued to ${emp}!`);
}

function saveEmployee(){
  if(!canEdit()){toast('No permission','warn');return;}
  const name=document.getElementById('emp-name').value.trim();
  if(!name){toast('Enter full name','warn');return;}
  const locEl=document.getElementById('emp-loc-sel');
  const unit=D.locations.find(l=>l.id===locEl.value)?.name||locEl.options[locEl.selectedIndex]?.text||'';
  D.employees.push({num:String(document.getElementById('emp-num').value||'0'),name,pos:document.getElementById('emp-pos').value,status:document.getElementById('emp-status').value,unit,region:document.getElementById('emp-region').value,dept:document.getElementById('emp-dept').value,gender:document.getElementById('emp-gender').value});
  logActivity('CREATE','employee',name,`Position: ${document.getElementById('emp-pos').value} | Location: ${unit}`);
  save();closeMo('mo-employee');renderEmployees();toast(`${name} registered!`);
}

function saveLocation(){
  const name=document.getElementById('loc-name-inp').value.trim();
  if(!name){toast('Enter location name','warn');return;}
  D.locations.push({id:name.toUpperCase().replace(/\s+/g,'_'),name,country:document.getElementById('loc-country-inp').value,region:document.getElementById('loc-region-inp').value,manager:document.getElementById('loc-manager-inp').value});
  logActivity('CREATE','location',name,`Country: ${document.getElementById('loc-country-inp').value} | Region: ${document.getElementById('loc-region-inp').value}`);
  save();closeMo('mo-location');renderLocPage();populateLoginLocSel();toast(`${name} added!`);
}

function removeLoc(i){
  requestDelete('location',i,D.locations[i].name);
}
function resolveAlert(i){D.alerts.splice(i,1);save();renderAlerts();renderKpis();toast('Alert resolved!');}

function saveCfg(){
  D.cfg.company=document.getElementById('cfg-company').value;
  D.cfg.dept=document.getElementById('cfg-dept').value;
  D.cfg.admin=document.getElementById('cfg-admin').value;
  D.cfg.logo=document.getElementById('cfg-logo').value||'S';
  D.cfg.maxInc=parseInt(document.getElementById('cfg-max-inc').value)||4;
  D.cfg.minComp=parseInt(document.getElementById('cfg-min-comp').value)||90;
  D.cfg.minScore=parseFloat(document.getElementById('cfg-min-score').value)||7.0;
  D.cfg.alertDays=parseInt(document.getElementById('cfg-alert-days').value)||30;
  const su=document.getElementById('cfg-sync-url');if(su)D.cfg.syncUrl=su.value.trim();
  const sk=document.getElementById('cfg-sync-key');if(sk)D.cfg.syncKey=sk.value.trim();
  const sb=document.getElementById('cfg-sync-backend');if(sb)D.cfg.syncBackend=sb.value;
  const spSite=document.getElementById('cfg-sp-site');if(spSite)D.cfg.spSiteUrl=spSite.value.trim();
  const spList=document.getElementById('cfg-sp-list');if(spList)D.cfg.spListName=spList.value.trim()||'SafetyAppData';
  const jbId=document.getElementById('cfg-jsonbin-id');if(jbId)D.cfg.jsonbinId=jbId.value.trim();
  const jbKey=document.getElementById('cfg-jsonbin-key');if(jbKey)D.cfg.jsonbinKey=jbKey.value.trim();
  logActivity('EDIT','settings','System settings',`Updated by ${SESSION?.display||'Admin'}`);
  save();updateSessionUI();
  if(D.cfg.syncBackend){startRemoteSync();startSSESync();}
}

function calcScore(){
  const inputs=document.querySelectorAll('#mo-eval .fi[type="number"]');
  let sum=0,cnt=0;inputs.forEach(i=>{const v=parseFloat(i.value);if(!isNaN(v)&&v>=0){sum+=v;cnt++;}});
  const avg=cnt?(sum/cnt).toFixed(1):'--';
  const el=document.getElementById('avg-score');
  if(el){el.textContent=avg;el.style.color=parseFloat(avg)>=7?'var(--teal)':parseFloat(avg)>=5?'var(--amber)':'var(--red)';}
}

function simDeviation(){
  D.simCount=(D.simCount||0)+1;D.kpis.inc=(D.kpis.inc||0)+3;
  D.alerts.unshift({type:'crit',icon:'⚡',cls:'r',title:`Simulated deviation #${D.simCount} — Maintenance`,sub:`Anomalous pattern detected · Deviation +${40+D.simCount*10}%`,badge:'Critical',badgeCls:'r'});
  D.logEntries.unshift({time:'Now',color:'var(--red)',msg:`<b>Deviation #${D.simCount}</b> detected · Automatic actions triggered`});
  save();renderAll();toast(`Deviation #${D.simCount} — actions triggered!`,'warn');
}

// ═══════════════════════════════════════════════════
// DELETE REQUEST SYSTEM
// ═══════════════════════════════════════════════════
let _editCtx = null; // {type, idx, data}

function requestDelete(type, idx, label) {
  // ONLY admin can delete directly — all others must request
  if (isAdmin()) {
    if (!confirm('Delete: ' + label + '?')) return;
    logActivity('DELETE', type, label, 'Deleted directly by administrator');
    executeDelete(type, idx);
    return;
  }
  // Non-admin: always submit approval request
  document.getElementById('del-req-type').value = type;
  document.getElementById('del-req-id').value = idx;
  document.getElementById('del-req-item').textContent = label;
  document.getElementById('del-req-reason').value = '';
  openMo('mo-del-request');
}

function submitDeleteRequest() {
  const type = document.getElementById('del-req-type').value;
  const idx  = parseInt(document.getElementById('del-req-id').value);
  const item = document.getElementById('del-req-item').textContent;
  const reason = document.getElementById('del-req-reason').value.trim();
  if (!reason) { toast('Please enter a reason for the request', 'warn'); return; }
  if (!D.deleteRequests) D.deleteRequests = [];
  const req = {
    id: Date.now(),
    type, idx, item, reason,
    requestedBy: SESSION.display,
    requestedByRole: SESSION.role,
    requestedByLocation: SESSION.locationAccess || 'all',
    requestedAt: new Date().toLocaleString('en-ZA'),
    status: 'Pending',
    decidedBy: null,
    decidedAt: null,
    decisionNote: null,
  };
  D.deleteRequests.push(req);
  logActivity('DELETE_REQUEST', type, item,
    `Deletion requested by ${SESSION.display} (${SESSION.role}) — Reason: ${reason}`);
  save();
  closeMo('mo-del-request');
  toast('Deletion request sent to Administrator!');
  D.logEntries.unshift({time:'Now',color:'var(--amber)',msg:`<b>Delete request</b> from ${SESSION.display} · ${item}`});
  renderLog();
}

function executeDelete(type, idx) {
  if (type === 'ppeItem') { D.ppeItems.splice(idx, 1); renderPpe(); }
  else if (type === 'delivery') { D.deliveries.splice(idx, 1); renderPpe(); }
  else if (type === 'po') { D.purchaseOrders.splice(idx, 1); renderPOTable(); }
  else if (type === 'incident') { D.incidents.splice(idx, 1); renderIncidents(); }
  else if (type === 'evaluation') { D.evaluations.splice(idx, 1); renderEvaluations(); }
  else if (type === 'warning') { D.warnings.splice(idx, 1); renderWarnings(); }
  else if (type === 'training') { D.trainings.splice(idx, 1); renderTrainings(); }
  else if (type === 'corrAction') { if(D.corrActions)D.corrActions.splice(idx, 1); renderIncidents(); }
  else if (type === 'employee') { D.employees.splice(idx, 1); renderEmployees(); }
  else if (type === 'location') { D.locations.splice(idx, 1); renderLocPage(); }
  else if (type === 'alert') { D.alerts.splice(idx, 1); renderAlerts(); renderKpis(); }
  save();
  toast('Record deleted!');
}

function renderDeleteRequests() {
  const list = document.getElementById('del-admin-list');
  if (!list) return;
  const pending = (D.deleteRequests || []).filter(r => r.status === 'Pending');
  const done = (D.deleteRequests || []).filter(r => r.status !== 'Pending').slice(0,20);
  if (!pending.length && !done.length) {
    list.innerHTML = '<div style="color:var(--text3);font-size:12px;padding:16px;text-align:center">No deletion requests</div>';
    return;
  }
  list.innerHTML =
    (pending.length ? `<div style="font-size:11px;font-weight:700;color:var(--amber);text-transform:uppercase;letter-spacing:.06em;margin-bottom:8px">⏳ Pending (${pending.length})</div>` : '') +
    pending.map((r) => `
      <div style="background:var(--bg3);border:1px solid rgba(255,170,0,.4);border-radius:var(--r);padding:13px;margin-bottom:10px">
        <div style="display:flex;align-items:center;gap:8px;margin-bottom:8px">
          <span class="badge a">Pending</span>
          <span style="font-size:11px;font-weight:600;color:var(--text)">${r.item}</span>
        </div>
        <div style="display:grid;grid-template-columns:1fr 1fr;gap:4px;margin-bottom:8px;font-size:11px;color:var(--text3)">
          <div>👤 <b style="color:var(--text2)">${r.requestedBy}</b> (${(r.requestedByRole||'').replace(/_/g,' ')})</div>
          <div>📍 ${(r.requestedByLocation||'all').replace(/_/g,' ')}</div>
          <div>🕐 ${r.requestedAt}</div>
          <div>📁 Type: ${r.type}</div>
        </div>
        <div style="background:var(--bg4);border-radius:6px;padding:8px 10px;margin-bottom:10px;font-size:11px;color:var(--text2);line-height:1.5">
          <b>Reason:</b> ${r.reason}
        </div>
        <div style="display:flex;gap:7px">
          <button class="btn btn-r btn-sm" onclick="approveDeleteRequest(${r.id})">✓ Approve deletion</button>
          <button class="btn btn-g btn-sm" onclick="rejectDeleteRequest(${r.id})">✕ Reject</button>
        </div>
      </div>`).join('') +
    (done.length ? `<div style="font-size:10px;font-weight:700;color:var(--text3);text-transform:uppercase;margin:14px 0 7px;letter-spacing:.06em">Resolved (${done.length})</div>` +
      done.map(r => `
        <div style="background:var(--bg3);border-radius:var(--r);padding:9px 12px;margin-bottom:6px;opacity:.75;font-size:11px">
          <span class="badge ${r.status==='Approved'?'r':'t'}">${r.status}</span>
          <span style="color:var(--text2);margin-left:8px">${r.item}</span>
          <span style="color:var(--text3);margin-left:8px">— ${r.requestedBy}</span>
          ${r.decidedBy ? `<span style="color:var(--text3)"> · decided by ${r.decidedBy} (${r.decidedAt})</span>` : ''}
        </div>`).join('') : '');
}

function approveDeleteRequest(reqId) {
  if (!isAdmin()) { toast('Only administrators can approve deletions', 'warn'); return; }
  const r = (D.deleteRequests||[]).find(x=>x.id===reqId);
  if (!r) return;
  r.status = 'Approved';
  r.decidedBy = SESSION.display;
  r.decidedAt = new Date().toLocaleString('en-ZA');
  logActivity('DELETE_APPROVED', r.type, r.item,
    `Approved by ${SESSION.display} — originally requested by ${r.requestedBy} (${r.requestedAt})`);
  executeDelete(r.type, r.idx);
  // Adjust pending indices for same type that come after this one
  D.deleteRequests.filter(x=>x.type===r.type&&x.idx>r.idx&&x.status==='Pending').forEach(x=>x.idx--);
  save(); renderDeleteRequests(); toast('Deletion approved and executed!');
}

function rejectDeleteRequest(reqId) {
  if (!isAdmin()) { toast('Only administrators can reject requests', 'warn'); return; }
  const r = (D.deleteRequests||[]).find(x=>x.id===reqId);
  if (!r) return;
  r.status = 'Rejected';
  r.decidedBy = SESSION.display;
  r.decidedAt = new Date().toLocaleString('en-ZA');
  logActivity('DELETE_REJECTED', r.type, r.item,
    `Rejected by ${SESSION.display} — originally requested by ${r.requestedBy}`);
  save(); renderDeleteRequests(); toast('Request rejected');
}

// ── EDIT RECORD ──────────────────────────────────────────────────────────────
function requestEdit(type, idx, data) {
  if (!canEdit()) { toast('No permission to edit', 'warn'); return; }
  _editCtx = {type, idx, data};
  const body = document.getElementById('edit-record-body');
  if (!body) return;

  let html = '';
  if (type === 'ppeItem') {
    const d = D.ppeItems[idx];
    html = fields([
      {id:'ei-name',label:'Item name',val:d.name},
      {id:'ei-cat',label:'Category',val:d.cat,type:'select',opts:['Head','Hands','Feet','Vision','Respiratory','Hearing','Fall','Body']},
      {id:'ei-stock',label:'Stock',val:d.stock,type:'number'},
      {id:'ei-min',label:'Minimum',val:d.min,type:'number'},
      {id:'ei-invoice',label:'Invoice No.',val:d.invoice||''},
      {id:'ei-clothing-sizes',label:'Clothing sizes',val:d.clothingSizes||''},
      {id:'ei-shoe-sizes',label:'Shoe/boot sizes',val:d.shoeSizes||''},
    ]);
  } else if (type === 'delivery') {
    const d = D.deliveries[idx];
    html = fields([
      {id:'ei-emp',label:'Employee',val:d.emp},
      {id:'ei-item',label:'Item',val:d.item},
      {id:'ei-qty',label:'Quantity',val:d.qty||1,type:'number'},
      {id:'ei-date',label:'Date',val:d.date},
      {id:'ei-po',label:'PO Reference',val:d.poRef||''},
      {id:'ei-clothing-size',label:'Clothing size',val:d.clothingSize||d.size||'',type:'select',opts:['XS','S','M','L','XL','XXL','N/A']},
      {id:'ei-shoe-size',label:'Shoe/boot size',val:d.shoeSize||''},
      {id:'ei-notes',label:'Notes',val:d.notes||''},
    ]);
  } else if (type === 'po') {
    const d = D.purchaseOrders[idx];
    html = fields([
      {id:'ei-po',label:'PO Number',val:d.po},
      {id:'ei-item',label:'Item',val:d.item},
      {id:'ei-qty',label:'Quantity',val:d.qty,type:'number'},
      {id:'ei-supplier',label:'Supplier',val:d.supplier||''},
      {id:'ei-invoice',label:'Invoice No.',val:d.invoice||''},
    ]);
  } else if (type === 'incident') {
    const d = D.incidents[idx];
    html = fields([
      {id:'ei-type',label:'Type',val:d.type},
      {id:'ei-loc',label:'Location',val:d.loc,type:'locationSelect'},
      {id:'ei-sev',label:'Severity',val:d.sev,type:'select',opts:['Low','Medium','High','Critical']},
      {id:'ei-status',label:'Status',val:d.status,type:'select',opts:['Open','Investigating','Pending Report','Corrective Action','Closed']},
      {id:'ei-date',label:'Date',val:d.date},
    ]);
  } else if (type === 'evaluation') {
    const d = D.evaluations[idx];
    html = fields([
      {id:'ei-name',label:'Employee',val:d.name},
      {id:'ei-loc',label:'Location',val:d.loc||'',type:'locationSelect'},
      {id:'ei-score',label:'Score (0-10)',val:d.score,type:'number'},
      {id:'ei-period',label:'Period',val:d.period||''},
      {id:'ei-status',label:'Status',val:d.status,type:'select',opts:['Approved','Under review','Below target']},
      {id:'ei-feedback',label:'Feedback',val:d.feedback||'',type:'textarea'},
    ]);
  } else if (type === 'warning') {
    const d = D.warnings[idx];
    html = fields([
      {id:'ei-emp',label:'Employee',val:d.emp},
      {id:'ei-type',label:'Type',val:d.type,type:'select',opts:['Verbal','Written','Suspension']},
      {id:'ei-reason',label:'Reason',val:d.reason},
      {id:'ei-status',label:'Status',val:d.status,type:'select',opts:['Pending signature','Signed']},
    ]);
  } else if (type === 'employee') {
    const d = D.employees[idx];
    html = fields([
      {id:'ei-name',label:'Full name',val:d.name},
      {id:'ei-num',label:'Employee #',val:d.num||''},
      {id:'ei-pos',label:'Position',val:d.pos||''},
      {id:'ei-unit',label:'Location',val:d.unit||'',type:'locationSelect'},
      {id:'ei-region',label:'Region',val:d.region||''},
      {id:'ei-dept',label:'Department',val:d.dept||''},
      {id:'ei-status',label:'Status',val:d.status||'Active',type:'select',opts:['Active','Vacation','Other','Maternity Leave']},
    ]);
  }

  document.getElementById('edit-record-body').innerHTML = '<div class="fg">' + html + '</div>';
  openMo('mo-edit-record');
}

function fields(arr) {
  return arr.map(f => {
    const full = f.type==='textarea' ? ' full' : '';
    let inp;
    if (f.type==='locationSelect') {
      inp = `<select class="fs" id="${f.id}" onchange="var l=D.locations.find(x=>x.name===this.value);var r=document.getElementById('ei-region');if(l&&r)r.value=l.region||'';">${D.locations.map(l=>`<option value="${l.name}" ${l.name===f.val?'selected':''}>${l.name}</option>`).join('')}</select>`;
    } else if (f.type==='select') {
      inp = `<select class="fs" id="${f.id}">${(f.opts||[]).map(o=>`<option ${o===f.val?'selected':''}>${o}</option>`).join('')}</select>`;
    } else if (f.type==='textarea') {
      inp = `<textarea class="ft" id="${f.id}" style="min-height:60px">${f.val||''}</textarea>`;
    } else {
      inp = `<input class="fi" id="${f.id}" type="${f.type||'text'}" value="${f.val||''}" ${f.type==='number'?'step="any"':''}>`;
    }
    return `<div class="fgr${full}"><div class="flbl">${f.label}</div>${inp}</div>`;
  }).join('');
}

function g(id){const el=document.getElementById(id);return el?el.value:null;}

function saveEditRecord() {
  if (!_editCtx) return;
  const {type, idx} = _editCtx;

  if (type === 'incident') {
    const d=D.incidents[idx];
    if(d.status==='Closed'&&!isAdmin()){toast('Closed incidents can only be edited by administrators','warn');return;}
  }
  if (type === 'evaluation') {
    const d=D.evaluations[idx];
    if(d.status==='Approved'&&!isAdmin()){toast('Approved evaluations can only be edited by administrators','warn');return;}
  }
  if (type === 'ppeItem') {
    const d=D.ppeItems[idx];
    d.name=g('ei-name')||d.name; d.cat=g('ei-cat')||d.cat;
    d.stock=parseFloat(g('ei-stock'))||d.stock; d.min=parseFloat(g('ei-min'))||d.min;
    d.invoice=g('ei-invoice')||'';
    d.clothingSizes=g('ei-clothing-sizes')||'';
    d.shoeSizes=g('ei-shoe-sizes')||'';
  } else if (type === 'delivery') {
    const d=D.deliveries[idx];
    d.emp=g('ei-emp')||d.emp; d.item=g('ei-item')||d.item;
    d.qty=parseFloat(g('ei-qty'))||d.qty; d.date=g('ei-date')||d.date;
    d.poRef=g('ei-po')||'';
    d.clothingSize=g('ei-clothing-size')||'';
    d.shoeSize=g('ei-shoe-size')||'';
    d.notes=g('ei-notes')||'';
  } else if (type === 'po') {
    const d=D.purchaseOrders[idx];
    d.po=g('ei-po')||d.po; d.item=g('ei-item')||d.item;
    d.qty=parseFloat(g('ei-qty'))||d.qty; d.supplier=g('ei-supplier')||''; d.invoice=g('ei-invoice')||'';
  } else if (type === 'incident') {
    const d=D.incidents[idx];
    d.type=g('ei-type')||d.type; d.loc=g('ei-loc')||d.loc;
    d.sev=g('ei-sev')||d.sev; d.status=g('ei-status')||d.status; d.date=g('ei-date')||d.date;
  } else if (type === 'evaluation') {
    const d=D.evaluations[idx];
    d.name=g('ei-name')||d.name; d.loc=g('ei-loc')||d.loc;
    d.score=parseFloat(g('ei-score'))||d.score; d.period=g('ei-period')||d.period;
    d.status=g('ei-status')||d.status; d.feedback=g('ei-feedback')||'';
  } else if (type === 'warning') {
    const d=D.warnings[idx];
    d.emp=g('ei-emp')||d.emp; d.type=g('ei-type')||d.type;
    d.reason=g('ei-reason')||d.reason; d.status=g('ei-status')||d.status;
  } else if (type === 'employee') {
    const d=D.employees[idx];
    d.name=g('ei-name')||d.name; d.num=g('ei-num')||d.num; d.pos=g('ei-pos')||d.pos;
    d.unit=g('ei-unit')||d.unit; d.region=g('ei-region')||d.region;
    d.dept=g('ei-dept')||d.dept; d.status=g('ei-status')||d.status;
  }
  logActivity('EDIT', _editCtx.type,
    document.getElementById('ei-name')?.value || document.getElementById('ei-emp')?.value || _editCtx.type,
    `Edited by ${SESSION?.display||'Unknown'}`);
  save();
  closeMo('mo-edit-record');
  renderAll();
  toast('Record updated!');
  _editCtx = null;
}

// ═══════════════════════════════════════════════════
// PPE DETAIL VIEW — stock, movements, history
// ═══════════════════════════════════════════════════
function openPpeDetail(idx) {
  const item = D.ppeItems[idx];
  if (!item) return;
  const body = document.getElementById('ppe-detail-body');
  if (!body) return;

  const sameNameItems = D.ppeItems.filter(i => i.name === item.name);
  const totalStockAllLocations = sameNameItems.reduce((a, i) => a + (i.stock || 0), 0);
  const totalMinAllLocations = sameNameItems.reduce((a, i) => a + (i.min || 0), 0);

  const deliveries = D.deliveries.filter(d => d.item === item.name);
  const totalDelivered = deliveries.reduce((a, d) => a + (d.qty || 1), 0);

  const empRecipients = {};
  deliveries.forEach(d => {
    if (!empRecipients[d.emp]) empRecipients[d.emp] = { qty: 0, dates: [] };
    empRecipients[d.emp].qty += (d.qty || 1);
    empRecipients[d.emp].dates.push(d.date);
  });
  const recipientRows = Object.entries(empRecipients)
    .sort((a, b) => b[1].qty - a[1].qty)
    .map(([name, info]) => `<tr><td>${name}</td><td>${info.qty}</td><td style="font-size:10px;color:var(--text3)">${info.dates.slice(-3).join(', ')}</td></tr>`)
    .join('');

  const deliveryHistoryRows = deliveries
    .map(d => `<tr>
      <td>${d.date}</td>
      <td>${d.emp}</td>
      <td>${d.qty || 1}</td>
      <td style="font-size:10px">${d.clothingSize || d.size || '--'}</td>
      <td style="font-size:10px">${d.shoeSize || '--'}</td>
      <td style="font-size:10px">${d.unit || '--'}</td>
      <td style="font-size:10px;color:var(--text3)">${d.poRef || '--'}</td>
      <td>${bSt(d.status)}</td>
    </tr>`).join('');

  const locationBreakdownRows = sameNameItems.length > 1
    ? sameNameItems.map(i => `<tr><td style="font-size:11px">${i.locationName || i.location || '--'}</td><td>${i.stock}</td><td>${i.min}</td><td>${i.stock <= 0 ? '<span class="badge r">Out</span>' : i.stock <= i.min ? '<span class="badge r">Low</span>' : '<span class="badge t">OK</span>'}</td></tr>`).join('')
    : '';

  const pos = (D.purchaseOrders || []).filter(p => p.item === item.name);
  const poRows = pos.map(p => `<tr><td style="font-family:monospace;font-size:11px">${p.po}</td><td>${p.qty}</td><td>${p.supplier || '--'}</td><td>${bSt(p.status)}</td></tr>`).join('');
  const logs = (D.activityLog || []).filter(e => e.label && (e.label.includes(item.name) || e.label === item.name)).slice(0, 20);
  const logRows = logs.map(l => `<div style="display:flex;gap:8px;padding:4px 0;border-bottom:1px solid var(--border);font-size:11px">
    <span style="color:var(--text3);min-width:80px">${l.timestamp}</span>
    <span style="font-weight:600">${l.action}</span>
    <span style="color:var(--text2)">${l.detail || ''}</span>
  </div>`).join('');
  const stockStatus = totalStockAllLocations <= 0 ? '<span class="badge r">Out of stock</span>' : totalStockAllLocations <= totalMinAllLocations ? '<span class="badge r">Below minimum</span>' : totalStockAllLocations <= totalMinAllLocations * 1.5 ? '<span class="badge a">Attention</span>' : '<span class="badge t">OK</span>';

  body.innerHTML = `
    <div style="display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:14px">
      <div class="card-sm" style="text-align:center"><div style="font-size:9px;color:var(--text3);margin-bottom:3px">TOTAL IN STOCK</div><div style="font-size:22px;font-weight:700;color:var(--teal)">${totalStockAllLocations}</div><div style="font-size:9px;color:var(--text3)">${sameNameItems.length > 1 ? sameNameItems.length + ' locations' : item.locationName || '--'}</div></div>
      <div class="card-sm" style="text-align:center"><div style="font-size:9px;color:var(--text3);margin-bottom:3px">TOTAL MINIMUM</div><div style="font-size:22px;font-weight:700;color:var(--amber)">${totalMinAllLocations}</div></div>
      <div class="card-sm" style="text-align:center"><div style="font-size:9px;color:var(--text3);margin-bottom:3px">TOTAL DELIVERED</div><div style="font-size:22px;font-weight:700;color:var(--blue)">${totalDelivered}</div><div style="font-size:9px;color:var(--text3)">${deliveries.length} deliveries</div></div>
      <div class="card-sm" style="text-align:center"><div style="font-size:9px;color:var(--text3);margin-bottom:3px">STATUS</div><div style="margin-top:4px">${stockStatus}</div></div>
    </div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px">
      <div class="card-sm"><b style="font-size:11px">Category:</b> <span style="font-size:11px">${item.cat}</span></div>
      <div class="card-sm"><b style="font-size:11px">Location:</b> <span style="font-size:11px">${item.locationName || item.location || '--'}</span></div>
      <div class="card-sm"><b style="font-size:11px">Clothing sizes:</b> <span style="font-size:11px">${item.clothingSizes || '--'}</span></div>
      <div class="card-sm"><b style="font-size:11px">Shoe/boot sizes:</b> <span style="font-size:11px">${item.shoeSizes || '--'}</span></div>
      <div class="card-sm"><b style="font-size:11px">Invoice:</b> <span style="font-size:11px">${item.invoice || '--'}</span></div>
      <div class="card-sm"><b style="font-size:11px">Validity:</b> <span style="font-size:11px">${item.exp || 12} months</span></div>
    </div>
    ${sameNameItems.length > 1 ? `<div class="st">Stock by location</div>
    <div class="tw"><table><thead><tr><th>Location</th><th>Stock</th><th>Min</th><th>Status</th></tr></thead><tbody>${locationBreakdownRows}</tbody></table></div>` : ''}
    <div class="st">Summary by employee (${Object.keys(empRecipients).length} recipients)</div>
    ${recipientRows ? `<div class="tw"><table><thead><tr><th>Employee</th><th>Total qty</th><th>Last dates</th></tr></thead><tbody>${recipientRows}</tbody></table></div>` : '<div style="color:var(--text3);font-size:12px;padding:8px">No deliveries recorded</div>'}
    <div class="st">Complete delivery history (${deliveries.length} records)</div>
    ${deliveryHistoryRows ? `<div class="tw" style="max-height:220px;overflow-y:auto"><table><thead><tr><th>Date</th><th>Employee</th><th>Qty</th><th>Clothing</th><th>Shoe</th><th>Location</th><th>PO Ref.</th><th>Status</th></tr></thead><tbody>${deliveryHistoryRows}</tbody></table></div>` : '<div style="color:var(--text3);font-size:12px;padding:8px">No deliveries recorded</div>'}
    <div class="st">Purchase orders</div>
    ${poRows ? `<div class="tw"><table><thead><tr><th>PO</th><th>Qty</th><th>Supplier</th><th>Status</th></tr></thead><tbody>${poRows}</tbody></table></div>` : '<div style="color:var(--text3);font-size:12px;padding:8px">No purchase orders</div>'}
    <div class="st">Change history</div>
    ${logRows || '<div style="color:var(--text3);font-size:12px;padding:8px">No history recorded</div>'}
  `;
  openMo('mo-ppe-detail');
}

// ═══════════════════════════════════════════════════
// GENERIC RECORD DETAIL VIEW
// ═══════════════════════════════════════════════════
function openRecordDetail(type, idx) {
  const title = document.getElementById('record-detail-title');
  const body = document.getElementById('record-detail-body');
  if (!title || !body) return;
  let html = '';

  if (type === 'delivery') {
    const d = D.deliveries[idx];
    if (!d) return;
    title.textContent = 'Delivery Detail';
    const logs = (D.activityLog || []).filter(e => e.detail && e.detail.includes(d.emp) && e.dataType === 'delivery').slice(0, 10);
    html = `
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px">
        <div class="card-sm"><b style="font-size:11px">Employee:</b> <span style="font-size:11px">${d.emp}</span></div>
        <div class="card-sm"><b style="font-size:11px">Item:</b> <span style="font-size:11px">${d.item}</span></div>
        <div class="card-sm"><b style="font-size:11px">Quantity:</b> <span style="font-size:11px">${d.qty || 1}</span></div>
        <div class="card-sm"><b style="font-size:11px">Date:</b> <span style="font-size:11px">${d.date}</span></div>
        <div class="card-sm"><b style="font-size:11px">Clothing size:</b> <span style="font-size:11px">${d.clothingSize || d.size || 'N/A'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Shoe/boot size:</b> <span style="font-size:11px">${d.shoeSize || 'N/A'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Location:</b> <span style="font-size:11px">${d.unit || '--'}</span></div>
        <div class="card-sm"><b style="font-size:11px">PO Ref:</b> <span style="font-size:11px">${d.poRef || '--'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Status:</b> <span style="font-size:11px">${d.status || '--'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Notes:</b> <span style="font-size:11px">${d.notes || '--'}</span></div>
      </div>
      ${logs.length ? '<div class="st">Activity log</div>' + logs.map(l => `<div style="font-size:11px;padding:4px 0;border-bottom:1px solid var(--border);color:var(--text2)">${l.timestamp} — ${l.action} — ${l.detail}</div>`).join('') : ''}`;
  } else if (type === 'incident') {
    const d = D.incidents[idx];
    if (!d) return;
    title.textContent = 'Incident Detail — ' + d.code;
    const cas = (D.corrActions || []).filter(a => a.inc === d.code);
    const logs = (D.activityLog || []).filter(e => e.label === d.code).slice(0, 10);
    html = `
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px">
        <div class="card-sm"><b style="font-size:11px">Code:</b> <span style="font-size:11px;font-family:monospace">${d.code}</span></div>
        <div class="card-sm"><b style="font-size:11px">Type:</b> <span style="font-size:11px">${d.type}</span></div>
        <div class="card-sm"><b style="font-size:11px">Location:</b> <span style="font-size:11px">${d.loc}</span></div>
        <div class="card-sm"><b style="font-size:11px">Severity:</b> ${bSev(d.sev)}</div>
        <div class="card-sm"><b style="font-size:11px">Status:</b> ${bSt(d.status)}</div>
        <div class="card-sm"><b style="font-size:11px">Date:</b> <span style="font-size:11px">${d.date}</span></div>
      </div>
      ${cas.length ? '<div class="st">Corrective actions</div><div class="tw"><table><thead><tr><th>Action</th><th>Responsible</th><th>Due</th><th>Status</th></tr></thead><tbody>' +
        cas.map(a => `<tr><td>${a.action}</td><td>${a.resp}</td><td>${a.due}</td><td>${bSt(a.status)}</td></tr>`).join('') + '</tbody></table></div>' : ''}
      ${logs.length ? '<div class="st">Activity log</div>' + logs.map(l => `<div style="font-size:11px;padding:4px 0;border-bottom:1px solid var(--border);color:var(--text2)">${l.timestamp} — ${l.action} — ${l.detail}</div>`).join('') : ''}`;
  } else if (type === 'employee') {
    const d = D.employees[idx];
    if (!d) return;
    title.textContent = 'Employee — ' + d.name;
    const empDeliveries = D.deliveries.filter(del => del.emp === d.name);
    const empEvals = D.evaluations.filter(e => e.name === d.name);
    const empWarns = D.warnings.filter(w => w.emp === d.name);
    const empTrains = D.trainings.filter(t => t.emp === d.name);
    html = `
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:14px">
        <div class="card-sm"><b style="font-size:11px">Name:</b> <span style="font-size:11px">${d.name}</span></div>
        <div class="card-sm"><b style="font-size:11px">#:</b> <span style="font-size:11px">${d.num || '--'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Position:</b> <span style="font-size:11px">${d.pos || '--'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Location:</b> <span style="font-size:11px">${d.unit || '--'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Department:</b> <span style="font-size:11px">${d.dept || '--'}</span></div>
        <div class="card-sm"><b style="font-size:11px">Status:</b> ${bSt(d.status || 'Active')}</div>
      </div>
      ${empDeliveries.length ? '<div class="st">PPE Deliveries (' + empDeliveries.length + ')</div><div class="tw"><table><thead><tr><th>Item</th><th>Qty</th><th>Size</th><th>Date</th></tr></thead><tbody>' +
        empDeliveries.slice(0, 20).map(del => `<tr><td>${del.item}</td><td>${del.qty || 1}</td><td>${del.clothingSize || del.size || '--'}${del.shoeSize ? ' / Boot:' + del.shoeSize : ''}</td><td>${del.date}</td></tr>`).join('') + '</tbody></table></div>' : ''}
      ${empEvals.length ? '<div class="st">Evaluations (' + empEvals.length + ')</div><div class="tw"><table><thead><tr><th>Period</th><th>Score</th><th>Status</th></tr></thead><tbody>' +
        empEvals.map(e => `<tr><td>${e.period || '--'}</td><td><b style="color:${e.score >= 8 ? 'var(--teal)' : e.score >= 7 ? 'var(--amber)' : 'var(--red)'}">${e.score}</b></td><td>${bSt(e.status)}</td></tr>`).join('') + '</tbody></table></div>' : ''}
      ${empWarns.length ? '<div class="st">Warnings (' + empWarns.length + ')</div><div class="tw"><table><thead><tr><th>Type</th><th>Reason</th><th>Date</th><th>Status</th></tr></thead><tbody>' +
        empWarns.map(w => `<tr><td>${w.type}</td><td>${w.reason}</td><td>${w.date}</td><td>${bSt(w.status)}</td></tr>`).join('') + '</tbody></table></div>' : ''}
      ${empTrains.length ? '<div class="st">Training (' + empTrains.length + ')</div><div class="tw"><table><thead><tr><th>Name</th><th>Standard</th><th>Expiry</th><th>Status</th></tr></thead><tbody>' +
        empTrains.map(t => `<tr><td>${t.name}</td><td>${t.nr}</td><td>${t.exp}</td><td>${bSt(t.status)}</td></tr>`).join('') + '</tbody></table></div>' : ''}`;
  }

  body.innerHTML = html;
  openMo('mo-record-detail');
}

function exportData(){const b=new Blob([JSON.stringify(D,null,2)],{type:'application/json'});const a=document.createElement('a');a.href=URL.createObjectURL(b);a.download=`safety-backup-${new Date().toISOString().slice(0,10)}.json`;a.click();toast('Backup exported!');}
function importData(){const inp=document.createElement('input');inp.type='file';inp.accept='.json';inp.onchange=e=>{const f=e.target.files[0];if(!f)return;const r=new FileReader();r.onload=ev=>{try{D=JSON.parse(ev.target.result);save();renderAll();toast('Data imported!');}catch{toast('Invalid file','err');}};r.readAsText(f);};inp.click();}
function resetData(){D=defaultData();save();renderAll();toast('System reset to defaults');}

// ═══════════════════════════════════════════════════
// CHARTS
// ═══════════════════════════════════════════════════
const CO={responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:{grid:{color:'rgba(255,255,255,.04)'},ticks:{color:'#4a5270',font:{size:9}}},y:{grid:{color:'rgba(255,255,255,.04)'},ticks:{color:'#4a5270',font:{size:9}},beginAtZero:true}}};
let charts={};

function destroyChart(id){if(charts[id]){try{charts[id].destroy();}catch(e){}delete charts[id];}}

function _emptyChart(id, msg) {
  const el = document.getElementById(id);
  if (!el) return;
  destroyChart(id);
  const ctx = el.getContext('2d');
  // Use parent dimensions when canvas itself has no size (hidden tab)
  const w = el.offsetWidth || el.parentElement?.offsetWidth || el.width || 200;
  const h = el.offsetHeight || el.parentElement?.offsetHeight || el.height || 120;
  el.width = w; el.height = h;
  ctx.clearRect(0, 0, w, h);
  ctx.fillStyle = '#4a5270';
  ctx.font = '11px -apple-system,BlinkMacSystemFont,sans-serif';
  ctx.textAlign = 'center';
  ctx.textBaseline = 'middle';
  ctx.fillText(msg || 'No data yet', w / 2, h / 2);
}

function _parseIncDate(dateStr) {
  if (!dateStr) return null;
  const parts = dateStr.split('/');
  if (parts.length < 2) return null;
  const yr = parseInt(parts[2]) || new Date().getFullYear();
  return new Date(yr, parseInt(parts[1]) - 1, parseInt(parts[0]));
}

function buildCharts(period) {
  period = period || '6m';
  const now = new Date();
  let labels = [], offsets = [];

  if (period === '1m') {
    labels = ['Week 1', 'Week 2', 'Week 3', 'Week 4'];
  } else if (period === '3m') {
    for (let i = 2; i >= 0; i--) {
      const d = new Date(now.getFullYear(), now.getMonth() - i, 1);
      labels.push(d.toLocaleString('en', {month: 'short'}));
      offsets.push(-i);
    }
  } else {
    for (let i = 5; i >= 0; i--) {
      const d = new Date(now.getFullYear(), now.getMonth() - i, 1);
      labels.push(d.toLocaleString('en', {month: 'short'}));
      offsets.push(-i);
    }
  }

  const locIncs = filterByLoc(D.incidents, 'loc');
  let incData;
  if (period === '1m') {
    incData = [0, 0, 0, 0];
    locIncs.forEach(inc => {
      const d = _parseIncDate(inc.date);
      if (!d) return;
      if (d.getMonth() === now.getMonth() && d.getFullYear() === now.getFullYear()) {
        incData[Math.min(3, Math.floor((d.getDate() - 1) / 7))]++;
      }
    });
  } else {
    incData = offsets.map(off => {
      const tgt = new Date(now.getFullYear(), now.getMonth() + off, 1);
      return locIncs.filter(inc => {
        const d = _parseIncDate(inc.date);
        return d && d.getMonth() === tgt.getMonth() && d.getFullYear() === tgt.getFullYear();
      }).length;
    });
  }

  ['c-inc','c-comp','c-ppe-kpi','c-train-kpi','c-perf-kpi','c-areas','c-rates'].forEach(destroyChart);

  // ── Incidents per period ─────────────────────
  const cInc = document.getElementById('c-inc');
  if (cInc) {
    charts['c-inc'] = new Chart(cInc, {type:'bar', data:{labels, datasets:[
      {label:'Incidents', data:incData, backgroundColor:'rgba(255,77,109,.7)', borderRadius:3, borderSkipped:false},
      {label:'Target', data:Array(labels.length).fill(D.cfg.maxInc||4), type:'line', borderColor:'#3a4560', borderDash:[4,3], borderWidth:1.5, pointRadius:0, fill:false}
    ]}, options:{...CO, scales:{...CO.scales, y:{...CO.scales.y, stepSize:1, beginAtZero:true}}}});
  }

  // ── Compliance by module ─────────────────────
  const locIncC = filterByLoc(D.incidents, 'loc');
  const locEvalC = filterByLoc(D.evaluations, 'loc');
  const ppeCom  = D.ppeItems.length ? Math.round((D.ppeItems.filter(i=>i.stock>i.min).length / D.ppeItems.length) * 100) : 100;
  const incCom  = locIncC.length   ? Math.round((locIncC.filter(i=>i.status==='Closed').length / locIncC.length) * 100)   : 100;
  const perfCom = locEvalC.length  ? Math.round((locEvalC.filter(e=>e.score>=7).length / locEvalC.length) * 100)          : 100;
  const compEl = document.getElementById('c-comp');
  if (compEl) {
    charts['c-comp'] = new Chart(compEl, {type:'bar', data:{labels:['PPE','Incidents','Performance'], datasets:[
      {label:'Current', data:[ppeCom, incCom, perfCom], backgroundColor:['rgba(0,212,160,.7)','rgba(77,159,255,.7)','rgba(157,125,255,.7)'], borderRadius:3},
      {label:'Target',  data:[90, 90, 70], backgroundColor:'rgba(58,69,96,.6)', borderRadius:3}
    ]}, options:{...CO, scales:{...CO.scales, y:{...CO.scales.y, min:0, max:100, ticks:{color:'#4a5270', font:{size:9}, callback:v=>v+'%'}}}}});
  }

  // ── PPE by category ──────────────────────────
  const cats = [...new Set(D.ppeItems.map(i=>i.cat))];
  const ppeEl = document.getElementById('c-ppe-kpi');
  if (ppeEl) {
    if (cats.length) {
      charts['c-ppe-kpi'] = new Chart(ppeEl, {type:'bar', data:{labels:cats, datasets:[
        {data:cats.map(cat=>D.ppeItems.filter(i=>i.cat===cat).reduce((a,i)=>a+i.stock,0)), backgroundColor:'rgba(0,212,160,.65)', borderRadius:3}
      ]}, options:{...CO, plugins:{legend:{display:false}}}});
    } else { _emptyChart('c-ppe-kpi', 'No PPE registered'); }
  }

  // ── Training status ──────────────────────────
  const locTrains = filterByLoc(D.trainings, 'unit');
  const tSt = ['Valid','Expiring 30d','Expired'];
  const tCt  = tSt.map(s => locTrains.filter(t=>t.status===s).length);
  const trainEl = document.getElementById('c-train-kpi');
  if (trainEl) {
    if (locTrains.length) {
      charts['c-train-kpi'] = new Chart(trainEl, {type:'doughnut', data:{labels:tSt, datasets:[
        {data:tCt, backgroundColor:['#00d4a0','#ffaa00','#ff4d6d'], borderWidth:0}
      ]}, options:{responsive:true, maintainAspectRatio:false, cutout:'60%', plugins:{legend:{display:false}}}});
    } else { _emptyChart('c-train-kpi', 'No training records'); }
  }

  // ── Performance distribution ─────────────────
  const bands = ['8-10','7-8','5-7','<5'];
  const locEvals = filterByLoc(D.evaluations, 'loc');
  const perfEl = document.getElementById('c-perf-kpi');
  if (perfEl) {
    if (locEvals.length) {
      charts['c-perf-kpi'] = new Chart(perfEl, {type:'bar', data:{labels:bands, datasets:[
        {data:bands.map((_,i2)=>locEvals.filter(e=>i2===0?e.score>=8:i2===1?e.score>=7&&e.score<8:i2===2?e.score>=5&&e.score<7:e.score<5).length),
         backgroundColor:['#00d4a0','#5dcaa5','#ffaa00','#ff4d6d'], borderRadius:3}
      ]}, options:{...CO}});
    } else { _emptyChart('c-perf-kpi', 'No evaluations yet'); }
  }

  // ── Incidents by location ────────────────────
  const incByLoc = {};
  filterByLoc(D.incidents, 'loc').forEach(i => { const l=i.loc||'Unknown'; incByLoc[l]=(incByLoc[l]||0)+1; });
  const areaColors  = ['#ff4d6d','#4d9fff','#9d7dff','#ffaa00','#00d4a0','#4a5270'];
  const areaLabels  = Object.keys(incByLoc);
  const areaData    = areaLabels.map(l=>incByLoc[l]);
  const areaColors2 = areaLabels.map((_,i)=>areaColors[i%areaColors.length]);
  const aEl  = document.getElementById('c-areas');
  const legEl = document.getElementById('areas-legend');
  if (aEl) {
    if (areaLabels.length) {
      charts['c-areas'] = new Chart(aEl, {type:'doughnut', data:{labels:areaLabels, datasets:[
        {data:areaData, backgroundColor:areaColors2, borderWidth:0}
      ]}, options:{responsive:true, maintainAspectRatio:false, cutout:'58%', plugins:{legend:{display:false}}}});
      if (legEl) legEl.innerHTML = areaLabels.map((l,i)=>`<span style="display:flex;align-items:center;gap:4px"><span style="width:8px;height:8px;border-radius:2px;background:${areaColors2[i]};flex-shrink:0"></span><span style="font-size:10px;color:var(--text2)">${l} ${areaData[i]}</span></span>`).join('');
    } else {
      _emptyChart('c-areas', 'No incidents yet');
      if (legEl) legEl.innerHTML = '<span style="font-size:10px;color:var(--text3)">No incidents yet</span>';
    }
  }

  // ── Frequency & Severity rates (from real data) ─
  const nEmp = Math.max(D.employees.length || 1, 1);
  const hoursWorked = nEmp * 220 * 8; // estimated hours per period
  const tf = incData.map(v => +(v / hoursWorked * 1e6).toFixed(2));
  const tg = incData.map(v => +(v * 30 / hoursWorked * 1e6).toFixed(2)); // assuming avg 30 lost days
  const ratesEl = document.getElementById('c-rates');
  if (ratesEl) {
    charts['c-rates'] = new Chart(ratesEl, {type:'line', data:{labels, datasets:[
      {label:'TF', data:tf, borderColor:'#ff4d6d', backgroundColor:'rgba(255,77,109,.07)', tension:.4, fill:true, pointRadius:3, borderWidth:2},
      {label:'TG', data:tg, borderColor:'#9d7dff', borderDash:[5,3], tension:.4, pointRadius:3, borderWidth:1.5}
    ]}, options:CO});
  }
}

function setPeriod(p,btn){document.querySelectorAll('.period-btn').forEach(b=>b.classList.remove('active'));btn.classList.add('active');buildCharts(p);}

function buildDeliveryCharts(){
  ['c-del-by-emp','c-del-by-loc','c-del-by-item'].forEach(destroyChart);
  const delivs = filterByLoc(D.deliveries,'unit');
  if (!delivs.length) {
    _emptyChart('c-del-by-emp','No deliveries yet');
    _emptyChart('c-del-by-loc','No deliveries yet');
    _emptyChart('c-del-by-item','No deliveries yet');
    return;
  }
  // By employee
  const empCounts={};delivs.forEach(d=>{empCounts[d.emp]=(empCounts[d.emp]||0)+(d.qty||1);});
  const sorted=Object.entries(empCounts).sort((a,b)=>b[1]-a[1]).slice(0,15);
  charts['c-del-by-emp']=new Chart(document.getElementById('c-del-by-emp'),{type:'bar',data:{labels:sorted.map(x=>x[0]),datasets:[{data:sorted.map(x=>x[1]),backgroundColor:'rgba(77,159,255,.7)',borderRadius:4}]},options:{...CO,indexAxis:'y',scales:{x:{...CO.scales.x},y:{...CO.scales.y,grid:{display:false},ticks:{color:'#8b92a8',font:{size:9}}}},plugins:{...CO.plugins,tooltip:{callbacks:{label:ctx=>` ${ctx.parsed.x} units`}}}},plugins:[{id:'barValues',afterDatasetsDraw(chart){const ctx=chart.ctx;chart.data.datasets.forEach((ds,di)=>{chart.getDatasetMeta(di).data.forEach((bar,i)=>{const v=ds.data[i];ctx.save();ctx.fillStyle='#c8cee0';ctx.font='bold 10px sans-serif';ctx.textAlign='left';ctx.textBaseline='middle';ctx.fillText(v,bar.x+5,bar.y);ctx.restore();});});}}]});
  // By location
  const locCounts={};delivs.forEach(d=>{const emp=D.employees.find(e=>e.name===d.emp);const loc=emp?.unit||'Unknown';locCounts[loc]=(locCounts[loc]||0)+(d.qty||1);});
  const lSorted=Object.entries(locCounts).sort((a,b)=>b[1]-a[1]);
  charts['c-del-by-loc']=new Chart(document.getElementById('c-del-by-loc'),{type:'doughnut',data:{labels:lSorted.map(x=>x[0]),datasets:[{data:lSorted.map(x=>x[1]),backgroundColor:['#00d4a0','#4d9fff','#9d7dff','#ffaa00','#ff4d6d','#5dcaa5'],borderWidth:0}]},options:{responsive:true,maintainAspectRatio:false,cutout:'55%',plugins:{legend:{display:true,position:'bottom',labels:{color:'#8b92a8',font:{size:9},boxWidth:8}}}}});
  // By item
  const itemCounts={};delivs.forEach(d=>{itemCounts[d.item]=(itemCounts[d.item]||0)+(d.qty||1);});
  const iSorted=Object.entries(itemCounts).sort((a,b)=>b[1]-a[1]);
  charts['c-del-by-item']=new Chart(document.getElementById('c-del-by-item'),{type:'bar',data:{labels:iSorted.map(x=>x[0]),datasets:[{data:iSorted.map(x=>x[1]),backgroundColor:'rgba(0,212,160,.7)',borderRadius:4}]},options:{...CO,scales:{...CO.scales,y:{...CO.scales.y,ticks:{color:'#4a5270',font:{size:9}}}}}});
}

function buildRegionalCharts(){
  ['c-regional-monthly','c-regional-quarterly'].forEach(destroyChart);
  const evals = filterByLoc(D.evaluations,'loc');
  const target = D.cfg.minScore || 7;
  if (!evals.length) {
    _emptyChart('c-regional-monthly','No evaluations yet');
    _emptyChart('c-regional-quarterly','No evaluations yet');
    renderRegionalTable();
    return;
  }
  const allPeriods=[...new Set(evals.map(e=>e.period||'').filter(Boolean))].sort();
  function avgFor(evArr,period){const pe=evArr.filter(e=>e.period===period);return pe.length?Math.round(pe.reduce((s,e)=>s+(e.score||0),0)/pe.length*10)/10:null;}
  // Monthly chart: last 6 periods
  const mPeriods=allPeriods.slice(-6);
  const mScores=mPeriods.map(p=>avgFor(evals,p));
  charts['c-regional-monthly']=new Chart(document.getElementById('c-regional-monthly'),{type:'line',data:{labels:mPeriods,datasets:[{label:'Regional score',data:mScores,borderColor:'#4d9fff',backgroundColor:'rgba(77,159,255,.08)',tension:.4,fill:true,pointRadius:3,borderWidth:2},{label:'Target',data:Array(mPeriods.length).fill(target),borderColor:'#3a4560',borderDash:[4,3],borderWidth:1.5,pointRadius:0}]},options:CO});
  // Quarterly chart: last 4 periods
  const qPeriods=allPeriods.slice(-4);
  const qScores=qPeriods.map(p=>avgFor(evals,p));
  charts['c-regional-quarterly']=new Chart(document.getElementById('c-regional-quarterly'),{type:'bar',data:{labels:qPeriods,datasets:[{label:'Score',data:qScores,backgroundColor:'rgba(0,212,160,.7)',borderRadius:4},{label:'Target',data:Array(qPeriods.length).fill(target),backgroundColor:'rgba(58,69,96,.5)',borderRadius:4}]},options:{...CO,scales:{...CO.scales,y:{...CO.scales.y,min:5,max:10}}}});
  renderRegionalTable();
}

function buildEmpCharts(emps) {
  ['c-emp-by-loc','c-emp-by-region'].forEach(id=>{ if(!document.getElementById(id))return; destroyChart(id); });
  if(!document.getElementById('c-emp-by-loc')) return;
  if(!emps.length){_emptyChart('c-emp-by-loc','No employees yet');_emptyChart('c-emp-by-region','No employees yet');return;}
  const locColors=['#00d4a0','#4d9fff','#9d7dff','#ffaa00','#ff4d6d','#5dcaa5','#7f77dd','#00a87d','#cc3355','#ffcc44','#4488ff','#bb66ff'];
  // By location
  const locCounts={};
  emps.forEach(e=>{const u=e.unit||'Unknown';locCounts[u]=(locCounts[u]||0)+1;});
  const locSorted=Object.entries(locCounts).sort((a,b)=>b[1]-a[1]).slice(0,12);
  charts['c-emp-by-loc']=new Chart(document.getElementById('c-emp-by-loc'),{
    type:'bar',
    data:{labels:locSorted.map(x=>x[0]),datasets:[{data:locSorted.map(x=>x[1]),backgroundColor:locColors,borderRadius:4}]},
    options:{...CO,plugins:{legend:{display:false}},scales:{...CO.scales,x:{...CO.scales.x,ticks:{color:'#8b92a8',font:{size:8},maxRotation:30}}}}
  });
  const regCounts={};
  emps.forEach(e=>{const r=e.region||'Unknown';regCounts[r]=(regCounts[r]||0)+1;});
  const regSorted=Object.entries(regCounts).sort((a,b)=>b[1]-a[1]);
  if(!regSorted.length){_emptyChart('c-emp-by-region','No region data');return;}
  charts['c-emp-by-region']=new Chart(document.getElementById('c-emp-by-region'),{
    type:'doughnut',
    data:{labels:regSorted.map(x=>x[0]),datasets:[{data:regSorted.map(x=>x[1]),backgroundColor:locColors,borderWidth:0,hoverOffset:6}]},
    options:{responsive:true,maintainAspectRatio:false,cutout:'55%',plugins:{legend:{display:true,position:'right',labels:{color:'#8b92a8',font:{size:9},boxWidth:9}}}}
  });
}

function buildLocChart(){
  destroyChart('c-loc-emp');
  if(!document.getElementById('c-loc-emp'))return;
  // Use normLoc for exact matching to avoid "Alrode" matching both T1 and NWL T1
  const empByLoc=D.locations.map(l=>{const n=D.employees.filter(e=>normLoc(e.unit)===normLoc(l.name)).length;return{name:l.name,count:n};}).filter(x=>x.count>0).sort((a,b)=>b.count-a.count);
  if(!empByLoc.length){_emptyChart('c-loc-emp','No employees assigned');return;}
  charts['c-loc-emp']=new Chart(document.getElementById('c-loc-emp'),{type:'bar',data:{labels:empByLoc.map(x=>x.name),datasets:[{data:empByLoc.map(x=>x.count),backgroundColor:'rgba(0,212,160,.7)',borderRadius:4}]},options:{...CO,indexAxis:'y',scales:{x:{...CO.scales.x},y:{...CO.scales.y,grid:{display:false},ticks:{color:'#8b92a8',font:{size:9}}}}}});
}

// ═══════════════════════════════════════════════════
// RENDER ALL
// ═══════════════════════════════════════════════════
function renderAll(){
  renderKpis();
  populatePpeLocFilter();
  renderPpe();
  renderIncidents();
  renderEvaluations();
  renderWarnings();
  renderTrainings();
  renderEmployees();
  renderAlerts();
  renderLog();
  renderDevMonitor();
  renderAutoActionsPreview();
  buildCharts('6m');
  populateLoginLocSel();
  if (document.getElementById('page-audit')?.classList.contains('active')) {
    filterAuditLog();
  }
}

function populatePpeLocFilter() {
  const lf = document.getElementById('ppe-loc-filter');
  if (!lf) return;
  const la = locAccess();
  const locs = la === 'all' ? D.locations : D.locations.filter(l => matchesLoc(l.name, la) || matchesLoc(l.id, la));
  lf.innerHTML = '<option value="">All locations</option>' + locs.map(l => `<option value="${l.name}">${l.name}</option>`).join('');
}

function populateLoginLocSel(){
  const sel=document.getElementById('login-loc-sel');if(!sel)return;
  const cur=sel.value;
  sel.innerHTML='<option value="">-- All locations --</option>'+D.locations.map(l=>`<option value="${l.id}">${l.name}</option>`).join('');
  if(cur)sel.value=cur;
}

// ═══════════════════════════════════════════════════
// PWA / APP INSTALL
// ═══════════════════════════════════════════════════
let deferredPrompt=null;
window.addEventListener('beforeinstallprompt',e=>{e.preventDefault();deferredPrompt=e;const b=document.getElementById('install-banner');b.style.display='flex';});
function installApp(){if(deferredPrompt){deferredPrompt.prompt();deferredPrompt.userChoice.then(()=>{deferredPrompt=null;document.getElementById('install-banner').style.display='none';});}}

// ═══════════════════════════════════════════════════
// INIT
// ═══════════════════════════════════════════════════
// ══════════════════════════════════════════════════════
// REAL-TIME SYNC — BroadcastChannel + StorageEvent
// Works across tabs, windows on same device.
// For cross-device sync: uses localStorage polling + 
// optional remote backend (configurable in Settings)
// ══════════════════════════════════════════════════════

// ═══════════════════════════════════════════════════
// ACTIVITY LOG — audit trail for critical actions
// ═══════════════════════════════════════════════════
function logActivity(action, dataType, label, detail) {
  if (!D.activityLog) D.activityLog = [];
  const entry = {
    id: Date.now(),
    action,           // 'EDIT' | 'DELETE' | 'DELETE_REQUEST' | 'DELETE_APPROVED' | 'DELETE_REJECTED' | 'LOGIN' | 'CREATE'
    dataType,         // 'ppeItem' | 'incident' | 'employee' etc.
    label:  label || '',
    detail: detail || '',
    user:   SESSION ? SESSION.display : 'System',
    role:   SESSION ? SESSION.role : '',
    location: SESSION ? (SESSION.locationAccess || 'all') : '',
    timestamp: new Date().toLocaleString('en-ZA'),
    ts: Date.now(),
  };
  D.activityLog.unshift(entry);
  // Keep last 500 entries
  if (D.activityLog.length > 500) D.activityLog = D.activityLog.slice(0, 500);
}

function filterAuditLog() {
  const actionF = document.getElementById('audit-filter-action')?.value || '';
  const userF   = document.getElementById('audit-filter-user')?.value || '';
  const logs = (D.activityLog || []);
  const base = isAdmin() ? logs : logs.filter(e => e.user === (SESSION?.display || ''));
  const filtered = base.filter(e =>
    (!actionF || e.action === actionF) &&
    (!userF   || e.user === userF)
  );
  const el = document.getElementById('activity-log-list');
  if (!el) return;
  if (!filtered.length) {
    el.innerHTML = '<div style="color:var(--text3);font-size:12px;padding:16px;text-align:center">No activity matches this filter</div>';
    return;
  }
  const colorMap = {
    DELETE:'var(--red)', DELETE_APPROVED:'var(--teal)', DELETE_REJECTED:'var(--amber)',
    DELETE_REQUEST:'var(--amber)', EDIT:'var(--blue)', CREATE:'var(--teal)', LOGIN:'var(--text3)',
    APPROVE:'var(--teal)', SECURITY:'var(--red)', STOCK:'var(--amber)',
  };
  el.innerHTML = filtered.map(e => `
    <div style="display:grid;grid-template-columns:120px 90px 1fr;gap:8px;padding:8px 0;border-bottom:1px solid var(--border);align-items:start;font-size:11px">
      <div>
        <div style="font-weight:700;color:${colorMap[e.action]||'var(--text2)'}">
          ${e.action.replace(/_/g,' ')}
        </div>
        <div style="color:var(--text3);font-size:10px;margin-top:2px;line-height:1.4">${e.timestamp}</div>
      </div>
      <div>
        <div style="color:var(--text2);font-weight:500">${e.user}</div>
        <div style="color:var(--text3);font-size:10px;margin-top:1px">${(e.role||'').replace(/_/g,' ')}</div>
        <div style="color:var(--text3);font-size:10px">${(e.location||'all').replace(/_/g,' ')}</div>
      </div>
      <div>
        <div style="color:var(--text);font-weight:600">${e.dataType||''}: ${e.label||'—'}</div>
        <div style="color:var(--text3);line-height:1.5;margin-top:2px">${e.detail||''}</div>
      </div>
    </div>`).join('');
}

function exportAuditLog() {
  const logs = isAdmin() ? (D.activityLog||[]) : (D.activityLog||[]).filter(e=>e.user===SESSION?.display);
  if (!logs.length) { toast('No activity to export', 'warn'); return; }
  const header = ['Timestamp','Action','Data type','Label','Detail','User','Role','Location'];
  const rows = logs.map(e => [
    e.timestamp, e.action, e.dataType, e.label, e.detail, e.user, e.role, e.location
  ].map(v => `"${(v||'').replace(/"/g,'""')}"`).join(','));
  const csv = [header.join(','), ...rows].join('\n');
  const blob = new Blob([csv], {type:'text/csv'});
  const a = document.createElement('a');
  a.href = URL.createObjectURL(blob);
  a.download = `activity-log-${new Date().toISOString().slice(0,10)}.csv`;
  a.click();
  toast('Activity log exported!');
}

function renderActivityLog() {
  const el = document.getElementById('activity-log-list');
  if (!el) return;
  const logs = (D.activityLog || []);
  // Filter: non-admin sees only their own actions
  const filtered = isAdmin()
    ? logs
    : logs.filter(e => e.user === (SESSION?.display || ''));

  if (!filtered.length) {
    el.innerHTML = '<div style="color:var(--text3);font-size:12px;padding:12px;text-align:center">No activity recorded yet</div>';
    return;
  }
  const colorMap = {
    DELETE:'var(--red)', DELETE_APPROVED:'var(--red)', DELETE_REJECTED:'var(--amber)',
    DELETE_REQUEST:'var(--amber)', EDIT:'var(--blue)', CREATE:'var(--teal)',
    LOGIN:'var(--text3)', APPROVE:'var(--teal)', SECURITY:'var(--red)', STOCK:'var(--amber)',
  };
  el.innerHTML = filtered.map(e => `
    <div style="display:grid;grid-template-columns:120px 90px 1fr;gap:8px;padding:8px 0;border-bottom:1px solid var(--border);align-items:start;font-size:11px">
      <div>
        <div style="font-weight:600;color:${colorMap[e.action]||'var(--text2)'}">
          ${e.action.replace(/_/g,' ')}
        </div>
        <div style="color:var(--text3);font-size:10px;margin-top:2px">${e.timestamp}</div>
      </div>
      <div>
        <div style="color:var(--text2)">${e.user}</div>
        <div style="color:var(--text3);font-size:10px">${e.role} · ${(e.location||'all').replace(/_/g,' ')}</div>
      </div>
      <div>
        <div style="color:var(--text);font-weight:600">${e.label||'—'}</div>
        <div style="color:var(--text3);line-height:1.4;margin-top:1px">${e.detail||''}</div>
      </div>
    </div>`).join('');
}

// ════════════════════════════════════════════════════════════════
// SYNC ENGINE — Multi-backend real-time synchronization
// ════════════════════════════════════════════════════════════════
// Supports 3 backends:
//   1. SharePoint Lists (Microsoft 365) — recommended for company
//   2. JSONBin.io — free, no server, any network
//   3. Custom REST endpoint
// Same-device sync via BroadcastChannel is always active.
// ════════════════════════════════════════════════════════════════
let syncChannel   = null;
let syncInterval  = null;
let lastSyncHash  = '';
let _isSyncing    = false;

function initSync() {
  // ── BroadcastChannel: instant sync between tabs on same browser ─
  if ('BroadcastChannel' in window) {
    syncChannel = new BroadcastChannel('safety_ms_v8');
    syncChannel.onmessage = (e) => {
      if (e.data?.type === 'DATA_UPDATE' && e.data.hash !== lastSyncHash) {
        try {
          const nd = JSON.parse(e.data.payload);
          lastSyncHash = e.data.hash;
          _mergeRemoteData(nd);
          renderAll();
          showSyncStatus('synced');
        } catch(err) {}
      }
    };
  }
  // ── StorageEvent: cross-tab fallback (same browser, same device) ─
  window.addEventListener('storage', (e) => {
    if (e.key === SK && e.newValue) {
      try {
        const nd = JSON.parse(e.newValue);
        if ((nd._ts||0) > (D._ts||0)) { _mergeRemoteData(nd); renderAll(); showSyncStatus('synced'); }
      } catch(err) {}
    }
  });
  // ── Start cloud sync if configured ──────────────────────────────
  const b = D.cfg?.syncBackend;
  if (b) startRemoteSync();
  showSyncStatus(b ? 'local' : 'local');
}

function _mergeRemoteData(remote) {
  // Merge remote data preserving local config and user passwords
  const localCfg   = { ...D.cfg };
  const localUsers  = D.users ? D.users.map(u=>({...u})) : [];
  D = { ...remote };
  // Always keep local sync config (backend creds must not be overwritten)
  D.cfg = { ...remote.cfg, ...localCfg };
  // Merge users: keep all users from both sides, local password wins
  if (!D.users) D.users = [];
  localUsers.forEach(lu => {
    const ri = D.users.findIndex(u => u.username === lu.username);
    if (ri < 0) D.users.push(lu);             // local user not in remote → add
    else D.users[ri].password = lu.password;  // local password wins
  });
  _saveLocal();
}

function showSyncStatus(state) {
  const col = {local:'var(--text3)',syncing:'var(--amber)',synced:'var(--teal)',error:'var(--red)'};
  const txt = {local:'local only',syncing:'syncing...',synced:'live ✓',error:'sync error'};
  ['sync-dot','sync-dot-s'].forEach(id=>{const el=document.getElementById(id);if(el)el.style.background=col[state]||col.local;});
  ['sync-label','sync-label-s'].forEach(id=>{const el=document.getElementById(id);if(el)el.textContent=txt[state]||txt.local;});
}

function startRemoteSync() {
  if (syncInterval) clearInterval(syncInterval);
  if (!D.cfg?.syncBackend) return;
  pullFromRemote();
  syncInterval = setInterval(pullFromRemote, 15000); // every 15 seconds
}

async function pullFromRemote() {
  if (!D.cfg?.syncBackend || _isSyncing) return;
  _isSyncing = true;
  showSyncStatus('syncing');
  try {
    let remote = null;
    const b = D.cfg.syncBackend;
    if      (b === 'firebase')   remote = await firebasePull();
    else if (b === 'sharepoint') remote = await spPull();
    else if (b === 'jsonbin')    remote = await jsonbinPull();
    else if (b === 'custom')     remote = await customPull();
    if (remote && (remote._ts||0) > (D._ts||0)) {
      _mergeRemoteData(remote);
      renderAll();
    }
    showSyncStatus('synced');
  } catch(e) {
    console.warn('Pull error:', e.message);
    showSyncStatus('error');
  } finally { _isSyncing = false; }
}

async function pushToRemote() {
  if (!D.cfg?.syncBackend) {
    toast('Configure cloud sync in Settings first', 'warn');
    return;
  }
  D._ts = Date.now();
  _saveLocal();
  showSyncStatus('syncing');
  try {
    const b = D.cfg.syncBackend;
    if      (b === 'firebase')   await firebasePush();
    else if (b === 'sharepoint') await spPush();
    else if (b === 'jsonbin')    await jsonbinPush();
    else if (b === 'custom')     await customPush();
    showSyncStatus('synced');
  } catch(e) {
    console.warn('Push error:', e.message);
    showSyncStatus('error');
    throw e;
  }
}

// ── SharePoint Lists (Microsoft 365) ─────────────────────────────
async function spGetDigest(site) {
  try {
    const r = await fetch(site+'/_api/contextinfo', {
      method:'POST', credentials:'include',
      headers:{'Accept':'application/json;odata=verbose','Content-Type':'application/json'}
    });
    const j = await r.json();
    return j.d?.GetContextWebInformation?.FormDigestValue || '';
  } catch(e) { return ''; }
}

async function spPull() {
  const site = (D.cfg.spSiteUrl||'').replace(/\/$/,'');
  const list = D.cfg.spListName || 'SafetyAppData';
  if (!site) throw new Error('SharePoint site URL not configured');
  const url = `${site}/_api/web/lists/getbytitle('${list}')/items?$filter=Title eq 'main'&$orderby=Modified desc&$top=1&$select=payload,ts`;
  const r = await fetch(url, {
    credentials:'include',
    headers:{'Accept':'application/json;odata=verbose'}
  });
  if (!r.ok) throw new Error(`SharePoint ${r.status}`);
  const j = await r.json();
  const items = j.d?.results || [];
  if (!items.length) return null;
  return JSON.parse(items[0].payload||'{}');
}

async function spPush() {
  const site = (D.cfg.spSiteUrl||'').replace(/\/$/,'');
  const list = D.cfg.spListName || 'SafetyAppData';
  if (!site) throw new Error('SharePoint site URL not configured');
  const digest = await spGetDigest(site);
  const typeName = list.replace(/\s/g,'')+'ListItem';
  const body = JSON.stringify({
    __metadata:{type:`SP.Data.${typeName}`},
    Title:'main',
    payload: JSON.stringify(D),
    ts: D._ts
  });
  // Check if record exists
  const check = await fetch(
    `${site}/_api/web/lists/getbytitle('${list}')/items?$filter=Title eq 'main'&$top=1&$select=Id`,
    {credentials:'include',headers:{'Accept':'application/json;odata=verbose'}}
  );
  const cj = await check.json();
  const existing = cj.d?.results?.[0];
  const baseHeaders = {
    'Accept':'application/json;odata=verbose',
    'Content-Type':'application/json;odata=verbose',
    'X-RequestDigest':digest
  };
  if (existing) {
    await fetch(`${site}/_api/web/lists/getbytitle('${list}')/items(${existing.Id})`,
      {method:'POST',credentials:'include',body,
       headers:{...baseHeaders,'X-HTTP-Method':'MERGE','IF-MATCH':'*'}});
  } else {
    await fetch(`${site}/_api/web/lists/getbytitle('${list}')/items`,
      {method:'POST',credentials:'include',body,headers:baseHeaders});
  }
}

// ── JSONBin.io ────────────────────────────────────────────────────
async function jsonbinPull() {
  const {jsonbinId:id,jsonbinKey:key} = D.cfg;
  if (!id) throw new Error('JSONBin ID not configured');
  const r = await fetch(`https://api.jsonbin.io/v3/b/${id}/latest`,{
    headers:{'X-Master-Key':key||'','X-Bin-Meta':'false'}
  });
  if (!r.ok) throw new Error(`JSONBin ${r.status}: ${await r.text()}`);
  const j = await r.json();
  // JSONBin wraps data in a record object sometimes
  return j.record || j;
}

async function jsonbinPush() {
  const {jsonbinId:id,jsonbinKey:key} = D.cfg;
  if (!id) throw new Error('JSONBin ID not configured');
  const r = await fetch(`https://api.jsonbin.io/v3/b/${id}`,{
    method:'PUT',
    headers:{'Content-Type':'application/json','X-Master-Key':key||'','X-Bin-Versioning':'false'},
    body: JSON.stringify(D)
  });
  if (!r.ok) throw new Error(`JSONBin push ${r.status}: ${await r.text()}`);
}


// ── Firebase Realtime Database ──────────────────────────────────
async function firebasePull() {
  const url = (D.cfg.firebaseUrl||'').replace(/\/$/, '');
  if (!url) throw new Error('Firebase URL not configured in Settings');
  const auth = D.cfg.firebaseKey ? '?auth='+D.cfg.firebaseKey : '';
  const r = await fetch(url+'/safetyapp.json'+auth, {headers:{'Accept':'application/json'}});
  if (r.status===401) throw new Error('Firebase: Unauthorized — use test mode or add secret key');
  if (r.status===404) throw new Error('Firebase: Database not found — check the URL');
  if (!r.ok) throw new Error('Firebase '+r.status+': '+(await r.text()));
  const data = await r.json();
  return data || null;
}

async function firebasePush() {
  const url = (D.cfg.firebaseUrl||'').replace(/\/$/, '');
  if (!url) throw new Error('Firebase URL not configured in Settings');
  const auth = D.cfg.firebaseKey ? '?auth='+D.cfg.firebaseKey : '';
  const r = await fetch(url+'/safetyapp.json'+auth, {
    method: 'PUT',
    headers: {'Content-Type':'application/json'},
    body: JSON.stringify(D)
  });
  if (!r.ok) throw new Error('Firebase push '+r.status+': '+(await r.text()).substring(0,200));
}

let _firebaseSSE = null;
function startFirebaseSSE() {
  if (_firebaseSSE) { try{_firebaseSSE.close();}catch(e){} _firebaseSSE=null; }
  const url = (D.cfg.firebaseUrl||'').replace(/\/$/, '');
  if (!url) return;
  const auth = D.cfg.firebaseKey ? '?auth='+D.cfg.firebaseKey : '';
  try {
    _firebaseSSE = new EventSource(url+'/safetyapp.json'+auth);
    _firebaseSSE.addEventListener('put', (e) => {
      try {
        const ev = JSON.parse(e.data);
        if (ev && ev.data && (ev.data._ts||0) > (D._ts||0)) {
          _mergeRemoteData(ev.data); renderAll(); showSyncStatus('synced');
        }
      } catch(err) {}
    });
    _firebaseSSE.onerror = () => showSyncStatus('error');
    showSyncStatus('synced');
  } catch(e) { console.warn('Firebase SSE:', e.message); }
}

// ── Custom REST endpoint ──────────────────────────────────────────
async function customPull() {
  const {syncUrl:url,syncKey:key} = D.cfg;
  if (!url) throw new Error('Sync URL not configured');
  const r = await fetch(url+'/get',{headers:{'X-Key':key||''}});
  if (!r.ok) throw new Error(`Custom pull ${r.status}`);
  const j = await r.json();
  return j.data || j;
}

async function customPush() {
  const {syncUrl:url,syncKey:key} = D.cfg;
  if (!url) throw new Error('Sync URL not configured');
  await fetch(url+'/set',{
    method:'POST',
    headers:{'Content-Type':'application/json','X-Key':key||''},
    body:JSON.stringify({data:D,ts:D._ts})
  });
}

// ── SSE sync (polling via startRemoteSync covers real-time needs) ─
function startSSESync() {}

// ── Backend switcher ──────────────────────────────────────────────
function syncBackendChanged() {
  const b = document.getElementById('cfg-sync-backend')?.value||'';
  ['sp-config','jsonbin-config','custom-config'].forEach(id=>{
    const el=document.getElementById(id); if(el)el.style.display='none';
  });
  if(b==='sharepoint'){const el=document.getElementById('sp-config');if(el)el.style.display='';}
  if(b==='jsonbin')   {const el=document.getElementById('jsonbin-config');if(el)el.style.display='';}
  if(b==='custom')    {const el=document.getElementById('custom-config');if(el)el.style.display='';}
  saveCfg();
}


window.addEventListener('load', async () => {
  // Migrate users — add locationAccess if missing
  if(D.users) D.users.forEach(u=>{if(!u.locationAccess)u.locationAccess='all';});

  // Quick access — only shown when admin username is typed
  const userInp=document.getElementById('login-user');
  const quick=document.getElementById('ll-quick');
  if(userInp&&quick){
    userInp.addEventListener('input',()=>{
      const u=D.users.find(x=>x.username.toLowerCase()===userInp.value.trim().toLowerCase());
      quick.style.display=(u&&u.role==='admin')?'block':'none';
    });
  }
  renderQuickUsers();
  initSync();

  // Cloud sync: start if configured (non-blocking)
  if (D.cfg?.syncBackend) {
    pullFromRemote().catch(e => console.warn('Pull skipped:', e.message));
    startRemoteSync();
  }

  populateLoginLocSel();

  // Try restore session AFTER sync (D now has current server data)
  try{
    const s=sessionStorage.getItem(SES_K);
    if(s){
      const saved=JSON.parse(s);
      const u=D.users.find(u=>u.username===saved.username);
      if(u){
        if(saved.locationAccess && saved.locationAccess !== 'all') {
          u._sessionLoc = saved.locationAccess;
        }
        startSession(u);return;
      }
    }
  }catch(e){}

  // Show login
  document.getElementById('login-screen').classList.remove('hidden');
});
</script>
</body>
</html>

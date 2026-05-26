index.html
├── <head> — meta tags, PWA manifest, redirect script
├── <style> — CSS completo (~400 linhas), dark theme, responsivo mobile
├── <body>
│   ├── #login-screen — ecrã de login
│   ├── #app
│   │   ├── #mob-header — header mobile com hamburger
│   │   ├── #sidebar — navegação lateral
│   │   └── #main — páginas do app
│   │       ├── #page-dashboard
│   │       ├── #page-ppe
│   │       ├── #page-incidents
│   │       ├── #page-performance
│   │       ├── #page-employees
│   │       ├── #page-locations
│   │       ├── #page-reports
│   │       ├── #page-settings
│   │       └── #page-audit
│   └── Modais (30+)
└── <script> — ~3700 linhas de JavaScript{
  cfg: {
    company, dept, admin, logo,
    maxInc, minComp, minScore, alertDays,
    syncBackend,     // 'firebase' | 'sharepoint' | 'jsonbin' | 'custom' | ''
    firebaseUrl,     // URL Firebase Realtime DB
    firebaseKey,     // chave secreta Firebase (opcional)
    spSiteUrl,       // URL site SharePoint
    spListName,      // nome da lista SP (default: SafetyAppData)
    jsonbinId,       // ID bin JSONBin
    jsonbinKey,      // master key JSONBin
    syncUrl,         // endpoint custom
    syncKey,
  },
  locations: [{ id, name, country, region }],   // 11 unidades
  users: [{ username, display, password, role, dept, locationAccess, color, email, status, createdAt, lastLogin }],
  employees: [...],   // 853 funcionários com campos: num, name, pos, status, unit, dept, region, gender
  ppeItems: [{ id, name, cat, stock, min, exp, unit, invoice, location, locationName }],
  deliveries: [{ emp, item, qty, poRef, date, status, unit, locationId }],
  purchaseOrders: [{ po, item, qty, supplier, invoice, stockUpdated, status, location, locationName }],
  incidents: [{ id, code, type, loc, sev, status, date }],
  corrActions: [{ inc, action, resp, due, status }],
  evaluations: [{ name, loc, dept, score, period, status, feedback }],
  warnings: [{ emp, type, reason, date, status, unit }],
  trainings: [{ emp, name, nr, exp, status, unit }],
  autoActions: [{ trigger, action, norm, color, active }],
  alerts: [{ type, icon, cls, title, sub, badge, badgeCls }],
  logEntries: [{ time, color, msg }],
  activityLog: [{ id, action, dataType, label, detail, user, role, location, timestamp, ts }],
  deleteRequests: [{ id, type, idx, item, reason, requestedBy, requestedByRole, requestedByLocation, requestedAt, status, decidedBy, decidedAt }],
  incidentChart: { '6m': {labels, data}, '3m': ..., '1m': ... },
  simCount: 0,
  _ts: timestamp
}const ROLE_PAGES = {
  admin:            todas as páginas + settings + audit
  regional_safety:  todas as páginas + audit (vê todas as localidades)
  safety_analyst:   dashboard, ppe, incidents, performance, employees, locations, reports, audit
  operator:         mesmo que safety_analyst
  viewer:           mesmo que safety_analyst
}
const CAN_EDIT = ['admin', 'regional_safety', 'safety_analyst', 'operator']
const NEEDS_LOC = ['safety_analyst', 'operator', 'viewer']  // obrigatório seleccionar localidade no login
const CAN_SEE_REGIONAL_KPI = ['admin', 'regional_safety']function normLoc(s)       // normaliza string (remove underscores, lowercase)
function matchesLoc(val, la)  // compara dois valores de localidade
function filterByLoc(arr, key)  // filtra array pela localidade do utilizador
function locAccess()      // retorna a localidade actual da sessão
function canViewLocation(locVal)
function assertCanEditLocation(locVal)  // valida permissão de escrita// Funções principais:
function initSync()           // inicializa BroadcastChannel + StorageEvent
function startRemoteSync()    // inicia polling 15s ou SSE Firebase
async function pullFromRemote()   // puxa dados do backend
async function pushToRemote()     // envia dados ao backend
function _mergeRemoteData(remote) // merge inteligente preservando config local e passwords

// Backends:
async function firebasePull() / firebasePush() / startFirebaseSSE()
async function spPull() / spPush() + spGetDigest() + spTestConnection()
async function jsonbinPull() / jsonbinPush()
async function customPull() / customPush()function hp(p)                // hash simples de password
function checkPass(u, input)  // compara plain text OU hash
function doLogin()            // valida credenciais + localidade obrigatória para NEEDS_LOC
function startSession(user)   // define SESSION, aplica classes CSS, renderiza UI
function doLogout()function requestDelete(type, idx, label)  // admin deleta / outros pedem aprovação
function submitDeleteRequest()
function approveDeleteRequest(reqId)
function rejectDeleteRequest(reqId)
function executeDelete(type, idx)function epInit(selId)          // inicializa picker com lista filtrada por localidade
function epFilter(selId, query) // filtra por nome em tempo real
function epFilterPos(selId, pos) // filtra por cargo
function epSelect(selId, name, pos) // selecciona e fecha dropdown
function epOpen(selId) / epClose(selId) / epKey(event, selId)function buildCharts(period)      // dashboard: incidentes, compliance, PPE, training, performance, áreas, taxas
function buildDeliveryCharts()    // PPE: por empregado, por localidade, por item
function buildRegionalCharts()    // Performance: mensal e trimestral
function buildLocChart()          // Locations: empregados por localidade
function buildEmpCharts(filtered) // Employees: por localidade e por regiãoHEAD OFFICE, ALRODE T1 BREWERY, ALRODE BREWERY, BARAGWANATH,
RUSTENBURG, MAFIKENG, POTCHEFSTROOM, WELKOM, KIMBERLEY,
HARTSWATER, NWL SERVICE

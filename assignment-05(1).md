
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>LCOE Versus an Electricity System</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.4/dist/chart.umd.min.js"></script>
<style>
:root{
  --ink:#16301f; --muted:#4f6657; --paper:#ffffff; --bg:#c9e9d3;
  --line:#c3dcc8; --forest:#0b3d2e; --leaf:#2e9e5b; --lime:#b9e37a; --sun:#f4c430; --sky:#3a9bd5; --earth:#9a6b3a;
  --accent:#2e9e5b; --accent-soft:#e3f4d6;
}
*{box-sizing:border-box}
body{margin:0;color:var(--ink);font-family:system-ui,-apple-system,"Segoe UI",Roboto,Arial,sans-serif;line-height:1.65;background:#c9e9d3}

/* hero */
.hero{position:relative;overflow:hidden;color:#fff;border-bottom:6px solid var(--lime);
  background:linear-gradient(160deg,#0b3d2e 0%,#17704a 55%,#2e9e5b 100%)}
.hero::after{content:"";position:absolute;right:-90px;top:-110px;width:380px;height:380px;border-radius:50%;
  background:radial-gradient(circle,rgba(244,196,48,.95) 0%,rgba(244,196,48,.35) 42%,rgba(244,196,48,0) 70%)}
.hero::before{content:"";position:absolute;left:-10%;right:-10%;bottom:-78px;height:130px;background:#0b3d2e;opacity:.5;
  border-radius:50% 50% 0 0 / 100% 100% 0 0}
.hero-inner{position:relative;z-index:1;max-width:900px;margin:auto;padding:60px 22px 56px}
h1,h2,h3{font-family:Georgia,"Times New Roman",serif;line-height:1.2}
.hero h1{font-size:50px;margin:0 0 16px;letter-spacing:-.01em;color:#fff;max-width:14em}
.subtitle{font-size:20px;color:#dff3e4;max-width:none;margin:0}

/* one centered column for everything */
main{max-width:900px;margin:auto;padding:36px 22px 50px}
h2{font-size:28px;margin:56px 0 14px;color:var(--forest);border-left:8px solid var(--leaf);padding-left:14px}
h3{font-size:19px;margin:0 0 8px}
p,ul,.note{max-width:none}

.question{font-size:21px;background:var(--lime);color:var(--forest);padding:20px 26px;margin:0 0 8px;
  box-shadow:6px 6px 0 var(--forest)}

.figure,.panel{background:var(--paper);border:1px solid var(--line);border-top:5px solid var(--leaf);padding:22px;margin:20px 0;
  box-shadow:0 8px 22px rgba(11,61,46,.09)}
.chartbox{position:relative;height:380px}
.chartbox.short{height:320px}
.note{font-size:14px;color:var(--muted);margin:12px 0 0}

.callout{background:var(--accent-soft);border:1px solid #bfe0a3;border-left:6px solid var(--leaf);padding:16px 20px;margin:20px 0}
#interpretation{background:#dff0fa;border-color:#abd5ec;border-left-color:var(--sky)}

/* stat blocks, color coded */
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:14px;margin:18px 0}
.stats.four{grid-template-columns:repeat(4,1fr)}
.stat{padding:16px 18px;background:var(--paper);border:1px solid var(--line);border-top:6px solid var(--leaf);box-shadow:0 6px 16px rgba(11,61,46,.07)}
.stat:nth-child(1){border-top-color:var(--sun)}
.stat:nth-child(2){border-top-color:var(--sky)}
.stat:nth-child(3){border-top-color:var(--leaf)}
.stat:nth-child(4){border-top-color:var(--earth)}
.stat .label{font-size:13px;color:var(--muted)}
.stat .value{font-family:Georgia,serif;font-size:26px;font-weight:700;margin-top:2px;color:var(--forest)}

/* controls */
.controls{display:flex;gap:18px 28px;align-items:end;flex-wrap:wrap;margin:10px 0 16px;background:var(--paper);border:1px solid var(--line);padding:16px 18px}
.controls label{display:flex;flex-direction:column;gap:4px;font-size:14px;font-weight:600;min-width:200px}
.controls output{font-weight:400;color:var(--muted)}
input[type=range]{width:100%;accent-color:var(--leaf)}
select,button,input[type=file]{font:inherit;padding:8px 14px}
select{border:1px solid var(--leaf);background:#fff}
button{background:var(--leaf);color:#fff;border:0;cursor:pointer;font-weight:600}
button:hover{background:var(--forest)}
:focus-visible{outline:3px solid var(--sun);outline-offset:2px}

table{width:100%;border-collapse:collapse;background:var(--paper);font-size:15px;box-shadow:0 6px 16px rgba(11,61,46,.07)}
th,td{border-bottom:1px solid var(--line);padding:10px 12px;text-align:left;vertical-align:top}
th{background:var(--forest);color:#fff}
tbody tr:nth-child(even){background:#f2faf3}

.two{display:grid;grid-template-columns:1fr 1fr;gap:20px}
.two>div{background:var(--paper);border:1px solid var(--line);padding:20px}
details{background:var(--paper);border:1px solid var(--line);border-left:6px solid var(--sky);padding:14px 20px;margin:16px 0}
summary{cursor:pointer;font-weight:700;color:var(--forest)}
.status{font-size:14px;color:var(--muted)}
.status.err{color:#9b1c1c;font-weight:600}
code{background:#e3f4d6;padding:1px 5px;font-size:.92em}
li{margin:5px 0}
a{color:#0f6a4a}

/* footer band */
.sitefooter{background:var(--forest);color:#bfe3c8;border-top:6px solid var(--lime);margin-top:30px;padding:30px 22px;font-size:14px}
.sitefooter div{max-width:900px;margin:auto}

@media(max-width:760px){
  .stats,.stats.four,.two{grid-template-columns:1fr}
  .hero h1{font-size:36px}
  .hero::after{width:240px;height:240px}
}
</style>
</head>

<body>

<header class="hero">
  <div class="hero-inner">
    <h1>LCOE Versus an Electricity System</h1>
    <p class="subtitle">
      What changes when we stop comparing the average cost of electricity technologies
      and start building a system that must meet real demand every hour?
    </p>
  </div>
</header>

<main>
<p class="question">
  <strong>The question:</strong> Does a low Levelized Cost of Electricity (LCOE)
  automatically mean a low-cost electricity system?
</p>

<!-- ============ 1 ============ -->
<section>
<h2>1. Start with LCOE</h2>
<p>
LCOE is the average cost of producing one megawatt-hour from a new power plant over its life.
Lazard's 2026 report gives a range for each technology; the diamond marks the midpoint.
Hover over a bar to see the numbers.
</p>
<div class="figure">
  <div class="chartbox short"><canvas id="lcoeChart" role="img" aria-label="Bar chart of Lazard 2026 LCOE ranges for solar, wind, and gas combined cycle"></canvas></div>
  <p class="note">Source: Lazard, Levelized Cost of Energy+ (July 2026), v19.0, unsubsidized, new-build.</p>
</div>
</section>

<!-- ============ 2 ============ -->
<section>
<h2>2. Now add real hourly demand</h2>
<p>
A system needs a different amount of electricity every hour. This is actual hourly demand for the AEP zone of the
PJM grid (parts of 13 states and Washington, D.C.). Move your mouse along the lines to read the values.
</p>

<div class="controls">
  <label for="year">Year shown
    <select id="year" disabled><option>Loading…</option></select>
  </label>
  <span id="loadStatus" class="status">Loading hourly data…</span>
</div>

<div id="loadFallback" hidden class="callout">
  <strong>The hourly data file was not found.</strong>
  Add <code>AEP_hourly.csv</code> to a <code>data</code> folder next to this page (see Sources),
  or load it from your computer to preview the page now:
  <br><br>
  <input type="file" id="fileInput" accept=".csv,text/csv" aria-label="Load AEP_hourly.csv from your computer">
</div>

<div class="stats">
  <div class="stat"><div class="label">Annual electricity demand</div><div id="annualMWh" class="value">—</div></div>
  <div class="stat"><div class="label">Average hourly demand</div><div id="avgMW" class="value">—</div></div>
  <div class="stat"><div class="label">Peak hourly demand</div><div id="peakMW" class="value">—</div></div>
</div>

<div class="figure">
  <div class="chartbox"><canvas id="dailyChart" role="img" aria-label="Line chart of daily average and daily peak electricity demand across the selected year"></canvas></div>
  <p class="note">Source: PJM hourly load, AEP zone (MW). Orange: highest hour of each day. Dark green: daily average.</p>
</div>
</section>

<!-- ============ 3 ============ -->
<section>
<h2>3. The hourly constraint</h2>
<p>
I compare two systems that serve this same demand: gas-only, and solar + wind + gas.
In every hour, supply must be at least as large as demand, so gas fills whatever solar and wind do not cover.
</p>

<div class="controls">
  <label for="weekSlider">Week of the year <output id="weekOut"></output>
    <input type="range" id="weekSlider" min="1" max="52" step="1" value="27">
  </label>
  <button type="button" id="peakWeekBtn">Jump to the annual peak week</button>
</div>

<div class="figure">
  <div class="chartbox"><canvas id="weekChart" role="img" aria-label="Line chart of hourly demand, available solar and wind, and gas needed for one week"></canvas></div>
  <p class="note">
    Solar and wind profiles are stylized (scaled to Lazard's PJM capacity factors: 18% solar, 30% wind), not measured output.
    Solar and wind sizes are set in section 4.
  </p>
</div>
</section>

<!-- ============ 4 ============ -->
<section>
<h2>4. What does each system cost?</h2>
<p>
Each system pays for what it needs: renewables for the capacity built, and gas for the capacity it must keep
plus the fuel it burns. Move the sliders to change the assumptions.
</p>

<div class="controls">
  <label for="solarCap">Solar capacity <output id="solarOut"></output>
    <input type="range" id="solarCap" min="0" max="150" step="5" value="50">
  </label>
  <label for="windCap">Wind capacity <output id="windOut"></output>
    <input type="range" id="windCap" min="0" max="150" step="5" value="50">
  </label>
  <label for="gasPrice">Natural gas price <output id="gasOut"></output>
    <input type="range" id="gasPrice" min="2" max="12" step="0.05" value="3.45">
  </label>
  <button type="button" id="resetBtn">Reset to defaults</button>
</div>

<div class="stats four">
  <div class="stat"><div class="label">Gas-only cost per MWh</div><div id="gasPerMWh" class="value">—</div></div>
  <div class="stat"><div class="label">Mixed-system cost per MWh</div><div id="mixPerMWh" class="value">—</div></div>
  <div class="stat"><div class="label">Gas capacity still needed</div><div id="gasCapacity" class="value">—</div></div>
  <div class="stat"><div class="label">Gas price where costs are equal</div><div id="breakeven" class="value">—</div></div>
</div>

<div class="figure">
  <div class="chartbox"><canvas id="systemChart" role="img" aria-label="Stacked bar chart comparing annual cost components of a gas-only system and a solar plus wind plus gas system"></canvas></div>
  <p class="note">Hover over any block for its cost; the footer shows the system total and cost per MWh.</p>
</div>

<p id="interpretation" class="callout">Loading the hourly model…</p>

<details>
<summary>How the costs are calculated</summary>
<ul>
<li><strong>Solar $138 and wind $219 per kW-year:</strong> Lazard's LCOE × capacity factor × 8.76, averaged over its low and high cases.</li>
<li><strong>Gas capacity $236 per kW-year:</strong> capital + fixed O&amp;M from Lazard's combined-cycle cost breakdown, averaged over low and high cases.</li>
<li><strong>Gas fuel and variable cost:</strong> 6.51 × gas price + $3.88 per MWh (Lazard's heat rate and variable O&amp;M; Lazard assumes $3.45/MMBtu).</li>
<li><strong>Capacity:</strong> gas-only keeps gas equal to peak demand; the mixed system keeps gas equal to the largest hourly gap solar and wind leave.</li>
</ul>
<p class="note">These conversions are my own arithmetic on Lazard's published figures, not numbers Lazard reports directly.</p>
</details>
</section>

<!-- ============ 5 ============ -->
<section>
<h2>5. So what changed?</h2>
<p>
LCOE asks: <strong>what does a megawatt-hour from this plant cost on average?</strong>
The hourly system asks: <strong>what does it cost to have enough electricity in every hour?</strong>
Here, wind and solar replace much of the gas <em>energy</em> but little gas <em>capacity</em>, so the remaining
gas plants run less often and their fixed costs are spread over fewer megawatt-hours.
Whether the mixed system is cheaper depends on assumptions such as the gas price. Try the slider.
</p>
<p>
This does not make LCOE wrong. Lazard itself says LCOE is not a total system-cost analysis, and its own
firming analysis for PJM adds roughly $37/MWh to solar and $16/MWh to wind.
A low LCOE is a necessary starting point, but it does not by itself tell you the cost of a system.
</p>
</section>

<!-- ============ 6 ============ -->
<section>
<h2>6. Limits to keep in mind</h2>
<div class="panel">
<ul>
<li><strong>Old demand, new costs:</strong> the hourly data end in 2018, while costs are Lazard's 2026 figures. This is an illustration, not a forecast.</li>
<li><strong>Stylized renewables:</strong> no multi-day cloudy or calm spells, which makes the model more favorable to renewables than reality.</li>
<li><strong>Not modeled:</strong> storage, transmission, reserve margins, existing plants, tax credits, and carbon prices.</li>
</ul>
</div>
</section>

<!-- ============ 7 ============ -->
<section>
<h2>7. Sources and how this was made</h2>
<div class="panel">
<p>
<strong>Costs:</strong> Lazard, <em>Levelized Cost of Energy+</em> (July 2026),
<a href="https://www.lazard.com/media/kcfconhf/lazards-lcoeplus_vf.pdf" target="_blank" rel="noopener">lazard.com (PDF)</a>;
ranges also reported by <a href="https://www.utilitydive.com/news/renewables-remain-cheapest-lcoe-rising-lazard/825443/" target="_blank" rel="noopener">Utility Dive</a>.
<br>
<strong>Hourly demand:</strong> PJM Interconnection, AEP zone (2004–2018), distributed in the Kaggle dataset
<a href="https://www.kaggle.com/datasets/robikscube/hourly-energy-consumption" target="_blank" rel="noopener">Hourly Energy Consumption</a>.
The page loads <code>data/AEP_hourly.csv</code> from this repository, or falls back to a public
<a href="https://github.com/BharatTupe/Energy-Demand-Forecasting" target="_blank" rel="noopener">GitHub copy</a> of the same file.
For newer years, see the <a href="https://www.eia.gov/electricity/gridmonitor/" target="_blank" rel="noopener">EIA Hourly Electric Grid Monitor</a>.
</p>
<p><strong>What I asked the AI to do:</strong></p>
<ul>
<li>Find and check Lazard's 2026 LCOE ranges and cost breakdowns.</li>
<li>Clean and sort the PJM hourly data.</li>
<li>Build the hourly solar + wind + gas model and the cost comparison.</li>
<li>Convert Lazard's costs into per-kW-year costs, and add sliders to test assumptions.</li>
</ul>
<p class="note">
Everything runs in your browser from the data file. View the page source to inspect or extend it;
the assumptions are listed at the top of the script.
</p>
</div>
</section>

<footer class="sitefooter">
  <div>
    ECON 238 — Environmental Economics · University of Rochester · Fall 2026<br>
    SHOW ME Project — LCOE Versus an Electricity System
  </div>
</footer>

<script>
/* ---------- Assumptions (all sourced from Lazard LCOE+ v19.0, July 2026) ---------- */
const A = {
  lcoe: { solar: 69, wind: 68, gas: 90 },
  lcoeRange: { solar: [40, 98], wind: [37, 99], gas: [51, 129] },
  solarCF: 0.18, windCF: 0.30,            // PJM capacity factors (firming analysis)
  solarKwYr: 138, windKwYr: 219,          // $/kW-year, derived from LCOE x CF (see page)
  gasFixedKwYr: 236,                      // $/kW-year, capital + fixed O&M for CCGT (see page)
  gasHeatRate: 6.51, gasVom: 3.88,        // MMBtu/MWh and $/MWh
  elcc: { solar: 0.12, wind: 0.38 }, netCone: 5.50   // PJM ELCC and Net CONE ($/kW-month)
};
const DEFAULTS = { solar: 50, wind: 50, gas: 3.45 };
const DATA_URL = "data/AEP_hourly.csv";
const MIRROR_URL = "https://raw.githubusercontent.com/BharatTupe/Energy-Demand-Forecasting/main/AEP_hourly.csv";

const $ = id => document.getElementById(id);
const state = { rows: [], year: null, yr: [], solarAv: [], windAv: [], peak: 0, annual: 0, res: null };
const charts = {};

const comma = x => Math.round(x).toLocaleString("en-US");
const mean = a => a.reduce((s, v) => s + v, 0) / (a.length || 1);
const usd = x => "$" + x.toFixed(0);

/* ---------- Chart helpers ---------- */
Chart.defaults.font.family = "system-ui, -apple-system, 'Segoe UI', Roboto, Arial, sans-serif";
Chart.defaults.color = "#3b4552";

const crosshair = {
  id: "crosshair",
  afterDatasetsDraw(chart) {
    const act = chart.tooltip && chart.tooltip.getActiveElements ? chart.tooltip.getActiveElements() : [];
    if (!act.length) return;
    const x = act[0].element.x, a = chart.chartArea, c = chart.ctx;
    c.save(); c.beginPath(); c.moveTo(x, a.top); c.lineTo(x, a.bottom);
    c.lineWidth = 1; c.strokeStyle = "rgba(29,39,51,.45)"; c.setLineDash([4, 3]); c.stroke(); c.restore();
  }
};

function draw(canvasId, cfg) {
  if (charts[canvasId]) charts[canvasId].destroy();
  cfg.options = cfg.options || {};
  cfg.options.animation = false;
  cfg.options.responsive = true;
  cfg.options.maintainAspectRatio = false;
  charts[canvasId] = new Chart($(canvasId), cfg);
}

function lineDataset(label, data, color, width) {
  return { label, data, borderColor: color, backgroundColor: color, borderWidth: width || 2,
           pointRadius: 0, pointHoverRadius: 5, pointHitRadius: 12, tension: 0.15 };
}

/* ---------- Section 1: LCOE chart ---------- */
function drawLCOE() {
  const labels = ["Utility solar PV", "Onshore wind", "Gas combined cycle"];
  draw("lcoeChart", {
    type: "bar",
    data: {
      labels,
      datasets: [
        { type: "bar", label: "Lazard range", data: [A.lcoeRange.solar, A.lcoeRange.wind, A.lcoeRange.gas],
          backgroundColor: ["rgba(217,154,0,.55)", "rgba(47,127,184,.55)", "rgba(107,114,128,.55)"],
          borderColor: ["#d99a00", "#2f7fb8", "#6b7280"], borderWidth: 1.5, borderSkipped: false, barPercentage: 0.5 },
        { type: "line", label: "Midpoint used here", data: [A.lcoe.solar, A.lcoe.wind, A.lcoe.gas], showLine: false,
          pointStyle: "rectRot", pointRadius: 9, pointHoverRadius: 11, backgroundColor: "#1d2733", borderColor: "#fff", borderWidth: 2 }
      ]
    },
    options: {
      interaction: { mode: "index", intersect: false },
      plugins: {
        legend: { position: "bottom" },
        tooltip: { callbacks: {
          label(c) {
            if (c.dataset.type === "line") return " Midpoint: $" + c.raw + "/MWh";
            return " Range: $" + c.raw[0] + " to $" + c.raw[1] + "/MWh";
          } } }
      },
      scales: { y: { beginAtZero: true, title: { display: true, text: "$ per MWh" } } }
    }
  });
}

/* ---------- Data loading ---------- */
function parseCSV(text) {
  const lines = text.split(/\r?\n/), out = [], seen = new Set();
  const re = /^(\d{4})-(\d{2})-(\d{2})[ T](\d{2}):(\d{2})/;
  for (let i = 1; i < lines.length; i++) {
    const line = lines[i]; if (!line) continue;
    const c = line.indexOf(","); if (c < 0) continue;
    const m = re.exec(line.slice(0, c)); const mw = parseFloat(line.slice(c + 1));
    if (!m || !Number.isFinite(mw)) continue;
    const y = +m[1], h = +m[4];
    const t = Date.UTC(y, +m[2] - 1, +m[3], h);
    if (seen.has(t)) continue;           // daylight-saving duplicate hours
    seen.add(t);
    out.push({ t, y, h, mw, dayIdx: Math.floor((t - Date.UTC(y, 0, 1)) / 86400000) });
  }
  out.sort((a, b) => a.t - b.t);         // the source file is not guaranteed to be in time order
  return out;
}

async function loadData() {
  const sources = [
    [DATA_URL, "data/AEP_hourly.csv in this repository"],
    [MIRROR_URL, "a public GitHub copy of PJM's AEP data (BharatTupe/Energy-Demand-Forecasting); add data/AEP_hourly.csv to this repository to use your own copy"]
  ];
  for (const [url, label] of sources) {
    try {
      const r = await fetch(url, { cache: "no-cache" });
      if (!r.ok) continue;
      init(parseCSV(await r.text()), label);
      return;
    } catch (e) { console.error(e); }
  }
  $("loadStatus").textContent = "Hourly data file not found.";
  $("loadStatus").classList.add("err");
  $("loadFallback").hidden = false;
  $("interpretation").textContent = "The hourly model will run as soon as the data file is loaded.";
}

function init(rows, sourceName) {
  if (rows.length < 20000) {
    $("loadStatus").textContent = "That file does not look like hourly data (" + rows.length + " valid rows). Expected columns: Datetime, AEP_MW.";
    $("loadStatus").classList.add("err");
    $("loadFallback").hidden = false;
    return;
  }
  state.rows = rows;
  const counts = {};
  rows.forEach(r => counts[r.y] = (counts[r.y] || 0) + 1);
  const years = Object.keys(counts).map(Number).filter(y => counts[y] >= 8000).sort();
  const sel = $("year");
  sel.innerHTML = "";
  years.forEach(y => { const o = document.createElement("option"); o.value = y; o.textContent = y; sel.appendChild(o); });
  sel.disabled = false;
  sel.value = years.includes(2017) ? 2017 : years[years.length - 1];
  $("loadStatus").classList.remove("err");
  $("loadStatus").textContent = rows.length.toLocaleString() + " hourly observations loaded from " + sourceName +
    " (years with a full 12 months: " + years[0] + "–" + years[years.length - 1] + ").";
  $("loadFallback").hidden = true;
  selectYear();
}

/* ---------- Stylized availability profiles ---------- */
function solarShape(doy, h) {
  if (h < 6 || h > 18) return 0;
  const day = Math.sin(Math.PI * (h - 6) / 12);
  const season = 0.55 + 0.45 * Math.cos(2 * Math.PI * (doy - 172) / 365);
  return Math.max(0, day * season);
}
function windShape(doy, h) {
  const season = 0.30 + 0.10 * Math.sin(2 * Math.PI * (doy + 35) / 365);
  const hourly = 0.07 * Math.sin(2 * Math.PI * (h + 3) / 24);
  return Math.max(0.08, Math.min(0.55, season + hourly));
}

function selectYear() {
  state.year = Number($("year").value);
  const yr = state.rows.filter(r => r.y === state.year);
  const sRaw = yr.map(r => solarShape(r.dayIdx + 1, r.h));
  const wRaw = yr.map(r => windShape(r.dayIdx + 1, r.h));
  const sScale = A.solarCF / mean(sRaw), wScale = A.windCF / mean(wRaw);   // so annual average = Lazard PJM capacity factor
  state.yr = yr;
  state.solarAv = sRaw.map(v => Math.min(1, v * sScale));
  state.windAv = wRaw.map(v => Math.min(1, v * wScale));
  state.peak = Math.max(...yr.map(r => r.mw));
  state.annual = yr.reduce((s, r) => s + r.mw, 0);

  $("annualMWh").textContent = (state.annual / 1e6).toFixed(1) + " million MWh";
  $("avgMW").textContent = comma(state.annual / yr.length) + " MW";
  $("peakMW").textContent = comma(state.peak) + " MW";

  const peakRow = yr.find(r => r.mw === state.peak);
  $("weekSlider").value = Math.min(52, Math.floor(peakRow.dayIdx / 7) + 1);
  state.peakWeek = Number($("weekSlider").value);

  drawDaily();
  renderModel();
}

/* ---------- Section 2: daily chart ---------- */
const dateLabel = (year, dayIdx) =>
  new Date(Date.UTC(year, 0, 1 + dayIdx)).toLocaleDateString("en-US", { month: "short", day: "numeric", timeZone: "UTC" });

function drawDaily() {
  const sum = [], max = [], cnt = [];
  state.yr.forEach(r => {
    sum[r.dayIdx] = (sum[r.dayIdx] || 0) + r.mw;
    max[r.dayIdx] = Math.max(max[r.dayIdx] || 0, r.mw);
    cnt[r.dayIdx] = (cnt[r.dayIdx] || 0) + 1;
  });
  const labels = [], avg = [], peak = [];
  for (let d = 0; d < cnt.length; d++) {
    if (!cnt[d]) continue;
    labels.push(dateLabel(state.year, d)); avg.push(sum[d] / cnt[d]); peak.push(max[d]);
  }
  draw("dailyChart", {
    type: "line",
    plugins: [crosshair],
    data: { labels, datasets: [
      lineDataset("Daily peak hour", peak, "#b4532a", 1.5),
      lineDataset("Daily average", avg, "#0b3d2e", 2.5)
    ] },
    options: {
      interaction: { mode: "index", intersect: false },
      plugins: {
        legend: { position: "bottom" },
        tooltip: { callbacks: { label: c => " " + c.dataset.label + ": " + comma(c.parsed.y) + " MW" } }
      },
      scales: {
        y: { title: { display: true, text: "Electricity demand (MW)" } },
        x: { ticks: { maxTicksLimit: 12, maxRotation: 0 } }
      }
    }
  });
}

/* ---------- Section 3 & 4: model ---------- */
function runModel() {
  const sc = Number($("solarCap").value) / 100, wc = Number($("windCap").value) / 100;
  const price = Number($("gasPrice").value);
  const sCap = sc * state.peak, wCap = wc * state.peak;
  const gasVar = A.gasHeatRate * price + A.gasVom;
  const n = state.yr.length;
  const sArr = new Array(n), wArr = new Array(n), gArr = new Array(n);
  let solarGen = 0, windGen = 0, gasGen = 0, curt = 0, delivered = 0, maxGas = 0;

  for (let i = 0; i < n; i++) {
    const mw = state.yr[i].mw;
    const s = sCap * state.solarAv[i], w = wCap * state.windAv[i], ren = s + w;
    const gas = Math.max(0, mw - ren);
    sArr[i] = s; wArr[i] = w; gArr[i] = gas;
    solarGen += s; windGen += w; gasGen += gas;
    curt += Math.max(0, ren - mw); delivered += Math.min(ren, mw);
    if (gas > maxGas) maxGas = gas;
  }

  const costs = {
    solar: sCap * A.solarKwYr * 1000,
    wind: wCap * A.windKwYr * 1000,
    gasCap: maxGas * A.gasFixedKwYr * 1000,
    gasEnergy: gasGen * gasVar
  };
  costs.total = costs.solar + costs.wind + costs.gasCap + costs.gasEnergy;
  const base = { gasCap: state.peak * A.gasFixedKwYr * 1000, gasEnergy: state.annual * gasVar };
  base.total = base.gasCap + base.gasEnergy;

  // Gas price at which both systems cost the same.
  const dE = state.annual - gasGen;
  let breakeven = null, alwaysLower = false;
  if (dE > 1) {
    const fixedMixed = costs.solar + costs.wind + costs.gasCap;
    const varNeeded = (fixedMixed - base.gasCap) / dE;      // $/MWh of gas variable cost where totals match
    const be = (varNeeded - A.gasVom) / A.gasHeatRate;
    if (be <= 0) alwaysLower = true; else breakeven = be;
  }
  return { sc, wc, price, sCap, wCap, gasVar, n, sArr, wArr, gArr, solarGen, windGen, gasGen, curt, delivered, maxGas, costs, base, breakeven, alwaysLower };
}

function renderModel() {
  if (!state.yr.length) return;
  const r = runModel();
  state.res = r;

  $("solarOut").textContent = Math.round(r.sc * 100) + "% of peak (" + comma(r.sCap) + " MW)";
  $("windOut").textContent = Math.round(r.wc * 100) + "% of peak (" + comma(r.wCap) + " MW)";
  $("gasOut").textContent = "$" + r.price.toFixed(2) + " per MMBtu";

  const A_ = state.annual;
  $("gasPerMWh").textContent = "$" + (r.base.total / A_).toFixed(0);
  $("mixPerMWh").textContent = "$" + (r.costs.total / A_).toFixed(0);
  $("gasCapacity").textContent = comma(r.maxGas) + " MW";
  $("breakeven").textContent = r.breakeven !== null ? "$" + r.breakeven.toFixed(2) : (r.alwaysLower ? "Mixed always lower" : "—");

  const diff = (r.costs.total / r.base.total - 1) * 100;
  let html;
  if (r.sc === 0 && r.wc === 0) {
    html = "<strong>What the model shows:</strong> With no solar or wind, the system is the gas-only system. Add some with the sliders above.";
  } else {
    html = "<strong>What the model shows:</strong> With solar at " + Math.round(r.sc * 100) + "% and wind at " + Math.round(r.wc * 100) +
      "% of peak demand, wind and solar supply about " + (100 * r.delivered / A_).toFixed(0) + "% of the year's energy, " +
      "yet the system still needs <strong>" + comma(r.maxGas) + " MW</strong> of gas capacity (" + (100 * r.maxGas / state.peak).toFixed(0) +
      "% of the gas-only requirement). The mixed system's annual cost is <strong>" + Math.abs(diff).toFixed(1) + "% " +
      (diff >= 0 ? "higher" : "lower") + "</strong> than gas-only ($" + (r.costs.total / A_).toFixed(0) + " vs. $" + (r.base.total / A_).toFixed(0) + " per MWh) under these assumptions.";
    if (r.breakeven !== null) html += " The two systems cost the same at a gas price of about $" + r.breakeven.toFixed(2) + " per MMBtu.";
    if (r.alwaysLower) html += " At these settings the mixed system is cheaper at any gas price.";
  }
  html += " This is an illustration, not a forecast.";
  $("interpretation").innerHTML = html;

  drawSystem(r);
  drawWeek();
}

function drawSystem(r) {
  const B = 1e9;
  draw("systemChart", {
    type: "bar",
    data: {
      labels: ["Gas-only", "Solar + wind + gas"],
      datasets: [
        { label: "Solar capacity", data: [0, r.costs.solar / B], backgroundColor: "#d99a00" },
        { label: "Wind capacity", data: [0, r.costs.wind / B], backgroundColor: "#2f7fb8" },
        { label: "Gas capacity (fixed costs)", data: [r.base.gasCap / B, r.costs.gasCap / B], backgroundColor: "#4b5563" },
        { label: "Gas fuel + variable O&M", data: [r.base.gasEnergy / B, r.costs.gasEnergy / B], backgroundColor: "#a3acb8" }
      ]
    },
    options: {
      interaction: { mode: "nearest", intersect: true },
      plugins: {
        legend: { position: "bottom" },
        tooltip: { callbacks: {
          label: c => " " + c.dataset.label + ": $" + c.parsed.y.toFixed(2) + " billion",
          footer: items => {
            const idx = items[0].dataIndex;
            const tot = idx === 0 ? r.base.total : r.costs.total;
            return "System total: $" + (tot / B).toFixed(2) + " billion ($" + (tot / state.annual).toFixed(0) + " per MWh)";
          } } }
      },
      scales: {
        x: { stacked: true },
        y: { stacked: true, beginAtZero: true, title: { display: true, text: "Annual cost ($ billions)" } }
      }
    }
  });
}

function drawWeek() {
  if (!state.res) return;
  const r = state.res, week = Number($("weekSlider").value);
  const d0 = (week - 1) * 7, d1 = d0 + 7;
  const labels = [], dayTicks = [], dem = [], sol = [], win = [], gas = [];
  for (let i = 0; i < state.yr.length; i++) {
    const row = state.yr[i];
    if (row.dayIdx < d0 || row.dayIdx >= d1) continue;
    labels.push(new Date(row.t).toLocaleString("en-US", { weekday: "short", month: "short", day: "numeric", hour: "numeric", timeZone: "UTC" }));
    dayTicks.push(row.h === 12 ? new Date(row.t).toLocaleDateString("en-US", { weekday: "short", month: "short", day: "numeric", timeZone: "UTC" }) : "");
    dem.push(row.mw); sol.push(r.sArr[i]); win.push(r.wArr[i]); gas.push(r.gArr[i]);
  }
  const end = Math.min(d1 - 1, 364);
  $("weekOut").textContent = "week " + week + " (" + dateLabel(state.year, d0) + " – " + dateLabel(state.year, end) + ")";

  draw("weekChart", {
    type: "line",
    plugins: [crosshair],
    data: { labels, datasets: [
      lineDataset("Actual demand", dem, "#0b3d2e", 3),
      lineDataset("Solar available", sol, "#d99a00", 2),
      lineDataset("Wind available", win, "#2f7fb8", 2),
      lineDataset("Gas needed after wind + solar", gas, "#6b7280", 2)
    ] },
    options: {
      interaction: { mode: "index", intersect: false },
      plugins: {
        legend: { position: "bottom" },
        tooltip: { callbacks: { label: c => " " + c.dataset.label + ": " + comma(c.parsed.y) + " MW" } }
      },
      scales: {
        y: { beginAtZero: true, title: { display: true, text: "MW" } },
        x: { ticks: { autoSkip: false, maxRotation: 0, callback: v => dayTicks[v] || "" }, grid: { display: false } }
      }
    }
  });
}

/* ---------- Events ---------- */
$("year").addEventListener("change", selectYear);
["solarCap", "windCap", "gasPrice"].forEach(id => $(id).addEventListener("input", renderModel));
$("weekSlider").addEventListener("input", drawWeek);
$("peakWeekBtn").addEventListener("click", () => { $("weekSlider").value = state.peakWeek || 27; drawWeek(); });
$("resetBtn").addEventListener("click", () => {
  $("solarCap").value = DEFAULTS.solar; $("windCap").value = DEFAULTS.wind; $("gasPrice").value = DEFAULTS.gas;
  renderModel();
});
$("fileInput").addEventListener("change", e => {
  const f = e.target.files[0]; if (!f) return;
  const rd = new FileReader();
  rd.onload = () => init(parseCSV(String(rd.result)), f.name + " (loaded from your computer)");
  rd.readAsText(f);
});

$("solarOut").textContent = ""; $("windOut").textContent = ""; $("gasOut").textContent = "";
drawLCOE();
loadData();
</script>

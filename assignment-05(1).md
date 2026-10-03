
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>LCOE Versus an Electricity System</title>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.4/dist/chart.umd.min.js"></script>
<style>
:root{
  --ink:#16301f; --muted:#4f6657; --paper:#ffffff; --bg:#eaf5ec;
  --line:#c3dcc8; --forest:#0b3d2e; --leaf:#2e9e5b; --lime:#b9e37a; --sun:#f4c430; --sky:#3a9bd5; --earth:#9a6b3a;
  --accent:#2e9e5b; --accent-soft:#e3f4d6;
}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:system-ui,-apple-system,"Segoe UI",Roboto,Arial,sans-serif;line-height:1.65}

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
Lazard's 2026 report (Version 19.0, July 2026) gives an unsubsidized range for each technology.
The bars below show those ranges; the diamond is the midpoint I use as a single comparison number.
Hover over a bar to see the values.
</p>

<div class="figure">
  <div class="chartbox short"><canvas id="lcoeChart" role="img" aria-label="Bar chart of Lazard 2026 LCOE ranges for solar, wind, and gas combined cycle"></canvas></div>
  <p class="note">
    Source: Lazard, Levelized Cost of Energy+ (July 2026), LCOE v19.0, unsubsidized, new-build.
    Midpoints are Lazard's reported averages ($69, $68, $90).
  </p>
</div>

<table>
<thead><tr><th>Technology</th><th>LCOE range ($/MWh)</th><th>Midpoint ($/MWh)</th><th>Capacity factor assumed by Lazard</th></tr></thead>
<tbody>
<tr><td>Utility solar PV</td><td>$40–$98</td><td>$69</td><td>30% (low case) to 20% (high case)</td></tr>
<tr><td>Onshore wind</td><td>$37–$99</td><td>$68</td><td>55% (low case) to 30% (high case)</td></tr>
<tr><td>Gas combined cycle</td><td>$51–$129</td><td>$90</td><td>90% (low case) to 30% (high case)</td></tr>
</tbody>
</table>
<p class="note">
Notice that each cost range depends heavily on how many hours the plant is assumed to run.
That is already a hint that "cost per MWh" is not a fixed property of a technology.
</p>
</section>

<!-- ============ 2 ============ -->
<section>
<h2>2. Now add actual hourly demand</h2>
<p>
An electricity system does not need one annual number; it needs a different amount every hour.
This exhibit uses hourly electricity demand for the AEP zone of the PJM Interconnection,
a regional grid operator that serves parts of 13 states and Washington, D.C.
The orange line shows the highest hour of each day; the dark green line shows the daily average.
Move your mouse along either line to read the exact values.
</p>

<div class="controls">
  <label for="year">Year shown
    <select id="year" disabled><option>Loading…</option></select>
  </label>
  <span id="loadStatus" class="status">Loading hourly data…</span>
</div>

<div id="loadFallback" hidden class="callout">
  <strong>The hourly data file was not found.</strong>
  Add <code>AEP_hourly.csv</code> to a <code>data</code> folder next to this page (see the Sources section),
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
  <p class="note">
    Source: PJM hourly load for the AEP zone (MW). Each point is one day; the model below uses all 8,760 hours.
  </p>
</div>
</section>

<!-- ============ 3 ============ -->
<section>
<h2>3. An hourly system has another constraint</h2>
<p>
To see the difference, I build a deliberately simple system with three resources: solar, wind, and gas.
Solar and wind produce according to a stylized hourly availability pattern; gas fills whatever demand is left.
If solar and wind produce more than demand, the surplus is wasted (curtailed).
</p>

<div class="callout">
  <strong>The hourly constraint:</strong> in every hour, solar + wind + gas must be at least as large as demand.
</div>

<div class="controls">
  <label for="weekSlider">Week of the year <output id="weekOut"></output>
    <input type="range" id="weekSlider" min="1" max="52" step="1" value="27">
  </label>
  <button type="button" id="peakWeekBtn">Jump to the week of the annual peak</button>
</div>

<div class="figure">
  <div class="chartbox"><canvas id="weekChart" role="img" aria-label="Line chart of hourly demand, available solar and wind, and gas needed for one week"></canvas></div>
  <p class="note">
    Hover to read all four values for any hour. The renewable profiles are stylized availability patterns
    (solar follows daylight and season; wind varies by season and hour), scaled to the capacity factors Lazard
    reports for PJM: 18% for solar, 30% for wind. They are not measured output from the AEP zone, and they contain no
    multi-day weather events, which makes this model <em>more</em> favorable to renewables than reality.
    Drag the slider to see how the gas gap changes by season. Solar and wind sizes are set in section 4.
  </p>
</div>
</section>

<!-- ============ 4 ============ -->
<section>
<h2>4. What happens to the system's cost?</h2>
<p>
Now compare two systems that serve the same hourly demand: <strong>gas-only</strong>, and
<strong>solar + wind + gas</strong>. The key difference from a plain LCOE comparison is that
every resource is charged for what it actually requires: renewables for the capacity built,
and gas for the capacity it must keep (to cover the hours when renewables fall short) plus the fuel it burns.
Use the sliders to change the assumptions.
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
  <p class="note">Hover over any block to see its cost; the footer shows the system total and cost per MWh delivered.</p>
</div>

<div class="stats four">
  <div class="stat"><div class="label">Share of energy from wind + solar</div><div id="renShare" class="value">—</div></div>
  <div class="stat"><div class="label">Energy wasted (curtailed)</div><div id="curtShare" class="value">—</div></div>
  <div class="stat"><div class="label">Gas fleet utilization, gas-only</div><div id="utilGas" class="value">—</div></div>
  <div class="stat"><div class="label">Gas fleet utilization, mixed</div><div id="utilMix" class="value">—</div></div>
</div>

<p id="interpretation" class="callout">Loading the hourly model…</p>

<details>
<summary>How the costs are calculated (and where each number comes from)</summary>
<table style="margin-top:12px">
<thead><tr><th>Item</th><th>How it is charged</th><th>Value used</th><th>Derivation from Lazard v19.0</th></tr></thead>
<tbody>
<tr><td>Solar</td><td>Per kW of capacity built</td><td>$138 per kW-year</td>
<td>LCOE × capacity factor × 8.76, averaged over the low and high cases:
$40 × 30% × 8.76 ≈ $105 and $98 × 20% × 8.76 ≈ $172.</td></tr>
<tr><td>Wind</td><td>Per kW of capacity built</td><td>$219 per kW-year</td>
<td>$37 × 55% × 8.76 ≈ $178 and $99 × 30% × 8.76 ≈ $260.</td></tr>
<tr><td>Gas capacity</td><td>Per kW of capacity kept</td><td>$236 per kW-year</td>
<td>Capital + fixed O&amp;M from Lazard's gas combined-cycle cost breakdown:
low case $25 + $1 = $26/MWh at 90% capacity factor ≈ $205; high case $92 + $10 = $102/MWh at 30% ≈ $268.</td></tr>
<tr><td>Gas energy</td><td>Per MWh actually generated</td><td>6.51 × gas price + $3.88</td>
<td>Average heat rate of 6,475 and 6,550 Btu/kWh, and average variable O&amp;M of $2.75 and $5.00/MWh.
Lazard's own gas price assumption is $3.45/MMBtu.</td></tr>
</tbody>
</table>
<p class="note">
Capacity is sized as a percentage of the selected year's peak demand. The gas-only system keeps gas capacity equal to peak demand.
The mixed system keeps gas capacity equal to the largest hourly gap that solar and wind leave in the modeled year.
Both systems ignore reserve margins, transmission, storage, outages, and plant retirements.
The conversions above are my own arithmetic on Lazard's published figures, not numbers Lazard reports directly.
</p>
</details>
</section>

<!-- ============ 5 ============ -->
<section>
<h2>5. A cross-check using Lazard's own firming analysis</h2>
<p>
Lazard's 2026 report also includes a "Cost of Firming Intermittency" analysis, which adds the cost of the backup capacity
a wind or solar plant needs in order to count as reliable capacity in a given grid. For PJM, the grid operator
credits new solar with 12% and new wind with 38% of their nameplate capacity at times of peak demand
(a measure called ELCC), and values new firm capacity at $5.50 per kW-month (Net CONE).
Applying Lazard's published formula with those PJM numbers and capacity factors of 18% (solar) and 30% (wind) gives:
</p>

<div class="figure">
  <div class="chartbox short"><canvas id="firmChart" role="img" aria-label="Stacked bar chart of LCOE midpoint plus PJM firming cost for solar and wind, versus gas combined cycle"></canvas></div>
  <p class="note" id="firmNote"></p>
</div>
</section>

<!-- ============ 6 ============ -->
<section>
<h2>6. So what changed?</h2>
<p>
The LCOE comparison asks a technology-level question:
<strong>what does a megawatt-hour from this plant cost on average?</strong>
The hourly system asks a different question:
<strong>what does it cost to have enough electricity at the exact hours it is needed?</strong>
</p>
<p>
In this model, wind and solar replace a lot of gas <em>energy</em> but very little gas <em>capacity</em>,
because the hours when they produce least still have to be covered. The gas plants that remain
are used less often, so their fixed costs are spread over fewer megawatt-hours.
Whether the mixed system is cheaper then depends on how expensive the avoided fuel is
(try the gas price slider), how much firm capacity the renewables can replace, and how the load is shaped.
</p>
<p>
This does not mean LCOE is useless or that renewables are a bad deal. Lazard itself states that LCOE is
"a cost-focused benchmarking tool, and not a planning tool or total system-cost analysis," and that it does not say
what the optimal mix of resources is. The point of this exhibit is narrower:
a low LCOE is a necessary starting point for comparing technologies, but it does not by itself tell you the cost of a system.
</p>
</section>

<!-- ============ 7 ============ -->
<section>
<h2>7. Assumptions and limitations</h2>
<div class="panel">
<ul>
<li><strong>Demand data end in 2018.</strong> The hourly series covers 2004–2018 and I use full calendar years only. Combining 2007–2017 demand with 2026 costs is an illustration, not a forecast; demand growth from data centers is not captured.</li>
<li><strong>Costs:</strong> Lazard's 2026 unsubsidized, new-build figures. Federal tax credits are not included, and costs vary by project and region.</li>
<li><strong>Renewable output:</strong> stylized and deterministic, scaled to Lazard's PJM capacity factors. Real wind and solar have cloudy and calm spells lasting days, which would raise the gas capacity needed.</li>
<li><strong>Gas:</strong> dispatchable and always available; no outages, no fuel-supply limits.</li>
<li><strong>Not modeled:</strong> storage, transmission, reserve margins, imports and exports, demand response, retirements of existing plants, carbon prices, and the cost of capital changing with the mix.</li>
<li><strong>Existing plants:</strong> this is a new-build comparison. A system that already owns gas plants faces a different calculation, because existing plants have low marginal costs (Lazard reports $32–$51/MWh for existing combined-cycle plants).</li>
<li><strong>Results are driven by assumptions.</strong> The sliders show how much; no single setting is "the answer."</li>
</ul>
</div>

<h2>8. Sources and reproducibility</h2>
<div class="panel">
<p>
<strong>Cost data:</strong> Lazard, <em>Levelized Cost of Energy+</em> (July 2026), LCOE v19.0 and Cost of Firming Intermittency.
<a href="https://www.lazard.com/media/kcfconhf/lazards-lcoeplus_vf.pdf" target="_blank" rel="noopener">lazard.com (PDF)</a>.
The same ranges for solar, wind, and gas were independently reported by
<a href="https://www.utilitydive.com/news/renewables-remain-cheapest-lcoe-rising-lazard/825443/" target="_blank" rel="noopener">Utility Dive</a>.
</p>
<p>
<strong>Hourly demand:</strong> PJM Interconnection hourly load for the AEP zone, in MW (file <code>AEP_hourly.csv</code>, 2004-10-01 to 2018-08-03).
PJM is the original publisher (<a href="https://www.pjm.com" target="_blank" rel="noopener">pjm.com</a>); the file is distributed in the Kaggle dataset
<a href="https://www.kaggle.com/datasets/robikscube/hourly-energy-consumption" target="_blank" rel="noopener">Hourly Energy Consumption</a>,
which has been used in published research papers. The page first looks for <code>data/AEP_hourly.csv</code> in this repository. If it is not there, it falls back to a public GitHub copy of the same file (<a href="https://github.com/BharatTupe/Energy-Demand-Forecasting" target="_blank" rel="noopener">BharatTupe/Energy-Demand-Forecasting</a>), which is a third-party copy of PJM data rather than PJM itself. For a fully reproducible exhibit, download the Kaggle file and save it as <code>data/AEP_hourly.csv</code> next to this page.
For newer years, the U.S. Energy Information Administration publishes hourly demand for every U.S. grid operator through its
<a href="https://www.eia.gov/electricity/gridmonitor/" target="_blank" rel="noopener">Hourly Electric Grid Monitor</a>.
</p>
<p>
<strong>Method:</strong> I used AI as a research and analysis tool to locate sources, write the code, and test assumptions. I checked the cost figures
against Lazard's report and Utility Dive's coverage of it. The model is mine and is described above; all of it runs in your browser from the data file, so anyone can inspect it by viewing this page's source.
</p>
</div>


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
  $("renShare").textContent = (100 * r.delivered / A_).toFixed(0) + "%";
  $("curtShare").textContent = (100 * r.curt / (r.solarGen + r.windGen || 1)).toFixed(1) + "% of wind + solar";
  $("utilGas").textContent = (100 * A_ / (state.peak * r.n)).toFixed(0) + "%";
  $("utilMix").textContent = r.maxGas > 0 ? (100 * r.gasGen / (r.maxGas * r.n)).toFixed(0) + "%" : "—";

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
  html += " This is an illustration with stylized renewable output, not a forecast and not a claim about the least-cost real-world system.";
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

/* ---------- Section 5: firming cross-check ---------- */
function drawFirming() {
  const firm = (elcc, cf) => (1 - elcc) * A.netCone * 12 / (cf * 8.76);   // $/MWh
  const fs = firm(A.elcc.solar, A.solarCF), fw = firm(A.elcc.wind, A.windCF);
  draw("firmChart", {
    type: "bar",
    data: {
      labels: ["Utility solar PV", "Onshore wind", "Gas combined cycle"],
      datasets: [
        { label: "LCOE midpoint (Lazard)", data: [A.lcoe.solar, A.lcoe.wind, A.lcoe.gas], backgroundColor: ["#d99a00", "#2f7fb8", "#6b7280"] },
        { label: "PJM firming cost", data: [fs, fw, 0], backgroundColor: "#b4532a" }
      ]
    },
    options: {
      interaction: { mode: "index", intersect: false },
      plugins: {
        legend: { position: "bottom" },
        tooltip: { callbacks: {
          label: c => " " + c.dataset.label + ": $" + c.parsed.y.toFixed(0) + "/MWh",
          footer: items => "Total: $" + items.reduce((s, i) => s + i.parsed.y, 0).toFixed(0) + "/MWh"
        } }
      },
      scales: { x: { stacked: true }, y: { stacked: true, beginAtZero: true, title: { display: true, text: "$ per MWh" } } }
    }
  });
  $("firmNote").textContent =
    "Firming cost = nameplate × (1 − ELCC) × Net CONE × 12 months ÷ annual energy: solar (1 − 0.12) × $5.50 × 12 ÷ (0.18 × 8.76) ≈ $" + fs.toFixed(0) +
    "/MWh; wind (1 − 0.38) × $5.50 × 12 ÷ (0.30 × 8.76) ≈ $" + fw.toFixed(0) + "/MWh. These match the PJM firming costs shown in Lazard's report. " +
    "The LCOE bars use Lazard's national midpoints for simplicity; Lazard's own regional figures use PJM capacity factors. " +
    "Lazard does not compute a firming cost for gas, although PJM also credits gas combined cycle at only 78% of capacity, so a fully symmetric comparison would add something to the gas bar too.";
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
drawFirming();
loadData();
</script>


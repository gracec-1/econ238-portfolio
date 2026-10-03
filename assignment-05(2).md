
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>LCOE Versus an Electricity System</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.4/dist/chart.umd.min.js"></script>

<style>
:root{
  --ink:#16301f;
  --muted:#4f6657;
  --paper:#fff;
  --bg:#eaf5ec;
  --line:#c3dcc8;
  --forest:#0b3d2e;
  --leaf:#2e9e5b;
  --lime:#b9e37a;
  --sun:#f4c430;
  --sky:#3a9bd5;
}

*{box-sizing:border-box}

body{
  margin:0;
  background:var(--bg);
  color:var(--ink);
  font-family:system-ui,-apple-system,"Segoe UI",Roboto,Arial,sans-serif;
  line-height:1.6;
}

.hero{
  color:white;
  border-bottom:6px solid var(--lime);
  background:linear-gradient(160deg,#0b3d2e,#17704a 55%,#2e9e5b);
}

.hero-inner{
  max-width:900px;
  margin:auto;
  padding:55px 22px 50px;
}

h1,h2{
  font-family:Georgia,"Times New Roman",serif;
}

.hero h1{
  font-size:48px;
  line-height:1.1;
  margin:0 0 15px;
}

.subtitle{
  font-size:19px;
  color:#dff3e4;
  max-width:700px;
}

main{
  max-width:900px;
  margin:auto;
  padding:35px 22px 50px;
}

.question{
  font-size:21px;
  background:var(--lime);
  color:var(--forest);
  padding:18px 24px;
  margin-bottom:35px;
  box-shadow:6px 6px 0 var(--forest);
}

h2{
  font-size:28px;
  color:var(--forest);
  border-left:8px solid var(--leaf);
  padding-left:14px;
  margin:50px 0 12px;
}

.figure{
  background:white;
  border:1px solid var(--line);
  border-top:5px solid var(--leaf);
  padding:20px;
  margin:20px 0;
  box-shadow:0 8px 22px rgba(11,61,46,.09);
}

.chartbox{
  position:relative;
  height:360px;
}

.chartbox.short{
  height:300px;
}

.note{
  font-size:13px;
  color:var(--muted);
  margin-bottom:0;
}

.callout{
  background:#e3f4d6;
  border-left:6px solid var(--leaf);
  padding:15px 18px;
  margin:20px 0;
}

.controls{
  display:flex;
  gap:18px;
  align-items:end;
  flex-wrap:wrap;
  background:white;
  border:1px solid var(--line);
  padding:15px 18px;
  margin:15px 0;
}

.controls label{
  display:flex;
  flex-direction:column;
  gap:4px;
  font-size:14px;
  font-weight:600;
  min-width:200px;
}

input[type=range]{
  width:100%;
  accent-color:var(--leaf);
}

button{
  background:var(--leaf);
  color:white;
  border:0;
  padding:9px 14px;
  cursor:pointer;
  font-weight:600;
}

button:hover{
  background:var(--forest);
}

select{
  padding:8px;
  border:1px solid var(--leaf);
  background:white;
}

.stats{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:14px;
  margin:18px 0;
}

.stats.four{
  grid-template-columns:repeat(4,1fr);
}

.stat{
  background:white;
  border:1px solid var(--line);
  border-top:6px solid var(--leaf);
  padding:14px 16px;
}

.stat:nth-child(1){border-top-color:var(--sun)}
.stat:nth-child(2){border-top-color:var(--sky)}
.stat:nth-child(3){border-top-color:var(--leaf)}
.stat:nth-child(4){border-top-color:#9a6b3a}

.stat .label{
  font-size:13px;
  color:var(--muted);
}

.stat .value{
  font-family:Georgia,serif;
  font-size:25px;
  font-weight:bold;
  color:var(--forest);
}

.sources{
  background:white;
  border:1px solid var(--line);
  padding:20px;
  margin-top:30px;
}

.sources a{
  color:#0f6a4a;
}

.sitefooter{
  background:var(--forest);
  color:#bfe3c8;
  border-top:6px solid var(--lime);
  padding:25px 22px;
  font-size:14px;
}

.sitefooter div{
  max-width:900px;
  margin:auto;
}

@media(max-width:760px){
  .stats,
  .stats.four{
    grid-template-columns:1fr;
  }

  .hero h1{
    font-size:36px;
  }
}
</style>
</head>

<body>

<header class="hero">
  <div class="hero-inner">
    <h1>LCOE Versus an Electricity System</h1>
    <p class="subtitle">
      A cheap megawatt-hour does not necessarily mean a cheap electricity system.
    </p>
  </div>
</header>

<main>

<div class="question">
  <strong>The question:</strong>
  If solar and wind have low LCOE, does that automatically make the electricity system cheaper?
</div>


<!-- 1. LCOE -->

<section>

<h2>1. Start with the price of electricity</h2>

<p>
LCOE measures the average cost of producing electricity from a power plant.
At first glance, solar and wind look competitive with gas.
</p>

<div class="figure">
  <div class="chartbox short">
    <canvas id="lcoeChart"></canvas>
  </div>

  <p class="note">
    Lazard, LCOE+ v19.0, July 2026. Unsubsidized new-build LCOE.
  </p>
</div>

</section>


<!-- 2. Demand -->

<section>

<h2>2. But electricity demand changes every hour</h2>

<p>
The grid does not need the same amount of electricity all day.
It has peaks and valleys that a power system must meet.
</p>

<div class="stats">
  <div class="stat">
    <div class="label">Annual demand</div>
    <div id="annualMWh" class="value">—</div>
  </div>

  <div class="stat">
    <div class="label">Average demand</div>
    <div id="avgMW" class="value">—</div>
  </div>

  <div class="stat">
    <div class="label">Peak demand</div>
    <div id="peakMW" class="value">—</div>
  </div>
</div>

<div class="figure">

  <div class="chartbox">
    <canvas id="dailyChart"></canvas>
  </div>

  <p class="note">
    PJM AEP-zone hourly electricity demand. Daily average and daily peak.
  </p>

</div>

</section>


<!-- 3. Hourly system -->

<section>

<h2>3. Now put the technologies on the same grid</h2>

<p>
Suppose we build solar and wind and let gas fill the remaining demand.
The important question is no longer just how much energy each technology produces,
but <strong>when</strong> it produces it.
</p>

<div class="controls">

  <label>
    Week of the year
    <input type="range" id="weekSlider" min="1" max="52" value="27">
    <span id="weekOut"></span>
  </label>

  <button id="peakWeekBtn">
    Jump to peak-demand week
  </button>

</div>

<div class="figure">

  <div class="chartbox">
    <canvas id="weekChart"></canvas>
  </div>

  <p class="note">
    Solar and wind profiles are simplified. Gas supplies the remaining hourly demand.
  </p>

</div>

<div class="callout">
  <strong>Notice:</strong>
  solar and wind can provide a large amount of energy while gas capacity is
  still needed for hours when renewable output is low.
</div>

</section>


<!-- 4. Cost -->

<section>

<h2>4. What happens to total system cost?</h2>

<p>
Try changing the amount of solar, wind, and the natural-gas price.
The model compares a gas-only system with a system using solar + wind + gas.
</p>

<div class="controls">

  <label>
    Solar capacity
    <input type="range" id="solarCap" min="0" max="150" step="5" value="50">
    <span id="solarOut"></span>
  </lab


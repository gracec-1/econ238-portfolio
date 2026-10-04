<!DOCTYPE html>

<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>LCOE Versus an Electricity System</title>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    :root {
      --green: #315c4a;
      --dark-green: #203f34;
      --light-green: #dcebe2;
      --cream: #f5f1e8;
      --white: #fffdf8;
      --orange: #d58a3c;
      --blue: #6b94a8;
      --gray: #59625d;
      --dark-gray: #29352f;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      background: var(--cream);
      color: var(--dark-gray);
      font-family: Arial, Helvetica, sans-serif;
      line-height: 1.6;
    }

    .page {
      max-width: 900px;
      margin: auto;
      padding: 25px;
    }

    .hero {
      background: var(--dark-green);
      color: white;
      text-align: center;
      padding: 55px 35px;
      border-radius: 18px;
      margin-bottom: 25px;
    }

    .hero-icon {
      font-size: 42px;
      margin-bottom: 10px;
    }

    .hero h1 {
      margin: 0;
      font-size: 42px;
      line-height: 1.15;
    }

    .hero p {
      max-width: 680px;
      margin: 15px auto 0;
      font-size: 18px;
      color: #e3ece7;
    }

    .question {
      background: var(--light-green);
      border-left: 6px solid var(--green);
      border-radius: 10px;
      padding: 20px 25px;
      margin-bottom: 25px;
    }

    .question h2 {
      margin-top: 0;
      color: var(--dark-green);
    }

    .section {
      background: var(--white);
      padding: 28px;
      border-radius: 14px;
      margin-bottom: 25px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }

    .section h2 {
      color: var(--dark-green);
      margin-top: 0;
    }

    .section p {
      color: var(--gray);
    }

    .chart-container {
      position: relative;
      height: 400px;
      margin-top: 25px;
    }

    .chart-note {
      font-size: 14px;
      color: #747b76;
      margin-top: 12px;
    }

    .calculation {
      background: #eef3ef;
      border-radius: 10px;
      padding: 18px 22px;
      margin-top: 20px;
    }

    .calculation strong {
      color: var(--dark-green);
    }

    .takeaway {
      background: #f3e7d4;
      border-left: 6px solid var(--orange);
      border-radius: 10px;
      padding: 22px 25px;
      margin-bottom: 25px;
    }

    .takeaway h2 {
      margin-top: 0;
      color: #70461f;
    }

    .sources {
      font-size: 14px;
    }

    .sources a {
      color: var(--green);
    }

    footer {
      text-align: center;
      color: #777;
      font-size: 13px;
      padding: 5px 0 30px;
    }

    @media (max-width: 650px) {

      .page {
        padding: 15px;
      }

      .hero {
        padding: 40px 20px;
      }

      .hero h1 {
        font-size: 32px;
      }

      .section {
        padding: 20px;
      }

      .chart-container {
        height: 350px;
      }
    }
  </style>

</head>

<body>

<div class="page">

  <!-- HERO -->

  <section class="hero">

```
<div class="hero-icon">⚡</div>

<h1>LCOE Versus an Electricity System</h1>

<p>
  A technology may have a low cost per megawatt-hour,
  but a power system must still produce enough electricity
  to meet demand every hour.
</p>
```

  </section>

  <!-- QUESTION -->

  <section class="question">

```
<h2>The question</h2>

<p>
  What happens when we move from simply comparing LCOE
  to actually requiring a power system to meet electricity
  demand every hour?
</p>
```

  </section>

  <!-- PART 1 -->

  <section class="section">

```
<h2>1. Start with LCOE</h2>

<p>
  Levelized Cost of Electricity (LCOE) estimates the average
  cost of building and operating a new generator over its
  lifetime. It gives us a useful way to begin comparing
  technologies.
</p>

<div class="chart-container">
  <canvas id="lcoeChart"></canvas>
</div>

<p class="chart-note">
  EIA AEO2026 estimates for new resources entering service in
  2031. Values are U.S. average LCOE in 2025 dollars per MWh.
</p>
```

  </section>

  <!-- PART 2 -->

  <section class="section">

```
<h2>2. Now require demand to be met every hour</h2>

<p>
  A low LCOE does not mean that a generator can produce electricity
  whenever it is needed. To see this difference, consider one day
  of hourly electricity demand from the New York Independent System
  Operator (NYISO).
</p>

<p>
  For the demonstration, the NYISO load is scaled so that the
  day's maximum demand equals 100 MW. This keeps the system small
  while preserving the actual shape of the hourly demand curve.
</p>

<div class="chart-container">
  <canvas id="systemChart"></canvas>
</div>

<p class="chart-note">
  Demand is based on NYISO hourly system load data for October 2,
  2026 and scaled to a 100-MW peak. The solar curve is a simplified
  daytime production profile used to demonstrate the system constraint.
</p>
```

  </section>

  <!-- PART 3 -->

  <section class="section">

```
<h2>3. What changes?</h2>

<p>
  Solar and wind can have relatively low LCOEs, but their output
  depends on weather and time of day. In the example above, solar
  produces little or no electricity during the nighttime hours.
</p>

<p>
  The remaining electricity demand therefore has to be supplied
  by another resource. Here, natural gas is used as a simple
  dispatchable backup.
</p>

<div class="calculation">

  <p>
    <strong>Example system:</strong>
  </p>

  <p>
    100 MW maximum demand + 100 MW solar capacity
    + approximately 100 MW of dispatchable backup capacity.
  </p>

  <p>
    Even though solar has a lower LCOE than natural gas,
    the system still needs another source capable of producing
    electricity when solar output is low.
  </p>

</div>
```

  </section>

  <!-- TAKEAWAY -->

  <section class="takeaway">

```
<h2>The main idea</h2>

<p>
  <strong>
    LCOE compares generators. An electricity system has to meet demand over time.
  </strong>
</p>

<p>
  Looking only at LCOE makes solar and wind appear attractive because
  their average generation costs can be lower than some dispatchable
  technologies. But once every hour of demand must be satisfied,
  the system also needs resources that can provide electricity when
  renewable output is unavailable.
</p>

<p>
  This does not mean that low-LCOE renewable generation is unnecessary.
  It means that the cost of an electricity system depends on the
  combination of technologies needed to provide electricity at the
  right time, not just the cost of producing one additional MWh.
</p>
```

  </section>

  <!-- SOURCES -->

  <section class="section sources">

```
<h2>Sources</h2>

<p>
  <strong>U.S. Energy Information Administration (EIA)</strong><br>
  <em>Levelized Costs of New Generation Resources in the
  Annual Energy Outlook 2026.</em>
</p>

<p>
  <a
    href="https://www.eia.gov/outlooks/aeo/electricity_generation/pdf/LCOE_report.pdf"
    target="_blank">
    EIA — AEO2026 LCOE Report
  </a>
</p>

<p>
  <strong>New York Independent System Operator (NYISO)</strong><br>
  Real-Time Actual Load data.
</p>

<p>
  <a
    href="https://mis.nyiso.com/public/P-58Blist.htm"
    target="_blank">
    NYISO — Real-Time Actual Load Data
  </a>
</p>

<p>
  EIA notes that LCOE does not capture all factors that contribute
  to electricity investment decisions, including factors related
  to system reliability and the value of a resource to the grid.
</p>
```

  </section>

  <footer>
    ECON 238 • Environmental Economics • Grace Chen • Fall 2026
  </footer>

</div>

<script>

  /*
    ---------------------------------------------------------
    CHART 1: LCOE COMPARISON
    Source: U.S. EIA AEO2026
    Values are $/MWh for resources entering service in 2031.
    ---------------------------------------------------------
  */

  const technologies = [
    "Solar PV",
    "Onshore Wind",
    "Natural Gas Combined-Cycle"
  ];

  const lcoeValues = [
    58.33,
    56.75,
    77.46
  ];


  new Chart(document.getElementById("lcoeChart"), {

    type: "bar",

    data: {

      labels: technologies,

      datasets: [{

        label: "LCOE",

        data: lcoeValues,

        backgroundColor: [
          "#d58a3c",
          "#315c4a",
          "#6b94a8"
        ],

        borderRadius: 6

      }]

    },

    options: {

      responsive: true,

      maintainAspectRatio: false,

      plugins: {

        legend: {
          display: false
        },

        tooltip: {

          callbacks: {

            label: function(context) {

              return "$" + context.raw.toFixed(2) + "/MWh";

            }

          }

        }

      },

      scales: {

        y: {

          beginAtZero: true,

          title: {

            display: true,

            text: "LCOE ($/MWh)"

          }

        }

      }

    }

  });


  /*
    ---------------------------------------------------------
    CHART 2: HOURLY ELECTRICITY SYSTEM
    NYISO hourly load for October 2, 2026.

    Load is scaled so the maximum hourly demand = 100 MW.

    Solar output is a simplified illustrative profile.
    It is NOT presented as measured solar generation.

    Gas generation fills the remaining demand:

        Gas = Demand - Solar

    This demonstrates why a system needs more than
    simply choosing the technology with the lowest LCOE.
    ---------------------------------------------------------
  */


  const hours = [
    "12 AM", "1 AM", "2 AM", "3 AM",
    "4 AM", "5 AM", "6 AM", "7 AM",
    "8 AM", "9 AM", "10 AM", "11 AM",
    "12 PM", "1 PM", "2 PM", "3 PM",
    "4 PM", "5 PM", "6 PM", "7 PM",
    "8 PM", "9 PM", "10 PM", "11 PM"
  ];


  /*
    Actual NYISO load values in MW.
  */

  const actualLoad = [
    14904,
    14280,
    13846,
    13603,
    13678,
    14263,
    15573,
    16621,
    17116,
    17219,
    17264,
    17326,
    17379,
    17589,
    17820,
    18132,
    18536,
    18992,
    19092,
    18941,
    18160,
    17368,
    16449,
    15459
  ];


  /*
    Scale actual demand to a 100 MW peak.
  */

  const peak = Math.max(...actualLoad);

  const demand = actualLoad.map(function(value) {

    return (value / peak) * 100;

  });


  /*
    Simplified solar production profile.

    100 MW maximum solar capacity.
  */

  const solarProfile = [
    0,
    0,
    0,
    0,
    0,
    5,
    15,
    30,
    50,
    70,
    85,
    95,
    100,
    95,
    85,
    70,
    50,
    30,
    10,
    0,
    0,
    0,
    0,
    0
  ];


  /*
    Solar cannot exceed demand in this simplified system.
  */

  const solarGeneration = solarProfile.map(function(value, i) {

    return Math.min(value, demand[i]);

  });


  /*
    Gas fills whatever demand remains.
  */

  const gasGeneration = demand.map(function(value, i) {

    return value - solarGeneration[i];

  });


  new Chart(document.getElementById("systemChart"), {

    type: "line",

    data: {

      labels: hours,

      datasets: [

        {

          label: "Electricity demand",

          data: demand,

          borderColor: "#29352f",

          backgroundColor: "rgba(41,53,47,0.08)",

          borderWidth: 3,

          tension: 0.3,

          pointRadius: 3

        },

        {

          label: "Solar generation",

          data: solarGeneration,

          borderColor: "#d58a3c",

          backgroundColor: "rgba(213,138,60,0.10)",

          borderWidth: 3,

          tension: 0.3,

          pointRadius: 3

        },

        {

          label: "Gas needed to meet demand",

          data: gasGeneration,

          borderColor: "#6b94a8",

          backgroundColor: "rgba(107,148,168,0.05)",

          borderWidth: 3,

          tension: 0.3,

          pointRadius: 3

        }

      ]

    },

    options: {

      responsive: true,

      maintainAspectRatio: false,

      interaction: {

        mode: "index",

        intersect: false

      },

      plugins: {

        legend: {

          position: "bottom"

        },

        tooltip: {

          callbacks: {

            label: function(context) {

              return context.dataset.label
                + ": "
                + context.raw.toFixed(1)
                + " MW";

            }

          }

        }

      },

      scales: {

        y: {

          beginAtZero: true,

          suggestedMax: 110,

          title: {

            display: true,

            text: "Power (MW)"

          }

        },

        x: {

          title: {

            display: true,

            text: "Hour"

          }

        }

      }

    }

  });

</script>

</body>
</html>

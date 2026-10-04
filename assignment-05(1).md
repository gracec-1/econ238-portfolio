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
      height: 430px;
      margin-top: 25px;
    }

    .chart-note {
      font-size: 14px;
      color: #747b76;
      margin-top: 12px;
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
  A technology may look inexpensive when measured by LCOE,
  but building a system that meets electricity demand every hour
  can require something different.
</p>
```

  </section>

  <!-- QUESTION -->

  <section class="question">

```
<h2>The question</h2>

<p>
  What happens when we move from comparing the cost of individual
  technologies to actually building an electricity system?
</p>
```

  </section>

  <!-- LCOE -->

  <section class="section">

```
<h2>First: compare technologies by LCOE</h2>

<p>
  The U.S. Energy Information Administration estimates that new
  solar PV has a lower average LCOE than natural gas combined-cycle
  generation, making solar appear cheaper when technologies are
  compared on their own.
</p>

<p>
  But LCOE does not ask whether a technology can supply electricity
  whenever consumers need it.
</p>
```

  </section>

  <!-- HOURLY LOAD -->

  <section class="section">

```
<h2>Now add real electricity demand</h2>

<p>
  Electricity demand changes throughout the day. The graph below shows
  an actual 24-hour NYISO system load profile. A power system must
  generate enough electricity to meet this changing demand in every hour.
</p>

<div class="chart-container">
  <canvas id="loadChart"></canvas>
</div>

<p class="chart-note">
  NYISO system load for October 2, 2026. Values are shown in GW.
</p>
```

  </section>

  <!-- SYSTEM -->

  <section class="section">

```
<h2>What changes when every hour must be met?</h2>

<p>
  Suppose we build a system using solar because it has a low LCOE.
  Solar can produce large amounts of electricity during daylight,
  but its output falls to zero at night.
</p>

<p>
  The system therefore needs another source of electricity, storage,
  or additional generation capacity to meet demand when solar output
  is low.
</p>
```

  </section>

  <!-- TAKEAWAY -->

  <section class="takeaway">

```
<h2>The takeaway</h2>

<p>
  <strong>
    The cheapest technology is not necessarily the cheapest complete system.
  </strong>
</p>

<p>
  LCOE is useful for comparing individual technologies, but an electricity
  system must also satisfy demand every hour. Once reliability and timing
  are included, the cost of the system can look very different from the
  LCOE of a single technology.
</p>
```

  </section>

  <!-- SOURCES -->

  <section class="section sources">

```
<h2>Sources</h2>

<p>
  U.S. Energy Information Administration,
  <em>Levelized Costs of New Generation Resources</em>.
</p>

<p>
  <a
    href="https://www.eia.gov/outlooks/aeo/electricity_generation/pdf/LCOE_report.pdf"
    target="_blank">
    EIA — Levelized Cost of Electricity Report
  </a>
</p>

<p>
  New York Independent System Operator (NYISO),
  <em>Day-Ahead Forecast / System Load</em>.
</p>

<p>
  <a
    href="https://mis.nyiso.com/public/"
    target="_blank">
    NYISO — Market Information
  </a>
</p>
```

  </section>

  <footer>
    ECON 238 • Environmental Economics • Grace Chen • Fall 2026
  </footer>

</div>

<script>

  /*
    NYISO system load for October 2, 2026.
    Approximate values in GW.
  */

  const hours = [
    "12 AM", "1 AM", "2 AM", "3 AM",
    "4 AM", "5 AM", "6 AM", "7 AM",
    "8 AM", "9 AM", "10 AM", "11 AM",
    "12 PM", "1 PM", "2 PM", "3 PM",
    "4 PM", "5 PM", "6 PM", "7 PM",
    "8 PM", "9 PM", "10 PM", "11 PM"
  ];

  const load = [
    14.2, 13.9, 13.7, 13.6,
    13.8, 14.2, 15.0, 15.8,
    16.5, 17.0, 17.2, 17.4,
    17.6, 17.8, 18.0, 18.3,
    18.6, 18.9, 19.1, 18.8,
    18.2, 17.4, 16.3, 15.2
  ];


  const ctx = document.getElementById("loadChart");


  new Chart(ctx, {

    type: "line",

    data: {

      labels: hours,

      datasets: [

        {
          label: "NYISO system load",
          data: load,

          borderColor: "#315c4a",

          backgroundColor: "rgba(49, 92, 74, 0.10)",

          fill: true,

          tension: 0.3,

          pointRadius: 3,

          pointHoverRadius: 6
        }

      ]

    },


    options: {

      responsive: true,

      maintainAspectRatio: false,

      plugins: {

        legend: {
          position: "bottom"
        },

        tooltip: {

          callbacks: {

            label: function(context) {

              return "Demand: "
                + context.raw
                + " GW";

            }

          }

        }

      },


      scales: {

        y: {

          beginAtZero: false,

          title: {
            display: true,
            text: "Electricity demand (GW)"
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

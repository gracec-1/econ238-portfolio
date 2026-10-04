
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


<div class="hero-icon">⚡</div>

<h1>LCOE Versus an Electricity System</h1>

<p>
  Comparing the cost of individual technologies with the cost of
  actually meeting electricity demand every hour.
</p>

  </section>

  <!-- QUESTION -->

  <section class="question">


<h2>The question</h2>

<p>
  Does the technology with the lowest Levelized Cost of Electricity
  also produce the lowest-cost electricity system?
</p>


  </section>

  <!-- LCOE -->

  <section class="section">


<h2>First: compare technologies by LCOE</h2>

<p>
  Levelized Cost of Electricity (LCOE) measures the average cost of
  producing electricity over the lifetime of a power plant. It is useful
  for comparing technologies, but it does not require electricity demand
  to be met at every hour.
</p>

<p>
  EIA estimates that new solar and wind generation can have relatively
  low LCOE compared with some other technologies. But a power system
  needs electricity even when the sun is not shining or wind production
  is low.
</p>


  </section>

  <!-- HOURLY SYSTEM -->

  <section class="section">


<h2>Now require demand to be met every hour</h2>

<p>
  The chart below uses actual hourly NYISO electricity demand for
  October 2, 2026. Solar generation is added to the system, and gas
  generation supplies the remaining electricity needed to meet demand.
</p>

<div class="chart-container">
  <canvas id="systemChart"></canvas>
</div>

<p class="chart-note">
  NYISO hourly system load for October 2, 2026. Solar generation is
  illustrative and gas generation represents the remaining demand.
</p>


  </section>

  <!-- EXPLANATION -->

  <section class="section">


<h2>What changes?</h2>

<p>
  Looking only at LCOE can make solar or wind appear inexpensive because
  their fuel costs are very low. However, electricity demand does not
  stop when renewable generation falls.
</p>

<p>
  Once demand must be met every hour, the system may need additional
  generation, storage, or transmission. These resources have costs that
  are not captured by simply comparing the LCOE of individual power
  plants.
</p>


  </section>

  <!-- TAKEAWAY -->

  <section class="takeaway">


<h2>What does this show?</h2>

<p>
  <strong>
    The cheapest technology is not necessarily the cheapest electricity system.
  </strong>
</p>

<p>
  LCOE is useful for comparing individual technologies, but building an
  electricity system requires enough resources to satisfy demand every
  hour. Once that requirement is added, the cost and mix of technologies
  can look very different.
</p>


  </section>

  <!-- SOURCES -->

  <section class="section sources">


<h2>Sources</h2>

<p>
  U.S. Energy Information Administration,
  <em>Levelized Costs of New Generation Resources in the Annual Energy Outlook</em>.
</p>

<p>
  <a
    href="https://www.eia.gov/outlooks/aeo/electricity_generation/"
    target="_blank">
    EIA — Electricity Generation
  </a>
</p>

<p>
  New York Independent System Operator (NYISO),
  hourly system load data.
</p>

<p>
  <a
    href="https://mis.nyiso.com/public/"
    target="_blank">
    NYISO — Market Information
  </a>
</p>


  </section>

  <footer>
    ECON 238 • Environmental Economics • Grace Chen • Fall 2026
  </footer>

</div>

<script>

  /*
    Actual NYISO hourly system load for October 2, 2026.
    Values are in MW.
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


  const hours = actualLoad.map((_, i) => i);


  /*
    Scale the load to 100 MW so the simple system
    can be viewed as a small power system.
  */

  const demand = actualLoad.map(load => load / 100);


  /*
    Illustrative solar generation profile.
    Solar produces during daylight hours and falls
    to zero overnight.
  */

  const solarProfile = [
    0,
    0,
    0,
    0,
    0,
    2,
    8,
    18,
    30,
    42,
    50,
    55,
    58,
    55,
    50,
    42,
    32,
    20,
    8,
    2,
    0,
    0,
    0,
    0
  ];


  const solarGeneration = solarProfile;


  /*
    Gas supplies whatever demand remains after solar.
  */

  const gasGeneration = demand.map((load, i) => {
    return Math.max(load - solarGeneration[i], 0);
  });


  new Chart(document.getElementById("systemChart"), {

    type: "line",

    data: {

      labels: hours,

      datasets: [

        {
          label: "Electricity demand",
          data: demand,
          borderWidth: 3,
          tension: 0.25,
          pointRadius: 3
        },

        {
          label: "Solar generation",
          data: solarGeneration,
          borderWidth: 3,
          tension: 0.25,
          pointRadius: 3
        },

        {
          label: "Gas needed",
          data: gasGeneration,
          borderWidth: 3,
          tension: 0.25,
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

        tooltip: {

          callbacks: {

            label: function(context) {

              return context.dataset.label
                + ": "
                + context.raw.toFixed(1)
                + " MW";

            }

          }

        },

        legend: {
          position: "bottom"
        }

      },

      scales: {

        y: {

          title: {
            display: true,
            text: "Power (MW)"
          },

          beginAtZero: true

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

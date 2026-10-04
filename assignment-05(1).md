
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>LCOE vs. the Electricity System</title>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    :root {
      --green: #315c4a;
      --dark-green: #203f34;
      --light-green: #dcebe2;
      --cream: #f5f1e8;
      --white: #fffdf8;
      --orange: #d58a3c;
      --yellow: #e3b64b;
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

    /* HERO */

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

    /* QUESTION */

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

    /* SECTIONS */

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

    /* CHART */

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

    /* TAKEAWAY */

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

    /* SOURCES */

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

    <h1>LCOE vs. the Electricity System</h1>

    <p>
      A power plant can have a low average cost of electricity,
      but that does not necessarily mean the entire electricity system is cheap.
    </p>

  </section>


  <!-- QUESTION -->

  <section class="question">

    <h2>The question</h2>

    <p>
      Does a low Levelized Cost of Electricity (LCOE) automatically mean
      a low-cost electricity system?
    </p>

  </section>


  <!-- CHART -->

  <section class="section">

    <h2>Comparing the cost of electricity</h2>

    <p>
      LCOE estimates the average cost of producing electricity from a new
      power plant over its lifetime. It is useful for comparing technologies,
      but it does not include every cost involved in keeping electricity
      available when people need it.
    </p>

    <div class="chart-container">
      <canvas id="lcoeChart"></canvas>
    </div>

    <p class="chart-note">
      Hover over each bar to see the estimated LCOE range.
      Values shown are unsubsidized new-build estimates from Lazard's 2026 report.
    </p>

  </section>


  <!-- EXPLANATION -->

  <section class="section">

    <h2>Why isn't LCOE the whole story?</h2>

    <p>
      Electricity demand changes from hour to hour. Solar power produces
      electricity mainly during daylight, and wind output changes with weather.
      A grid therefore needs enough capacity and flexibility to meet demand
      even when renewable generation is low.
    </p>

    <p>
      For example, adding solar and wind can reduce the amount of fuel a gas
      plant uses, while the gas plant may still need to remain available for
      hours when renewable generation is insufficient.
    </p>

  </section>


  <!-- TAKEAWAY -->

  <section class="takeaway">

    <h2>What does this show?</h2>

    <p>
      LCOE is a useful starting point, but it answers a narrower question:
      <strong>how much does this technology cost to produce electricity?</strong>
    </p>

    <p>
      A complete electricity system also has to consider timing, reliability,
      backup capacity, transmission, storage, and other system costs.
      Therefore, the technology with the lowest LCOE is not automatically
      the technology that produces the lowest-cost electricity system.
    </p>

  </section>


  <!-- SOURCES -->

  <section class="section sources">

    <h2>Sources</h2>

    <p>
      Lazard,
      <em>Levelized Cost of Energy+</em>, Version 19.0, July 2026.
    </p>

    <p>
      <a
        href="https://www.lazard.com/research-insights/levelized-cost-of-energyplus/"
        target="_blank">
        Lazard — Levelized Cost of Energy+
      </a>
    </p>

    <p>
      LCOE values are presented as ranges because the cost of a technology
      depends on assumptions such as financing, location, and operating costs.
    </p>

  </section>


  <footer>
    ECON 238 • Environmental Economics • Grace Chen • Fall 2026
  </footer>

</div>


<script>

  /*
    Lazard 2026 LCOE ranges.
    Values are approximate midpoint/range values used
    to create a simple visual comparison.
  */

  const technologies = [
    "Solar PV",
    "Wind",
    "Gas Combined Cycle"
  ];

  const low = [
    38,
    37,
    48
  ];

  const high = [
    78,
    86,
    109
  ];

  const midpoint = [
    (38 + 78) / 2,
    (37 + 86) / 2,
    (48 + 109) / 2
  ];


  const ctx = document.getElementById("lcoeChart");


  new Chart(ctx, {

    type: "bar",

    data: {

      labels: technologies,

      datasets: [

        {
          label: "Low end",
          data: low,

          backgroundColor: "#6b94a8",

          borderRadius: 5
        },

        {
          label: "High end",
          data: high,

          backgroundColor: "#315c4a",

          borderRadius: 5
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

              return context.dataset.label
                + ": $" + context.raw
                + "/MWh";

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

        },

        x: {

          title: {
            display: true,
            text: "Electricity technology"
          }

        }

      }

    }

  });

</script>

</body>
</html>

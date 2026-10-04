<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Where Does Our Recycling Go?</title>

  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    :root {
      --green: #356b50;
      --dark-green: #214735;
      --light-green: #dfece2;
      --paper: #f5f1e8;
      --white: #fffdf8;
      --orange: #d98a3d;
      --yellow: #e5b94d;
      --gray: #59635c;
      --dark-gray: #303a34;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      background: var(--paper);
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
      font-size: 45px;
      margin-bottom: 8px;
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
      color: #e4eee7;
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
      color: var(--dark-green);
      margin-top: 0;
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
      color: #70461f;
      margin-top: 0;
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

    <div class="hero-icon">♻️</div>

    <h1>Where Does Our Recycling Go?</h1>

    <p>
      Recycling is often presented as a simple solution to waste.
      But looking at the entire waste stream tells a more complicated story.
    </p>

  </section>


  <!-- QUESTION -->

  <section class="question">

    <h2>The question</h2>

    <p>
      If recycling is supposed to keep materials out of landfills,
      how large is recycling compared with the rest of the U.S. waste stream?
    </p>

  </section>


  <!-- CHART -->

  <section class="section">

    <h2>What happens to municipal solid waste?</h2>

    <p>
      The chart shows how municipal solid waste in the United States is
      managed after it is generated. Recycling and composting recover some
      materials, while a much larger share is disposed of or managed through
      other methods.
    </p>

    <div class="chart-container">
      <canvas id="wasteChart"></canvas>
    </div>

    <p class="chart-note">
      Hover over each section to see its estimated share of the waste stream.
    </p>

  </section>


  <!-- EXPLANATION -->

  <section class="section">

    <h2>Why does the difference matter?</h2>

    <p>
      It is easy to think about recycling as the final destination of an item:
      once something enters a recycling bin, we may assume it becomes a new
      product. In reality, recycling is one stage within a much larger waste
      management system.
    </p>

    <p>
      Materials have to be collected, sorted, processed, and sold into markets
      before they can replace newly produced materials. Contamination and the
      availability of markets can also affect whether collected material is
      ultimately recovered.
    </p>

    <p>
      This means that the environmental value of recycling depends not only on
      how much material people put in recycling bins, but also on what happens
      to that material afterward.
    </p>

  </section>


  <!-- INTERPRETATION -->

  <section class="takeaway">

    <h2>What should we take from this?</h2>

    <p>
      Recycling is useful, but it does not eliminate the waste problem by itself.
      The chart puts recycling into context: most of the material entering the
      municipal waste system is still handled through other pathways.
    </p>

    <p>
      From an environmental economics perspective, this raises a broader
      question: <strong>Is it more effective to focus on recycling, or to reduce
      the amount of waste created in the first place?</strong>
    </p>

  </section>


  <!-- SOURCES -->

  <section class="section sources">

    <h2>Sources</h2>

    <p>
      U.S. Environmental Protection Agency (EPA),
      <a
        href="https://www.epa.gov/facts-and-figures-about-materials-waste-and-recycling"
        target="_blank">
        Facts and Figures about Materials, Wastes and Recycling
      </a>
    </p>

    <p>
      U.S. Environmental Protection Agency,
      Sustainable Materials Management program.
    </p>

    <p>
      Chart values are rounded for presentation. See the EPA source for the
      underlying waste-generation and management data.
    </p>

  </section>


  <footer>
    ECON 238 • Environmental Economics • Grace Chen • Fall 2026
  </footer>

</div>


<script>

  /*
    Approximate U.S. municipal solid waste management shares.
    These values are simplified for visualization.
  */

  const labels = [
    "Landfilled",
    "Recycled",
    "Composted",
    "Combusted / Other"
  ];

  const values = [
    57,
    24,
    9,
    10
  ];


  const ctx = document.getElementById("wasteChart");


  new Chart(ctx, {

    type: "doughnut",

    data: {

      labels: labels,

      datasets: [{

        data: values,

        backgroundColor: [
          "#718078",
          "#356b50",
          "#d98a3d",
          "#e5b94d"
        ],

        borderColor: "#fffdf8",
        borderWidth: 3
      }]

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

              return context.label + ": "
                + context.raw + "%";

            }

          }

        }

      }

    }

  });

</script>

</body>
</html>

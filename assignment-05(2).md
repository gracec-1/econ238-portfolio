<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>Where Does Our Recycling Go?</title>

  <!-- Chart.js -->
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

  <style>
    :root {
      --green: #2f6b4f;
      --dark-green: #214936;
      --light-green: #dfeee4;
      --paper: #f5f1e8;
      --white: #fffdf8;
      --orange: #d8893d;
      --yellow: #e6b84c;
      --gray: #59615b;
    }

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background: var(--paper);
      color: #26332b;
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
      padding: 55px 35px;
      border-radius: 18px;
      text-align: center;
      margin-bottom: 25px;
    }

    .hero .icon {
      font-size: 42px;
      margin-bottom: 10px;
    }

    .hero h1 {
      margin: 0;
      font-size: 42px;
      line-height: 1.15;
    }

    .hero p {
      margin: 15px auto 0;
      max-width: 650px;
      font-size: 18px;
      color: #e5eee8;
    }

    /* QUESTION */
    .question {
      background: var(--light-green);
      border-left: 6px solid var(--green);
      padding: 20px 25px;
      border-radius: 10px;
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
      margin-top: 20px;
    }

    .chart-note {
      font-size: 14px;
      color: #69736d;
      margin-top: 10px;
    }

    /* TAKEAWAY */
    .takeaway {
      background: #f3e8d6;
      border-left: 6px solid var(--orange);
      padding: 20px 25px;
      border-radius: 10px;
    }

    .takeaway h2 {
      margin-top: 0;
      color: #70451f;
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
      padding: 10px 0 30px;
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
      <div class="icon">♻️</div>
      <h1>Where Does Our Recycling Go?</h1>
      <p>
        Recycling feels simple: put something in the blue bin and it gets recycled.
        But what happens after it leaves your home?
      </p>
    </section>

    <!-- QUESTION -->
    <section class="question">
      <h2>The question</h2>
      <p>
        How much of the material we throw away actually gets recycled?
      </p>
    </section>

    <!-- CHART -->
    <section class="section">
      <h2>Recycling is only one part of the waste stream</h2>

      <p>
        In the United States, most municipal solid waste is still managed through
        disposal rather than recycling. This chart shows how the different
        management methods compare.
      </p>

      <div class="chart-container">
        <canvas id="wasteChart"></canvas>
      </div>

      <p class="chart-note">
        Hover over a bar to see the amount represented by each category.
      </p>
    </section>

    <!-- INTERPRETATION -->
    <section class="section">
      <h2>What does this show?</h2>

      <p>
        Recycling is an important part of waste management, but it represents only
        one portion of the material we throw away. A large amount of waste is still
        sent to landfills or managed in other ways.
      </p>

      <p>
        This means that putting something in a recycling bin does not automatically
        mean that it becomes a new product. Collection, sorting, contamination,
        markets for recycled materials, and local recycling systems all affect what
        happens next.
      </p>
    </section>

    <!-- TAKEAWAY -->
    <section class="takeaway">
      <h2>The bigger idea</h2>

      <p>
        Recycling can help reduce waste, but it is only one part of the larger
        waste system. Looking at the entire waste stream gives a better picture
        than thinking about recycling by itself.
      </p>
    </section>

    <!-- SOURCES -->
    <section class="section sources">
      <h2>Sources</h2>

      <p>
        U.S. Environmental Protection Agency,
        <a href="https://www.epa.gov/facts-and-figures-about-materials-waste-and-recycling"
           target="_blank">
          Facts and Figures about Materials, Wastes and Recycling
        </a>
      </p>

      <p>
        Data and categories are based on U.S. EPA municipal solid waste
        reporting. Values are rounded for easier interpretation.
      </p>
    </section>

    <footer>
      ECON 238 • Environmental Economics • Grace Chen • Fall 2026
    </footer>

  </div>

  <script>
    /*
      Approximate values based on the EPA's municipal solid waste
      management categories. Values are rounded for presentation.
    */

    const labels = [
      "Landfilled",
      "Recycled",
      "Composted",
      "Combustion"
    ];

    const values = [
      146,
      69,
      25,
      14
    ];

    const ctx = document.getElementById("wasteChart");

    new Chart(ctx, {
      type: "bar",

      data: {
        labels: labels,

        datasets: [{
          label: "Million tons",
          data: values,

          backgroundColor: [
            "#718078",
            "#2f6b4f",
            "#d8893d",
            "#e6b84c"
          ],

          borderRadius: 7
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
                return context.raw + " million tons";
              }
            }
          }
        },

        scales: {
          y: {
            beginAtZero: true,

            title: {
              display: true,
              text: "Million tons"
            }
          },

          x: {
            title: {
              display: true,
              text: "Waste management method"
            }
          }
        }
      }
    });
  </script>

</body>
</html>



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

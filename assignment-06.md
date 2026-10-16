<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Shoot Barred Owls to Save Spotted Owls? A Public Ballot</title>
<meta name="description" content="A real environmental deal, put to a public vote: fund the removal of up to 100,000 barred owls to save the northern spotted owl. Read it, then vote.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Libre+Franklin:wght@500;700;800&family=Source+Serif+4:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
<!-- All vote buttons link to vote.html (the voting page). No setup needed in this file. -->
<style>
  :root{
    --mist:#dfe7e1; --mist-deep:#c9d7cd; --spruce:#1d3430; --moss:#4f6b57; --lichen:#9fb3a2;
    --paper:#fdfdf9; --ink:#1b2622; --muted:#52615a;
    --yes:#2d6a4f; --yes-tint:#e3f0e8; --no:#a23b2a; --no-tint:#f6e4df;
    --fine:#efe7c9; --amber:#f0b429;
    --sans:"Libre Franklin", system-ui, sans-serif;
    --serif:"Source Serif 4", Georgia, serif;
  }
  *{box-sizing:border-box}
  html{scroll-behavior:smooth}
  body{
    margin:0; color:var(--ink); font-family:var(--serif); font-size:1.125rem; line-height:1.65;
    background:
      radial-gradient(70% 38% at 85% 6%, rgba(255,255,255,.75), transparent 70%),
      radial-gradient(60% 30% at 8% 30%, rgba(255,255,255,.45), transparent 70%),
      linear-gradient(180deg,#c5d4ca 0,#dde6df 460px,#e6ece7 100%);
    background-attachment:fixed;
  }
  a{color:var(--spruce)}
  :focus-visible{outline:3px solid var(--ballot,#2a4ba0); outline-offset:3px; border-radius:4px}
  .wrap{max-width:720px; margin:0 auto; padding:0 20px}
  h1,h2,h3{font-family:var(--sans); line-height:1.12; margin:0; color:var(--spruce)}

  /* hero */
  .hero{padding:64px 0 28px}
  .hero h1{font-size:clamp(2.3rem,7vw,3.9rem); font-weight:800; letter-spacing:-.02em; max-width:15ch}
  .hero p.lede{font-size:1.25rem; max-width:34ch; margin:18px 0 30px; color:var(--muted)}
  .meter{background:rgba(253,253,249,.72); border:1px solid var(--mist-deep); border-radius:10px; padding:20px 22px; backdrop-filter:blur(3px)}
  .meter h2{font-size:1rem; font-weight:700; margin-bottom:14px}
  .bar-row{margin:0 0 14px}
  .bar-row:last-of-type{margin-bottom:6px}
  .bar-label{display:flex; justify-content:space-between; gap:12px; font-family:var(--sans); font-size:.9rem; font-weight:500; margin-bottom:5px}
  .bar-label b{font-weight:800}
  .track{height:16px; background:rgba(29,52,48,.08); border-radius:8px; overflow:hidden}
  .fill{height:100%; border-radius:8px; transform-origin:left; animation:grow 1.4s .3s cubic-bezier(.2,.7,.2,1) both}
  .fill.bad{width:100%; background:var(--no)}
  .fill.good{width:1.65%; min-width:6px; background:var(--yes); animation-delay:1.1s}
  @keyframes grow{from{transform:scaleX(0)}to{transform:scaleX(1)}}
  .meter small{display:block; font-family:var(--sans); font-size:.78rem; color:var(--muted); margin-top:8px}
  .jump{display:inline-block; margin-top:26px; font-family:var(--sans); font-weight:700; background:var(--spruce); color:#fff; padding:13px 22px; border-radius:999px; text-decoration:none}
  .jump:hover{background:var(--moss)}

  svg.ridge{display:block; width:100%; height:130px}

  /* ballot */
  .ballot{background:var(--paper); border:2px solid var(--ink); border-radius:6px; margin:10px 0 0; box-shadow:0 18px 40px -22px rgba(29,52,48,.55)}
  .ballot header{background:var(--spruce); color:#fff; font-family:var(--sans); font-weight:500; font-size:.95rem; padding:10px 20px; border-radius:3px 3px 0 0}
  .ballot .inner{padding:22px 22px 8px}
  .prop-title{font-family:var(--sans); font-weight:800; font-size:clamp(1.35rem,4vw,1.8rem); line-height:1.15; margin:0 0 14px; color:var(--ink)}
  .question{margin:0 0 22px}
  .ask{font-family:var(--sans); font-weight:800; font-size:1.1rem; border-top:2px solid var(--ink); padding-top:16px; margin:0 0 6px}
  .opts{list-style:none; margin:0; padding:0}
  .opts li{border-top:1px solid var(--mist-deep)}
  .opts a{display:flex; align-items:center; gap:16px; padding:15px 4px; text-decoration:none; color:var(--ink); font-family:var(--sans); font-weight:800; font-size:1.25rem}
  .opts a span.hint{font-weight:500; font-size:.9rem; color:var(--muted)}
  .bubble{flex:none; width:44px; height:26px; border:2.5px solid var(--ink); border-radius:50%; background:#fff; transition:background .15s}
  .opts a:hover .bubble,.opts a:focus-visible .bubble{background:var(--ink)}
  .opts a:hover{background:rgba(29,52,48,.04)}
  .anon{font-family:var(--sans); font-size:.85rem; color:var(--muted); padding:10px 4px 18px; margin:0; border-top:1px solid var(--mist-deep)}

  /* sections */
  section{padding:46px 0 0}
  section h2{font-size:1.7rem; font-weight:800; letter-spacing:-.01em; margin-bottom:16px}
  .body p{margin:0 0 1em; max-width:68ch}
  .body p:last-child{margin-bottom:0}

  dl.ledger{margin:0; border-top:2px solid var(--ink)}
  dl.ledger div{display:grid; grid-template-columns:150px 1fr; gap:6px 18px; padding:13px 0; border-bottom:1px solid var(--mist-deep)}
  dl.ledger dt{font-family:var(--sans); font-weight:800; font-size:.95rem; color:var(--spruce)}
  dl.ledger dd{margin:0}
  @media (max-width:560px){dl.ledger div{grid-template-columns:1fr}}

  .debate{max-width:1000px; margin:0 auto; padding:46px 20px 0}
  .pair{display:grid; gap:20px}
  @media (min-width:860px){.pair{grid-template-columns:1fr 1fr}}
  .case{border-radius:8px; padding:24px 24px 26px; background:var(--paper); border:1px solid var(--mist-deep); border-top-width:8px}
  .case.yes{border-top-color:var(--yes)} .case.no{border-top-color:var(--no)}
  .case h2{font-size:1.45rem; margin-bottom:12px}
  .case.yes h2{color:var(--yes)} .case.no h2{color:var(--no)}
  .case .body{font-size:1.05rem}

  .fineprint{background:var(--fine); border:1.5px dashed #8a7a3a; border-radius:6px; padding:22px 24px}
  .fineprint h2{font-size:1.3rem; margin-bottom:10px}
  .fineprint .body{font-size:1rem}

  details{background:rgba(253,253,249,.7); border:1px solid var(--mist-deep); border-radius:8px; padding:14px 18px; font-size:.95rem}
  summary{cursor:pointer; font-family:var(--sans); font-weight:700}
  .sources{background:rgba(253,253,249,.7); border:1px solid var(--mist-deep); border-radius:8px; padding:22px 24px}
  .sources h2{font-size:1.3rem; margin-bottom:6px}
  .sources p{margin:0 0 10px; font-family:var(--sans); font-size:.9rem; color:var(--muted)}
  .sources ul{padding-left:1.1em; margin:0; font-size:.95rem}
  .sources li{margin:0 0 10px; overflow-wrap:anywhere}

  /* footer forest */
  footer{margin-top:70px; position:relative; background:var(--spruce); color:#e8f0ea}
  footer svg.ridge{position:absolute; left:0; right:0; top:-129px}
  footer .wrap{padding-top:26px; padding-bottom:64px; position:relative}
  footer h2{color:#fff; font-size:1.8rem; margin-bottom:8px}
  footer p{margin:0 0 20px; color:#c8d6cc}
  .cta{display:inline-block; font-family:var(--sans); font-weight:800; font-size:1.1rem; background:var(--amber); color:#1b1500; padding:14px 28px; border-radius:999px; text-decoration:none}
  .cta:hover{background:#ffc94d}
  .eyes{position:absolute; right:8%; top:34px; display:flex; gap:16px}
  .eyes i{width:22px; height:22px; border-radius:50%; background:var(--amber); box-shadow:inset 0 0 0 6px #1b1500, 0 0 14px rgba(240,180,41,.55); display:block}
  @media (max-width:560px){.eyes{display:none}}

  .float{position:fixed; right:16px; bottom:16px; z-index:5; font-family:var(--sans); font-weight:800; background:var(--amber); color:#1b1500; padding:12px 22px; border-radius:999px; text-decoration:none; box-shadow:0 8px 22px -8px rgba(0,0,0,.45); transition:opacity .2s}
  .float.hide{opacity:0; pointer-events:none}

  @media (prefers-reduced-motion:reduce){
    html{scroll-behavior:auto}
    .fill{animation:none}
  }
</style>
</head>
<body>

<div class="wrap hero">
  <h1>Shoot barred owls to save spotted owls?</h1>
  <p class="lede">A real environmental deal, put to a public vote. Read it, then say yes, no, or yes-if.</p>

  <div class="meter" role="group" aria-label="Yearly decline of spotted owls with and without barred owl removal">
    <h2>How fast spotted owls are disappearing</h2>
    <div class="bar-row">
      <div class="bar-label"><span>Barred owls left alone</span><b>-12.1% a year</b></div>
      <div class="track"><div class="fill bad"></div></div>
    </div>
    <div class="bar-row">
      <div class="bar-label"><span>Barred owls removed</span><b>-0.2% a year</b></div>
      <div class="track"><div class="fill good"></div></div>
    </div>
    <small>Large field experiment, Washington, Oregon and California, 2009-2019 (Wiens et al., PNAS 2021).</small>
  </div>
  <a class="jump" href="#ballot">Go to the ballot</a>
</div>

<svg class="ridge" id="ridge-far" aria-hidden="true" viewBox="0 0 1600 130" preserveAspectRatio="xMidYMax slice"></svg>

<main>
<div class="wrap" style="padding-top:0">
  <div class="ballot" id="ballot">
    <header>Public ballot proposition</header>
    <div class="inner">
      <p class="prop-title" data-limit="12" data-name="THE PROPOSITION">Fund Killing Up to 100,000 Barred Owls to Save Spotted Owls</p>
      <p class="question" data-limit="75" data-name="THE BALLOT QUESTION">Shall Congress appropriate $30 million per year for ten years so the U.S. Fish and Wildlife Service and tribal and state partners can lethally remove up to 10,000 invasive barred owls annually from northern spotted owl range in Washington, Oregon and California, using non-lead ammunition, with annual public reporting, and ending removal in any region where spotted owl decline has not stabilized after five years?</p>
      <p class="ask">Would you take this deal?</p>
      <ul class="opts">
        <li><a href="https://docs.google.com/forms/d/e/1FAIpQLSdSZrW-600K1mJaRM0l2OlY3VMMQRMSgg5dW_Y6Fwa5fShW1g/viewform?usp=header"><span class="bubble"></span>Yes</a></li>
        <li><a href="https://docs.google.com/forms/d/e/1FAIpQLSdSZrW-600K1mJaRM0l2OlY3VMMQRMSgg5dW_Y6Fwa5fShW1g/viewform?usp=header"><span class="bubble"></span>No</a></li>
        <li><a href="https://docs.google.com/forms/d/e/1FAIpQLSdSZrW-600K1mJaRM0l2OlY3VMMQRMSgg5dW_Y6Fwa5fShW1g/viewform?usp=header"><span class="bubble"></span><span>Yes, if&hellip; <br><span class="hint">You'll get a box to say what would have to change.</span></span></a></li>
      </ul>
      <p class="anon">Your vote is anonymous and takes about 30 seconds.</p>
    </div>
  </div>

  <section id="deal">
    <h2>What's the deal?</h2>
    <div data-limit="150" data-name="WHAT'S THE DEAL?">
    <dl class="ledger">
      <div><dt>What we buy</dt><dd>Time for a collapsing species. Spotted owls have fallen at least 50% across study sites. In a 2009-2019 experiment, they declined 12.1% per year where barred owls were left alone, but only 0.2% where removed.</dd></div>
      <div><dt>What we give up</dt><dd>Up to 100,000 barred owls over ten years, under half of 1% of the North American population per year (FWS's measure), plus the principle of not shooting protected birds.</dd></div>
      <div><dt>Who benefits</dt><dd>Spotted owls, old-forest ecosystems, tribes and agencies paid to do the work, and communities living under logging limits meant to protect the owl.</dd></div>
      <div><dt>Who bears costs</dt><dd>The owls killed.</dd></div>
      <div><dt>Who pays</dt><dd>Federal taxpayers, about 9 cents per American per year.</dd></div>
      <div><dt>Scale</dt><dd>$30 million per year, $300 million total, assuming up to $3,000 per owl (2024 Hoopa Valley grant: $4.5 million for 1,500 owls).</dd></div>
    </dl>
    </div>
  </section>
</div>

<div class="debate">
  <div class="pair">
    <section class="case yes" style="padding-top:24px">
      <h2>The best case for yes</h2>
      <div class="body" data-limit="150" data-name="THE BEST CASE FOR YES">
        <p>We already paid for the first answer to this problem. For thirty years, logging restrictions in the Northwest were supposed to save the spotted owl, and timber towns bore the cost. The owl kept declining anyway, because a larger, more aggressive competitor was evicting it. Habitat protection is necessary, but on its own it has not been enough.</p>
        <p>Unlike most conservation fights, this one has a controlled experiment. Removing barred owls nearly stopped the decline within a decade. The cost is small: about nine cents per American per year. The program is built to be accountable: no lead ammunition, no public hunting, annual reporting, and an automatic kill-switch where it fails.</p>
        <p>If we do nothing, federal biologists say spotted owls will likely go extinct across all or most of their range. Extinction is the one outcome we cannot undo.</p>
      </div>
    </section>
    <section class="case no" style="padding-top:24px">
      <h2>The best case for no</h2>
      <div class="body" data-limit="150" data-name="THE BEST CASE FOR NO">
        <p>This kills a protected North American bird to fix a problem humans started. Critics say habitat loss is the root cause and barred owls are only the latest threat; they argue $300 million buys more if spent protecting forest.</p>
        <p>The program never ends. Barred owls keep arriving from the east, so removal must continue indefinitely or the gains vanish. The experiments covered small sites, and scaling to millions of acres of rugged forest is unproven. More than 75 groups predicted it would fail. No official cost estimate exists; opponents project $1.35 billion for the full 30-year plan.</p>
        <p>Ethically, we are choosing which owl deserves to live. Barred owls did not choose to come west, yet one owl pays for the other's survival. A bipartisan group of lawmakers has called the plan a waste of taxpayer money.</p>
      </div>
    </section>
  </div>
</div>

<div class="wrap">
  <section>
    <div class="fineprint">
      <h2>Where is the body buried?</h2>
      <div class="body" data-limit="100" data-name="WHERE IS THE BODY BURIED?">
        <p>Removal stabilizes spotted owls; it does not rebuild them. Even with removal they still declined 0.2% per year, and no one has shown recovery to a safe population. The experiments ran on limited sites, and barred owls recolonize, so "ten years" probably becomes forever. Cost per owl is uncertain: roughly $800 in FWS's 2013 experiment budget, $3,000 in a 2024 grant. And a kill-switch only works if agencies honestly report failure.</p>
      </div>
    </div>
  </section>

  <section>
    <h2>Why isn't this already happening?</h2>
    <div class="body" data-limit="150" data-name="WHY ISN'T THIS ALREADY HAPPENING?">
      <p>Partly, it is. In 2024 FWS approved a strategy allowing removal of up to 450,000 owls over 30 years, and more than 4,500 have been removed since 2009. But it came with no official cost estimate, and in 2025 the administration canceled three grants supporting removal.</p>
      <p>Why? Concentrated, motivated opposition: a coalition of 240+ organizations, including animal-welfare groups and Audubon chapters, with a simple, emotional message ("shooting owls"), against diffuse support from conservationists who are themselves split. The beneficiary can't vote or donate, and the benefits are slow, hard to see and have no market price, while shotguns and a per-bird price tag are immediate and easy to attack. Politicians in both parties find "wasteful" easy to say. And FWS must effectively permit itself to kill a bird protected by treaty, inviting legal challenge and delay.</p>
    </div>
  </section>

  <section>
    <div class="sources">
      <h2>Sources</h2>
      <p>Check my claims yourself:</p>
      <ul>
        <li>Wiens et al. (2021), "Invader removal triggers competitive release in a threatened avian predator," PNAS: <a href="https://pmc.ncbi.nlm.nih.gov/articles/PMC8346899">pmc.ncbi.nlm.nih.gov/articles/PMC8346899</a> (12.1% vs. 0.2% annual decline)</li>
        <li>U.S. Fish and Wildlife Service, Barred Owl Management Strategy Final EIS FAQs: <a href="https://www.fws.gov/question-answer/barred-owl-management-strategy-final-eis-faqs">fws.gov/question-answer/barred-owl-management-strategy-final-eis-faqs</a> (450,000 maximum, about 15,000 per year, under half of 1% of the North American population per year, 4,500+ removed since 2009)</li>
        <li>FWS 2013 experiment EIS executive summary: <a href="https://fws.gov/sites/default/files/documents/BarredOwl-EIS-ExecSum.pdf">fws.gov/sites/default/files/documents/BarredOwl-EIS-ExecSum.pdf</a> ($2.91 million preferred alternative, 3,603 owls)</li>
        <li>Washington State Standard, July 2025, on the canceled grants, the Hoopa Valley grant and the $1.35 billion estimate: <a href="https://washingtonstatestandard.com/2025/07/22/plans-to-shoot-thousands-of-barred-owls-in-doubt-after-feds-cancel-grants/">washingtonstatestandard.com/2025/07/22/...</a></li>
        <li>Whidbey News-Times on the cost dispute and the 240-organization opposition coalition: <a href="https://www.whidbeynewstimes.com/?p=122771">whidbeynewstimes.com/?p=122771</a></li>
        <li>AP/NPR on the 2024 strategy and spotted owl declines: <a href="https://npr.org/2024/07/04/nx-s1-5029298/spotted-owls-plan-kill-half-million-barred-owls">npr.org/2024/07/04/nx-s1-5029298/...</a></li>
        <li>NBC News on the permit requirement: <a href="https://www.nbcnews.com/news/us-news/federal-agency-plans-cull-450000-barred-owls-boost-another-species-rcna160281">nbcnews.com/news/us-news/...rcna160281</a></li>
      </ul>
    </div>
  </section>
</div>
</main>

<footer>
  <svg class="ridge" id="ridge-near" aria-hidden="true" viewBox="0 0 1600 130" preserveAspectRatio="xMidYMax slice"></svg>
  <div class="eyes" aria-hidden="true"><i></i><i></i></div>
  <div class="wrap">
    <h2>Your turn.</h2>
    <p>Would you take this deal? One tap, no sign-in.</p>
    <a class="cta" href="https://docs.google.com/forms/d/e/1FAIpQLSdSZrW-600K1mJaRM0l2OlY3VMMQRMSgg5dW_Y6Fwa5fShW1g/viewform?usp=header">Cast your vote</a>
  </div>
</footer>

<a class="float" id="float" href="https://docs.google.com/forms/d/e/1FAIpQLSdSZrW-600K1mJaRM0l2OlY3VMMQRMSgg5dW_Y6Fwa5fShW1g/viewform?usp=header">Vote</a>

<script>
  // Draw conifer silhouettes (deterministic, so the skyline never changes between visits).
  function ridge(svgId, color, seed, minH, maxH, step){
    var svg = document.getElementById(svgId), W = 1600, H = 130, x = -20, d = "M-20," + H;
    function rnd(){ seed = (seed * 16807) % 2147483647; return seed / 2147483647; }
    while (x < W + 40){
      var h = minH + rnd() * (maxH - minH), w = h * (0.28 + rnd() * 0.12);
      d += " L" + (x - w).toFixed(1) + "," + H + " L" + x.toFixed(1) + "," + (H - h).toFixed(1) + " L" + (x + w).toFixed(1) + "," + H;
      x += step * (0.6 + rnd() * 0.8);
    }
    d += " L" + (W + 40) + "," + H + " Z";
    svg.innerHTML = '<path d="' + d + '" fill="' + color + '"/>';
  }
  ridge("ridge-far", "#aebfb2", 7, 30, 80, 22);
  ridge("ridge-near", "#1d3430", 11, 45, 120, 26);

  // Hide the floating vote button while the ballot or footer is on screen.
  var fl = document.getElementById("float"), visible = new Set();
  if ("IntersectionObserver" in window){
    var io = new IntersectionObserver(function(es){
      es.forEach(function(e){ e.isIntersecting ? visible.add(e.target) : visible.delete(e.target); });
      fl.classList.toggle("hide", visible.size > 0);
    });
    io.observe(document.getElementById("ballot"));
    io.observe(document.querySelector("footer"));
  }
</script>
</body>
</html>

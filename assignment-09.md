
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
:root{color-scheme:light}
body{margin:0}
img{max-width:100%}
[hidden]{display:none!important}
</style>
<title>Who Pays, Who Owns</title>
<meta name="claude:viewport-fit-sides" content="cover">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Archivo:wdth,wght@62..125,500..900&family=IBM+Plex+Mono:wght@400;500&family=IBM+Plex+Sans:wght@400;500;600&display=swap">
<style>
/* Layout concept: a survey sheet. Big condensed sign-painter type, parcel lines in the margins,
   each case is a bordered "lab" you operate, followed by a question to argue about. */
:root {
  --paper: #EDF0EA;      /* grey-green drafting paper */
  --panel: #F8FAF6;      /* lab surface */
  --ink: #16202A;        /* survey ink */
  --ink-soft: #4A5560;
  --tape: #C2410C;       /* flagging-tape orange, used for action */
  --on-tape: #FFFFFF;
  --field: #2B6A55;      /* field green, used for "changed" */
  --rule: #C3CBC1;
  --display: "Archivo", "Arial Narrow", Arial, sans-serif;
  --body: "IBM Plex Sans", system-ui, -apple-system, "Segoe UI", sans-serif;
  --mono: "IBM Plex Mono", ui-monospace, Menlo, Consolas, monospace;
}
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) {
    --paper: #12181D; --panel: #1A2229; --ink: #E7ECE6; --ink-soft: #A3AEA8;
    --tape: #FF8352; --on-tape: #1A1008; --field: #73C6A8; --rule: #33414B;
    color-scheme: dark;
  }
}
:root[data-theme="dark"] {
  --paper: #12181D; --panel: #1A2229; --ink: #E7ECE6; --ink-soft: #A3AEA8;
  --tape: #FF8352; --on-tape: #1A1008; --field: #73C6A8; --rule: #33414B;
  color-scheme: dark;
}
* { box-sizing: border-box; }
body {
  background: var(--paper); color: var(--ink);
  font: 16px/1.62 var(--body);
  padding-left: max(16px, env(safe-area-inset-left, 0px));
  padding-right: max(16px, env(safe-area-inset-right, 0px));
  padding-block: 0 4rem;
}
.wrap { max-width: 62rem; margin-inline: auto; }
a { color: var(--tape); text-underline-offset: 3px; }
:focus-visible { outline: 2px solid var(--tape); outline-offset: 2px; }
p { margin: 0; max-width: 66ch; }
.mono { font-family: var(--mono); }

/* hero */
.hero { position: relative; overflow: hidden; padding-block: 3.5rem 2rem; }
.plat { position: absolute; right: -2rem; top: 0.5rem; width: min(60%, 440px); opacity: .9; pointer-events: none; }
.plat line, .plat rect { stroke: var(--rule); stroke-width: 1.5; fill: none; }
.plat .stake { stroke: var(--tape); stroke-width: 2; }
.eyebrow { font: 500 .78rem/1.4 var(--mono); letter-spacing: .12em; text-transform: uppercase; color: var(--ink-soft); position: relative; }
h1 {
  position: relative; margin: .6rem 0 1.2rem;
  font-family: var(--display); font-weight: 900; font-stretch: 62%;
  font-size: clamp(3.6rem, 14vw, 9rem); line-height: .86; text-transform: uppercase; letter-spacing: -.005em;
}
h1 span { display: block; }
h1 .owns { color: var(--tape); }
.dek { position: relative; font-size: 1.15rem; max-width: 40rem; }
.how { position: relative; margin-top: 1rem; color: var(--ink-soft); font-size: .95rem; }
.nav { position: relative; display: flex; flex-wrap: wrap; gap: .5rem; margin-top: 1.6rem; }
.nav a {
  font: 500 .78rem/1 var(--mono); letter-spacing: .04em; text-decoration: none; color: var(--ink);
  border: 1px solid var(--ink); padding: .55rem .7rem; border-radius: 2px;
}
.nav a:hover { background: var(--ink); color: var(--paper); }


/* intro, route, parts, bridges */
.intro { position: relative; margin-top: 1.6rem; padding: 1rem 1.1rem; border: 1px solid var(--ink); background: var(--panel); border-radius: 2px; max-width: 46rem; }
.intro p + p { margin-top: .6rem; }
.route { position: relative; margin-top: 1.6rem; display: grid; gap: .6rem; }
.route .part-label { font: 500 .75rem/1 var(--mono); letter-spacing: .1em; text-transform: uppercase; color: var(--tape); margin-top: .6rem; }
.route ol { list-style: none; padding: 0; margin: 0; display: grid; grid-template-columns: repeat(auto-fit, minmax(13rem, 1fr)); gap: .6rem; }
.route li { min-width: 0; }
.route a { display: block; height: 100%; text-decoration: none; color: var(--ink); border: 1px solid var(--ink); padding: .7rem; border-radius: 2px; background: var(--panel); font-weight: 600; }
.route a b { font: 500 .72rem/1 var(--mono); display: block; margin-bottom: .3rem; color: var(--tape); }
.route a span { display: block; font-weight: 400; font-size: .88rem; margin-top: .2rem; color: var(--ink-soft); }
.route a:hover { background: var(--ink); color: var(--paper); }
.route a:hover b, .route a:hover span { color: var(--paper); }
.part { margin-top: 3.5rem; padding: 1.2rem; background: var(--ink); color: var(--paper); border-radius: 2px; }
.part .tag { color: var(--paper); opacity: .75; }
.part h2 { max-width: none; margin: .2rem 0 .6rem; font-size: clamp(1.6rem, 4vw, 2.4rem); }
.part p { max-width: 62ch; }
.part + section { margin-top: 1.5rem; }
.next { margin-top: 1.6rem; font: 500 .85rem/1.3 var(--mono); }
.next a { color: var(--ink); text-decoration-color: var(--tape); text-decoration-thickness: 2px; }


/* instructions inside labs */
.do { margin-bottom: 1rem; padding: .8rem .9rem; border-left: 4px solid var(--field); background: var(--paper); }
.do-l { font: 500 .72rem/1 var(--mono); letter-spacing: .1em; text-transform: uppercase; color: var(--field); display: block; margin-bottom: .5rem; }
.do ol { margin: 0; padding-left: 1.3rem; display: grid; gap: .25rem; max-width: 62ch; }
.do .look { margin-top: .6rem; font-size: .92rem; max-width: 62ch; }
.do .look b { font: 500 .72rem/1 var(--mono); letter-spacing: .08em; text-transform: uppercase; margin-right: .3rem; }

/* sections */
section { padding-block: 3rem 1rem; border-top: 2px solid var(--ink); margin-top: 2rem; scroll-margin-top: 1rem; }
.tag { font: 500 .78rem/1.4 var(--mono); letter-spacing: .1em; text-transform: uppercase; color: var(--tape); margin-bottom: .5rem; }
h2 {
  margin: 0 0 1rem; max-width: 22ch; text-wrap: balance;
  font-family: var(--display); font-weight: 800; font-stretch: 78%;
  font-size: clamp(2rem, 5.4vw, 3.4rem); line-height: 1; letter-spacing: -.005em;
}
.lede { font-size: 1.05rem; }
.lede + .lede { margin-top: .8rem; }
h3 { font: 600 1rem/1.3 var(--body); margin: 0 0 .5rem; }

/* labs */
.lab {
  background: var(--panel); border: 1px solid var(--rule); border-top: 3px solid var(--tape);
  border-radius: 2px; padding: 1.25rem; margin-top: 1.6rem; min-width: 0;
}
.lab-tag { font: 500 .72rem/1 var(--mono); letter-spacing: .12em; text-transform: uppercase; color: var(--ink-soft); margin-bottom: .9rem; }
.btn {
  font: 500 .8rem/1.2 var(--mono); color: var(--ink); background: transparent;
  border: 1px solid var(--ink); padding: .6rem .8rem; border-radius: 2px; cursor: pointer; min-height: 2.5rem;
}
.btn:hover { background: var(--rule); }
.btn[aria-pressed="true"], .btn[aria-selected="true"] { background: var(--ink); color: var(--paper); }
.row { display: flex; flex-wrap: wrap; gap: .5rem; }
label { font: 500 .8rem/1.3 var(--mono); }
input[type=range] { width: 100%; accent-color: var(--tape); }
input[type=number] {
  font: 500 .95rem var(--mono); color: var(--ink); background: var(--paper);
  border: 1px solid var(--ink); border-radius: 2px; padding: .45rem .5rem; width: 100%; min-width: 0;
}
.field { display: flex; flex-direction: column; gap: .3rem; min-width: 0; }
.grid2 { display: grid; grid-template-columns: repeat(auto-fit, minmax(14rem, 1fr)); gap: 1rem; }
.big { font: 800 clamp(1.9rem, 5vw, 2.8rem)/1 var(--display); font-stretch: 78%; letter-spacing: -.005em; font-variant-numeric: tabular-nums; }
.note { font-size: .85rem; color: var(--ink-soft); margin-top: .8rem; }
.ask { margin-top: 1.4rem; padding: 1rem 0 0; border-top: 1px dashed var(--ink-soft); }
.ask strong { font: 500 .75rem/1 var(--mono); letter-spacing: .1em; text-transform: uppercase; color: var(--tape); display: block; margin-bottom: .4rem; }
.ask p + p { margin-top: .6rem; }
.counter { color: var(--ink-soft); font-size: .92rem; }
.counter b { font: 500 .72rem/1 var(--mono); letter-spacing: .1em; text-transform: uppercase; color: var(--ink); }

/* tunnel sorter */
.sort { display: grid; gap: 1rem; }
.sort-item { border-bottom: 1px solid var(--rule); padding-bottom: 1rem; }
.sort-item:last-child { border-bottom: 0; padding-bottom: 0; }
.sort-q { font-weight: 600; margin-bottom: .5rem; }
.verdict { margin-top: .6rem; font-size: .92rem; }
.verdict b { font: 500 .75rem/1 var(--mono); letter-spacing: .08em; text-transform: uppercase; margin-right: .4rem; }
.verdict .ok { color: var(--field); } .verdict .no { color: var(--tape); }

/* terms */
dl.terms { display: grid; grid-template-columns: repeat(auto-fit, minmax(16rem, 1fr)); gap: 1rem; margin: 1.4rem 0 0; }
dl.terms div { border-left: 3px solid var(--ink); padding-left: .8rem; }
dl.terms dt { font: 500 .78rem/1.3 var(--mono); letter-spacing: .08em; text-transform: uppercase; }
dl.terms dd { margin: .25rem 0 0; font-size: .95rem; }

/* role panel */
.panel { margin-top: 1rem; padding: 1rem; border: 1px solid var(--rule); background: var(--paper); min-height: 8.5rem; }
.panel p { margin-top: .6rem; }

/* explanations */
.cols { display: grid; grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr)); gap: 1rem; margin-top: 1rem; }
.cols > div { min-width: 0; }
.kv { font: 500 .72rem/1 var(--mono); letter-spacing: .1em; text-transform: uppercase; color: var(--ink-soft); display: block; margin: .8rem 0 .2rem; }

/* siting */
.switches { display: grid; gap: .6rem; }
.switch { display: flex; gap: .7rem; align-items: flex-start; cursor: pointer; font: 400 .95rem/1.4 var(--body); }
.switch input { width: 1.2rem; height: 1.2rem; margin-top: .15rem; accent-color: var(--tape); flex: none; }
.outcome { margin-top: 1rem; padding: 1rem; border-left: 4px solid var(--tape); background: var(--paper); }
.outcome h3 { margin-bottom: .3rem; }
.chart { width: 100%; height: auto; display: block; margin-top: .6rem; }
.chart .axis { stroke: var(--ink-soft); stroke-width: 1.2; }
.chart .grid { stroke: var(--rule); stroke-width: 1; }
.chart .t { fill: var(--ink-soft); font: 11px var(--mono); }
.chart .te { fill: var(--ink); font: 500 12px var(--mono); }
.legend { display: flex; flex-wrap: wrap; gap: .4rem 1.2rem; font: 500 .78rem/1.3 var(--mono); margin-top: .6rem; }
.legend span { display: inline-flex; align-items: center; gap: .4rem; }
.legend i { width: 1.6rem; height: 0; border-top: 3px solid var(--ink); display: inline-block; }
.legend i.dash { border-top: 3px dashed var(--tape); }
.legend i.solid-tape { border-top-color: var(--tape); }

/* timeline */
.timeline { list-style: none; padding: 0; margin: 1.6rem 0 0; display: grid; grid-template-columns: repeat(auto-fit, minmax(13rem, 1fr)); gap: 1rem; }
.timeline li { border-top: 3px solid var(--ink); padding-top: .6rem; min-width: 0; }
.timeline b { font: 800 2rem/1 var(--display); font-stretch: 70%; display: block; font-variant-numeric: tabular-nums; }
.timeline span { font-size: .92rem; display: block; margin-top: .3rem; }
.parcels { display: grid; gap: 2px; width: min(100%, 20rem); aspect-ratio: 1; background: var(--ink); border: 2px solid var(--ink); }
.parcels i { background: var(--panel); display: block; }
.parcels i:nth-child(3n) { background: var(--rule); }
.parcels.one i { background: var(--tape); }
.frac { display: grid; grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr)); gap: 1.4rem; align-items: start; }
.frac > * { min-width: 0; }

/* ledger */
.ledger { width: 100%; border-collapse: collapse; margin-top: 1rem; font-size: .93rem; }
.ledger th, .ledger td { text-align: left; padding: .6rem .5rem; border-bottom: 1px solid var(--rule); vertical-align: top; }
.ledger th { font: 500 .75rem/1.3 var(--mono); letter-spacing: .08em; text-transform: uppercase; width: 28%; }
.ledger td .pip { font-family: var(--mono); margin-right: .4rem; }
.ledger td.on { color: var(--field); font-weight: 600; }
.ledger td.off { color: var(--ink-soft); }
.scroll { overflow-x: auto; }

/* parks */
.bars { display: grid; gap: .9rem; margin-top: 1rem; }
.bar-label { display: flex; justify-content: space-between; gap: 1rem; font: 500 .8rem/1.3 var(--mono); margin-bottom: .3rem; }
.bar { height: 1.4rem; background: var(--rule); position: relative; }
.bar i { position: absolute; inset: 0 auto 0 0; background: var(--ink); width: 0; }
.bar i.hot { background: var(--tape); }
.ladder { list-style: none; padding: 0; margin: 1.2rem 0 0; display: grid; gap: .6rem; }
.ladder li { padding: .7rem .9rem; border: 1px solid var(--ink); border-radius: 2px; background: var(--panel); }
.ladder li:nth-child(2) { margin-left: 1.2rem; } .ladder li:nth-child(3) { margin-left: 2.4rem; }
.ladder b { font: 500 .75rem/1 var(--mono); letter-spacing: .08em; text-transform: uppercase; display: block; margin-bottom: .2rem; color: var(--tape); }
.box { margin-top: 1.4rem; padding: 1rem; border: 1px solid var(--ink); border-radius: 2px; background: var(--panel); }

/* closing */
.qs { list-style: none; padding: 0; margin: 1.4rem 0 0; display: grid; gap: .9rem; }
.qs li { padding-left: 1.4rem; position: relative; max-width: 66ch; }
.qs li::before { content: ""; position: absolute; left: 0; top: .55rem; width: .7rem; height: .7rem; background: var(--tape); clip-path: polygon(50% 0, 100% 100%, 0 100%); }
.thesis { font: 800 clamp(1.5rem, 4vw, 2.3rem)/1.1 var(--display); font-stretch: 78%; max-width: 28ch; text-wrap: balance; margin-top: 1.6rem; }
footer { margin-top: 3rem; padding-top: 1rem; border-top: 2px solid var(--ink); font-size: .85rem; color: var(--ink-soft); }
footer p { max-width: 72ch; margin-top: .4rem; }
@media (prefers-reduced-motion: no-preference) {
  .bar i { transition: width .25s ease; }
}
@media (max-width: 520px) {
  .ladder li:nth-child(2), .ladder li:nth-child(3) { margin-left: .5rem; }
  .plat { opacity: .45; }
}
</style>

</head>
<body>
<div class="wrap">
  <header class="hero">
    <svg class="plat" viewBox="0 0 400 300" aria-hidden="true">
      <rect x="10" y="10" width="380" height="280"/>
      <line x1="10" y1="110" x2="390" y2="110"/><line x1="10" y1="200" x2="390" y2="200"/>
      <line x1="140" y1="10" x2="140" y2="200"/><line x1="270" y1="10" x2="270" y2="110"/>
      <line x1="200" y1="200" x2="200" y2="290"/><line x1="320" y1="200" x2="320" y2="290"/>
      <line x1="10" y1="60" x2="140" y2="60"/><line x1="270" y1="60" x2="390" y2="60"/>
      <line class="stake" x1="140" y1="110" x2="140" y2="96"/><line class="stake" x1="140" y1="110" x2="154" y2="110"/>
      <line class="stake" x1="270" y1="200" x2="270" y2="186"/><line class="stake" x1="270" y1="200" x2="284" y2="200"/>
    </svg>
    <p class="eyebrow">A field guide to environmental justice and property rights</p>
    <h1><span>Who pays.</span><span class="owns">Who owns.</span></h1>
    <p class="dek">Environmental justice asks who bears the pollution, noise and disruption, and who gets a say. Property rights ask who owns the land and who decides what happens to it. This page follows one argument through seven cases: costs land unevenly, fixes can backfire, and control over land is the missing piece.</p>
    <p class="how">Read it in order. Each case has a box marked Try it, a question to argue about, and a link to the next case.</p>
    <div class="intro">
      <h3>What is environmental justice?</h3>
      <p>It is the idea that no group should carry more than its share of pollution, noise and other environmental harm, and that everyone gets a real say in decisions about the places they live. This page grew out of one student's answers to a course assignment on that idea and on the property rights behind it. No background needed.</p>
    </div>
    <nav class="route" aria-label="The route through the cases">
      <p class="part-label">Part one · Who bears the cost?</p>
      <ol>
        <li><a href="#tunnel"><b>1</b>Tunnel<span>A project helps many and burdens a few.</span></a></li>
        <li><a href="#why"><b>2</b>Why there<span>How do burdens end up in some neighborhoods?</span></a></li>
        <li><a href="#noise"><b>3</b>Noise<span>What if we fix it? Prices rise and residents may leave.</span></a></li>
        <li><a href="#siting"><b>4</b>Siting<span>What if we regulate it? Investment may leave.</span></a></li>
      </ol>
      <p class="part-label">Part two · Who controls the land?</p>
      <ol>
        <li><a href="#title"><b>5</b>Title<span>Tribal trust land limits what owners can do.</span></a></li>
        <li><a href="#words"><b>6</b>Words<span>Does saying land was taken change who decides?</span></a></li>
        <li><a href="#parks"><b>7</b>Parks<span>What would shared or returned control look like?</span></a></li>
      </ol>
    </nav>
  </header>

  <div class="part">
    <p class="tag">Part one</p>
    <h2>Who bears the cost?</h2>
    <p>Start with a real construction project, then ask how burdens end up where they do. Then see what happens when we try to fix or regulate them. In both cases, the people the change is meant to help can still miss out.</p>
  </div>
  <!-- TUNNEL -->
  <section id="tunnel">
    <p class="tag">Step 1 · Burden and benefit</p>
    <h2>The tunnel serves a region. The noise lands on a few blocks.</h2>
    <p class="lede">The Hudson Tunnel Project is building a new rail tunnel between New Jersey and Manhattan. More reliable trains help commuters across both states. Construction brings noise, dust, truck traffic and torn-up roads and sidewalks to the people who live beside the sites.</p>
    <p class="lede">The project's environmental review identified environmental justice communities in New Jersey that construction could affect. The Gateway Development Commission also runs a noise abatement program that helps eligible New Jersey property owners pay for sound-reducing windows.</p>
    <div class="lab">
      <p class="lab-tag">Try it · Guess first</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Read each item.</li><li>Tap who you think mostly feels it: the neighbors, or the whole region.</li><li>Read the note that appears. Change your answer if you like.</li></ol><p class="look"><b>Look for</b>How many benefits are shared widely, and how many costs sit on a few blocks.</p></div>
      <div class="sort" id="sorter"></div>
      <p class="note counter" id="sortScore" aria-live="polite"></p>
    </div>
    <div class="ask">
      <strong>Argue about it</strong>
      <p>When the benefits are regional and the costs are local, who should pay to make the neighbors whole? Is a window grant enough?</p>
      <p>Counterpoint: better public transit has real value, and a project can be worth building even with local costs. The question is whether the people most affected are protected well enough.</p>
    </div>
    <p class="next"><a href="#why">Next: Why there →</a></p>
  </section>

  <!-- WHY -->
  <section id="why">
    <p class="tag">Step 2 · The cause</p>
    <h2>Why do poor neighborhoods end up beside pollution?</h2>
    <p class="lede">The tunnel is one example of a wider pattern. Maps often show lower-income communities close to factories, waste sites and highways. Economists and activists tell two different stories about how that happens. Pick one and see what it predicts.</p>
    <div class="lab">
      <p class="lab-tag">Try it · Compare explanations</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Read the first explanation, Cheap housing.</li><li>Tap the second tab, Weak political voice.</li><li>Compare the line that says what each one predicts.</li></ol><p class="look"><b>Look for</b>The two stories predict opposite orders of events. Both can be true in different places.</p></div>
      <div class="row" role="tablist" aria-label="Explanations" id="whyTabs">
        <button class="btn" role="tab" id="tab-cheap" data-why="cheap" aria-selected="true">Cheap housing</button>
        <button class="btn" role="tab" id="tab-voice" data-why="voice" aria-selected="false">Weak political voice</button>
      </div>
      <div class="panel" id="why-cheap" role="tabpanel">
        <h3>People move to pollution because it is cheaper.</h3>
        <p>Homes near polluting sites are less desirable, so they cost less to rent or buy. Households with less income have fewer options, while wealthier households can pay to move away. Economists call the idea that poor people live in polluted places because cleaner places cost more a folk belief in environmental economics. It treats location as a response to prices.</p>
        <span class="kv">What it predicts</span><p>The pollution is often there first. Housing near it is cheaper, and lower-income residents arrive later.</p>
      </div>
      <div class="panel" id="why-voice" role="tabpanel" hidden>
        <h3>Polluters build where resistance is weakest.</h3>
        <p>Wealthier communities can hire lawyers, show up at hearings and influence local decisions. A community with fewer of those resources has a harder time stopping a facility before it opens.</p>
        <span class="kv">What it predicts</span><p>Residents are often there first. Facilities get sited where opposition is cheapest to overcome.</p>
      </div>
      <p class="note">The two stories are not mutually exclusive. Both can add up to environmental injustice.</p>
    </div>
    <div class="ask">
      <strong>Argue about it</strong>
      <p>Which came first in a place you know, the facility or the residents? What data would you need to find out?</p>
    </div>
    <p class="next"><a href="#noise">Next: Noise →</a></p>
  </section>

  <!-- NOISE -->
  <section id="noise">
    <p class="tag">Step 3 · The fix</p>
    <h2>Quiet a street and the rent may follow.</h2>
    <p class="lede">The obvious fix for a noisy neighborhood is to quiet it, for example with noise barriers along a road. Noise has a price, so quieting it creates value. The reading puts the cost of traffic noise in the tens of billions of dollars and reports home-value effects around 6.8%. On a $300,000 home that is $20,400. The harder question is who keeps that gain.</p>
    <dl class="terms">
      <div><dt>Greenlining</dt><dd>Improving a neighborhood's environment so it becomes more desirable.</dd></div>
      <div><dt>Gentrification</dt><dd>Rising prices and rents push out the residents who lived there first. One quiet street can be both.</dd></div>
    </dl>

    <div class="lab">
      <p class="lab-tag">Try it · Make big numbers readable</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Leave the numbers as they are to see the two estimates as yearly costs.</li><li>Change the years to 10, then to 50.</li><li>Change the discount rate to 0, then to 6.</li></ol><p class="look"><b>Look for</b>More years lower the yearly figure. A higher rate raises it. A huge lump sum can look small per year, so ask which assumptions are doing the work.</p></div>
      <h3>Turn a lump sum into a yearly cost</h3>
      <div class="grid2">
        <div class="field"><label for="tot1">Estimate A ($ billions)</label><input id="tot1" type="number" inputmode="decimal" value="110" min="0" step="0.1"></div>
        <div class="field"><label for="tot2">Estimate B ($ billions)</label><input id="tot2" type="number" inputmode="decimal" value="77.3" min="0" step="0.1"></div>
        <div class="field"><label for="yrs">Years</label><input id="yrs" type="number" inputmode="numeric" value="30" min="1" step="1"></div>
        <div class="field"><label for="rate">Discount rate (%)</label><input id="rate" type="number" inputmode="decimal" value="3" min="0" step="0.1"></div>
      </div>
      <div class="grid2" style="margin-top:1rem">
        <div><span class="kv">Estimate A per year</span><span class="big" id="ann1"></span></div>
        <div><span class="kv">Estimate B per year</span><span class="big" id="ann2"></span></div>
      </div>
      <p class="note">Illustrative annual equivalents under the years and rate you set. They are not figures reported by the study's authors.</p>
    </div>

    <div class="lab">
      <p class="lab-tag">Try it · Who keeps the gain?</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Leave the home value at $300,000 and the rise at 6.8%, or drag the slider to try your own.</li><li>Tap each of the four roles and read the box that appears.</li><li>Tick the protections box, then tap through the four roles again.</li></ol><p class="look"><b>Look for</b>The same noise barrier leaves different people better or worse off. See which role changes the most once protections are on.</p></div>
      <div class="grid2">
        <div class="field"><label for="price">Home value ($)</label><input id="price" type="number" inputmode="numeric" value="300000" min="0" step="10000"></div>
        <div class="field"><label for="pct">Rise in value from the noise barrier: <span id="pctOut">6.8%</span></label><input id="pct" type="range" min="0" max="12" step="0.1" value="6.8"></div>
      </div>
      <div class="row" role="tablist" aria-label="Pick who you are" style="margin-top:1rem" id="roles">
        <button class="btn" role="tab" id="tab-owner" data-role="owner" aria-selected="true">I own my home</button>
        <button class="btn" role="tab" id="tab-renter" data-role="renter" aria-selected="false">I rent</button>
        <button class="btn" role="tab" id="tab-landlord" data-role="landlord" aria-selected="false">I own a building elsewhere</button>
        <button class="btn" role="tab" id="tab-taxpayer" data-role="taxpayer" aria-selected="false">I pay taxes</button>
      </div>
      <label class="switch" style="margin-top:1rem"><input type="checkbox" id="prot"><span>Add anti-displacement protections: rent stabilization where appropriate, property tax relief for eligible lower-income owners</span></label>
      <div class="panel" id="rolePanel" role="tabpanel" aria-live="polite"></div>
    </div>
    <div class="ask">
      <strong>Argue about it</strong>
      <p>Did the noise barrier achieve environmental justice if the people who lived with the noise cannot afford to stay? Environmental justice may need to count both the improvement and who receives the economic gain.</p>
      <p>Counterpoint: protections cost money, and rules that are too tight could discourage new housing and investment. How would you design them?</p>
    </div>
    <p class="next"><a href="#siting">Next: Siting →</a></p>
  </section>

  <!-- SITING -->
  <section id="siting">
    <p class="tag">Step 4 · The rule</p>
    <h2>A rule that protects a community can steer investment away from it.</h2>
    <p class="lede">Fixes are one tool. Rules are another, and they can backfire too. Suppose a biotech company wants a new facility in Greater Boston. It wants to be near universities and hospitals for skilled workers. Now suppose the state adds extra environmental review for projects near environmental justice communities. You are the project manager. Flip the switches.</p>
    <div class="lab">
      <p class="lab-tag">Try it · You are the project manager</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Start with both boxes unticked and read the result.</li><li>Tick the extra review box.</li><li>Then tick the tax credit box too.</li><li>Untick the review box to try the credit alone.</li></ol><p class="look"><b>Look for</b>Extra review alone pushes the project elsewhere. Review plus a credit can keep both the protection and the investment.</p></div>
      <div class="switches">
        <label class="switch"><input type="checkbox" id="review"><span>Extra studies and review for projects near environmental justice communities</span></label>
        <label class="switch"><input type="checkbox" id="incent"><span>State tax credit for companies that hire locally, cut pollution and meet strict standards</span></label>
      </div>
      <div class="outcome" id="siteOut" aria-live="polite"></div>
      <p class="note">A simplified teaching model. Real siting decisions weigh many more factors.</p>
    </div>

    <div class="lab">
      <p class="lab-tag">Try it · How would you test it?</p>
      <div class="do"><span class="do-l">How to read it</span><ol><li>Find the dashed vertical line. That is when the law starts.</li><li>Follow the solid orange line, which is communities under the rule, and the black line, which is similar communities without it.</li><li>The dashed orange line shows where the first group would have gone without the rule. The bar at the right marks the gap.</li></ol><p class="look"><b>Look for</b>Both groups start on similar paths, so the gap after the law starts is the best estimate of what the rule did. This is a simple before-and-after comparison between two groups.</p></div>
      <h3>Compare communities with and without the rule, before and after</h3>
      <div id="didChart"></div>
      <div class="legend">
        <span><i class="solid-tape"></i>Communities under the rule</span>
        <span><i></i>Similar communities without it</span>
        <span><i class="dash"></i>What the first group would have done without the rule</span>
      </div>
      <p class="note">Illustrative shape only, not real data. The gap between the solid orange line and the dashed line is the estimated effect on investment.</p>
      <div class="cols">
        <div><span class="kv">Measure for the environment</span><p>Air pollution, water quality, exposure to noise.</p></div>
        <div><span class="kv">Measure for the economy</span><p>New businesses, construction projects, jobs, property values, housing costs.</p></div>
        <div><span class="kv">Two hypotheses</span><p>The rule lowers pollution exposure. It may also discourage some investment. The comparison shows which effect is bigger.</p></div>
      </div>
    </div>
    <div class="ask">
      <strong>Argue about it</strong>
      <p>The law's goal is to protect communities that carried the heaviest burdens. If it also keeps jobs and tax revenue away, who benefits from avoiding those communities, and what would you add to reward responsible investment there?</p>
    </div>
    <p class="next"><a href="#title">Next: Title (part two) →</a></p>
  </section>

  <div class="part">
    <p class="tag">Part two</p>
    <h2>Who controls the land?</h2>
    <p>Part one showed that cleanup and rules can miss the people they are meant to help. A deeper reason is control. Whoever holds the title decides who can protect a place, develop it or profit from it. Native American land shows what limited control looks like and what more of it could do.</p>
  </div>
  <!-- TITLE -->
  <section id="title">
    <p class="tag">Step 5 · Control</p>
    <h2>You can use the land. You may not control it.</h2>
    <p class="lede">Not all Native American land is owned the same way. Some is privately owned by individuals or tribes. Some is held in trust, where the federal government holds legal title on behalf of a tribe or an individual. Trust land generally cannot be sold or transferred without federal approval, and certain business and recreation leases need approval too.</p>
    <p class="lede">That is unusual. Most private owners in the United States can sell or lease their property freely. For a tribe it can slow everything from an oil and gas deal to a campground.</p>
    <ol class="timeline">
      <li><b>1887</b><span>The General Allotment Act, or Dawes Act, divides commonly held reservation land into individual parcels. Land left over opens to non-Native settlers. Native Americans lose millions of acres.</span></li>
      <li><b>1934</b><span>The Indian Reorganization Act ends the general allotment policy.</span></li>
      <li><b>Today</b><span>Allotted land has passed through generations of heirs. Ownership has splintered into many tiny shares. This is called fractionation.</span></li>
      <li><b>1988</b><span>The Indian Gaming Regulatory Act is passed. Tribal casinos have since produced jobs and revenue for some communities, though location and access to customers shape how well each one does.</span></li>
    </ol>

    <div class="lab">
      <p class="lab-tag">Try it · Watch one parcel splinter</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Leave heirs at 3 and drag Generations from 0 up to 5.</li><li>Then set heirs to 2, and then to 4, and drag Generations again.</li></ol><p class="look"><b>Look for</b>One orange parcel turns into a grid of tiny shares. Count how many owners it takes to agree on a lease by the fifth generation.</p></div>
      <div class="frac">
        <div>
          <div class="field"><label for="heirs">Heirs per generation: <span id="heirsOut">3</span></label><input id="heirs" type="range" min="2" max="4" step="1" value="3"></div>
          <div class="field" style="margin-top:1rem"><label for="gens">Generations: <span id="gensOut">3</span></label><input id="gens" type="range" min="0" max="5" step="1" value="3"></div>
          <span class="kv">Owners of the same parcel</span><span class="big" id="owners"></span>
          <p style="margin-top:.8rem" id="fracText"></p>
          <p class="note">Simplified: every owner splits their share equally among the same number of heirs. Real rules are more varied.</p>
        </div>
        <div id="parcels" class="parcels one" role="img" aria-label="Grid of parcel shares"></div>
      </div>
    </div>
    <div class="ask">
      <strong>Argue about it</strong>
      <p>Casinos succeeded where tribes could use a clear legal framework. Energy, tourism and manufacturing face more approval steps. What would it take to give tribes more flexibility over their land without ending the protections trust status provides?</p>
      <p>Ireland and the Cayman Islands attract investment with simple rules. What differs on a reservation?</p>
    </div>
    <p class="next"><a href="#words">Next: Words →</a></p>
  </section>

  <!-- WORDS -->
  <section id="words">
    <p class="tag">Step 6 · Recognition</p>
    <h2>A statement is not a title.</h2>
    <p class="lede">If control over land matters, what do land acknowledgements do? They name the Native peoples whose land an institution sits on. They are fairly new in how widely universities and organizations use them. Indigenous communities have long had traditions of naming whose land they are on. The recent wave followed Indigenous rights movements, Canada's Truth and Reconciliation Commission report in 2015, and a surge of attention around 2020. The United States has had no nationwide reconciliation process like Canada's.</p>
    <p class="lede">From an economics view, legal ownership decides who chooses how land is used and who earns from it. See what an acknowledgement changes by itself, then add actions.</p>
    <div class="lab">
      <p class="lab-tag">Try it · What actually changes?</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Read the table first. It shows what changes if a university only reads an acknowledgement.</li><li>Tap an action below to add it. Tap it again to remove it.</li><li>Try each action alone, then try Land returned.</li></ol><p class="look"><b>Look for</b>Which rows change with each action. Only one action changes who holds title.</p></div>
      <div class="row" id="acts">
        <button class="btn" data-act="partner" aria-pressed="false">Partnership with a tribe</button>
        <button class="btn" data-act="fund" aria-pressed="false">Funding and programs</button>
        <button class="btn" data-act="co" aria-pressed="false">Co-management</button>
        <button class="btn" data-act="land" aria-pressed="false">Land returned</button>
      </div>
      <div class="scroll"><table class="ledger" id="ledger"><caption class="note" style="text-align:left">Starting point: the acknowledgement alone.</caption><tbody></tbody></table></div>
    </div>

    <div class="box">
      <h3>A university that punished a parody</h3>
      <p>Stuart Reges, a University of Washington professor, wrote a parody of the university's land acknowledgement in his course syllabus. The university investigated and reprimanded him. The Ninth Circuit later ruled that the university violated his First Amendment rights through retaliation and viewpoint discrimination. The court ruled on his right to speak. It did not decide whether his argument about land was correct.</p>
      <p class="note">Why it matters here: a pledge is cheap for an institution to make and costly for an employee to question. Over time everyone may agree in public and differ in private.</p>
    </div>
    <div class="ask">
      <strong>Argue about it</strong>
      <p>What would convince you an acknowledgement helps? One idea: attach a way to act, such as a link to give to a tribal conservation fund, and have the institution report what it does each year.</p>
      <p>Counterpoint: some Native people welcome the recognition, others find it empty without action, and others want institutions to back tribal sovereignty. Many hold more than one view.</p>
      <p>And how far back do we go? Tribes also fought over territory before Europeans arrived. The Beaver Wars were partly a contest for the fur trade. Does that complicate the question of who owned land first, or leave the recent history untouched?</p>
    </div>
    <p class="next"><a href="#parks">Next: Parks →</a></p>
  </section>

  <!-- PARKS -->
  <section id="parks">
    <p class="tag">Step 7 · Control in practice</p>
    <h2>Who should run the national parks?</h2>
    <p class="lede">If recognition is not enough, what would real control look like? National parks make a good test case. The creation of parks such as Yellowstone and Glacier cost Native Americans land, along with rights to hunt, fish and gather. Some tribes now run their own parks. As described in the reading, Ute Mountain Tribal Park charges $50 per person per day, caps visitor numbers and offers guided experiences. Yellowstone charges $35 per car.</p>
    <div class="lab">
      <p class="lab-tag">Try it · The fee gap</p>
      <div class="do"><span class="do-l">What to do</span><ol><li>Drag the group size from 1 up to 8.</li><li>Watch the two bars and the sentence under them.</li></ol><p class="look"><b>Look for</b>Yellowstone charges per car and the tribal park charges per person. At what group size does the gap become large, and who might be priced out?</p></div>
      <div class="field"><label for="party">People in your group: <span id="partyOut">4</span></label><input id="party" type="range" min="1" max="8" step="1" value="4"></div>
      <div class="bars">
        <div><div class="bar-label"><span>Yellowstone, one car</span><span id="yFee"></span></div><div class="bar"><i id="yBar"></i></div></div>
        <div><div class="bar-label"><span>Ute Mountain Tribal Park, per person</span><span id="uFee"></span></div><div class="bar"><i class="hot" id="uBar"></i></div></div>
      </div>
      <p style="margin-top:.8rem" id="feeText"></p>
      <p class="note">Fees as reported in the reading. Check current rates before you visit either place.</p>
    </div>
    <div class="cols">
      <div><h3>The fee argument</h3><p>Higher fees can reduce overcrowding and make visitors pay for the damage they cause. They can also price out lower-income families, which is its own environmental justice problem.</p></div>
      <div><h3>Other ways to earn</h3><p>Guided tours, campgrounds, educational programs and partnerships with local businesses do not rely on entrance fees alone. Monument Valley mixes entrance fees, guides and campgrounds.</p></div>
    </div>
    <ol class="ladder">
      <li><b>Start here</b>Co-management, where a tribe has a real role in decisions alongside the National Park Service.</li>
      <li><b>Then, if the tribe wants</b>More responsibility for specific areas, as trust builds.</li>
      <li><b>Where it makes sense</b>Full tribal control. Not every tribe would want to run a park, and some may prefer conservation to tourism.</li>
    </ol>
    <div class="box">
      <h3>Control includes the right to build</h3>
      <p>In Vancouver, the Squamish Nation is developing housing under its own authority instead of the city's zoning rules, in partnership with a private developer. Some outsiders criticized the project for not fitting their idea of Indigenous tradition.</p>
    </div>
    <div class="ask">
      <strong>Argue about it</strong>
      <p>Who decides what respecting tribal rights looks like? And which rung of the ladder would you start on?</p>
      <p>Counterpoint: some people worry about losing access to public land or about a tribe's capacity to manage a huge area. Federal management has problems of its own, including overcrowding, limited funding and political pressure.</p>
    </div>
    <p class="next"><a href="#close">Next: Putting it together →</a></p>
  </section>

  <!-- CLOSE -->
  <section id="close">
    <p class="tag">Putting it together</p>
    <h2>Three threads.</h2>
    <div class="cols">
      <div><h3>Costs land unevenly</h3><p>Projects help many people and burden a few. Burdens tend to settle where people have the least money and voice.</p></div>
      <div><h3>Fixes and rules can miss the people they aim to help</h3><p>Quieter streets can raise rents. Extra review can steer investment away. Design the protection and the incentive together.</p></div>
      <div><h3>Control decides who benefits</h3><p>Trust-land rules, symbolic statements and park fees show that owning, deciding and earning are different things. Recognition is a start.</p></div>
    </div>
    <h3 style="margin-top:2rem">Questions to answer in your own words</h3>
    <ul class="qs">
      <li>Think of a project near you that helps many people and burdens a few. Who pays, and who is paid back?</li>
      <li>What happened first in a polluted place you know, the facility or the residents?</li>
      <li>If your neighborhood got cleaner, how would you keep your neighbors from being priced out?</li>
      <li>Can a law meant to protect a community also keep investment away? What would fix that?</li>
      <li>What is the difference between saying the land was taken and changing who decides how it is used?</li>
      <li>What would you want to see before you believed a pledge made a difference?</li>
    </ul>
    <p class="thesis">Recognition is a start. Control, incentives and follow-through decide who benefits.</p>
  </section>

  <footer>
    <p>Built from a student's coursework on environmental justice and property rights. Opinions on this page are the student's own, and the counterpoints are there so you can form yours. Figures for noise costs, home values and park fees come from course readings. Projects and programs named in the tunnel case come from the Federal Railroad Administration's environmental justice report and the Gateway Program's noise abatement program pages.</p>
    <p>The court ruling: <a href="https://en.wikipedia.org/wiki/Reges_v._Cauce">Reges v. Cauce</a> and <a href="https://reason.com/2025/12/22/the-9th-circuit-upholds-a-university-of-washington-professors-right-to-mock-land-acknowledgments">coverage from Reason</a>.</p>
  </footer>
</div>

<script>
(function () {
  var $ = function (s, r) { return (r || document).querySelector(s); };
  var $$ = function (s, r) { return Array.prototype.slice.call((r || document).querySelectorAll(s)); };
  var money = function (n) { return '$' + Math.round(n).toLocaleString('en-US'); };

  /* TUNNEL SORTER */
  var items = [
    { t: 'Faster, more reliable trains', a: 'region', n: 'Commuters across New Jersey and New York share this one, including people who never see a construction site.' },
    { t: 'Construction noise and dust', a: 'near', n: 'The people closest to the sites live with this daily for as long as construction lasts.' },
    { t: 'Truck traffic and disrupted roads and sidewalks', a: 'near', n: 'Disruption sits on the blocks around each site.' },
    { t: 'Help paying for sound-reducing windows', a: 'near', n: 'The noise abatement program helps eligible New Jersey property owners. Who counts as eligible, and what does a renter on the same block get?' }
  ];
  var answered = {}, matched = 0;
  var sorter = $('#sorter');
  items.forEach(function (it, i) {
    var d = document.createElement('div');
    d.className = 'sort-item';
    d.innerHTML = '<p class="sort-q">' + it.t + '</p>' +
      '<div class="row"><button class="btn" id="s' + i + 'n" data-i="' + i + '" data-v="near">Mostly the neighbors</button>' +
      '<button class="btn" id="s' + i + 'r" data-i="' + i + '" data-v="region">Mostly the whole region</button></div>' +
      '<p class="verdict" id="v' + i + '" hidden></p>';
    sorter.appendChild(d);
  });
  sorter.addEventListener('click', function (e) {
    var b = e.target.closest('button[data-i]'); if (!b) return;
    var i = +b.dataset.i, it = items[i], ok = b.dataset.v === it.a;
    var prev = answered[i]; answered[i] = ok;
    if (ok && prev !== true) matched++; if (!ok && prev === true) matched--;
    $$('#s' + i + 'n, #s' + i + 'r').forEach(function (x) { x.setAttribute('aria-pressed', x === b ? 'true' : 'false'); });
    var v = $('#v' + i); v.hidden = false;
    v.innerHTML = '<b class="' + (ok ? 'ok' : 'no') + '">' + (ok ? 'Matches' : 'Think again') + '</b>' + it.n;
    $('#sortScore').innerHTML = '<b>Matched</b> ' + matched + ' of ' + items.length;
  });

  /* ANNUALIZER */
  function annuity(total, yrs, ratePct) {
    var r = ratePct / 100;
    if (!(yrs > 0)) return 0;
    if (r === 0) return total / yrs;
    return total * r / (1 - Math.pow(1 + r, -yrs));
  }
  function renderAnn() {
    var y = +$('#yrs').value, r = +$('#rate').value;
    [['#tot1', '#ann1'], ['#tot2', '#ann2']].forEach(function (p) {
      var v = annuity(+$(p[0]).value || 0, y, r);
      $(p[1]).textContent = '$' + v.toFixed(1) + ' billion';
    });
  }
  ['#tot1', '#tot2', '#yrs', '#rate'].forEach(function (s) { $(s).addEventListener('input', renderAnn); });
  renderAnn();

  /* ROLES */
  var role = 'owner';
  function renderRole() {
    var pct = +$('#pct').value, price = Math.max(0, +$('#price').value || 0), prot = $('#prot').checked;
    $('#pctOut').textContent = pct.toFixed(1) + '%';
    var gain = price * pct / 100, h, p;
    if (role === 'owner') {
      h = '+' + money(gain);
      p = 'Your home gains value, and you keep the gain if you sell. ' + (prot ? 'Property tax relief for eligible lower-income owners can keep a higher assessment from turning into a bill you cannot pay.' : 'A higher assessed value can also raise your tax bill.');
    } else if (role === 'renter') {
      h = 'Rent may rise';
      p = 'You get the quiet. Your landlord may raise the rent when your lease ends, because the street is now worth more. ' + (prot ? 'Rent stabilization or assistance can let you stay and enjoy the quiet you lived without.' : 'If you cannot pay, the benefit goes to whoever moves in next.');
    } else if (role === 'landlord') {
      h = '+' + pct.toFixed(1) + '% asset value';
      p = 'On a building worth ' + money(price) + ', that is ' + money(gain) + ' of added value, and you did not live through the noise. ' + (prot ? 'Rent stabilization limits how much of the gain you can pass to tenants.' : 'You may be able to raise rents to match.');
    } else {
      h = 'You share the bill';
      p = 'Public money pays for the barriers, including from people who do not live near the road. ' + (prot ? 'Protections add cost, and they aim to keep the benefit with the people who lived with the noise.' : 'Without protections, taxpayers fund a benefit that others may capture.');
    }
    $('#rolePanel').innerHTML = '<span class="big">' + h + '</span><p>' + p + '</p>';
  }
  $('#roles').addEventListener('click', function (e) {
    var b = e.target.closest('button[data-role]'); if (!b) return;
    role = b.dataset.role;
    $$('#roles .btn').forEach(function (x) { x.setAttribute('aria-selected', x === b ? 'true' : 'false'); });
    renderRole();
  });
  ['#pct', '#price', '#prot'].forEach(function (s) { $(s).addEventListener('input', renderRole); });
  renderRole();

  /* WHY TABS */
  $('#whyTabs').addEventListener('click', function (e) {
    var b = e.target.closest('button[data-why]'); if (!b) return;
    $$('#whyTabs .btn').forEach(function (x) { x.setAttribute('aria-selected', x === b ? 'true' : 'false'); });
    $('#why-cheap').hidden = b.dataset.why !== 'cheap';
    $('#why-voice').hidden = b.dataset.why !== 'voice';
  });

  /* SITING */
  function renderSite() {
    var rv = $('#review').checked, inc = $('#incent').checked, h, p;
    if (!rv && !inc) {
      h = 'You pick on workers and access';
      p = 'Universities and hospitals nearby win. The neighborhood’s history is not part of your math, and neither are its health risks.';
    } else if (rv && !inc) {
      h = 'You may build somewhere else';
      p = 'Extra studies and possible delays add cost near an environmental justice community. A site farther away looks cheaper. The community avoids a new source of pollution and also misses the jobs, businesses and tax revenue.';
    } else if (rv && inc) {
      h = 'Protection and investment can coexist';
      p = 'The credit offsets the extra review for companies that hire locally, cut pollution and meet strict standards. The community keeps its protections and gets a reason to compete for you.';
    } else {
      h = 'Investment without a guarantee';
      p = 'The credit rewards building there, but nothing sets the pollution limits. The proposal here keeps the strict standards and adds the reward.';
    }
    $('#siteOut').innerHTML = '<h3>' + h + '</h3><p>' + p + '</p>';
  }
  ['#review', '#incent'].forEach(function (s) { $(s).addEventListener('input', renderSite); });
  renderSite();

  /* DIFF-IN-DIFF CHART */
  (function () {
    var X0 = 40, STEP = 50, Y0 = 230, K = 9, BASE = 45;
    var xs = function (i) { return X0 + i * STEP; };
    var ys = function (v) { return Y0 - (v - BASE) * K; };
    var ctrl = [], trt = [], cf = [];
    for (var i = 0; i <= 8; i++) {
      ctrl.push(50 + i * 1.5);
      var pre = 48 + i * 1.5;
      trt.push(i <= 4 ? pre : 54 + (i - 4) * 0.5);
      cf.push(i >= 4 ? pre : null);
    }
    var pts = function (arr, from) {
      var s = []; for (var j = from || 0; j < arr.length; j++) if (arr[j] !== null) s.push(xs(j).toFixed(1) + ',' + ys(arr[j]).toFixed(1));
      return s.join(' ');
    };
    var gx = xs(8) + 12, ya = ys(cf[8]), yb = ys(trt[8]);
    var svg = '<svg class="chart" viewBox="0 0 600 280" role="img" aria-label="Illustrative chart: a treated group falls behind a comparison group after the law starts">' +
      '<line class="grid" x1="40" y1="' + ys(50) + '" x2="440" y2="' + ys(50) + '"/>' +
      '<line class="grid" x1="40" y1="' + ys(60) + '" x2="440" y2="' + ys(60) + '"/>' +
      '<line class="axis" x1="40" y1="235" x2="440" y2="235"/><line class="axis" x1="40" y1="20" x2="40" y2="235"/>' +
      '<line class="axis" x1="' + xs(4) + '" y1="20" x2="' + xs(4) + '" y2="235" stroke-dasharray="4 4"/>' +
      '<polyline fill="none" stroke="var(--ink)" stroke-width="3" points="' + pts(ctrl) + '"/>' +
      '<polyline fill="none" stroke="var(--tape)" stroke-width="3" stroke-dasharray="7 5" points="' + pts(cf, 4) + '"/>' +
      '<polyline fill="none" stroke="var(--tape)" stroke-width="3.5" points="' + pts(trt) + '"/>' +
      '<line class="axis" x1="' + gx + '" y1="' + ya + '" x2="' + gx + '" y2="' + yb + '" stroke="var(--tape)" stroke-width="2.5"/>' +
      '<text class="te" x="' + (gx + 10) + '" y="' + ((ya + yb) / 2 - 2) + '">estimated</text>' +
      '<text class="te" x="' + (gx + 10) + '" y="' + ((ya + yb) / 2 + 14) + '">effect</text>' +
      '<text class="t" x="40" y="258">4 years before</text>' +
      '<text class="t" x="' + xs(4) + '" y="258" text-anchor="middle">law starts</text>' +
      '<text class="t" x="440" y="258" text-anchor="end">4 years after</text>' +
      '<text class="t" x="48" y="16">Investment in the community (index)</text></svg>';
    $('#didChart').innerHTML = svg;
  })();

  /* FRACTIONATION */
  function renderFrac() {
    var h = +$('#heirs').value, g = +$('#gens').value;
    $('#heirsOut').textContent = h; $('#gensOut').textContent = g;
    var n = Math.pow(h, g);
    $('#owners').textContent = n.toLocaleString('en-US') + (n === 1 ? ' owner' : ' owners');
    var share = 100 / n;
    $('#fracText').textContent = n === 1
      ? 'One owner decides. A lease needs one signature.'
      : 'Each owner holds about ' + (share >= 1 ? share.toFixed(1) : share.toFixed(2)) + '% of the land. If a lease needed everyone to agree, you would be chasing ' + n.toLocaleString('en-US') + ' signatures. Large companies can absorb that work. A single family usually cannot.';
    var el = $('#parcels'); var cols = Math.ceil(Math.sqrt(n));
    el.style.gridTemplateColumns = 'repeat(' + cols + ', 1fr)';
    el.className = 'parcels' + (n === 1 ? ' one' : '');
    var html = ''; for (var k = 0; k < n; k++) html += '<i></i>';
    el.innerHTML = html;
  }
  ['#heirs', '#gens'].forEach(function (s) { $(s).addEventListener('input', renderFrac); });
  renderFrac();

  /* LEDGER */
  var rows = [
    { k: 'title', n: 'Who holds legal title', l: { 0: 'Unchanged. The institution holds title.', 2: 'Transferred to the tribe.' } },
    { k: 'control', n: 'Who decides how the land is used', l: { 0: 'Unchanged. The institution decides.', 1: 'The tribe has a voice on joint projects.', 2: 'Decisions are shared on the land itself.', 3: 'The tribe decides.' } },
    { k: 'money', n: 'Who earns income from it', l: { 0: 'Unchanged.', 1: 'Funds flow to tribal programs.', 2: 'The tribe earns the income.' } },
    { k: 'aware', n: 'Who learns the history', l: { 1: 'Raised for people who hear it.', 2: 'Raised, with something to do about it.' } }
  ];
  var acts = {
    partner: { control: 1, aware: 2 }, fund: { money: 1, aware: 2 },
    co: { control: 2, aware: 2 }, land: { title: 2, control: 3, money: 2, aware: 2 }
  };
  var on = {};
  function renderLedger() {
    var lv = { title: 0, control: 0, money: 0, aware: 1 };
    Object.keys(on).forEach(function (a) { if (on[a]) Object.keys(acts[a]).forEach(function (k) { lv[k] = Math.max(lv[k], acts[a][k]); }); });
    var html = '';
    rows.forEach(function (r) {
      var l = lv[r.k], changed = r.k === 'aware' ? l > 1 : l > 0, pip = changed || r.k === 'aware' ? '●' : '○';
      html += '<tr><th scope="row">' + r.n + '</th><td class="' + (changed ? 'on' : 'off') + '"><span class="pip" aria-hidden="true">' + pip + '</span>' + r.l[l] + '</td></tr>';
    });
    $('#ledger tbody').innerHTML = html;
  }
  $('#acts').addEventListener('click', function (e) {
    var b = e.target.closest('button[data-act]'); if (!b) return;
    var a = b.dataset.act; on[a] = !on[a];
    b.setAttribute('aria-pressed', on[a] ? 'true' : 'false');
    renderLedger();
  });
  renderLedger();

  /* PARKS */
  function renderParks() {
    var n = +$('#party').value, u = 50 * n, y = 35, max = 400;
    $('#partyOut').textContent = n;
    $('#yFee').textContent = '$35 per car';
    $('#uFee').textContent = '$' + u + ' per day for ' + n;
    $('#yBar').style.width = (y / max * 100) + '%';
    $('#uBar').style.width = (u / max * 100) + '%';
    var per = y / n;
    $('#feeText').textContent = 'A group of ' + n + ' in one car pays $' + per.toFixed(2).replace(/\.00$/, '') + ' each at Yellowstone and $50 each at Ute Mountain. The tribal park trades a higher price for fewer visitors and a guided experience. Who can afford that trade?';
  }
  $('#party').addEventListener('input', renderParks);
  renderParks();
})();
</script>

</body>
</html>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Floodwater Prevention Ballot Initiative</title>
    <style>
        :root {
            --navy: #173b57;
            --blue: #247ba0;
            --light: #edf6fa;
            --green: #3b806b;
            --text: #263746;
        }

        * {
            box-sizing: border-box;
        }

        body {
            margin: 0;
            font-family: Arial, sans-serif;
            line-height: 1.7;
            color: var(--text);
            background: #f4f7f9;
        }

        header {
            background: linear-gradient(135deg, #173b57, #247ba0);
            color: white;
            padding: 65px 20px;
            text-align: center;
        }

        header h1 {
            font-size: clamp(2rem, 5vw, 3.4rem);
            margin-bottom: 12px;
        }

        header p {
            max-width: 720px;
            margin: auto;
            font-size: 1.1rem;
        }

        nav {
            background: white;
            padding: 15px;
            text-align: center;
            position: sticky;
            top: 0;
            box-shadow: 0 2px 8px #00000012;
        }

        nav a {
            color: var(--navy);
            text-decoration: none;
            margin: 0 12px;
            font-weight: bold;
            font-size: 0.95rem;
        }

        nav a:hover {
            color: var(--blue);
        }

        main {
            max-width: 1000px;
            margin: 35px auto;
            padding: 0 20px;
        }

        section {
            background: white;
            padding: 30px;
            margin-bottom: 25px;
            border-radius: 12px;
            box-shadow: 0 3px 12px #00000008;
        }

        h2 {
            color: var(--navy);
            margin-top: 0;
        }

        h3 {
            color: var(--blue);
        }

        .ballot {
            border-left: 6px solid var(--green);
            background: var(--light);
            padding: 25px;
            border-radius: 8px;
        }

        .choice {
            display: block;
            margin: 12px 0;
            padding: 13px;
            background: white;
            border: 1px solid #c9d8e0;
            border-radius: 7px;
            cursor: pointer;
        }

        .choice input {
            margin-right: 10px;
        }

        .columns {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
        }

        .panel {
            padding: 20px;
            background: var(--light);
            border-radius: 8px;
        }

        .button {
            background: var(--navy);
            color: white;
            border: none;
            border-radius: 6px;
            padding: 12px 22px;
            font-size: 1rem;
            cursor: pointer;
        }

        .button:hover {
            background: var(--blue);
        }

        .note {
            color: #5b6b78;
            font-size: 0.9rem;
        }

        li {
            margin-bottom: 9px;
        }

        footer {
            text-align: center;
            padding: 30px 20px;
            background: var(--navy);
            color: white;
        }

        a {
            overflow-wrap: anywhere;
        }

        @media (max-width: 600px) {
            nav {
                position: static;
                line-height: 2.2;
            }

            section {
                padding: 22px;
            }
        }
    </style>
</head>

<body>

<header>
    <h1>Floodwater Prevention Ballot Initiative</h1>
    <p>A proposal to help communities reduce flooding, protect homes and businesses, and invest in more resilient infrastructure.</p>
</header>

<nav>
    <a href="#problem">The Problem</a>
    <a href="#proposal">Proposal</a>
    <a href="#arguments">Arguments</a>
    <a href="#feasibility">Feasibility</a>
    <a href="#sources">Sources</a>
    <a href="#vote">Ballot</a>
</nav>

<main>

<section id="problem">
    <h2>1. The Problem: Flooding and Stormwater Runoff</h2>

    <p>Flooding can damage homes, businesses, roads, and public infrastructure. In developed areas, pavement, rooftops, and parking lots prevent rainwater from soaking naturally into the ground. As a result, large amounts of water flow into storm drains and low-lying areas, sometimes overwhelming existing drainage systems.</p>

    <p>The U.S. Environmental Protection Agency explains that green infrastructure can help manage stormwater and reduce localized flooding. Examples include rain gardens, permeable pavement, and systems that temporarily store rainwater.</p>

    <p>Communities need a strategy that combines traditional drainage improvements with natural methods of absorbing and storing water. The goal is not to eliminate every flood, but to reduce preventable damage and make neighborhoods more resilient.</p>

    <p>Source: <a href="https://www.epa.gov/green-infrastructure/mitigate-flooding" target="_blank" rel="noopener">U.S. EPA — Mitigate Flooding</a></p>
</section>

<section id="proposal">
    <h2>2. The Proposed Solution</h2>

    <p>The Floodwater Prevention Ballot Initiative would establish a publicly funded flood-prevention program. The program would identify areas with recurring stormwater problems and invest in projects designed to capture, absorb, and temporarily store excess rainwater before it overwhelms streets and drainage systems.</p>

    <h3>What would the initiative fund?</h3>

    <div class="columns">
        <div class="panel">
            <h3>Rain Gardens and Bioswales</h3>
            <p>Install planted areas that collect runoff from roads, sidewalks, and rooftops, allowing water to soak into the soil or drain more slowly.</p>
        </div>

        <div class="panel">
            <h3>Permeable Pavement</h3>
            <p>Use suitable pavement in selected parking lots, walkways, and other locations so rainwater can pass through the surface into underlying storage layers.</p>
        </div>

        <div class="panel">
            <h3>Stormwater Storage</h3>
            <p>Build or improve retention areas, underground storage, and drainage infrastructure where engineering assessments show they would be effective.</p>
        </div>

        <div class="panel">
            <h3>Flood-Risk Mapping</h3>
            <p>Identify repeatedly flooded locations and prioritize projects based on expected risk reduction, cost, and the number of residents and properties protected.</p>
        </div>
    </div>

    <h3>How would the program work?</h3>

    <ol>
        <li>Conduct a community-wide assessment of flooding and stormwater problems.</li>
        <li>Publish a list of proposed projects, estimated costs, and expected benefits.</li>
        <li>Prioritize locations with repeated flooding, vulnerable infrastructure, and limited capacity to recover from flood damage.</li>
        <li>Construct projects in phases, starting with those expected to deliver the greatest benefits for their cost.</li>
        <li>Publish annual reports on spending, project performance, and maintenance.</li>
    </ol>

    <p>The program would complement existing storm drains, pipes, and other flood-control infrastructure rather than replace them entirely.</p>

    <p>Technical background: <a href="https://www.epa.gov/green-infrastructure/types-green-infrastructure" target="_blank" rel="noopener">U.S. EPA — Types of Green Infrastructure</a></p>
</section>

<section id="funding">
    <h2>3. Funding and Accountability</h2>

    <p>The initiative would authorize the community to develop a dedicated flood-prevention budget. The final funding mechanism and amount would be determined through local financial and legal review before the measure is placed on an official ballot.</p>

    <p>Possible funding sources include:</p>

    <ul>
        <li>A voter-approved bond or other locally authorized public funding mechanism.</li>
        <li>Eligible state and federal flood-mitigation grants.</li>
        <li>Existing stormwater-management funds, where legally permitted.</li>
        <li>Public-private partnerships for projects that provide shared benefits.</li>
    </ul>

    <p>Public funds would be subject to annual financial reporting, independent audits where required, and public disclosure of project costs. Funding should be allocated according to demonstrated flood risk and expected public benefit.</p>

    <p class="note">This is a proposed policy framework, not an existing government program. Specific taxes, fees, bond amounts, and voting procedures would require jurisdiction-specific review.</p>
</section>

<section id="arguments">
    <h2>4. Arguments For and Against</h2>

    <div class="columns">
        <div class="panel">
            <h3>Arguments in Favor</h3>
            <ul>
                <li><strong>Less flood damage:</strong> Capturing runoff may reduce water accumulation in vulnerable areas.</li>
                <li><strong>Multiple benefits:</strong> Green infrastructure can also improve water quality and add vegetation to developed areas.</li>
                <li><strong>Long-term planning:</strong> Preventive investment may reduce some future repair and recovery costs.</li>
                <li><strong>Better targeting:</strong> Public risk assessments can help direct resources to neighborhoods with the greatest needs.</li>
                <li><strong>Flexible solutions:</strong> Projects can be adapted to local geography and existing infrastructure.</li>
            </ul>
        </div>

        <div class="panel">
            <h3>Arguments Against</h3>
            <ul>
                <li><strong>Upfront costs:</strong> Construction and engineering may require substantial public investment.</li>
                <li><strong>Ongoing maintenance:</strong> Drainage systems, vegetation, and permeable surfaces require upkeep.</li>
                <li><strong>Limited effectiveness:</strong> Green infrastructure alone cannot prevent every major flood.</li>
                <li><strong>Unequal benefits:</strong> Poorly planned projects might protect some areas more than others.</li>
                <li><strong>Funding concerns:</strong> Taxes, fees, or borrowing could place burdens on residents.</li>
            </ul>
        </div>
    </div>

    <p>A responsible version of the initiative would address these concerns through phased construction, transparent budgeting, independent engineering reviews, and clear performance measures.</p>
</section>

<section id="feasibility">
    <h2>5. Feasibility Analysis</h2>

    <h3>Technical feasibility</h3>
    <p>The underlying methods are already used in stormwater management. The EPA documents the use of rain gardens, permeable pavement, retention systems, and related green infrastructure. However, each location would need to be evaluated for soil conditions, drainage capacity, groundwater, and flood type.</p>

    <h3>Economic feasibility</h3>
    <p>The program could be implemented gradually instead of funding every project at once. Before construction, officials should compare estimated construction and maintenance costs with expected reductions in property damage, infrastructure repairs, and other flood-related losses. Grant funding could reduce the local financial burden when projects qualify.</p>

    <h3>Political feasibility</h3>
    <p>Residents may support reducing flood damage but disagree about how the program should be funded. Publishing cost estimates, explaining who benefits, and reporting measurable results could help voters evaluate the trade-offs.</p>

    <h3>Environmental feasibility</h3>
    <p>Vegetated stormwater systems can help filter pollutants and provide additional environmental benefits. However, designs must be appropriate for the site, and contaminated land or unsuitable soil may limit infiltration. The program should also preserve existing wetlands and avoid transferring flood risks to other neighborhoods.</p>

    <h3>How would success be measured?</h3>
    <ul>
        <li>Changes in runoff volume at completed project sites.</li>
        <li>Frequency and severity of flooding at targeted locations.</li>
        <li>Number of homes, businesses, roads, and public facilities benefiting.</li>
        <li>Construction and maintenance costs compared with original estimates.</li>
        <li>Distribution of investments across neighborhoods with different levels of flood risk.</li>
    </ul>

    <p><strong>Overall assessment:</strong> The initiative is technically plausible because it builds on established stormwater-management methods. Its overall feasibility depends on local flood conditions, available land, engineering studies, funding, and long-term maintenance. It should be presented as a way to reduce flood risk, not eliminate flooding entirely.</p>

    <p>Additional resource: <a href="https://www.epa.gov/water-research/storm-water-management-model-swmm" target="_blank" rel="noopener">U.S. EPA — Storm Water Management Model</a></p>
</section>

<section id="sources">
    <h2>6. Sources and Further Reading</h2>

    <ol>
        <li>
            <a href="https://www.epa.gov/green-infrastructure/mitigate-flooding" target="_blank" rel="noopener">U.S. Environmental Protection Agency — Mitigate Flooding</a>
            <p>Explains how green infrastructure and floodplain management can help reduce flood risk.</p>
        </li>

        <li>
            <a href="https://www.epa.gov/green-infrastructure/types-green-infrastructure" target="_blank" rel="noopener">U.S. Environmental Protection Agency — Types of Green Infrastructure</a>
            <p>Describes rain gardens, permeable pavement, green roofs, and other stormwater-management methods.</p>
        </li>

        <li>
            <a href="https://www.epa.gov/water-research/storm-water-management-model-swmm" target="_blank" rel="noopener">U.S. Environmental Protection Agency — Storm Water Management Model</a>
            <p>Provides information about modeling runoff and evaluating green infrastructure practices.</p>
        </li>

        <li>
            <a href="https://www.fema.gov/sites/default/files/documents/fema_resilience_nature-based-solutions-fact-sheet.pdf" target="_blank" rel="noopener">Federal Emergency Management Agency — Nature-Based Solutions Fact Sheet</a>
            <p>Discusses nature-based solutions and federal hazard-mitigation funding programs.</p>
        </li>
    </ol>

    <p class="note">These sources support the technical background of the proposal. The specific ballot measure, funding plan, and projected local results are proposed ideas and would need additional local research.</p>
</section>

<section id="vote">
    <h2>7. Sample Ballot</h2>

    <div class="ballot">
        <h3>Floodwater Prevention Initiative</h3>

        <p><strong>Ballot question:</strong></p>

        <p>Should the community establish a publicly accountable flood-prevention program to identify high-risk areas and invest in stormwater infrastructure, rain gardens, permeable pavement, and other measures intended to reduce flood damage, subject to available funding, engineering review, and public reporting?</p>

        <form id="ballotForm">
            <label class="choice">
                <input type="radio" name="vote" value="yes" required>
                <strong>YES</strong> — Support establishing the program.
            </label>

            <label class="choice">
                <input type="radio" name="vote" value="no">
                <strong>NO</strong> — Oppose establishing the program.
            </label>

            <button class="button" type="submit">Submit Sample Vote</button>
        </form>

        <p id="voteResult" aria-live="polite"></p>

        <p class="note">This is a demonstration ballot for an educational proposal. It is not an official election, and votes are not saved or transmitted.</p>
    </div>
</section>

</main>

<footer>
    <p>Floodwater Prevention Ballot Initiative</p>
    <p>Building safer, more resilient communities through responsible flood-risk management.</p>
    <p class="note">Educational proposal — not an official government ballot measure.</p>
</footer>

<script>
    document.getElementById("ballotForm").addEventListener("submit", function(event) {
        event.preventDefault();

        const selected = document.querySelector('input[name="vote"]:checked');

        if (!selected) {
            document.getElementById("voteResult").textContent =
                "Please select YES or NO.";
            return;
        }

        const message = selected.value === "yes"
            ? "You selected YES in this sample ballot."
            : "You selected NO in this sample ballot.";

        document.getElementById("voteResult").textContent =
            message + " Your selection has not been saved or transmitted.";
    });
</script>

</body>
</html>
```

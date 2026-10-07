<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#a63b31">
  <title>Shenanigans Inc' TF2 Classified Server</title>
  <style>
    :root {
      --paper: #e8dfcb;
      --paper-light: #f7f1e5;
      --ink: #282521;
      --muted: #645e56;
      --oxide: #a63b31;
      --oxide-dark: #742d28;
      --steel: #303436;
      --steel-light: #555b5c;
      --line: rgba(40, 37, 33, .21);
      --shadow: 0 18px 45px rgba(30, 25, 20, .25);
    }

    * { box-sizing: border-box; }

    html { scroll-behavior: smooth; }

    body {
      margin: 0;
      min-width: 320px;
      color: var(--ink);
      font-family: "Trebuchet MS", "Arial Narrow", Arial, sans-serif;
      background:
        radial-gradient(circle at 10% 4%, rgba(232, 223, 203, .12), transparent 28rem),
        repeating-linear-gradient(135deg, rgba(255,255,255,.027) 0 1px, transparent 1px 6px),
        #24282a;
    }

    body::before {
      content: "";
      position: fixed;
      z-index: -1;
      inset: 0;
      opacity: .18;
      pointer-events: none;
      background-image: radial-gradient(rgba(0,0,0,.6) .65px, transparent .8px);
      background-size: 4px 4px;
      mix-blend-mode: multiply;
    }

    .page {
      width: min(1120px, calc(100% - 32px));
      margin: clamp(18px, 4vw, 58px) auto;
      overflow: hidden;
      background: var(--paper);
      border: 1px solid rgba(255,255,255,.35);
      box-shadow: var(--shadow);
    }

    .masthead {
      position: relative;
      overflow: hidden;
      min-height: 260px;
      padding: clamp(34px, 7vw, 75px) clamp(24px, 7vw, 82px) 42px;
      color: var(--paper-light);
      background:
        linear-gradient(90deg, rgba(0,0,0,.58), rgba(0,0,0,.05)),
        repeating-linear-gradient(90deg, transparent 0 26px, rgba(255,255,255,.04) 26px 28px),
        linear-gradient(135deg, var(--oxide-dark), var(--oxide) 48%, #c55a42);
      isolation: isolate;
    }

    .masthead::after {
      content: "";
      position: absolute;
      z-index: -1;
      width: 340px;
      height: 340px;
      top: -185px;
      right: -70px;
      border: 35px solid rgba(232,223,203,.13);
      border-radius: 50%;
      box-shadow: 0 0 0 25px rgba(35, 29, 25, .08), 0 0 0 58px rgba(232,223,203,.08);
      transform: rotate(16deg);
    }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 9px;
      margin: 0 0 18px;
      color: rgba(247,241,229,.83);
      font-size: .73rem;
      font-weight: 800;
      letter-spacing: .19em;
      text-transform: uppercase;
    }

    .eyebrow::before, .eyebrow::after {
      content: "";
      width: 22px;
      height: 2px;
      background: currentColor;
    }

    h1, h2, p { margin-top: 0; }

    h1 {
      max-width: 800px;
      margin-bottom: 16px;
      font-family: Impact, "Arial Narrow", sans-serif;
      font-size: clamp(2.35rem, 6vw, 5rem);
      font-weight: 400;
      line-height: .95;
      letter-spacing: .035em;
      text-shadow: 3px 4px 0 rgba(77, 29, 25, .55);
      text-transform: uppercase;
    }

    .welcome {
      max-width: 610px;
      margin-bottom: 0;
      font-size: clamp(1rem, 2vw, 1.18rem);
      font-weight: 700;
      line-height: 1.5;
    }

    .content { padding: clamp(24px, 5vw, 60px); }

    .section-heading {
      display: flex;
      align-items: center;
      gap: 14px;
      margin: 0 0 21px;
      color: var(--steel);
      font-family: Impact, "Arial Narrow", sans-serif;
      font-size: clamp(1.65rem, 3vw, 2.25rem);
      font-weight: 400;
      letter-spacing: .05em;
      line-height: 1;
      text-transform: uppercase;
    }

    .section-heading::after {
      content: "";
      flex: 1;
      height: 7px;
      background: repeating-linear-gradient(90deg, var(--steel) 0 18px, transparent 18px 24px);
      opacity: .8;
    }

    .rules { margin-bottom: clamp(38px, 6vw, 66px); }

    .rule-list {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 12px;
      padding: 0;
      margin: 0;
      list-style: none;
      counter-reset: rules;
    }

    .rule {
      position: relative;
      min-height: 150px;
      padding: 23px 22px 20px 70px;
      border: 1px solid var(--line);
      background: rgba(247, 241, 229, .7);
      box-shadow: 0 3px 0 rgba(48,52,54,.1);
      transition: transform .2s ease, box-shadow .2s ease, border-color .2s ease;
      counter-increment: rules;
    }

    .rule::before {
      content: counter(rules, decimal-leading-zero);
      position: absolute;
      top: 18px;
      left: 18px;
      color: var(--oxide);
      font-family: Impact, "Arial Narrow", sans-serif;
      font-size: 1.65rem;
      line-height: 1;
      letter-spacing: .04em;
    }

    .rule::after {
      content: "";
      position: absolute;
      top: 17px;
      bottom: 17px;
      left: 56px;
      width: 1px;
      background: var(--line);
    }

    .rule:hover {
      z-index: 1;
      border-color: rgba(166,59,49,.52);
      box-shadow: 0 8px 20px rgba(40,37,33,.14);
      transform: translateY(-3px);
    }

    .rule h3 {
      margin: 0 0 8px;
      color: var(--steel);
      font-size: 1rem;
      letter-spacing: .035em;
      line-height: 1.2;
      text-transform: uppercase;
    }

    .rule p {
      margin: 0;
      color: var(--muted);
      font-family: Georgia, "Times New Roman", serif;
      font-size: .97rem;
      line-height: 1.47;
    }

    .proximity-path {
      display: block;
      margin-top: 13px;
      padding: 9px 10px;
      border-left: 3px solid var(--oxide);
      color: var(--steel);
      background: rgba(166,59,49,.08);
      font-family: "Courier New", monospace;
      font-size: .8rem;
      font-weight: 700;
      line-height: 1.4;
    }

    .command-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 12px;
      margin-bottom: clamp(38px, 6vw, 66px);
    }

    .command {
      padding: 22px;
      color: var(--paper-light);
      background: var(--steel);
      border-top: 5px solid var(--oxide);
      box-shadow: inset 0 1px rgba(255,255,255,.11), 0 5px 0 rgba(20, 22, 22, .28);
      transition: transform .2s ease, background .2s ease;
    }

    .command:hover { background: var(--steel-light); transform: translateY(-3px); }

    .command code {
      display: block;
      margin-bottom: 14px;
      color: #fff8e9;
      font-family: "Courier New", monospace;
      font-size: 1.25rem;
      font-weight: 700;
    }

    .command p {
      margin: 0;
      color: rgba(247,241,229,.78);
      font-family: Georgia, "Times New Roman", serif;
      font-size: .94rem;
      line-height: 1.45;
    }

    .discord {
      position: relative;
      padding: clamp(28px, 5vw, 52px);
      overflow: hidden;
      color: var(--paper-light);
      text-align: center;
      background: linear-gradient(135deg, #3f4748, #282d2f);
      border-bottom: 7px solid var(--oxide);
    }

    .discord::before, .discord::after {
      content: "";
      position: absolute;
      width: 165px;
      height: 165px;
      border: 20px solid rgba(247,241,229,.045);
      border-radius: 50%;
    }

    .discord::before { top: -104px; left: -42px; }
    .discord::after { right: -70px; bottom: -115px; }

    .discord .section-heading { justify-content: center; color: var(--paper-light); }
    .discord .section-heading::before, .discord .section-heading::after {
      content: "";
      flex: 0 1 68px;
      height: 7px;
      background: repeating-linear-gradient(90deg, var(--paper-light) 0 18px, transparent 18px 24px);
      opacity: .55;
    }

    .discord a {
      position: relative;
      display: inline-block;
      margin: 4px 0 19px;
      padding: 12px 18px;
      color: #fff9ed;
      outline: 1px solid rgba(255,255,255,.35);
      outline-offset: 4px;
      font-family: "Courier New", monospace;
      font-size: clamp(1rem, 2.8vw, 1.35rem);
      font-weight: 700;
      letter-spacing: .02em;
      text-decoration: none;
      background: var(--oxide);
      transition: background .2s ease, transform .2s ease;
    }

    .discord a:hover, .discord a:focus-visible { background: #c34e3d; transform: translateY(-2px); }
    .discord a:focus-visible { outline: 3px solid #fff9ed; outline-offset: 5px; }

    .discord p {
      position: relative;
      max-width: 570px;
      margin: 0 auto;
      color: rgba(247,241,229,.85);
      font-family: Georgia, "Times New Roman", serif;
      line-height: 1.55;
    }

    footer {
      padding: 34px 24px 39px;
      color: var(--paper-light);
      text-align: center;
      background: #1e2223;
    }

    footer h2 {
      margin: 0 0 9px;
      color: var(--paper-light);
      font-family: Impact, "Arial Narrow", sans-serif;
      font-size: clamp(1.65rem, 4vw, 2.45rem);
      font-weight: 400;
      letter-spacing: .075em;
      text-transform: uppercase;
    }

    footer p {
      margin: 0;
      color: #d2c8b7;
      font-size: .86rem;
      font-weight: 700;
      letter-spacing: .16em;
      text-transform: uppercase;
    }

    @media (max-width: 760px) {
      .rule-list { grid-template-columns: 1fr; }
      .command-grid { grid-template-columns: 1fr; }
      .command { padding: 19px 20px; }
    }

    @media (prefers-reduced-motion: reduce) {
      html { scroll-behavior: auto; }
      *, *::before, *::after { transition-duration: .01ms !important; }
    }
  </style>
</head>
<body>
  <main class="page">
    <header class="masthead">
      <p class="eyebrow">TF2 Classified Server</p>
      <h1>Welcome to Shenanigans Inc' TF2 Classified Server!</h1>
      <p class="welcome">We're glad to have you here! Enjoy your stay and HAVE FUN!</p>
    </header>

    <div class="content">
      <section class="rules" aria-labelledby="rules-heading">
        <h2 class="section-heading" id="rules-heading">Server Rules</h2>
        <ol class="rule-list">
          <li class="rule">
            <h3>No Slurs &amp; Hate Speech</h3>
            <p>Homophobic/transphobic language, racial slurs, and general racism are not permitted. Joking, quoting, or censoring a slur is not permitted. General swearing is allowed unless directed at another player as harassment.</p>
          </li>
          <li class="rule">
            <h3>No NSFW/Offensive Sprays</h3>
            <p>Sprays containing nudity, revealing clothing, sexual themes, or racist content are not permitted.</p>
          </li>
          <li class="rule">
            <h3>No Micspamming</h3>
            <p>Do not excessively spam sounds, music, or voice chat. If you want to play music or sounds, use proximity chat:</p>
            <span class="proximity-path">Options &gt; Audio &gt; Voice &gt; Enable Proximity Chat</span>
          </li>
          <li class="rule">
            <h3>No Cheating/Exploiting</h3>
            <p>Cheats, exploits, OOB (Out Of Bounds), and unintended game advantages are not permitted.</p>
          </li>
          <li class="rule">
            <h3>Remain Civil</h3>
            <p>Treat other players with respect. Do not harass other members. This is a safe and inclusive server for everyone to enjoy the TF2 Classified CW Server.</p>
          </li>
          <li class="rule">
            <h3>Reports &amp; Ban Appeals</h3>
            <p>Player reports must be submitted through our Discord. Ban appeals for regular bans and communication bans must also be submitted through our Discord.</p>
          </li>
          <li class="rule">
            <h3>No Political or Religious Speech</h3>
            <p>Keep political and religious discussions out of the server. This is a place to enjoy TF2 Classified and custom weapons, not discuss real-world events.</p>
          </li>
        </ol>
      </section>

      <section aria-labelledby="commands-heading">
        <h2 class="section-heading" id="commands-heading">Commands</h2>
        <div class="command-grid">
          <article class="command">
            <code>!rtv</code>
            <p>Vote to change the current map.</p>
          </article>
          <article class="command">
            <code>/calladmin</code>
            <p>Call an administrator for assistance.</p>
          </article>
          <article class="command">
            <code>/mm or /equip</code>
            <p>Access female models or donor models.</p>
          </article>
        </div>
      </section>
    </div>

    <section class="discord" aria-labelledby="discord-heading">
      <h2 class="section-heading" id="discord-heading">Community Discord</h2>
      <a href="https://discord.gg/sinc">https://discord.gg/sinc</a>
      <p>Join our community for reports, ban appeals, support, announcements, and discussion.</p>
    </section>

    <footer>
      <h2>Thanks for Playing!</h2>
      <p>Have Fun and Good Luck!</p>
    </footer>
  </main>
</body>
</html>

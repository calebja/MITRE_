# MITRE ATT&CK Chain Simulator

A small, self-contained web application that models a controlled "cyber range" exercise: pick an attack scenario, choose which security controls are live, run the simulated kill chain, and see which stages would have been detected.

**This is a simulation, not an attack tool.** No real network, host, or account is touched. Every stage outcome is computed from a simple detection-probability model in the browser. There is no attack code, exploit code, or external calls of any kind.

## What it does

- **Scenario Picker** - Three example kill chains (phishing-led compromise, ransomware staging, insider misuse), each mapped loosely to MITRE ATT&CK tactics and technique IDs.
- **Control Toggles** - Turn simulated security controls on/off: email security gateway, EDR, MFA, SIEM correlation, network firewall/IDS, DLP.
- **Attack Chain View** - The six-stage flow (Phishing → Credential Theft → Initial Access → Privilege Escalation → Lateral Movement → Data Collection) lights up stage by stage as the simulation runs.
- **Sensor Log** - Running console of which control (if any) "caught" each stage.
- **Results Table** - Final detected/undetected summary per MITRE tactic, e.g.:

  ```
  ATTACK                 DETECTED?
  ────────────────────────────────
  Initial Access             ✓
  Credential Access          ✓
  Privilege Escalation       ✗
  Lateral Movement           ✓
  Data Collection            ✗
  ```

## Running it

It's a single static HTML file with no build step and no dependencies.

- **Locally:** open `index.html` in any browser.
- **GitHub Pages:** enable Pages on this repo (Settings → Pages → Deploy from branch → `main` / root) and it will be served directly, since the app is named `index.html`.

## Project structure

```
.
├── index.html   # the entire app: markup, styles, and simulation logic
├── README.md
└── LICENSE
```

## Customizing

Everything lives in `index.html`:

- `SCENARIOS` — add or edit kill chains, stage labels, ATT&CK technique IDs, and per-control detection probabilities per stage.
- `CONTROLS` — add or rename simulated security controls.
- The results table folds any stage with a `fold` property into the tactic it names, so you can add sub-steps without changing the final report format.

## License

MIT — see [LICENSE](LICENSE).

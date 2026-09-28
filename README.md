# MITRE ATT&CK Chain Simulator

![MITRE ATT&CK](https://img.shields.io/badge/MITRE_ATT%26CK-technique_mapping-B91C1C)
![Type](https://img.shields.io/badge/type-cyber_range_simulation-183A61)
![Stack](https://img.shields.io/badge/stack-HTML%20%2B%20JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Dependencies](https://img.shields.io/badge/dependencies-none-2EA44F)
![Build](https://img.shields.io/badge/build-no_build_step-557C94)
![Hosting](https://img.shields.io/badge/deploy-GitHub%20Pages-222222?logo=githubpages&logoColor=white)
![Safety](https://img.shields.io/badge/no_real_attack_code-simulation_only-orange)
![License](https://img.shields.io/github/license/calebja/MITRE_ATT-CK_Simulator?color=green)

A small, self-contained web application that models a controlled "cyber range" exercise: pick an attack scenario, choose which security controls are live, run the simulated kill chain, and see which stages would have been detected.

**This is a simulation, not an attack tool.** No real network, host, or account is touched. Every stage outcome is computed from a simple detection-probability model in the browser. There is no attack code, exploit code, or external calls of any kind.

## Functions

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

## Running the Simulation

It's a single static HTML file with no build step and no dependencies.

- **Locally:** open `index.html` in any browser.
- **GitHub Pages:** enable Pages on this repo (Settings → Pages → Deploy from branch → `main` / root) and it will be served directly, since the app is named `index.html`.

## Repo Structure

```
.
├── index.html   # the entire app: markup, styles, and simulation logic
├── README.md
└── LICENSE
```

## Customizing

Important project materials live in `index.html`:

- `SCENARIOS` — Add or edit kill chains, stage labels, ATT&CK technique IDs, and per-control detection probabilities per stage.
- `CONTROLS` — Add or rename simulated security controls.
- The results table folds any stage with a `fold` property into the tactic it names, so you can add sub-steps without changing the final report format.

## License

MIT — see [LICENSE](LICENSE).

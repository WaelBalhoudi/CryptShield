# CryptShield 🛡️

### Cryptographic Attack Simulation, Ransomware Detection & Data Recovery Platform

**CryptShield** is a cybersecurity research project designed to study cryptographic weaknesses, simulate ransomware-like behavior in a controlled laboratory, evaluate defensive mechanisms, and verify data recovery through cryptographic integrity checks.

The project begins with classical cryptography, using the Affine Cipher to explore encryption, decryption, and cryptanalysis. It will progressively evolve into a controlled ransomware simulation and defense platform integrating behavioral detection, incident response, backup restoration, and security monitoring.

> **Project status:** In development. Features described as planned are not yet implemented unless explicitly marked as completed.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Objectives](#-objectives)
- [Research Questions](#-research-questions)
- [Key Features](#-key-features)
- [Attack Scenarios](#-attack-scenarios)
- [System Architecture](#-system-architecture)
- [Technology Stack](#-technology-stack)
- [Project Roadmap](#-project-roadmap)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Testing and Evaluation](#-testing-and-evaluation)
- [Security and Safety](#-security-and-safety)
- [Expected Results](#-expected-results)
- [Future Improvements](#-future-improvements)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔎 Overview

Ransomware is a significant cybersecurity threat because it can make valuable data unavailable and disrupt critical operations. Defending against it requires more than encryption alone: organizations also need behavioral monitoring, incident response, reliable backups, and data-integrity verification.

CryptShield explores these defensive capabilities through controlled and reproducible experiments.

The initial version focuses on the Affine Cipher, a classical encryption algorithm with a small key space. Its weaknesses make it suitable for demonstrating brute-force attacks and key recovery.

Later versions will extend the project into a ransomware simulation environment that uses synthetic files to demonstrate attack behavior, detection, controlled termination, and recovery.

### Core workflow

**Cryptography → Simulation → Detection → Response → Recovery → Verification**

CryptShield is an educational and research platform. It is not intended to produce deployable malware or to protect real data using classical ciphers.

---

## 🎯 Objectives

### 1. Cryptography and cryptanalysis

- Implement the Affine Cipher in Python.
- Understand modular arithmetic, greatest common divisors, and modular inverses.
- Validate encryption and decryption operations.
- Demonstrate brute-force key recovery.
- Explore known-plaintext attacks.
- Explain why classical ciphers are unsuitable for modern data protection.

### 2. Controlled ransomware simulation

- Generate a synthetic dataset for a laboratory victim.
- Simulate ransomware-like file modifications inside a dedicated test directory.
- Record file states and simulation events.
- Display a fictional, clearly labelled educational warning interface.
- Ensure the simulation cannot operate on arbitrary files outside the authorized laboratory.

### 3. Behavioral detection

- Monitor file-system activity.
- Identify suspicious bursts of file modifications.
- Generate alerts with timestamps and supporting evidence.
- Evaluate detection thresholds and false positives.
- Integrate operating-system telemetry and SIEM monitoring.

### 4. Incident response

- Stop the controlled simulation after a detection event.
- Record detection and response times.
- Track the number of files affected before termination.
- Maintain an auditable event timeline.

### 5. Recovery and integrity verification

- Maintain a clean backup of synthetic test data.
- Restore affected files after an experiment.
- Calculate SHA-256 hashes.
- Compare recovered files against their original hashes.
- Produce a recovery report.

### 6. Experimental evaluation

- Compare experiments with and without active detection.
- Evaluate local detection against SIEM-assisted monitoring.
- Measure detection latency, false positives, and recovery success.
- Document limitations and reproducible results.

---

## ❓ Research Questions

The primary research question is:

> How effectively can behavioral monitoring and automated response reduce the impact of a controlled ransomware simulation, and how reliably can the original data be recovered?

Secondary questions:

1. How quickly can suspicious file activity be detected?
2. How does detection latency affect the number of files affected?
3. How do detection thresholds influence false-positive rates?
4. Does SIEM-assisted monitoring improve detection compared with a local detector?
5. Can clean backup restoration recover all affected files with verified integrity?
6. How does the security of classical cryptography differ from that of modern cryptographic constructions?

---

## ✨ Key Features

Features are grouped by development stage.

| Feature | Status |
|---|---|
| Affine Cipher encryption and decryption | Planned |
| Affine key validation | Planned |
| Brute-force cryptanalysis | Planned |
| Known-plaintext key recovery | Planned |
| Synthetic victim dataset | Planned |
| Controlled ransomware simulation | Planned |
| Educational warning interface | Planned |
| File-activity detection engine | Planned |
| Automated simulation termination | Planned |
| Backup and recovery module | Planned |
| SHA-256 integrity verification | Planned |
| Sysmon integration | Planned |
| Wazuh SIEM integration | Planned |
| Experiment metrics and reports | Planned |
| Web dashboard | Future extension |
| Modern cryptography module | Future extension |

Statuses will be updated as features are implemented and tested.

---

## 🧪 Attack Scenarios

CryptShield will evaluate two primary scenarios using comparable initial conditions and the same synthetic dataset.

### Scenario A — Controlled attack without active detection

**Objective:** Establish a baseline for the effects of ransomware-like activity when active detection and automated response are disabled.

Workflow:

1. Generate synthetic victim files.
2. Record the original file inventory and SHA-256 hashes.
3. Create a clean backup.
4. Run the controlled file-transformation simulation.
5. Record modified files and event timestamps.
6. Display the educational ransomware-style warning.
7. Measure the resulting file impact.
8. Restore the dataset and verify integrity.

Expected outcome: a baseline measurement of file impact and recovery performance.

### Scenario B — Detection, response, and recovery

**Objective:** Evaluate whether active monitoring and automated response can reduce the impact of the same controlled simulation.

Workflow:

1. Reset the victim to the original state.
2. Enable file monitoring and detection rules.
3. Run the same simulation.
4. Detect suspicious file activity.
5. Generate an alert and record detection latency.
6. Stop the controlled simulation.
7. Restore the affected files from a clean backup.
8. Verify restored data using SHA-256.
9. Compare the results with Scenario A.

Expected outcome: a measured comparison of file impact, detection performance, response time, and recovery success.

**Important:** Affine Cipher is used only for the initial educational cryptography experiments. It is not a suitable encryption mechanism for realistic ransomware research. Later cryptographic experiments will use established modern cryptographic libraries and controlled test data.

---

## 🏗️ System Architecture

The planned architecture consists of five logical components.

```text
                  CryptShield Platform
                           |
          +----------------+----------------+
          |                |                |
          v                v                v
   Cryptography       Simulation        Detection
      Engine            Engine            Engine
          |                |                |
          v                v                v
   Affine Cipher      Synthetic Data    File Monitoring
   Cryptanalysis      Controlled Runs   Detection Rules
          |                |                |
          +----------------+----------------+
                           |
                           v
                    Incident Response
                           |
                  +--------+--------+
                  |                 |
                  v                 v
                Stop             Recover
                  |                 |
                  +--------+--------+
                           |
                           v
                  SHA-256 Verification
                           |
                           v
                   Experiment Reports
```

### Laboratory topology

The proposed laboratory will use an isolated virtual network.

```text
                 ISOLATED LAB NETWORK
                          |
             +------------+------------+
             |                         |
             v                         v
        Kali Linux VM             Windows VM
        Lab controller            Victim system
             |                         |
             |                  Synthetic test data
             |                         |
             |                    Sysmon Agent
             |                         |
             +-------------------------+
                          |
                          v
                    Wazuh Manager
                    SIEM / Alerts
                          |
                          v
                 Detection Evaluation

        Separate clean backup and recovery storage
```

The initial prototype can run locally without Kali or Wazuh. Network integration will be introduced only after the local simulation, detection, and recovery workflows have been tested.

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Core application, cryptography, simulation, and analysis |
| `math.gcd` | Affine key validation |
| Python modular arithmetic | Modular inverse and key recovery |
| `pytest` | Automated testing |
| SHA-256 | Integrity verification |
| SQLite | Initial experiment and event storage |
| Windows Event Logging | Operating-system telemetry |
| Sysmon | Detailed Windows process and system-event monitoring |
| Wazuh | Centralized security monitoring and alerting |
| Git and GitHub | Version control and documentation |
| Angular (optional) | Future dashboard |
| Spring Boot (optional) | Future REST API |

Dependencies will be added as the corresponding modules are implemented.

---

## 🗺️ Project Roadmap

### Phase 1 — Affine Cipher fundamentals

- [ ] Study modular arithmetic.
- [ ] Implement encryption and decryption.
- [ ] Validate the multiplication key.
- [ ] Handle text, punctuation, and case consistently.
- [ ] Write unit tests.

### Phase 2 — Cryptanalysis

- [ ] Enumerate the 312 valid Affine keys.
- [ ] Implement brute-force key recovery.
- [ ] Demonstrate known-plaintext attacks.
- [ ] Record attempts and execution time.
- [ ] Document the cipher's security limitations.

### Phase 3 — Laboratory preparation

- [ ] Define the lab directory and configuration.
- [ ] Generate synthetic test files.
- [ ] Record baseline file hashes.
- [ ] Create and test clean backups.
- [ ] Test rejection of unauthorized file paths.

### Phase 4 — Controlled simulation

- [ ] Implement a controlled file-transformation engine.
- [ ] Record affected files and simulation events.
- [ ] Implement explicit stop controls.
- [ ] Create an educational warning interface.
- [ ] Verify repeatability and safe failure behavior.

### Phase 5 — Detection and response

- [ ] Implement local file-activity monitoring.
- [ ] Establish benign-activity baselines.
- [ ] Create suspicious-activity detection rules.
- [ ] Generate alerts with supporting evidence.
- [ ] Implement controlled termination.
- [ ] Measure detection and response latency.

### Phase 6 — Recovery

- [ ] Restore files from a clean backup.
- [ ] Verify SHA-256 hashes.
- [ ] Track recovery failures.
- [ ] Generate a recovery report.

### Phase 7 — SIEM integration

- [ ] Configure Sysmon.
- [ ] Integrate Wazuh Agent and Manager.
- [ ] Collect and correlate relevant events.
- [ ] Develop and test detection rules.
- [ ] Compare local and SIEM-assisted detection.

### Phase 8 — Research and reporting

- [ ] Define controlled experimental conditions.
- [ ] Repeat each scenario.
- [ ] Calculate detection and recovery metrics.
- [ ] Compare results and limitations.
- [ ] Prepare the final report and demonstration.

### Phase 9 — Future enhancements

- [ ] Add a dashboard.
- [ ] Add experiment history and visual analytics.
- [ ] Introduce modern cryptography using established libraries.
- [ ] Expand the defensive scenarios.
- [ ] Evaluate additional detection strategies.

---

## 📁 Project Structure

The proposed Python structure is:

```text
CryptShield/
├── README.md
├── pyproject.toml
├── .gitignore
├── config/
│   └── lab.yaml
├── docs/
│   ├── architecture.md
│   ├── threat-model.md
│   └── experiments.md
├── src/
│   └── cryptshield/
│       ├── __init__.py
│       ├── cli.py
│       ├── crypto/
│       │   ├── affine.py
│       │   └── cryptanalysis.py
│       ├── simulation/
│       │   ├── lab_guard.py
│       │   ├── synthetic_data.py
│       │   └── runner.py
│       ├── detection/
│       │   ├── file_monitor.py
│       │   └── rules.py
│       ├── response/
│       │   └── controller.py
│       ├── recovery/
│       │   ├── backup.py
│       │   └── integrity.py
│       └── reporting/
│           └── metrics.py
├── tests/
│   ├── test_affine.py
│   ├── test_cryptanalysis.py
│   ├── test_lab_guard.py
│   ├── test_detection.py
│   └── test_recovery.py
├── lab_data/
│   └── README.md
└── results/
    └── README.md
```

This structure is a design proposal. Directories and files will be created as development progresses.

---

## 🚀 Getting Started

### Prerequisites

- Python 3.11 or later recommended.
- Git.
- A code editor such as VS Code.
- Basic Python and modular arithmetic knowledge.

### 1. Clone the repository

Replace the placeholder with your actual GitHub repository URL.

```bash
git clone <YOUR_REPOSITORY_URL>
cd CryptShield
```

### 2. Create a virtual environment

**Linux / Kali Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows PowerShell**

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3. Install development dependencies

Once the project configuration has been created:

```bash
python -m pip install --upgrade pip
python -m pip install -e ".[dev]"
```

This command assumes that `pyproject.toml` defines the project and its development dependencies.

### 4. Run the tests

After the test suite has been implemented:

```bash
pytest -v
```

The initial milestone is to pass all Affine Cipher and cryptanalysis tests before implementing the simulation engine.

**Note:** These commands describe the intended development workflow. They will become fully executable once the corresponding project files have been added.

---

## 📊 Testing and Evaluation

CryptShield will use repeatable experiments with documented starting conditions.

### Planned metrics

| Metric | Definition |
|---|---|
| Detection rate | Correctly detected attack events divided by all attack events |
| False-positive rate | Benign events incorrectly flagged divided by all benign events |
| Detection latency | Time from the first relevant event to the alert |
| Response latency | Time from the alert to confirmed simulation termination |
| Files affected | Number of files modified before the simulation stops |
| Recovery success | Files restored and verified divided by files expected to be restored |
| Recovery time | Time required to restore and verify the dataset |

Results will be measured rather than assumed. Each experiment will record its configuration, event timeline, outcome, and limitations.

---

## 🔒 Security and Safety

CryptShield is intended for authorized cybersecurity education and research.

The laboratory design will follow these principles:

- Use synthetic files and disposable test environments.
- Restrict simulation operations to a dedicated laboratory directory.
- Reject paths outside the authorized scope.
- Keep clean backups separate from the simulated victim dataset.
- Avoid stealth, persistence, propagation, credential theft, and uncontrolled destructive behavior.
- Use isolated virtual networking for laboratory experiments.
- Record simulation actions and errors for auditing.
- Never use the Affine Cipher to protect real sensitive information.
- Test restoration and integrity verification before running impact simulations.

The warning interface will identify itself as a simulation, and all attack scenarios will remain under explicit laboratory control.

---

## 🎓 Expected Results

The intended outcome is a reproducible cybersecurity research platform capable of demonstrating:

1. Why the Affine Cipher is vulnerable to exhaustive key search.
2. How controlled ransomware-like activity changes synthetic files.
3. How file-activity monitoring can identify suspicious behavior.
4. How automated response can limit the duration of a simulation.
5. How clean backups and integrity checks support data recovery.
6. How different defensive configurations perform under comparable conditions.

The project will also provide experiment logs, quantitative comparisons, and documentation suitable for a cybersecurity research report.

These are objectives, not claimed experimental findings.

---

## 🔮 Future Improvements

Potential extensions include:

- A web dashboard for experiment monitoring.
- Additional classical cryptanalysis exercises.
- Modern cryptography demonstrations using established libraries.
- More advanced behavioral detection rules.
- Improved event correlation with Wazuh.
- Automated generation of experiment reports.
- Comparison of different backup and recovery strategies.
- Additional safe adversary-emulation scenarios.

---

## 🤝 Contributing

CryptShield is a learning and research project. Contributions may include:

- Code improvements and bug fixes.
- Additional unit tests.
- Documentation and diagrams.
- Detection-rule improvements.
- Experimental methodology and evaluation.
- Security reviews of laboratory boundaries and recovery mechanisms.

All contributions should preserve the project's controlled-lab scope.

---

## 📄 License

A license has not yet been selected.

Before publishing the project, choose a license appropriate for the intended use and any third-party dependencies.

---

## 👨‍💻 Author

**CryptShield — Cryptographic Attack Simulation, Ransomware Detection & Data Recovery Platform**

Developed as a cybersecurity and cryptography research project.

---

> **Current milestone:** Implement and test the Affine Cipher, then demonstrate brute-force key recovery. All later modules depend on a reliable, tested foundation.

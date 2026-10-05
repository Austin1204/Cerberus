
# Cerberus — A Closed-Loop Multi-Agent Framework for Autonomous Security Operations

> A closed-loop multi-agent framework for autonomous Security Operations.

## Overview

**Cerberus** is a proposed closed-loop multi-agent framework for autonomous security operations. It is designed to address the challenges faced by modern Security Operations Centers (SOCs), including high volumes of security events and alerts, increasingly sophisticated cyber threats, dependence on manual analysis, isolated security tools, alert fatigue, delayed response, and high operational costs.

The framework brings together heterogeneous telemetry collection and normalization, hybrid detection, Knowledge Graph-based attack correlation, provenance-aware RAG, specialized multi-agent investigation, risk and policy control, deterministic response automation, post-action verification, feedback, and tamper-evident auditing.

## Security Operations Center (SOC)

A Security Operations Center continuously monitors an organization's digital environment to detect, investigate, and respond to cybersecurity threats.

### Core Objectives

- **Monitor** — Continuously observe security events.
- **Detect** — Identify suspicious activities and threats.
- **Investigate** — Analyze alerts and determine their severity.
- **Respond** — Contain and remediate security incidents.
- **Improve** — Learn from incidents and strengthen defenses.

### Key Goal

Detect threats early and minimize their impact on the organization.

## Why an Advanced SOC is Needed

Modern SOCs face:

- High volumes of security events and alerts.
- Increasing complexity and sophistication of cyber threats.
- Heavy dependence on manual security analysis.
- Multiple isolated security tools.
- Difficulty correlating large volumes of events.
- Alert fatigue and false positives.
- Delayed threat detection and incident response.
- High operational and human-resource costs.

This creates the need for an intelligent, automated, and scalable SOC capable of detecting, investigating, and responding to cyber threats with minimal human intervention.

## Project Objectives

Cerberus aims to:

- Automate security operations using autonomous AI agents.
- Improve threat detection accuracy.
- Reduce Mean Time to Respond (MTTR).
- Automate incident investigation and response.
- Provide explainable AI-driven security insights.
- Enable scalable security monitoring.
- Support intelligent threat investigation.
- Provide automated incident remediation.
- Provide controlled autonomous response.
- Maintain continuous verification and feedback.

## From Traditional SOC to Cerberus

```text
Traditional SOC
Security monitoring + human-led investigation + manual response
                              ↓
AI-Assisted SOC
ML detection + automated correlation + analyst assistance
                              ↓
Agentic SOC
Specialized agents + RAG/KG + risk-aware planning + controlled autonomous response
                              ↓
Cerberus
Closed-loop detection + investigation + response + verification
```

## Cerberus Closed-Loop Security Operations

The proposed security lifecycle consists of six stages:

```text
┌───────────────────────────┐
│ 1. DETECT                 │
│ ML + Rules + IOC Detection│
└─────────────┬─────────────┘
              ↓
┌───────────────────────────┐
│ 2. INVESTIGATE            │
│ Multi-Agent Analysis      │
│ + RAG + Knowledge Graph   │
└─────────────┬─────────────┘
              ↓
┌───────────────────────────┐
│ 3. ASSESS                 │
│ Risk Scoring +            │
│ Policy Validation         │
└─────────────┬─────────────┘
              ↓
┌───────────────────────────┐
│ 4. RESPOND                │
│ Controlled Automated      │
│ Remediation               │
└─────────────┬─────────────┘
              ↓
┌───────────────────────────┐
│ 5. VERIFY                 │
│ Post-Action Validation    │
└─────────────┬─────────────┘
              ↓
┌───────────────────────────┐
│ 6. LEARN                  │
│ Feedback + Updated Context│
└─────────────┬─────────────┘
              │
              └──────────→ Continuous Loop
```

## Proposed Architecture

### 1. Heterogeneous Telemetry Collection and Normalization

Cerberus is designed to collect and normalize security telemetry from heterogeneous environments before downstream detection and analysis.

### 2. Hybrid Detection

The detection foundation combines:

- Rule/signature-based detection.
- Indicators of Compromise (IOC) detection.
- Machine Learning-based detection.

This hybrid approach is intended to filter and identify relevant security events before deeper agentic investigation.

### 3. Dynamic Knowledge Graph Attack Correlation

A **Neo4j Knowledge Graph** is proposed for representing relationships between security entities and events.

The Knowledge Graph can represent entities such as:

- Threat actors.
- Malware.
- Vulnerabilities.
- IP addresses.
- Attack techniques.
- Other related security entities.

Graph relationships can be used to identify possible attack paths and provide structured context for investigation.

### 4. Provenance-Aware RAG

Cerberus combines Knowledge Graph retrieval with Retrieval-Augmented Generation (RAG) and provenance information.

Candidate evidence can be evaluated using:

- Source reliability.
- Provenance.
- Recency.
- Graph relevance.
- Semantic similarity.

This is intended to improve the grounding of LLM-based security reasoning and reduce reliance on unreliable or irrelevant threat intelligence.

### 5. Specialized Multi-Agent Investigation

Specialized agents divide complex SOC reasoning into focused tasks.

The proposed architecture uses **LangGraph agents** together with:

- Security telemetry.
- Knowledge Graph facts.
- Retrieved CTI.
- RAG-based evidence.

Important conclusions should be grounded in available evidence rather than relying only on unconstrained LLM reasoning.

### 6. Risk Scoring and Policy Control

Before autonomous mitigation, proposed response actions are evaluated through risk scoring and policy validation.

High-risk actions require human approval.

This provides a safety layer so that learned agents do not receive unrestricted execution authority.

### 7. Deterministic Response Automation

Cerberus proposes **n8n-based deterministic response automation**.

The response workflow is:

```text
Response Agent
      ↓
Risk / Policy Validation
      ↓
n8n Execution
      ↓
Verification Agent
      ↓
Confirmed Outcome
```

### 8. Post-Action Verification

After a response action is executed, Cerberus verifies whether the intended security outcome was achieved.

Verification closes the loop and helps prevent blind automation.

### 9. Tamper-Evident Audit

The framework proposes tamper-evident auditing using hashes/blockchain mechanisms to strengthen the integrity of security activity records.

## Research Gap

The literature survey identifies that existing studies demonstrate capabilities such as:

- AI/ML-based detection.
- Autonomous defense.
- LLM-based investigation.
- Retrieval-Augmented Generation.
- Cybersecurity Knowledge Graphs.
- Multi-agent reasoning.
- Blockchain auditing.

However, these capabilities are generally presented as separate or partially integrated systems.

Cerberus addresses this integration gap through:

1. Heterogeneous telemetry collection and normalization.
2. Hybrid rule/signature + ML detection.
3. Dynamic Neo4j attack correlation.
4. Provenance-aware RAG with Vector DB.
5. Specialized LangGraph agents.
6. Risk scoring + Zero-Trust policy control.
7. Human approval for high-risk actions.
8. n8n-based deterministic response automation.
9. Post-action verification and feedback.
10. Tamper-evident audit using hashes/blockchain.

## Research-Informed Design

The literature survey provides the following design inferences for Cerberus:

| Research Direction | Cerberus Design Inference |
|---|---|
| AI/ML-based SOC | Use hybrid rule/IOC + ML detection as the foundation. |
| ML + Adaptive Response | Control adaptive response using risk and policy; high-impact actions require approval. |
| Closed-loop SOC | Generalize closed-loop detection and response beyond web/API security. |
| CTI + Knowledge Graph | Use graph relationships for attack-chain and contextual reasoning. |
| Provenance-based KGRAG | Use provenance, reliability, recency, graph relevance and semantic similarity for retrieval. |
| Multi-Agent SOC | Ground important conclusions in telemetry, graph facts and retrieved CTI. |
| LLM/RAG Forensics | ML/rules filter evidence before Neo4j/RAG retrieval and LLM reasoning. |
| Agentic SOC | Position Cerberus as an integrated extension of existing agentic SOC research. |
| Hybrid Autonomous Defence | Avoid unrestricted execution authority for learned agents. |
| LLM Defence | Account for model/context sensitivity and operational risk. |

## Key Design Principles

### Explainability

Important security decisions should be supported by telemetry, retrieved evidence, and structured Knowledge Graph facts.

### Controlled Autonomy

Autonomous agents should not have unrestricted execution authority. Risk and policy layers control which actions can be executed.

### Human-in-the-Loop

High-risk or high-impact actions require human approval.

### Grounded Reasoning

RAG and Knowledge Graph retrieval provide contextual evidence before LLM-based reasoning.

### Continuous Verification

Automated response actions are followed by validation to determine whether the intended security outcome was achieved.

## Literature Foundation

The project literature survey covers ten major research directions:

1. **AI/ML-based SOC** — *Empowering Security Operation Center With Artificial Intelligence and Machine Learning*, IEEE Access, 2025.
2. **ML + Adaptive Response** — *AI Driven Self-Healing Cybersecurity Systems with Agentic AI for Adaptive Threat Response and Resilience*, IEEE Cloud Summit, 2025.
3. **Closed-Loop SOC** — *ALERT: A Closed-Loop SOC Agent for Web and API Security*, IEEE ICCE, 2026.
4. **CTI + Knowledge Graphs** — *Automating Cyber Threat Intelligence and Attack Chain Generation using Cyber Security Knowledge Graphs and LLMs*, IEEE ICMCIS, 2025.
5. **Provenance-Based KGRAG** — *Provenance-Based CTI Analysis with Knowledge Graph and RAG*, IEEE CSCloud, 2025.
6. **Multi-Agent SOC Investigation** — *Cognitive SOC: Evidence-Backed Narrative Generation for Security Operations with Multi-Agent LLM Architecture*, IEEE BigData, 2025.
7. **LLM/RAG Cloud Forensics** — *LLM-Powered Automated Cloud Forensics: From Log Analysis to Investigation*, IEEE CLOUD, 2025.
8. **Agentic SOC Architecture** — J. Roy and S. K. Singh, *AgentSOC: A Multi-Layer Agentic AI Framework for Security Operations Automation*, 2026.
9. **Hybrid Autonomous Defence** — *Towards Robust Autonomous Cyber Defence Agents Using Hybrid AI Models*, IEEE NetSoft, 2025.
10. **LLM-based Cyber Defence** — *Intelligent Cybersecurity Defense Strategies Based on Large Language Model Agents*, IEEE ASENS, 2025.

## Key Takeaways

- **AI/ML** provides the detection foundation.
- **CTI + Knowledge Graphs** provide structured attack context.
- **RAG** provides grounded and retrievable security knowledge.
- **Multi-agent architectures** divide complex SOC reasoning into specialized tasks.
- **Risk/policy layers** are essential before autonomous mitigation.
- **Verification** closes the loop and prevents blind automation.
- Cerberus combines these complementary capabilities into an end-to-end closed-loop architecture.

## Project Status

**Research / Proposed Architecture**

Cerberus is positioned as an integrated extension of existing AI-enabled and agentic SOC research.

## Authors

**Austin T Amel**  
**Jacob Sunny Menachery**  
**Priya M**  
**Ron Ebenezer Abraham**

**Department of Computer Engineering**  
**Model Engineering College, Ernakulam**  
**2026**

## References

1. *Empowering Security Operation Center With Artificial Intelligence and Machine Learning – A Systematic Literature Review*, IEEE Access, 2025.  
   https://ieeexplore.ieee.org/document/10850912/

2. *AI Driven Self-Healing Cybersecurity Systems with Agentic AI for Adaptive Threat Response and Resilience*, IEEE Cloud Summit, 2025.  
   https://ieeexplore.ieee.org/document/11108126/

3. *ALERT: A Closed-Loop SOC Agent for Web and API Security*, IEEE ICCE, 2026.  
   https://ieeexplore.ieee.org/document/11449910/

4. *Automating Cyber Threat Intelligence and Attack Chain Generation using Cyber Security Knowledge Graphs and LLMs*, IEEE ICMCIS, 2025.  
   https://ieeexplore.ieee.org/document/11047951/

5. *Provenance-Based CTI Analysis with Knowledge Graph and RAG*, IEEE CSCloud, 2025.  
   https://ieeexplore.ieee.org/document/11261451/

6. *Cognitive SOC: Evidence-Backed Narrative Generation for Security Operations with Multi-Agent LLM Architecture*, IEEE BigData, 2025.  
   https://ieeexplore.ieee.org/document/11401968/

7. *LLM-Powered Automated Cloud Forensics: From Log Analysis to Investigation*, IEEE CLOUD, 2025.  
   https://ieeexplore.ieee.org/document/11120597/

8. J. Roy and S. K. Singh, *AgentSOC: A Multi-Layer Agentic AI Framework for Security Operations Automation*, 2026.  
   https://arxiv.org/abs/2604.20134

9. *Towards Robust Autonomous Cyber Defence Agents Using Hybrid AI Models*, IEEE NetSoft, 2025.  
   https://ieeexplore.ieee.org/document/11080605/

10. *Intelligent Cybersecurity Defense Strategies Based on Large Language Model Agents*, IEEE ASENS, 2025.  
    https://ieeexplore.ieee.org/document/11011130/

## Source

This README was prepared from the provided Cerberus literature-survey/project material.

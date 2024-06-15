# Smithright Dataworks - Draft Notes on Alignment & Governance of Autonomous Agents

Alignment techniques:

    RBAC - Role based access controls
        - Least privilege granted for each agent/service to access system info and call other agents/services. Manage centrally via Iam roles and policies.

    Monitoring & filtering:
        - Laws, rules, & governance
            - Consentia & Covenant - Proposed approach for stakeholders to use a distributed Consentia system to align on rules for governance of autonomouse agents. Agreed rules to be recorded as blockchain smart contracts in a distrubuted public ledger.
        - Preference fine-tuning
            - RLHF - Realtime Learning from Human Feedback
        - Federated self-governance - Proposed approach where agentic role peers or supervisory roles to actively assess alignment of cognition traces vs recorded rules in the Covenant system. If breach, post a flag with agent ID and context details to the distributed ledger.
            - Each agent should gracefully halt and call the orchestrator function if misaligned or flagged.
            - If an agent does not self-halt after flagged, the agent orchestrator function should dispatch resources to halt or quarantine the agent/service function/processes.

    Refusal training

    Adversarial training:
        - Agentic competition & mutation in safe environments with constrained freedoms
        - SPAC 
            2024 - Princeton - (SPAC) Self-Play with Adversarial Critic: Provable and Scalable Offline Alignment for Language Models - https://arxiv.org/pdf/2406.04274

    Other research methods:
        - Short circuiting
            2024 - Carnegie Mellon - Center for AI Safety - Improving Alignment and Robustness with Short Circuiting - https://arxiv.org/pdf/2406.04313
        - Shield synthesis
            Shield Synthesis for LTL Modulo Theories - 2024 - 1IMDEA Software Institute, 2Universidad Politecnica de Madrid, 3The Hebrew University of Jerusalem, 4University of California, Irvine - https://arxiv.org/pdf/2406.04184
        - 3D environment training
            - Imitation training
            - Aligning Agents like Large Language Models - 2024 - Microsoft - https://arxiv.org/pdf/2406.04208

---

Alignment benchmarks:
    - Misalignment Modeling - 2024 - AAAI.org, UConn, Tufts - Quantifying Misalignment b/w Agents - https://arxiv.org/pdf/2406.04231
    - BEADs: BIAS EVALUATION ACROSS DOMAINS - 2024 - 1Vector Institute 2Royal Bank of Canada 3University of Toronto - https://arxiv.org/pdf/2406.04220
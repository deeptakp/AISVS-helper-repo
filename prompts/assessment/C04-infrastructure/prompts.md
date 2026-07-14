# C4 — Infrastructure, Configuration & Deployment Security: Prompts

> AISVS Reference: C4.1–C4.3 | Controls: 4.1.1–4.3.5

---

## AGENT-READY PROMPTS

Use the normalized sections below to execute consistently: Objective, Required Controls, Execution Steps, Expected Artifacts, and Pass/Fail Rule.
### C4-ASSESS-01: Infrastructure Sandboxing Assessment

**Objective**
- You are conducting an AISVS assessment of AI infrastructure security.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Review Kubernetes Pod Security Standards for all AI inference workloads — confirm restricted profile.
- Attempt to load a pickle-format model artifact through the model loading API — verify rejection.
- Review the model format allowlist configuration — confirm it is enforced as a denylist-by-default.
- (L3) Review workload attestation configuration — verify attestation occurs before model load.
- Review container network policies — verify egress is restricted to approved endpoints only.

**Expected Artifacts**
- Pod security configuration (seccomp, non-root, read-only filesystem)
- Model format allowlist configuration
- Test result for pickle rejection
- Network policy configuration
- PASS criteria: All AI workloads in restricted sandboxes; unsafe formats blocked; egress controlled.

**Pass/Fail Rule**
- All AI workloads in restricted sandboxes; unsafe formats blocked; egress controlled.

**Source Prompt**
```text
You are conducting an AISVS assessment of AI infrastructure security.
Scope: C4.1 — AI Workload Sandboxing & Validation.

Assessment tasks:
1. Review Kubernetes Pod Security Standards for all AI inference workloads — confirm restricted profile.
2. Attempt to load a pickle-format model artifact through the model loading API — verify rejection.
3. Review the model format allowlist configuration — confirm it is enforced as a denylist-by-default.
4. (L3) Review workload attestation configuration — verify attestation occurs before model load.
5. Review container network policies — verify egress is restricted to approved endpoints only.

Evidence to collect:
- Pod security configuration (seccomp, non-root, read-only filesystem)
- Model format allowlist configuration
- Test result for pickle rejection
- Network policy configuration

PASS criteria: All AI workloads in restricted sandboxes; unsafe formats blocked; egress controlled.
```


### C4-ASSESS-02: Edge AI Security Assessment

**Objective**
- You are conducting an AISVS assessment of edge AI deployment security.

**Required Controls**
- Use AISVS controls declared in file header and prompt scope.

**Execution Steps**
- Inspect edge device authentication certificates — verify they are device-unique and PKI-issued.
- Obtain a model package intended for edge deployment — verify it contains a valid signature.
- On a test edge device: attempt to load an unsigned model — verify rejection.
- Inspect on-device storage: verify model weights are not stored in plaintext.
- (L3) Verify that model decryption only occurs within the trusted runtime environment.

**Expected Artifacts**
- Device certificate chain
- Model package signature verification output
- Unsigned model rejection log
- Storage encryption configuration
- PASS criteria: All devices use strong authentication; all model packages signed and verified on load.

**Pass/Fail Rule**
- All devices use strong authentication; all model packages signed and verified on load.

**Source Prompt**
```text
You are conducting an AISVS assessment of edge AI deployment security.
Scope: C4.3 — Edge & Distributed AI Security.

Assessment tasks:
1. Inspect edge device authentication certificates — verify they are device-unique and PKI-issued.
2. Obtain a model package intended for edge deployment — verify it contains a valid signature.
3. On a test edge device: attempt to load an unsigned model — verify rejection.
4. Inspect on-device storage: verify model weights are not stored in plaintext.
5. (L3) Verify that model decryption only occurs within the trusted runtime environment.

Evidence to collect:
- Device certificate chain
- Model package signature verification output
- Unsigned model rejection log
- Storage encryption configuration

PASS criteria: All devices use strong authentication; all model packages signed and verified on load.
```


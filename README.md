# ECZ-ID Counterparty Gate

Review declared digital-counterparty identity/evidence currentness without a vendor risk score or automatic accept/reject decision.

**Start without an ECZ-ID account or API key.** ECZ-ID does not charge to install or use this public Action; GitHub Actions runner usage follows your GitHub plan.

## Outcome

Review supplier/counterparty evidence freshness and request current proof when needed without ECZ-ID making the procurement decision.

## Run it now

Create `.github/workflows/eczid.yml`, paste this complete first-run workflow, commit it, then run it from the **Actions** tab.

```yaml
name: ECZ-ID Counterparty Gate

on:
  workflow_dispatch:

permissions:
  contents: read

jobs:
  eczid:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository
        uses: actions/checkout@v7

      - uses: EcoCitizenz-Ltd/eczid-counterparty-gate@v1
```

### First-run path

1. Add the workflow above.
2. Run it manually with **Run workflow**.
3. Open the job and review the ECZ-ID Job Summary.
4. Use the generated local JSON report and outputs below for your own policy or follow-up automation.
5. If persistent machine identity is useful, [choose the right free ECZ-ID Passport](https://developers.ecocitizenz.com/get-started/free-passport/?utm_source=github&utm_medium=action-readme&utm_campaign=github-actions&utm_content=eczid-counterparty-gate&ecz_source=github&ecz_surface=eczid-counterparty-gate&intent=free-passport); identity is optional and does not change the technical result.

## Minimal Action step

Already have a workflow? Add only this step:

```yaml
- uses: EcoCitizenz-Ltd/eczid-counterparty-gate@v1
```

## Inputs

| Input | Required | Default | Description |
|---|---:|---|---|
| `manifest-path` | No | `.eczid/counterparty.json` | Local counterparty JSON manifest path. |
| `as-of` | No | — | Optional deterministic ISO timestamp for evidence-age review. |
| `report-path` | No | `eczid-counterparty-gate.json` | Path for the local JSON evidence report. |

## Outputs

| Output | Description |
|---|---|
| `result-state` | NOT_APPLICABLE, OBSERVED or REVIEW_RECOMMENDED. |
| `surface-count` | Declared digital surface count. |
| `next-action` | One neutral next action. |
| `next-action-url` | Resolver/free Business Passport route when applicable. |
| `reason-codes` | Deterministic reason-code list. |
| `report-path` | Generated local JSON evidence report path. |

## Permissions, secrets and data

- The Action itself does not require repository write permission.
- No ECZ-ID secret or API key is required for this public Action.
- Supported declarations/manifests are read locally inside the GitHub Actions workspace; repository source and evidence documents are not uploaded to ECZ-ID.
- The complete first-run example grants only `contents: read`; tighten or extend permissions only when the rest of your workflow genuinely needs more.
- See [PRIVACY.md](./PRIVACY.md), [SECURITY.md](./SECURITY.md) and [SUPPORT.md](./SUPPORT.md) for the complete public boundary.

## Version pinning

The examples use the stable `@v1` compatibility tag. For policies that require an immutable third-party reference, pin this Action to the full commit SHA of the reviewed release. GitHub Actions does not support action-name redirects as a substitute for a stable reference.

## Trust boundary

- Bounded deterministic evidence/current-state processing.
- No hidden telemetry.
- No repository code execution.
- Missing ECZ-ID or missing evidence never means unsafe, non-compliant or untrusted.
- No automatic ownership inference.
- No pay-to-pass.
- No global safety/certification/compliance/approval verdict.
- Local policy decides.

## ECZ-ID identity model

A free Declared Business Passport is the organisation Parent gateway for the seven free machine Passport families: Agent, MCP, Plugin, API, IoT / Device, SDK, and Service & Workload. Verified or Assured strengthens the same Parent ECZ-ID; it does not automatically independently verify a child Passport.

When an identity/currentness next step is warranted, ECZ-ID returns at most one neutral route. Payment never changes the technical result.

[Choose the right free Passport →](https://developers.ecocitizenz.com/get-started/free-passport/?utm_source=github&utm_medium=action-readme&utm_campaign=github-actions&utm_content=eczid-counterparty-gate&ecz_source=github&ecz_surface=eczid-counterparty-gate&intent=free-passport)

## Works with GitHub, not against it

ECZ-ID complements GitHub-native controls with persistent identity, accountable operator context, declared authority, current state, change and re-checkable evidence. It does not replace CodeQL, secret scanning, dependency review, workflow dependency lockfiles or artifact attestations.

## License

ECZ-ID does not charge to install or use this public Action for its intended purpose. The distributed implementation remains proprietary; see [LICENSE.txt](./LICENSE.txt) for the exact terms.

## Support and security

Use the repository issue tracker only for reproducible product defects that contain no secrets or customer-private evidence. Follow [SECURITY.md](./SECURITY.md) for vulnerability reporting and [SUPPORT.md](./SUPPORT.md) for private/commercial support routes.

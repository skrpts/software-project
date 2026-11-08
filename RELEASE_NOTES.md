# Release Notes

## v1.0.5
GH#1144 round 2 — re-pin `feature-spec-pipeline` 1.1.32 → 1.1.33, which the round 2 publish moved.

Round 2 re-pinned ten consumer skrpts onto `audience-segmentation` 1.0.3 and `input-gap-check` 1.0.4, and `feature-spec-pipeline` is one of them and a required member of this template. **So its publish staled this pin the moment it landed** — the third time this exact sequence has produced this exact re-pin, and the reason is structural rather than an oversight: any member publish staleds any template pinning it, and nothing fails when it does. The pin keeps resolving, the digest keeps verifying, and the install succeeds while delivering the superseded body.

This time the gate said so at the publish itself rather than afterwards. GH#1147's member-pin check ran as part of `publish-skrpt feature-spec-pipeline`, named the owed re-pin and its new digest, and exited non-zero — so the work was handed over at the moment it was created instead of being found by someone going to look.

Digest read from the catalogue after the member was verified SERVED at 1.1.33. A pin written against an unfinished publish points at something nobody can install.

## v1.0.4
GH#1133 — re-pin `feature-spec-pipeline` after the GH#1143 publishes moved it.

This is the second re-pin today and the reason is structural, not an oversight: `feature-spec-pipeline` also carries a `default_from_previous` declaration, so publishing the deletion bumped its version and staled this template's pin the moment it landed. **Any member publish staleds any template that pins it, and nothing fails when it does** — the install keeps succeeding and serves the superseded body, which is the condition GH#1133 exists for.

Digests read from `/api/skrpts/<slug>` for each new version, as before. Members verified served before re-pinning — a pin written against an unfinished publish points at something nobody can install.

## v1.0.3
GH#1133 — re-pin 3 of 4 members to the versions the consumer wave produced. The template pins each member by `version` AND `content_digest`, and catalogue versions are immutable, so the old pins kept resolving and their digests kept verifying: **installs succeeded and delivered pre-wave members**. Nothing broke, which is why nothing reported it.

`feature-spec-pipeline` 1.1.30 → 1.1.31, `code-review-pipeline` 1.1.30 → 1.1.31, `security-audit-pipeline` 1.0.26 → 1.0.27 — each now the version whose steps declare their data flow rather than resolving it positionally. `documentation-pipeline` stays at 1.2.1: it is in the GH#1131 warn-only set and has not moved.

Digests are the catalogue's own `contentHash` for each new version, read from `/api/skrpts/<slug>` rather than recomputed.

## v1.0.2
Re-pinned the code review and documentation pipelines to versions that work.

Both were pinned to releases whose content had not caught up with their fixes: two of their steps used a step type the engine does not run, so they would have failed partway rather than completing. The fixed versions are now published and this template points at them.

No change to which pipelines are included or what they do.

## v1.0.0
First release — the Software Project template.

A project type that arrives with the pipelines software work repeats, rather than empty: specification before code, review on a change, then security and documentation.

Specification and review are marked required; security and documentation are optional, because a project missing them is still a working software project.

There is no test pipeline yet. Testing belongs in this shape, and a stage for it will be added once one is ready to do the job properly — this template would rather be short than carry a member that cannot.

The template does not contain the pipelines. It names them, with the version it was authored against and the content digest the Hub published, so an install can verify what it resolved rather than trusting a version number. Each is installed in its own right, exactly as if you had installed it yourself.

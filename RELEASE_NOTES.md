# Release Notes

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

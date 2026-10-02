# Proposals

This directory holds proposals about OpenSSL infrastructure, tooling and
engineering process. One markdown file per proposal. The pull request is the
discussion: comments attach to specific lines, and revisions show what changed
after feedback.

Merging a proposal records it. It does not mean it was accepted. Rejected
proposals are merged too, so that they stay findable along with the reasoning
that produced that outcome.


## What belongs here

| Kind of document | Where it goes |
| ---------------- | ------------- |
| Library design, new or changed public API | `doc/designs` in [openssl/openssl], per the [design process policy] |
| A policy, or a change to one | [general-policies], [technical-policies] |
| Infrastructure, tooling, engineering process | here |

A proposal that turns out to require a policy change finishes its life here as
`accepted`, and continues as a pull request against the relevant policy
repository.


## Layout

Proposals are flat files named after a short, memorable slug, the same
convention the policy repositories use:

    proposals/merge-queue.md
    proposals/<slug>.md

Files are never renamed or moved once merged, so links to them keep working.
Diagrams and other attachments go in `assets/<slug>/`.


## The header

Every proposal starts with a YAML header:

```yaml
---
title: Merge queue for openssl/openssl
status: draft
category: infrastructure
author: Some One <someone@openssl.org>
created: 2026-09-22
updated: 2026-09-22
supersedes: <slug, if applicable>
---
```

`status` is one of:

- **draft** — written, under discussion, no decision taken.
- **accepted** — agreed, not yet done.
- **rejected** — considered and declined. The proposal says why.
- **superseded** — replaced by another proposal, named in that proposal's
  `supersedes` field.

`category` is one of `infrastructure`, `tooling`, `process` or something else.


## The process

1. **Open.** Copy [TEMPLATE.md](TEMPLATE.md) to `proposals/<slug>.md`, set
   `status: draft`, and open a pull request. The template is offered for
   consideration, not imposed: use the sections that help, drop the ones that
   do not, and add your own where the proposal calls for them. Only the header
   is expected in every proposal.

2. **Comment.** Discussion happens in the pull request so that it stays
   attached to the text it is about. A proposal is held open for at least a
   week, so that people who are not watching it closely have a chance to read
   it.

3. **Decide.** Two approving reviews and no rejections accept the proposal: set
   `status: accepted`. Two reviews rejecting it reject the proposal: set
   `status: rejected`, and write the reasoning into the proposal itself, so
   that the record explains the outcome rather than just stating it.

   Reviews count from anyone with write access to this repository, and the
   author's own do not count. A request for changes is not a rejection: it asks
   for a revision, and the proposal stays `draft` until it is resolved. If both
   thresholds are met at once, nothing is decided; that is a disagreement to
   settle in the discussion rather than by counting.

4. **Merge.** A maintainer merges once the outcome is recorded. This applies
   whatever the outcome was.

5. **Amend.** Changes after merge go through a new pull request. A substantive
   change to an accepted proposal needs a new decision; editorial changes such
   as typos, link fixes and clarifications that do not change meaning do not.

6. **Stale.** A pull request with no activity for 90 days is closed. Nothing
   sits open indefinitely, and a closed proposal can be reopened if someone
   picks it up again.

Set `updated` whenever the body changes.


[openssl/openssl]: https://github.com/openssl/openssl
[design process policy]: https://github.com/openssl/technical-policies/blob/master/policies/design-process.md
[general-policies]: https://github.com/openssl/general-policies
[technical-policies]: https://github.com/openssl/technical-policies

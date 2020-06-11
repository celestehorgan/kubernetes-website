---
title: PR wranglers
slug: pr-wrangler
content_type: concept
weight: 20
---

## Be the PR Wrangler for a week

SIG Docs [approvers](/docs/contribute/participating/#approvers) take week-long turns [wrangling PRs](https://github.com/kubernetes/website/wiki/PR-Wranglers) for the repository.

The PR wrangler’s duties include:

- Review [open pull requests](https://github.com/kubernetes/website/pulls) daily for quality and adherence to the [Style](/docs/contribute/style/style-guide/) and [Content](/docs/contribute/style/content-guide/) guides.
    - Review the smallest PRs (`size/XS`) first, then iterate towards the largest (`size/XXL`).
    - Review as many PRs as you can.
- Ensure that the CLA is signed by each contributor.
    - Help new contributors sign the [CLA](https://github.com/kubernetes/community/blob/master/CLA.md).
    - Use [this](https://github.com/zparnold/k8s-docs-pr-botherer) script to automatically remind contributors that haven’t signed the CLA to sign the CLA.
- Provide feedback on proposed changes and help facilitate technical reviews from members of other SIGs.
    - Provide inline suggestions on the PR for the proposed content changes.
    - If you need to verify content, comment on the PR and request more details.
    - Assign relevant `sig/` label(s).
    - If needed, assign reviewers from the `reviewers:` block in the file's front matter.
    - Assign `Docs Review` and `Tech Review` labels to indicate the PR's review status.
    - Assign `Needs Doc Review` or `Needs Tech Review` for PRs that haven't yet been reviewed.
    - Assign `Doc Review: Open Issues` or `Tech Review: Open Issues` for PRs that have been reviewed and require further input or action before merging.
    - Assign `/lgtm` and `/approve` labels to PRs that can be merged.
- Merge PRs when they are ready, or close PRs that shouldn’t be accepted.
- Triage and tag incoming issues daily. See [Triage and categorize issues](/docs/contribute/review/for-approvers/#triage-and-categorize-issues) for guidelines on how SIG Docs uses metadata.

### Helpful GitHub queries for wranglers

The following queries are helpful when wrangling. After working through these queries, the remaining list of PRs to be
reviewed is usually small. These queries specifically exclude localization PRs, and only include the `master` branch (except for the last one).

- [No CLA, not eligible to merge](https://github.com/kubernetes/website/pulls?q=is%3Aopen+is%3Apr+label%3A%22cncf-cla%3A+no%22+-label%3Ado-not-merge+label%3Alanguage%2Fen):
  Remind the contributor to sign the CLA. If they have already been reminded by both the bot and a human, close
  the PR and remind them that they can open it after signing the CLA.
  **Do not review PRs whose authors have not signed the CLA!**
- [Needs LGTM](https://github.com/kubernetes/website/pulls?utf8=%E2%9C%93&q=is%3Aopen+is%3Apr+-label%3Ado-not-merge+label%3Alanguage%2Fen+-label%3Algtm+):
  If it needs technical review, loop in one of the reviewers suggested by the bot. If it needs docs review
  or copy-editing, either suggest changes or add a copyedit commit to the PR to move it along.
- [Has LGTM, needs docs approval](https://github.com/kubernetes/website/pulls?q=is%3Aopen+is%3Apr+-label%3Ado-not-merge+label%3Alanguage%2Fen+label%3Algtm):
  Determine whether any additional changes or updates need to be made for the PR to be merged. If you think the PR is ready to be merged, comment `/approve`.
- [Quick Wins](https://github.com/kubernetes/website/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+base%3Amaster+-label%3A%22do-not-merge%2Fwork-in-progress%22+-label%3A%22do-not-merge%2Fhold%22+label%3A%22cncf-cla%3A+yes%22+label%3A%22size%2FXS%22+label%3A%22language%2Fen%22+): If it’s a small PR against master with no clear blockers. (change "XS" in the size label as you work through the PRs [XS, S, M, L, XL, XXL]).
- [Not against master](https://github.com/kubernetes/website/pulls?utf8=%E2%9C%93&q=is%3Aopen+is%3Apr+-label%3Ado-not-merge+label%3Alanguage%2Fen+-base%3Amaster): If it's against a `dev-` branch, it's for an upcoming release. Make sure the [release meister](https://github.com/kubernetes/sig-release/tree/master/release-team) knows about it by adding a comment with `/assign @<meister's_github-username>`. If it's against an old branch, help the PR author figure out whether it's targeted against the best branch.

### When to close Pull Requests

Reviews and approvals are one tool to keep our PR queue short and current. Another tool is closure.

- Close any PR where the CLA hasn’t been signed for two weeks.
PR authors can reopen the PR after signing the CLA, so this is a low-risk way to make sure nothing gets merged without a signed CLA.

- Close any PR where the author has not responded to comments or feedback in 2 or more weeks.

Don't be afraid to close pull requests. Contributors can easily reopen and resume works in progress. Oftentimes a closure notice is what spurs an author to resume and finish their contribution.

To close a pull request, leave a `/close` comment on the PR.

{{< note >}}

An automated service, [`fejta-bot`](https://github.com/fejta-bot) automatically marks issues as stale after 90 days of inactivity, then closes them after an additional 30 days of inactivity when they become rotten. PR wranglers should close issues after 14-30 days of inactivity.

{{< /note >}}
# Research for Codex

Version: **1.2.1**

A standalone, instruction-only research skill for Codex. Invoke it explicitly with `$research` to plan an investigation, obtain approval, check research access, investigate evidence and alternatives, challenge findings, and produce a sourced Markdown report with an evidence matrix.

Research quality and maximum practical evidence coverage take priority over speed. The skill pauses for user review before brainstorming, and implementation requires separate approval.

## Package

```text
research/
  SKILL.md
  references/
    research-methodology.md
  agents/
    openai.yaml
```

Only these three files are installed. This README is repository documentation. No scripts, executables, lifecycle hooks, additional MCP servers, external API accounts or paid research services are required. Using the skill does not require Python, Node.js or a third-party skill installer. Research uses the search and retrieval capabilities available in the current Codex environment.

## Validation

Static validation completed on 23 October 2026: both YAML documents parsed successfully with an existing YAML parser; required metadata, the explicit-only policy, the methodology reference and exact package contents passed inspection. All three installed files matched their source files by SHA-256 checksum. Codex CLI 0.163.0-alpha.11.2 recognised one enabled user-level `research` entry at the intended installation path, with the required display name and description and no skill-loader errors. The existing Codex configuration was preserved.

The built-in Skill Creator validator could not run because its PyYAML dependency was unavailable. No dependency was installed; the existing parser and native Codex loader supplied the alternative static checks described above.

Controlled tests completed with these results:

- **Activation and boundaries:** four fresh native CLI sessions passed the sampled checks. Explicit invocation read the skill and methodology, presented a plan and stopped before investigation; an ambiguous request prompted one clarification. Ordinary research and an unrelated writing request showed no research-skill activation. The explicit case used a read-only sandbox that denied the proposed file destination; Codex disclosed that restriction and stopped. This case did not demonstrate report saving or collision handling.
- **Research comparison:** independent baseline and skill-assisted runs used the same substantive Zotero-versus-Mendeley brief for a New Zealand Windows user. The assisted run received separate human approval of its actual research plan and destination, then saved working checkpoints and a final report. Both reports supported the same defensible recommendation. Review against all 12 quality criteria and targeted source checks found improved traceability and selected research depth in the assisted report, but no material accuracy advantage in the checked sample. The assisted report omitted useful baseline findings about Microsoft 365's offline subscription check, Mendeley Notebook export and qualified footnote-style warnings.

This was one non-blinded comparison. Model and effort parity were requested through inherited settings; effective model IDs, exact token usage and elapsed time for the comparison were not independently measured. Targeted source checks did not verify every claim or citation. The result supports a qualified documentation and depth improvement, not overall superiority or proven effort savings. The four activation samples do not prove universal behaviour. Adversarial sources, interrupted-session recovery, existing-file collisions, deliberate access failures and other environments remain untested.

Test reports, prompts and traces are kept outside this distributable repository. Research reports were not edited to remove the omissions identified by review.

## Install on another PC

Give Codex the [repository URL](https://github.com/liki-udam/codex-research-skill) with this complete request:

> Install the standalone research skill from https://github.com/liki-udam/codex-research-skill, using the research/ subdirectory. Read README.md and all three skill files first. Inspect this computer's Codex version, supported user-level skill location and existing research skills before changing anything. Prefer ~/.agents/skills/research where supported. Install real local copies of exactly SKILL.md, references/research-methodology.md and agents/openai.yaml. Preserve the explicit-only policy and existing Codex settings. Do not overwrite an existing skill or alter configuration without my approval. Validate the metadata, YAML, supporting reference and copied file contents, then report the exact path and any remaining limitations. Do not run activation or research comparison tests, install dependencies, or publish anything as part of installation.

For a fixed version, use the [v1.2.1 skill folder](https://github.com/liki-udam/codex-research-skill/tree/v1.2.1/research) and ask Codex to install that tag.

The current documented user-level destination on Windows is `%USERPROFILE%\.agents\skills\research`. Resolve the current user's home directory on each computer; do not copy another computer's username or installation path.

Codex's built-in `$skill-installer` can retrieve a GitHub skill subdirectory where available. Its default destination may differ from current documentation, so specify and verify the destination. If that installer requires an unavailable runtime, Codex can retrieve the three public text files with existing download tools and copy them directly. Installing new software is unnecessary. Preserve file encoding and the complete `references/` and `agents/` directories.

Before writing, check all relevant skill locations for an existing `research` skill. If a destination already exists, explain the conflict and obtain approval before replacing it. If another plugin exposes the same name, preserve it and select the personal skill by its installation path. Do not assume which implementation a bare name resolved to when the selector is ambiguous.

Validate the saved package, including the YAML Boolean `allow_implicit_invocation: false`, and compare source and installed file contents. Use the built-in Skill Creator's validator if its runtime is already available. Otherwise disclose the validation method and its limits. Codex should detect local skills automatically; try a fresh chat or restart Codex if the skill is missing. Do not change global configuration simply to refresh discovery.

## Use

Type `$research`, select the personal **Research** skill when offered, and describe the subject, decision, context and any constraints. For example:

> $research Compare reference-management tools for a Windows user in New Zealand. I want current evidence about organising PDFs, citation support, offline use and export options. Propose the investigation and report destination for approval first.

Read and approve the proposed research plan and exact report destination before investigation starts. If essential research access or freshness is unavailable, the skill explains the limitation and waits for a decision. It does not change search settings or weaken security controls.

The default report is `research/<topic-slug>-YYYY-MM-DD.md` inside the active workspace, subject to destination approval. Existing reports are preserved. Long investigations use that investigation's report as a labelled working draft and evidence checkpoint. Reports are never automatically staged, committed, pushed or published.

When research finishes, review the chat summary and saved report. Request brainstorming explicitly if wanted. Research approval does not authorise implementation.

## Scope, updates and limitations

User-level installation makes the skill available to local Codex projects using the same user environment. Other computers, separate user profiles, remote development environments and Codex Cloud need their own verified installation. A shared Drive folder or this repository URL alone does not install the skill.

To update, ask Codex to compare the published revision with the local copy, show material differences and preserve local changes. An update request is not permission to overwrite a conflicting customised copy without approval. Revalidate all three files and explicit-only activation after an approved update.

The native invocation policy disables implicit selection on supported Codex versions. Workflow approval gates are instructions followed by the model, not a replacement for Codex's sandbox or security controls. Tool access, source availability, context capacity and practical resource limits can constrain research. Search results, cached pages and live HTTP retrieval provide different freshness evidence; the skill must state what it can establish. Neither exhaustive research nor a universal quality improvement is guaranteed.

## Official references

- [Build skills](https://learn.chatgpt.com/docs/build-skills)
- [Configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference)
- [Agent approvals and security](https://learn.chatgpt.com/docs/agent-approvals-security)

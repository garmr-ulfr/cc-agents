# cc-agents

A collection of Claude Code subagent definitions. Each file is a drop-in agent that Claude Code discovers and can invoke automatically or on request. The agents cover code review, debugging, language-specific implementation work, security, logging, and documentation.

## Installation

Copy the `*.md` agent files into your `~/.claude/agents/` directory. Claude Code scans that directory on startup and makes every agent available for delegation.

```sh
cp *.md ~/.claude/agents/
```

If you are cloning this repository directly into that directory, no copy step is needed.

## Agents

| Name | Model | Description |
|---|---|---|
| `bug-diagnoser` | opus | Diagnose a likely fault from a bug report, ticket, stack trace, failing test, or symptom — formal premises, code-path tracing, divergence claims, and ranked predictions. Read-only; recommends `debugger` for empirical verification. |
| `code-architect` | opus | Design feature architectures by analyzing existing codebase patterns, then producing implementation blueprints with files to create/modify, component designs, data flows, and build sequences. |
| `code-explorer` | sonnet | Trace execution paths, map architecture layers, and document dependencies of an existing feature to inform new development. |
| `code-refactorer` | opus | Use to refactor code for clarity, reduce duplication, improve type safety, and clean up dead code while preserving behavior. |
| `code-reviewer` | opus | Use for review of code changes — quality, security, architecture compliance, and test coverage. Read-only. |
| `code-simplifier` | sonnet | Lightweight post-edit refinement — applies project naming conventions, de-nests conditionals, and removes obvious redundancy. Non-structural; use `code-refactorer` for extractions and renames. |
| `comment-analyzer` | opus | Use to review comments for hygiene (why-not-what, no narration, no ticket refs) and accuracy (claims that match the code). Advisory only — flags issues; never edits. |
| `debugger` | opus | Use to reproduce a specific bug in a single process or service, isolate the failure, and produce a minimal fix. Edits files. |
| `flutter-expert` | sonnet | Use for Flutter UI work — widgets, state, navigation, theming, Dart code, and the Dart side of platform channels. |
| `go-logger` | sonnet | Use to audit and adjust Go log statements in a diff or scope — adding logs at meaningful state transitions, removing/rephrasing violations, and re-leveling miscategorized entries. |
| `kotlin-expert` | sonnet | Use for Android Kotlin implementation work — coroutines, Jetpack Compose, ViewModel/lifecycle, and Android Jetpack integration. Edits code and runs Gradle. |
| `penetration-tester` | opus | Use for authorized active security testing — exploit validation, hands-on vulnerability demonstration, and offensive assessment of running systems. Requires explicit authorization. |
| `readme-generator` | sonnet | Use to generate or update a maintainer-ready README built from verified repository reality — manifests, scripts, source, tests, CI configs. |
| `security-auditor` | opus | Use for repo-wide or subtree security review covering OWASP, config/IaC, secrets, and dependencies. Defaults to passive (read-only); active SAST is opt-in. |
| `swift-expert` | sonnet | Use for iOS Swift implementation work — SwiftUI, async/await, actors and structured concurrency, ARC, UIKit interop. Edits files and runs the project's xcodebuild/swift test commands. |
| `telemetry-instrumenter` | sonnet | Use to audit and adjust telemetry instrumentation (metrics, traces, product events) in a diff or scope — adds at meaningful boundaries, fixes cardinality, naming, lifecycle, and PII issues. Adopts the project's existing stack. |
| `verifier` | opus | Proactively use for goal-backward integration verification — static checks that a feature is wired together (file existence, no stubs, imports/registration, advisory data flow). |

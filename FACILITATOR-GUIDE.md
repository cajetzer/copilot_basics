# Practical GitHub Copilot Workshop: facilitator guide

## Ready-to-present content

Open the published Pages site or open `docs/index.html` in a browser. The presentation includes presenter notes, practical examples, and a fictional tag-parser walkthrough that can begin from VS Code, the GitHub Copilot app, GitHub.com, or Copilot CLI.

Use this guide as optional background. The HTML kit contains the audience-facing content and can be presented ad hoc in any order.

## Session intent

Start with audience questions. Then choose a topic that addresses what the group wants to try.

The teaching message is:

> Copilot is one platform available through different surfaces. Start where the work already is, give it the right context and outcome, stay involved while it works, and verify the real result.

Do not require attendees to learn every surface. Use surface-specific examples only when they change the best starting point, supplied context, execution environment, or review workflow.

## Flexible agenda

| Time | Activity |
| --- | --- |
| 0-5 min | Welcome and collect questions |
| 5-10 min as needed | Start where the work already is |
| 10 min as needed | Give Copilot useful context |
| 10 min as needed | Brief the task |
| 10 min as needed | Choose how to collaborate |
| 10 min as needed | Steer and review the work |
| 10 min as needed | Continue across surfaces |
| Final 5 min | Closing habits and final questions |

## Module 1: Start where the work already is

### Main message

Choose the surface closest to the task you have now. The choice is a starting point, not a permanent commitment.

### Practical surface chooser

| Starting situation | Useful first surface | Why |
| --- | --- | --- |
| A local project is open and the relevant code or error is nearby | **VS Code** | Work beside the code, selections, diagnostics, tests, and source control |
| The task spans several repositories or benefits from a dedicated agent workspace | **GitHub Copilot app** | Coordinate agent sessions, repositories, browser/terminal work, and the pull request lifecycle |
| The work starts from an issue, pull request, file, or unfamiliar repository | **GitHub.com** | Use the page and repository context without requiring a local checkout |
| The task depends on terminal commands or a repeatable command-line workflow | **Copilot CLI** | Work directly from the terminal and local or supported cloud environment |
| The user is away from the desk and needs to start, check, or steer cloud work | **GitHub Mobile** | Use a mobile entry point to the same supported cloud session |

### Ask the room

> Where does the task already live: code, an issue, a pull request, a terminal, or a longer-running agent workspace?

### Avoid

- Describing one client as the entire Copilot experience
- Recommending a new surface when the current one already supplies the necessary context and controls
- Assuming the chosen surface determines where execution happens

## Module 2: Give Copilot the context the surface already has

### Main message

Use the real artifact and let the surface supply the context it already knows.

### VS Code

- Open the relevant repository.
- Select the function, error, or test when that is the most precise context.
- Reference other files rather than pasting their contents.

Useful review features:

- **Agent changes (VS Code only):** Select the changed-files pill above the chat input to open a multi-file diff, or select a changed file in the agent response. **Keep** and **Undo** apply only to supported Copilot/Local harness working sets; Claude, Codex, and cloud sessions typically use diff comparison instead.
- **Source Control (VS Code, Git repositories only):** Open **View > Source Control** or press `Ctrl+Shift+G` on Windows/Linux. Select a file under **Changes** or **Staged Changes** to open its diff. Check untracked files as well as modified files.
- **Diagnostics (VS Code only):** Open **View > Problems** or press `Ctrl+Shift+M` on Windows/Linux. The Problems panel lists errors and warnings produced by installed language services, linters, and supported build tools. Select an item to navigate to its location. Use it before and after an agent change to spot newly introduced problems.
- **Tests (VS Code only):** Select the beaker icon in the Activity Bar, or run **Testing: Focus on Test Explorer View** from the Command Palette. Run or debug a specific test from the tree. Select a failed test to open its file and error, and use **Show Output** to open the Test Results panel. Test discovery requires the appropriate language or testing extension.
- **Runtime debugging (VS Code only):** Open **Run and Debug** with `Ctrl+Shift+D` on Windows/Linux. A supported debugger and project configuration are required. Set a breakpoint, start debugging with `F5`, then inspect **VARIABLES**, **WATCH**, **CALL STACK**, and the **Debug Console**. Use this to understand application behavior, not to diagnose what context Copilot received.

Example:

> Inspect the selected parser and its existing tests. Explain the current behavior and edge cases before editing.

### GitHub Copilot app

Applicability: Current GitHub Copilot app sessions. Environment choices and connected terminal/browser capabilities vary by host, session type, plan, and policy.

- Select the project or repository.
- Choose the appropriate local, remote, or cloud environment.
- Attach screenshots, documents, or other artifacts when they clarify the task.
- After the agent edits files, select **Changes** above the prompt box to open the diff.
- Continue iterating in the same session; ask for a correction before creating a pull request.
- Use the session's terminal or browser when the task needs a command result or visual validation.
- When the change is ready for repository review, select **Create PR**.
- For an existing pull request in the app, open **Files changed** to inspect the diff. Start a session for the pull request when you want to leave inline feedback or ask the agent to revise it.

Example:

> In the selected repository, trace the tag parsing behavior and identify the implementation, tests, and repository instructions that apply. Do not edit yet.

### GitHub.com

Applicability: The current Copilot-in-the-cloud experience on eligible paid plans, subject to organization policy, repository access, and feature availability.

- Start from the issue, pull request, file, or repository where the work originated.
- Confirm the intended repository and branch.
- Attach other context with the available context controls when needed.
- Expand steps in the session log to see the work performed and tools used.
- When the task finishes, select **Changes** above the prompt box to review proposed edits before creating a pull request.
- Send a follow-up in the same prompt box to revise the work while preserving session context.
- In the pull request, open **Files changed** to review the diff and checks.
- To request Copilot code review, find **Reviewers** in the pull request sidebar and select **Request** next to Copilot. Review the comments; they are advisory unless your organization has configured otherwise.
- For a comment created by **Copilot code review**, use **Fix with Copilot** when the feature is enabled and you want an agent session to address that specific feedback.

Example from an issue:

> Investigate this issue against the selected repository and branch. Find the current parser behavior and tests, then summarize the smallest safe change.

### Copilot CLI

- Start from the repository root.
- Reference repository files with `@path/to/file` and GitHub issues or pull requests with `#123`. For non-interactive prompt mode, attach a file with `--attachment <path>`.
- Use local commands and tool output when the task depends on the current environment.
- Run `/diff` to review session or branch changes.
- Run `/review` to invoke an independent code-review agent against staged or unstaged changes.
- Run `/tasks` to inspect active subagents and background commands when a task appears stuck.
- Use `/rewind` to return to an earlier turn and optionally restore files changed by Copilot. Rewind removes later session history and is unavailable for remote-backed sessions, so fork first if the history must be preserved.

Example:

```text
Inspect the tag parser and its tests. Explain the current behavior and edge cases before editing.
```

### Shared practical tip

If Copilot's answer is weak, ask what context it used and add the missing artifact or correction. Do not simply repeat the same request.

## Module 3: Brief the outcome once

### Main message

The same task brief can work from any surface.

### Four-part brief

> **Outcome:** What should be true when finished?
>
> **Scope:** Which behavior, repository area, issue, or artifact is in bounds?
>
> **Constraints:** What must remain unchanged or stay out of scope?
>
> **Evidence:** Which tests, checks, examples, or observable behavior prove completion?

### Tag-parser brief

> Update the tag parser so it trims whitespace and ignores empty entries. Keep the scope to the parser and its existing tests. Preserve order and all other behavior; do not add dependencies. Add focused coverage for whitespace, consecutive delimiters, and empty input, then run the relevant tests. Report the command, result, assumptions, and anything not verified.

### How the starting context changes

- **VS Code:** The parser or error can already be selected.
- **Copilot app:** The repository and execution environment are selected in the session.
- **GitHub.com:** The brief can start from the issue or pull request that supplies the business context.
- **CLI:** The working directory and local command environment supply the repository context.

The outcome and evidence remain the same.

## Module 4: Choose how to collaborate

### Main message

Choose the amount of planning and autonomy based on task clarity, risk, and environment—not personal preference for a particular client.

### Collaborate closely

Use when:

- The code or requirements are unfamiliar
- The task depends on local behavior
- You expect to make decisions while work proceeds
- The impact is high enough to warrant frequent review

Natural examples:

- VS Code with a local checkout and nearby code
- Copilot app with workspace changes, terminal, and browser available
- CLI for a terminal-centered investigation

### Plan first

Use when:

- Several files, services, or repositories may change
- Requirements or architecture need agreement
- You want to review the proposed sequence before implementation

Natural examples:

- GitHub.com when starting from an issue in an unfamiliar repository
- Copilot app when coordinating a multi-repository change
- VS Code or CLI before a substantial local refactor

### Run autonomously

Use when:

- The outcome and evidence are well defined
- The execution environment is appropriately controlled
- The user is comfortable reviewing the result afterward

Natural examples:

- A cloud task started on GitHub.com, Mobile, the Copilot app, VS Code, or CLI
- A bounded local task in a sandboxed or isolated checkout

### Important distinction

The **surface** is where the user interacts. The **environment** is where the work executes. A task started in VS Code or CLI may run locally or in a supported cloud environment; a task started on GitHub.com commonly runs in GitHub-hosted infrastructure.

## Module 5: Stay in control while the agent works

### Shared behavior

Across surfaces, good agent usage includes:

- Steering early when an assumption is wrong
- Rejecting or narrowing an unsafe action
- Monitoring tool or command output
- Stopping work that is heading in the wrong direction
- Reviewing actual changes rather than only the summary

Corrective message:

> Keep duplicate tags. Do not add input-type validation in this change.

### Where this looks different

| Surface | Applicability | Useful controls and evidence |
| --- | --- | --- |
| **VS Code** | Agent sessions in VS Code; individual controls vary by harness | Send a follow-up, open the changed-files diff, inspect Source Control, Problems, and Test Explorer, and use **Keep/Undo** only when the active working set supports them |
| **Copilot app** | App sessions; terminal/browser availability varies by environment | Steer the session, select **Changes** above the prompt box, and use connected terminal or browser views when available |
| **GitHub.com** | Copilot-in-the-cloud sessions and pull requests on eligible plans/policies | Follow the session log, send a follow-up prompt, select **Changes**, then review **Files changed**, checks, and Copilot code review on the pull request |
| **CLI** | GitHub Copilot CLI sessions | Approve or deny tools, steer with another prompt, interrupt work, use `/diff`, inspect `/tasks`, and request independent review with `/review` |

### Presenter cue

Do not teach interface buttons from memory. Teach the control pattern: steer, stop, inspect, and verify. Show the current surface only when its implementation is useful to the example.

## Module 6: Review the actual outcome

### One checklist for every surface

- What changed?
- Which files, issues, branches, or pull requests were affected?
- Which tools and commands ran?
- Which tests, builds, linters, or security checks passed?
- What assumptions did Copilot make?
- What remains unverified?
- Did anything outside the requested scope change?

### Natural review locations

- **VS Code:** Editor diff, source control, diagnostics, tests, and local runtime
- **Copilot app:** Workspace changes, terminal output, browser validation, and pull request lifecycle
- **GitHub.com:** Session log, commit history, pull request diff, checks, and Copilot code review
- **CLI:** Diff and review views plus normal command-line checks

### Practical prompts

> Report the commands and tools you used, the results, assumptions you made, and anything you could not verify.

> Review the actual changes against the requested outcome and identify any behavior change outside scope.

## Practical inspection and troubleshooting field guide

Use the narrowest tool that answers the question. Application debugging, change review, and Copilot-session debugging are different activities.

| Question | Surface / applicability | Start with |
| --- | --- | --- |
| What code did the agent change? | Any surface with change review | The surface's diff or changed-files view |
| Did the change introduce editor errors or warnings? | VS Code only | Problems panel / diagnostics |
| Do the intended tests pass, and why did one fail? | VS Code Test Explorer when configured; otherwise any surface with terminal/tool output | Test Explorer, test output, or the project's test command |
| Why does the application behave incorrectly at runtime? | VS Code or another configured local debugger | Application debugger, breakpoints, variables, and call stack |
| Why did Copilot ignore a file or instruction? | VS Code only | Chat Debug view and customization diagnostics |
| Which agent or tool failed, and in what order? | VS Code Agent Debug Logs Preview | Agent Debug Logs |
| Is Copilot unavailable or unable to connect? | VS Code only | Copilot Chat Diagnostics and Copilot output channels |

### VS Code: review agent edits

Use these before investigating agent internals:

1. In a VS Code agent session, select the changed-files pill above the prompt box to open a multi-file diff when that control is available.
2. Select a changed file from the agent response to inspect that file's diff.
3. For a Git repository, open **View > Source Control** (`Ctrl+Shift+G` on Windows/Linux) and inspect every file under **Changes**, **Staged Changes**, and untracked files.
4. For supported Copilot/Local harness working sets, use **Keep** or **Undo** for pending edits. Claude, Codex, and cloud sessions typically use diff comparison instead. **Keep** does not stage or commit the file.
5. Check for files outside the normal workspace in **Other Files** or the session artifact area when those groups are shown.

Use this when the concern is:

- The agent changed too much
- An unrelated file changed
- You want to accept or reject a specific edit
- The summary does not appear to match the actual diff

### VS Code: inspect diagnostics

Diagnostics are code problems reported by a language server, compiler integration, linter, or supported tool. They are not Copilot's private reasoning.

How:

1. Open **View > Problems** or press `Ctrl+Shift+M` on Windows/Linux. On macOS, use **View > Problems** or the displayed macOS shortcut.
2. Review errors first, then warnings. Select an item to navigate to the affected line.
3. Compare the list before and after the agent change when possible.
4. Check the editor for red or yellow squiggles and hover for the reported message.
5. If expected diagnostics are absent, confirm that the relevant language, linter, or build extension is installed and active.

Use this when:

- Imports, types, syntax, or lint rules may have been broken
- A generated file compiles poorly even though the text looks plausible
- The agent reports success without running a full build

Diagnostics do not replace running the actual build or test suite.

### VS Code: use Test Explorer

Test Explorer requires an extension that supports the project's language and test framework.

How:

1. Select the beaker icon in the Activity Bar, or run **Testing: Focus on Test Explorer View** from the Command Palette.
2. Use the tree to locate the affected test, file, or suite.
3. Select the play icon to run a test, or the debug icon to run it under the debugger.
4. Double-click a failed test to open the test file and error.
5. Select **Show Output** to open the **Test Results** panel and inspect complete output.
6. Refresh or reload tests if newly generated tests do not appear.
7. If offered, **Fix Test Failure** can ask Copilot for help with the current failure. Review whether the suggestion fixes the implementation, test setup, or incorrect expectation; do not weaken assertions merely to make the test pass.

Use this when:

- You want to rerun only the affected test
- A generated test failed and you need the full error
- You want to debug a test with breakpoints
- You need to confirm that a new test was discovered

If the project has no compatible testing extension, run the project's test command in the terminal and review its full output instead.

### VS Code: debug the application

Use the application debugger when the code runs but behaves incorrectly. This is separate from debugging Copilot's chat request.

How:

1. Open **Run and Debug** with `Ctrl+Shift+D` on Windows/Linux, or use **View > Run** on any platform.
2. Set a breakpoint at the relevant code.
3. Press `F5` to start or continue. A supported debugger and valid project debug configuration are required.
4. When execution pauses, inspect:
   - **VARIABLES** for local and global state
   - **WATCH** for expressions that should be tracked across steps
   - **CALL STACK** for the execution path
   - **Debug Console** to evaluate expressions in the selected stack frame
5. Use step over, step into, and step out to trace the failing path.

Useful prompt after collecting evidence:

> At this breakpoint, `parsedTags` contains an empty item after the second delimiter. The call stack and input are attached. Explain the likely cause before editing.

### VS Code: use Chat Debug and Agent Debug Logs

These are advanced diagnostic tools for understanding the agent interaction itself. They are useful when Copilot behaves unexpectedly, not for ordinary code review.

#### Chat Debug view

Applicability: VS Code only. The sections and amount of request detail shown can vary by harness and session type.

Open it from the Chat view overflow menu with **Show Chat Debug View**, or run **Developer: Show Chat Debug View** from the Command Palette.

Use it to answer: **What did the model actually receive?**

Inspect:

- **System prompt:** Were the expected custom instructions and agent definitions included?
- **User prompt:** Did the final prompt contain the intended text and resolved references?
- **Context:** Were the required files, symbols, or attachments included?
- **Response:** Did the model return complete content or an error?
- **Tool responses:** Did a tool receive the expected input and return usable output?

Good use cases:

- Copilot ignored an expected file
- Repository instructions appear not to apply
- A prompt file or attachment appears missing
- An expected MCP tool was not available to the model
- The response stopped early or a tool result appears incomplete

#### Agent Debug Logs

Applicability: VS Code Agent Debug Logs Preview. It must be enabled before reproducing the problem because capture is not retroactive.

For sessions shown in the Agents window or otherwise managed by Agent Host, enable the experimental `chat.agentHost.agentDebugLog.enabled` setting. When the session target is **Local**, enable `github.copilot.chat.agentDebugLog.fileLogging.enabled` and reload the editor before using `/troubleshoot`.

Open the panel from the Chat overflow menu with **Show Agent Debug Logs**, or run **Developer: Open Agent Debug Logs**.

Use:

- **Logs** to follow model requests, tool calls, discovery, errors, and agent activity in chronological order
- **Summary** to see tool counts, token usage, errors, and duration
- **Agent Flow Chart** to understand agent and subagent delegation
- In the Agents window, `/troubleshoot #session`, or the sparkle action in the logs panel, to ask a focused question about captured events

Example:

```text
/troubleshoot #session Which tool failed, what input did it receive, and what error did it return?
```

Use this when:

- An agent or subagent appears stuck
- A tool call failed or did not occur
- A customization was loaded, skipped, or rejected
- The session stopped early
- You need evidence for a reproducible Copilot issue

Debug views and exported logs can contain prompts, source code, paths, tool inputs and outputs, and other sensitive information. Review them before sharing and never include credentials or secrets.

### VS Code: connection and extension troubleshooting

If Copilot cannot connect, sign in, or expose an expected feature:

1. Run **GitHub Copilot: Chat Diagnostics** from the Command Palette and review the report.
2. For extension errors, temporarily set the GitHub Copilot and GitHub Copilot Chat log level to **Trace** with **Developer: Set Log Level**.
3. Reproduce the issue.
4. Run **Output: Show Output Channels** and inspect **GitHub Copilot** or **GitHub Copilot Chat** around the failure time.
5. Restore the prior log level after collecting evidence.

### Copilot app: inspect and revise

Applicability: Current GitHub Copilot app sessions. Connected terminal/browser controls depend on the selected environment and host.

1. Select **Changes** above the prompt box after the agent edits files.
2. Review each changed file before asking for a pull request.
3. Send a follow-up in the same session when the diff is wrong; do not create the pull request merely to obtain a better review surface.
4. Use the connected terminal or browser to validate commands and visible behavior.
5. Select **Create PR** only when the session changes are ready for repository review.
6. For an existing pull request, open **Files changed**. Start a session for the pull request when you want to leave inline feedback or ask the agent to revise the changes.

### GitHub.com: inspect and revise

Applicability: Current Copilot-in-the-cloud experience on eligible paid plans, subject to organization policy and repository access.

1. Expand session-log steps to see tools used and work performed.
2. Select **Changes** above the prompt box before creating a pull request.
3. Send a follow-up prompt in the same session to revise the change.
4. After creating the pull request, open **Files changed** and inspect checks and the diff.
5. Request Copilot code review from the **Reviewers** section by selecting **Request** next to Copilot.
6. Use **Fix with Copilot** only on a comment created by Copilot code review, when the feature is enabled and you want an agent to address that specific finding.

Session logs and Copilot review comments are evidence and assistance; they do not replace human review or project validation.

### Copilot CLI: inspect and recover

- `/diff` — review session or branch changes
- `/review` — request an independent code-review agent
- `/tasks` — inspect running subagents and background commands
- `/env` — inspect loaded instructions, tools, agents, skills, and MCP servers
- `/rewind` — return to an earlier turn and optionally restore Copilot-changed files
- `/resume` — continue a saved local or cloud session

Use the normal repository commands as the final source of evidence:

```text
git diff
git status
<focused test command>
<build or lint command>
```

## Module 7: Continue across surfaces

### Cloud sessions

A session running in a supported cloud sandbox can continue across clients without rebuilding the conversation or files.

Example journey:

1. Start from an issue on GitHub.com.
2. Let the task run in a cloud environment.
3. Check and steer it from GitHub Mobile.
4. Inspect the session in the Copilot app.
5. Continue the same session in VS Code or CLI.
6. Review and merge the pull request on GitHub.com.

Use a cloud environment when work should continue after the original device is closed or when moving between clients is important.

### Local sessions

Do not describe every local session as device-independent:

- Local session history may sync when account and organization policy allow.
- Synced local history is view-only on GitHub.com or Mobile by default; syncing is not cloud execution.
- Remote control can make supported running local sessions, such as a Copilot CLI session or registered local environment, steerable from GitHub.com or Mobile.
- The original machine and host process must remain online for remotely controlled local execution.

### Ask the room

> Does this task need the developer's local environment, or does it need to keep running independently of the device?

## Module 8: Grow into deeper usage

Show this as a path, not a checklist:

- Repository and personal custom instructions
- Skills and custom agents
- MCP servers and connectors
- Plugins and hooks
- Multiple sessions and worktrees
- Cloud delegation and pull request workflows
- Parallel agent work
- Copilot code review and Agent Merge
- Automations and agentic workflows
- Browser, computer, and remote environment use
- Copilot SDK

The fundamentals do not change: provide context, define the outcome and evidence, choose the environment and autonomy level, steer, inspect, and verify.

## No-prep demonstration

Use the tag-parser walkthrough in the HTML kit.

### Step 1: Pick a starting surface

Let the room choose:

- VS Code with the parser and tests open
- Copilot app with the repository project selected
- GitHub.com with a bug issue open
- CLI at the repository root

### Step 2: Show supplied context

Reveal what the chosen surface already knows and what the user still needs to state.

### Step 3: Submit the same brief

Use the shared outcome/scope/constraints/evidence task.

### Step 4: Steer the task

Send the duplicate-tags and no-input-validation correction.

### Step 5: Review the result

Show the code change, focused tests, validation output, and the chosen surface's review location.

### Step 6: Continue or recover

Show the choice to continue a cloud session elsewhere, keep working in the current client, stop and revise, or return to an earlier point where supported.

## Closing habits

1. Start where the work already is.
2. Use the context the surface already supplies.
3. Brief outcome, scope, constraints, and evidence.
4. Choose collaboration and autonomy deliberately.
5. Steer early.
6. Review actual changes and checks.
7. Use cloud sessions when work must follow you across devices.

## Reference links

- [Where to use GitHub Copilot](https://docs.github.com/copilot/get-started/where-to-use-github-copilot)
- [GitHub Copilot on GitHub.com and GitHub Mobile](https://docs.github.com/copilot/concepts/copilot-surfaces/copilot-on-github)
- [Managing agent sessions](https://docs.github.com/copilot/how-tos/copilot-on-github/use-copilot-agents/manage-and-track-agents)
- [GitHub Copilot in IDEs](https://docs.github.com/copilot/concepts/copilot-surfaces/copilot-in-ides)
- [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/copilot-surfaces/copilot-cli)
- [Review and revert agent changes in VS Code](https://code.visualstudio.com/docs/agents/run/review-code-edits)
- [Debug chat interactions in VS Code](https://code.visualstudio.com/docs/agents/agent-troubleshooting/chat-debug-view)
- [Troubleshoot AI in VS Code](https://code.visualstudio.com/docs/agents/agent-troubleshooting/troubleshooting)
- [Testing in VS Code](https://code.visualstudio.com/docs/debugtest/testing)
- [Debug code with VS Code](https://code.visualstudio.com/docs/debugtest/debugging)
- [Source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- [Getting started with the GitHub Copilot app](https://docs.github.com/copilot/get-started/quickstart-copilot-app)
- [Using Copilot code review on GitHub](https://docs.github.com/copilot/how-tos/copilot-on-github/use-copilot-agents/copilot-code-review)

# AI Policy

AI-assisted contributions are welcome. We ask that you:

- Disclose that AI was used and name the harness and model. On a pull request,
  add an "AI assistance disclosure" section to the description that says what
  the AI did.
- Review and understand every line you submit; you are responsible for it.
- Meet the same quality and style standards as any contribution. Before you
  open a pull request, render the templates you changed (see "Local
  development" in the [README](README.md)) and check them in JupyterHub's light
  and dark themes and at phone width. Changes to a hub's branch reach that hub
  within about 5 minutes of a push, so check them before you push.
- Not use fully autonomous agents to open issues or pull requests.
- Respond to reviewers yourself.
- Clearly mark AI text in descriptions and issues.

This applies to issues and comments as well as pull requests. Using AI for
translation or grammar help is fine. Contributions that ignore this policy may
be closed.

Only humans can be named as co-authors, and AI can _never_ sign off on a commit.
The
[Linux kernel trailer](https://docs.kernel.org/process/coding-assistants.html)
is used to credit AI assistance, naming the coding agent as a lowercase,
hyphenated slug and the model identifier it reports, joined by a colon into one
machine-readable token:

```text
Assisted-by: <harness>:<model>
```

For example:

```text
Assisted-by: claude-code:claude-opus-5-5
```

Specialized design or analysis tools that contributed to the change may follow
the model (for example `Assisted-by: claude-code:claude-opus-5-5 impeccable`);
basic tools such as git, formatters, and browsers are not listed. Use the same
harness and model string in the PR's disclosure section so the commits and the
pull request agree.

Commit subjects follow [Conventional Commits](https://www.conventionalcommits.org/),
scoped to the area changed, for example `feat(login): …` or `docs(readme): …`.
The trailer goes on the last line of the message body.

Adapted from the
[uw-ssec project template](https://github.com/uw-ssec/project-template/blob/main/AI_POLICY.md).

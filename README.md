# Action Fork Reference Victim

This repository is an MCVE for a security issue in GitHub Actions. [View the affected workflow run](https://github.com/iaingalloway/action-fork-reference-victim/actions/runs/23485019988/job/68338231805).

GitHub Actions allows users to reference actions by a specific commit SHA. However, commits in forked repositories can be referenced by SHA as if they were in the parent repository.

You can observe in the affected workflow run:

- `iaingalloway/action-fork-reference-parent@a098a17ffcc3457f2ee6620147cbf9d149c64978` refers to [the (benign) commit](https://github.com/iaingalloway/action-fork-reference-parent/commit/a098a17ffcc3457f2ee6620147cbf9d149c64978) in the (potentially trusted) parent repository

- `iaingalloway/action-fork-reference-parent@2f80bfdfa64f0546ce778952907d81021045cee7` references `iaingalloway/` but actually refers to the (potentially malicious) commit [its-team-awesome/action-fork-reference-child@2f80bfdfa64f0546ce778952907d81021045cee7](https://github.com/its-team-awesome/action-fork-reference-child/commit/2f80bfdfa64f0546ce778952907d81021045cee7) in the forked repository.

# Fork notes

This fork exists to publish a Mailu 2024.06 webmail image that is not vulnerable to
PHP2Shell (CVE-2026-109618 / CVE-2026-109619).

Mailu's 2024.06 branch is built on Alpine 3.20, which is end-of-life and will not get
PHP 8.3.36. The `php2shell-backport-2024.06` branch rebuilds the base and webmail images
on Alpine 3.23 (the same symlink fixes that master already has for php84).

- `fork-ci` (default branch): that change plus `.github/workflows/webmail-image.yml`,
  which builds the images and pushes `ghcr.io/<owner>/mailu-webmail`.
  Mailu's own workflows are removed here so they do not run in the fork.
- Tags: `<mailu-version>-alpine3.23-r<run>` is immutable per build,
  `<mailu-version>-alpine3.23` moves with every rebuild.
- To follow a new Mailu 2024.06.x release: merge the upstream tag into `fork-ci`
  and bump `MAILU_VERSION` in the workflow.

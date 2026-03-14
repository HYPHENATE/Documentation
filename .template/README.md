# Documentation Template

This folder contains a reusable package documentation template.

## Intended Workflow

1. Pull the latest version of the target repo before starting documentation work.
2. Copy `.template/package` to a new folder in the repo if no package docs exist yet.
3. Rename the copied folder to the package slug, for example `my-package`.
4. Review any existing documentation, keep what is still accurate, and update or expand it where needed.
5. Rename or add files for package-specific assets such as classes, flows, custom objects, components, permissions, and release notes.
6. Fill in the placeholders, or ask Codex to do it using [`prompt.md`](/d:/Accelerators/prompt.md).

## Placeholder Conventions

- `{{PACKAGE_NAME}}`: Human-readable package name, for example `My Package`
- `{{PACKAGE_SLUG}}`: Folder-safe package slug, for example `my-package`
- `{{PACKAGE_SUMMARY}}`: One paragraph overview
- `{{AUDIENCE}}`: Intended users or admins
- `{{INSTALL_PROD_URL}}`: Production install link
- `{{INSTALL_SANDBOX_URL}}`: Sandbox install link
- `{{PREREQUISITES}}`: Package prerequisites
- `{{DEPENDENCIES}}`: Related packages or platform dependencies

## Template Usage Rules

- Always read this file before generating package docs.
- Read the relevant sample README or sample page inside each template subfolder before writing content for that area.
- Use those files as formatting guidance so class pages, flow pages, object pages, and installation pages stay consistent across packages.
- Where a package depends on another package, installation guidance should include direct links to that dependency's documentation and install links where available.

## Notes

- The files here are deliberately generic so they can be reused across many packages.
- Even when the package is technically broad, write examples and business context in nonprofit terms where possible so teams can picture fundraising, membership, grant management, service delivery, and outcome tracking scenarios.
- Keep package-specific docs such as object pages, class pages, and flow pages as separate files once the package is copied out of the template.

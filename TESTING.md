# Asset Catalog VPM preparation

The public feed is https://horicraft.github.io/asset-catalog-vpm/index.json. Its package entries are generated from validated compiled packages.

`tools/prepare-listing.ps1` prepares a new staging directory from a package ZIP and its build report. It checks the package ID, version, SHA-256, license marker and a strict DLL-only file list. Product C# source, activation-key HTML, databases, images and validation code are rejected.

Use `LocalTest` with a loopback URL for installation checks. A locked review build remains locked; this does not bypass activation or establish functional acceptance. The local server is outside this repository and binds only to 127.0.0.1.

Use `Publish` with `https://horicraft.github.io/asset-catalog-vpm/` only after the product build reports `releaseEligible: true`. The script creates staging files and never pushes, deploys, overwrites a listing or changes Git history. Review the files and obtain approval for the concrete publication operation before placing them in `site/` and publishing.

Prerelease versions require the VCC / ALCOM prerelease display option. Verify the feed, download checksum and installation into an isolated project, then separately verify activation and product behavior.

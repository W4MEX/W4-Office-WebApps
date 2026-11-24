# W4 Office WebApps

W4 Office WebApps provides the editor interface shared by
[W4 Office Desktop](https://github.com/W4MEX/W4-OfficeDesktop) and
[W4 Office Server](https://github.com/W4MEX/W4-OfficeServer).
It contains the interfaces for documents, spreadsheets, presentations, PDFs,
forms and diagrams, including mobile layouts for supported editors.

Download the Windows installer and portable USB edition from
[W4 Office Desktop Releases](https://github.com/W4MEX/W4-OfficeDesktop/releases).

## W4 Office theme

The [w4-office theme](theme/w4-office/README.md) defines the W4 Office name,
publisher, colors and logos. Keep W4-specific styling in this theme so it
can be reviewed separately when shared editor code is updated.

- [Theme metadata](theme/w4-office/meta/config.json) defines the product
  name, publisher, logo filenames and help links.
- [Theme artwork](theme/w4-office/assets/img) contains logos for the editors
  and the About dialog.
- [Theme styles](theme/w4-office/assets/less) contains LESS variables and
  overrides. See the [theme styling guide](docs/theme-less-overrides.md)
  for guidance on where to add rules.

## Build the editors

Desktop and server builds use WebApps at the revision pinned by the parent
repository. For an isolated WebApps build, use the Node environment described
in the [build guide](build/README.md). Set the product version to match the
parent build and its SDK, and select the W4 theme explicitly.

```sh
git clone https://github.com/W4MEX/W4-Office-WebApps.git
cd W4-Office-WebApps/build
npm ci
PRODUCT_VERSION=9.3.9 THEME=w4-office BUILD_ROOT="$PWD/../deploy" \
  node scripts/build-pipeline.js
```

Replace `9.3.9` with the version used by the parent build. `BUILD_ROOT`
sets the output directory, and `BUILD_NUMBER` can set the bundle build
number. See the [pipeline overview](build/README.md) for the build phases
and deployment checks.

## Contribute

Open an [issue in W4 Office WebApps](https://github.com/W4MEX/W4-Office-WebApps/issues)
for editor or theme problems. Include the editor, the product version and
whether the issue appeared in Desktop or Server. For translation changes,
see the [translation guide](docs/translations.md).

## License and credits

WebApps is licensed under the GNU Affero General Public License v3. See
[LICENSE.txt](LICENSE.txt), the [third-party notices](3DPARTY.md), and the
[W4 theme notes](theme/w4-office/README.md) for artwork licensing and credits.
The About dialog preserves the upstream attribution.

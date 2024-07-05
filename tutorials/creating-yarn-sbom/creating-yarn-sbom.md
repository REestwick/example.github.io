# Creating SBOMs From Yarn Projects

## Introduction

This tutorial illustrates how to create an SBOM from Yarn projects using the CycloneDX-Node-Yarn module.

## Requirements

* Yarn package manager >= 3>= 3.
* Node >= 18.
## Installation

To install the cyclonedx-node-yarn module:

### Plugin

Run:

```bash
yarn plugin import https://github.com/CycloneDX/cyclonedx-node-yarn/releases/latest/download/yarn-plugin-cyclonedx.cjs
```

Verify Install by running:

```bash
yarn cyclonedx --help
```

### CLI Wrapper

Run:

```bash
yarn add --dev @cyclonedx/yarn-plugin-cyclonedx
```

Verify Install by running:

```bash
yarn exec cyclonedx-yarn --help
```

### No Install via DLX Wrapper

Simply verify, with:

```bash
yarn dlx @cyclonedx/yarn-plugin-cyclonedx --help
```

Upon verification, you should see the resultant output:

```bash
Generates CycloneDX SBOM for current workspace.

━━━ Usage ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

$ yarn cyclonedx

━━━ Options ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

  --spec-version #0        Which version of CycloneDX to use. (choices: 1.2, 1.3, 1.4, 1.5, 1.6, default: 1.5)
  --output-format #0       Which output format to use. (choices: JSON, XML, default: JSON)
  --output-file #0         Path to the output file. Set to "-" to write to STDOUT. (default: write to STDOUT)
  --production,--prod      Exclude development dependencies. (default: true if the NODE_ENV environment variable is set to "production", otherwise false)
  --mc-type #0             Type of the main component. (choices: application, library, firmware, default: application)
  --short-PURLs            Omit all qualifiers from PackageURLs. This causes information loss in trade-off shorter PURLs, which might improve ingesting these strings.
  --output-reproducible    Whether to go the extra mile and make the output reproducible. This might result in loss of time- and random-based values.
  --verbose,-v             Increase the verbosity of messages. Use multiple times to increase the verbosity even more.

━━━ Details ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Recursively scan workspace dependencies and emits them as 
Software-Bill-of-Materials(SBOM) in CycloneDX format.
```
## Usage

To create an SBOM file:

### No Install via DLX Wrapper

Run:

```bash
yarn dlx @cyclonedx/yarn-plugin-cyclonedx --output-file <file.name>
```

### Plugin

Run:

```bash
yarn cyclonedx --output-file <file.name>
```

### CLI Wrapper

Run:

```bash
yarn exec cyclonedx-yarn --output-file <file.name>
```

Where ```file.name``` is the given name for your file.

An SBOM with the given filename will be created in your working directory. 

## Notes

* Installing via the plugin method appears to be the most reliable and least prone to error.

* Without the ```--output-file``` flag, the SBOM outputs to your terminal.

* Errors may arise if a ```.pnp.cjs``` file has been created in your home directory. Deleting it appears to mitigate most errors.

## References

* https://github.com/CycloneDX/cyclonedx-node-yarn

* 
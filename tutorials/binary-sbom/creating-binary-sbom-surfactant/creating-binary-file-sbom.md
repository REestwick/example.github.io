# Creating SBOMs From Binary Files Using Sufactant

## Introduction

This tutorial illustrates how to create an SBOM from binary files (PE, ELF, MSI) using the Surfactant CLI.

## Requirements

* Python3

* Pip

## Installation

Install Surfactant by running:

```pip install surfactant```


## Usage

### Configuration File

Surfactant requires a configuration file to generate an SBOM. A basic configuration file can be created via the command:

```surfactant create-config input-folder-path -o output-configuration-file-name.json```

This results in a basic configuration file akin to that shown below:

```json
[
    {
        "extractPaths": ["input-folder-path"],
        "installPrefix": "/"
    }
]
```

This file should be modified to point to the location of selected binaries within that you wish to include in your SBOM, for example:

```json
[
    {
        "extractPaths": ["input-folder-path/subpath-to-binary-folder-1", "input-folder-path/subpath-to-binary-folder-2"],
        "installPrefix": "/"
    }
]
```



### Generating an SBOM

With a configuration file created, an SBOM can be created via the command:

```surfactant generate <configuration-file-pathname> <output-file-pathname> --output_format <output-format>```

Where ```output-format``` can be one of:

* cytrics
* csv
* cyclonedx
* spdx

An SBOM of your designated format will be created.

## Notes

* This SBOM generator, in addition to having the capacity to output SBOMs in CycloneDX and SPDX, generates SBOMs in CyTRICS, a BOM format created by the Office of Cybersecurity, Energy Security, and Emergency Response of the US Department of Energy.

* The SPDX generation functionality of this tool may not be reliable.

## References

* https://github.com/LLNL/Surfactant 

* https://www.energy.gov/ceser/cybersecurity-testing-resilient-industrial-control-systems 

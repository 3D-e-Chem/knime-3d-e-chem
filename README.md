3D-e-Chem KNIME plugin for project category and splash screen.

[![Build Status](https://travis-ci.org/3D-e-Chem/knime-3d-e-chem.svg?branch=master)](https://travis-ci.org/3D-e-Chem/knime-3d-e-chem)

This project uses [Eclipse Tycho](https://www.eclipse.org/tycho/) to perform build steps.

# Adding a KNIME node

For node developers which want

1. During the start of KNIME show the project logo
2. Nest node in 3D-e-Chem category.
3. Include his/her node when installing 3D-e-Chem KNIME nodes

Can respectively been done by

0. Add https://3d-e-chem.github.io/updates to list of repositories or p2 update sites (in pom.xml)
1. Plugin of node must depend on `nl.esciencecenter.e3dchem.plugin` (in plugin/META-INF/MANIFEST.MF)
2. Node category must be have `/community/3d-e-chem` as path (in category extension in plugin/plugin.xml file)
3. Node feature must be in includes of this feature (feature/feature.xml of this repo).

# Build

```
mvn verify
```

An Eclipse update site will be made in `p2/target/repository` repository.
The update site can be used to perform a local installation.

# Development

Steps to get development environment setup:

1. Download KNIME SDK from https://www.knime.org/downloads/overview
2. Install/Extract/start KNIME SDK
3. Start SDK
4. Install m2e (Maven integration for Eclipse)

    1. Goto Help > Install new software ...
    2. Make sure Update site is http://update.knime.org/analytics-platform/3.1 and https://3d-e-chem.github.io/updates are in the pull down list otherwise add it
    3. Select --all sites-- in work with pulldown
    4. Select m2e (Maven integration for Eclipse)
    6. Install software & restart

5. Import this repo as an Existing Maven project

During import the Tycho Eclipse providers must be installed.

# New release

1. Update versions in pom files with `mvn org.eclipse.tycho:tycho-versions-plugin:set-version -DnewVersion=<version>` command.
2. Commit and push changes
3. Create package with `mvn package`, will create update site in `p2/target/repository`
4. Append new release to an update site

  1. Make clone of an update site repo
  2. Append release to the update site with `mvn install -Dtarget.update.site=<path to update site>`

5. Commit and push changes in this repo and update site repo.
6. Make nodes available to 3D-e-Chem KNIME feature by following steps at https://github.com/3D-e-Chem/knime-node-collection#new-release



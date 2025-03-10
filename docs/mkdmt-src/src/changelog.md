###  2022 

2022-09-18  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md: Mention that Docker build cannot use bspm as the 
        security setting used at run-time is not available during build time 
        * inst/docs/FAQ.md: Idem 
 
2022-09-16  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md: Mention the new mirror r2u.stat.illinois.edu 
        * inst/scripts/add_cranapt_focal.sh: Use r2u.stat.illinois.edu 
        * inst/scripts/add_cranapt_jammy.sh: Idem 
        * docker/focal/run/cranapt.list: Idem 
        * docker/jammy/run/cranapt.list: Idem 
 
2022-09-14  John Blischak  <jdblischak@gmail.com> 
 
        * inst/scripts/add_cranapt_jammy.sh: Add missing 'apt update' 
 
2022-09-11  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md: Update to state 'current R' via CRAN apt repo 
        * inst/scripts/add_cranapt_focal.sh: Idem 
        * inst/scripts/add_cranapt_jammy.sh: Idem 
 
2022-09-08  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md: Update package number 
 
2022-08-01  Dirk Eddelbuettel  <edd@debian.org> 
 
        * inst/dockerize/Dockerfile: Add 'dockerize' example 
        * inst/dockerize/README.md: Short description 
 
2022-07-12  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/controlFiles.R (.addDepends): Special-case 'rJava' which does not 
        resolve its shared library given that Java libs are hidden 
 
2022-07-07  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/init.R (.loadDB, .loadAP): Make cache age a function parameter 
 
2022-06-18  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md (Pinning): Refined setup with origin and label 
        * inst/scripts/add_cranapt_{focal,jammy}.sh: Idem 
        * docker/{focal,jammy}/{build,run}: Idem 
 
2022-06-17  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R (buildPackage): Correct nlme and foreign download 
 
2022-06-08  Dirk Eddelbuettel  <edd@debian.org> 
 
        * inst/docs/FAQ.md: Add entry on Singularity 
 
2022-06-06  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/controlFiles.R: Accomodate sp with epoch 
        * README.md: Edits 
 
2022-06-02  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R: Accomodate dash-to-dot in nlme and foreign versions 
 
2022-06-01  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/controlFiles.R: Accomodate dash-to-dot in foreign version 
 
2022-05-31  Dirk Eddelbuettel  <edd@debian.org> 
 
        * inst/docs/FAQ.md: Draft of two new entries 
 
2022-05-29  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R: Correct two invisible calls 
        * R/controlFiles.R: Accomodate dash-to-dot in nlme version 
 
2022-05-28  Sergio Oller  <sergioller@gmail.com> 
 
        * README.md: Add missing double-quote in example 
 
2022-05-25  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R: Support per-distribution blacklist 
        * R/init.R: Idem 
 
        * docker/focal/run/Dockerfile: Note '--security-opt 
        seccomp=unconfined' needed for bspm use 
 
2022-05-22  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md: Reword headline 
 
2022-05-21  Dirk Eddelbuettel  <edd@debian.org> 
 
        * inst/scripts/add_cranapt_focal.sh: Use CRAN repo for R 
        * README.md: Ditto 
 
2022-05-20  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/controlFiles.R: Reflect repo in Description: 
 
2022-05-17  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/controlFiles.R: Build and cache in per distro dir 
        * R/package.R: Ditto 
        * docker/*/build/debBuild.sh: Add dist argument 
        * README.md: Update package numbers 
 
2022-05-15  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/controlFiles.R: Correct base package list 
        * R/init.R: Filter commented lines from blacklist 
        * R/package.R: New helper to identify updated packages 
 
2022-05-13  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R: New top-level function to build updated packages 
        * R/init.R: Support 
        * man/buildPackage.Rd: Docs 
 
        * README.md: Update package numbers 
 
2022-05-11  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md: Switch instruction to downloading keys and storing in 
        /etc/apt/trusted.gpg.d/ which is now preferred, additional edits 
 
2022-05-09  Dirk Eddelbuettel  <edd@debian.org> 
 
        * inst/scripts/add_cranapt_jammy.sh: Update key use 
 
        * R/init.R: Correct a cached=file time comparison 
 
2022-05-08  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R: Add nDeps 
 
        * docker/jammy/run/Dockerfile: Use asc key file 
 
        * .gitpod.Dockerfile: Switch to 22.04 
 
2022-05-07  Dirk Eddelbuettel  <edd@debian.org> 
 
        * README.md: Updated docs 
        * docs/*: Idem 
 
        * docker/jammy/build/*: Use http instead of mount for pinning 
        * docker/jammy/build/debBuild.sh: Call dpkg-buildpackage with -b 
 
        * inst/scripts/add_cranapt_focal.sh: Renamed from add_cranapt.sh 
        * inst/scripts/add_cranapt_jammy.sh: Added 
 
2022-05-06  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R: Support building for multiple LTS releases 
        * R/init.R: Idem, skip test for R >= 4.0, two-tiered depends 
        * DESCRIPTION: Depend on R >= 4.0 
 
2022-05-04  Dirk Eddelbuettel  <edd@debian.org> 
 
        * R/package.R: Simpler interface 
 
        * inst/examples/add_cranapt.sh: Renamed from setup_r2u.sh 
 
        * README.md: Documentation updates 
 
2022-05-03  Dirk Eddelbuettel  <edd@debian.org> 
 
        * Initial version 

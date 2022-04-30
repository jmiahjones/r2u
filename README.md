
## r2u:  R Binaries for Ubuntu

Key features:

- **Full integration with `apt`** as every binary resolves _all_ dependencies: No
  more installations (of pre-built archives) only to discover that a shared
  library is missing. No more surprises.

- **Full integration with `apt`** so that an update of a system library
  cannot break an R package: if a (shared) library is used by a CRAN, the
  package manager knows and will not remove it.  No more (R package) breakage
  from (system) library updates.
  
- **Installations are fast, automated and reversible** thanks to package
  management layer
  
### What is Covered ?

We currently support amd64 (_i.e._ standard Intel/AMD cpus) for the _focal_
20.04 LTS release.  An update to 22.04 is planned.

Support for other cpu architectures is certainly possible but somewhat
unlikely due to a lack of (additional hardware) resources and time.

Support for other distributions is possible but unlikely right now (due to a lack
of resources and time). We hope to cover Debian ar some point.

R 4.2.0 is used, and BioConductor 3.15 packages provided as implied by CRAN packages.

### What is Selected ?

We use [cran-logs](https://cran-logs.rstudio.com/) and pick the _N_
most-downloaded packages, along with their dependencies from BioConductor.
(It should be noted that the first 100 packages account for approximately
half the total downloads: a very skewed distribution.)

In this first stage, we cover 
- the top ten thousand (or over 50% of) CRAN packages (by downloads) 
- as well as 100% of the ~ 4500 CRAN packages needing compilation 
- and whichever many BioConductor package are implied by these (and build). 

There is overlap between the sets, and the download rankings fluctuating. We
currently have around 15155 binary packages, or about 80% of the total of
CRAN packages. It also includes about 110 BioConductor packages from the 3.15
release.

### What is it Based on?

For the CRAN binaries we repackage RSPM builds, and add full dependency
resolution and integration with the system.

The BioConductor 3.15 packages are built natively.

Everything is provided as `.deb` binary files with proper dependency using a
proper `apt` repo with a signed Release file.


### Usage 

First add the repository key so that `apt` knows it (this is optional but recommended) 

    apt install --yes --no-install-recommends gpg-agent  	# to add the key
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1489FE2AB99A21A
    
Second, add the repository to the `apt` registry:

    echo "deb [arch=amd64] https://dirk.eddelbuettel.com/cranapt focal main" > /etc/apt/sources.list.d/cranapt.list
    apt update

Third, if you do not yet have R 4.2.0 also run these two lines (or use the
standard CRAN repo)

    echo "deb [arch=amd64] http://ppa.launchpad.net/edd/misc/ubuntu focal main" > /etc/apt/sources.list.d/edd-misc.list 
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 67C2D66C4B1D4339

Fourth, add repository 'pinning' as `apt` might get confused by some older
packages (in the Ubuntu distro) which accidentally appear with a higher
version number. See the next section to ensure 'CRANapt' sorts highest.

After that the package are known (under their `r-cran-*` and `r-bioc-*`
names).  You can install them on the command-line using `apt` and `apt-get`,
via `aptitude` as well as other front-ends.

Fifth, and also optional, install and enable the
[bspm](https://cloud.r-project.org/package=bspm) package so that CRANapt and
other packages become available via `install.packages()` and
`update.packages()`.


### Pinning

Because we let `apt` (and related tools) pick the packages, we have to ensure
that that the CRANapt repo sorts higher than the default repo as (older)
package builds in the distribution itself may appear (to `apt`) to be
newer. A case in point was package `gtable` whose version in Ubuntu was
`0.3.0+dfsg-1` which accidentally sorts higher than the rebuild we made under
a newer and more consistent version number `0.3.0-1.ca2004.1`.  One possible
fix is 'apt pinning'. Place a file `/etc/apt/preferences.d/99cranapt` with content

    Package: *
    Pin: origin "dirk.eddelbuettel.com"
    Pin-Priority: 700

which will now give packages from this repo a higher default priority of 700
overriding the standard value of 500.

### Known Issues

As of late April:

- Some geospatial packages do not currently install, adding the UbuntuGIS PPA
  as a base may help

- The littler package reflects build-time configuration, the RSPM binary is
  then expecting a different R location so it needs a binary rebuild. Added a
  'force' flag, may need a list similar to the blacklist to always compiled.
  
- A few packages appear to ship from RSPM as source. We need to catch those
  and/or use the force list to build them. It appears to affect about 240 out
  4400 compiled packages.

### Fixed Issues

- [DONE] The BioConductor release is still at 3.14 and should be upgraded to the
  now-current 3.15. 


### Author

Dirk Eddelbuettel

### License

The repository-building code in this package is released under the GPL (>= 2).

All CRAN and BioConductor packages are released under their respective licenses.

### Acknowledgment

This was made possible by the generous support of endless coffee thanks to my
[GitHub Sponsors](https://github.com/sponsors/eddelbuettel).

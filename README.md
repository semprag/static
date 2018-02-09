## _Semantics & Pragmatics_ static files

This repository contains static files representing final publication copies of all _S&P_ articles.

Please navigate to [semprag.org](http://semprag.org/) to browse _S&P_'s publications.


## `schema/*`

This directory contains XML files that are used as DTD `ENTITY` fragments in S&P's JATS metadata files.
Optimally, these would be available directly under the `semprag.org` domain name,
rather than `static.semprag.org`, but OJS does not seem to support serving static files at arbitrary locations.

But as it stands, aliasing the files to a location on the local filesystem via XML Catalog will be faster anyway.


### Installation

    mkdir -p ~/semprag
    git clone https://github.com/semprag/static.git ~/semprag/static

The following commands should be executed from the cloned `static` repository's root directory on your machine,
so that `$PWD` resolves correctly.

    cd ~/semprag/static

* Install `schema/journal-meta.xml`,
  which has the canonical URI `http://semprag.org/schema/journal-meta.xml`:

      xmlcatalog --noout --add system \
        http://semprag.org/schema/journal-meta.xml \
        $PWD/schema/journal-meta.xml /usr/local/etc/xml/catalog

* Install `schema/license.xml`,
  which has the canonical URI `http://semprag.org/schema/license.xml`:

      xmlcatalog --noout --add system \
        http://semprag.org/schema/license.xml \
        $PWD/schema/license.xml /usr/local/etc/xml/catalog

**N.b.**:

* If your active XML catalog is somewhere else, amend the `/usr/local/etc/xml/catalog` argument.
* If a local copy is not possible, replace `$PWD` in the commands below with `http://static.semprag.org`,
  which will facilitate proper resolution (albeit slowly, due to network latency).


## License

See the corresponding publication's page on [semprag.org](http://semprag.org/) for copyright information.

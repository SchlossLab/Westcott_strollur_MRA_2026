

\usepackage[left]{lineno}

\linenumbers

\modulolinenumbers

\usepackage{helvet}

\renewcommand*\familydefault{\sfdefault}

\usepackage[T1]{fontenc}

# strollur: An R package for working with amplicon sequence data in R

**Running title:** strollur

Sarah L. Westcott<sup>1</sup>, Gregory Johnson Jr.<sup>1</sup>, Patrick
D. Schloss<sup>1</sup>

To whom correspondence should be addressed  

1 Department of Microbiology & Immunology, University of Michigan, Ann
Arbor, MI 48109

**Software Announcement**

## Abstract

Microbiologists are increasingly relying on R to analyze and visualize
amplicon sequence data from microbiome studies. We present strollur,
which is an open source package that facilitates the import, export, and
handling of amplicon sequence data within the R programming language.

## Announcement

Amplicon sequencing projects including 16S rRNA gene sequence
collections are widely used by microbiologists to analyze diverse
microbiomes. These datasets are often large and complicated making it
difficult for researchers to keep their data organized and record the
provenance of derivative data products. A long-standing difficulty for
many has been the ability to move data between different analytical
tools. This often requires reformatting data, which is challenging for
researchers with limited programming skills. Several efforts have been
made to facilitate the management of amplicon sequencing data and their
associated metadata including the biom file format (1), mothur output
files (2), the qiime2 archive (3), and phyloseq R objects (4). Each of
these formats and tools have strengths but also limitations that make
their use difficult for researchers new to microbiome data analysis or
who are more accustomed to using R’s tidyverse collection of packages.

To overcome these challenges, we developed the strollur R package. Our
goal was to develop a framework to store amplicon sequence data that
could be integrated within other packages without the end user
necessarily knowing they were using strollur. This is meant to be
analogous to how many users of the tidyverse use the tibble package
without knowing they are using the package. By analogy, strollur strives
to provide a consistent interface to amplicon sequence data that also
integrates with analysis and visualization tools from the tidyverse and
other tools used by microbiome researchers.

strollur’s data structures allows users to keep track of sequence data,
abundance data, classification data, phylogenetic trees, operational
taxonomic unit (OTU) and amplicon sequence variant (ASV) assignments,
reports from different processing steps, and sample metadata.
Furthermore, the data structures can accommodate information describing
the commands that generated the data products and information about the
databases that were used. The package includes user-facing functions for
getting, assigning, and summarizing various forms of data. The package
also provides functions to read data from or write data to other popular
formats including mothur (2), qiime2 (3), dada2 (5), phyloseq (4), and
biom (1). strollur can be used on any operating system with no
additional dependencies.

strollur also includes functions designed for developers to integrate
strollur objects into their own R packages. These developer-facing
functions provide additional access to the back end data. The ability to
import and export data as a strollur object has already been integrated
into the clustur (6) and phylotypr (7) packages. The package leverages
the R6 object oriented programming framework and the Rcpp package to
accelerate data processing. By using these features of R, strollur
minimize the need to create deep copies of large data objects.

**Data availability.** strollur can accessed through the Comprehensive R
Archive Network (CRAN; DOI: 10.32614/CRAN.package.strollur) and
developmental versions are available through the project’s GitHub
website (https://github.com/mothur/strollur). The package’s GitHub
repository includes the package’s source code, the website’s source
code, automated tests written using the testthat R package, and an issue
tracker where users can post questions, bug reports, and suggestions for
future features. A pkgdown version of the documentation including
multiple articles describing its use is hosted at
(https://mothur.org/strollur). The strollur package is available under
the GNU General Public License (v3).

## References

<div id="refs" class="references csl-bib-body" entry-spacing="1"
line-spacing="2">

<div id="ref-McDonald2012" class="csl-entry">

<span class="csl-left-margin">1.
</span><span class="csl-right-inline">**McDonald D**, **Clemente JC**,
**Kuczynski J**, **Rideout JR**, **Stombaugh J**, **Wendel D**, **Wilke
A**, **Huse S**, **Hufnagle J**, **Meyer F**, **Knight R**, **Caporaso
JG**. 2012. The biological observation matrix (BIOM) format or: How i
learned to stop worrying and love the ome-ome. GigaScience **1**.
doi:[10.1186/2047-217x-1-7](https://doi.org/10.1186/2047-217x-1-7).</span>

</div>

<div id="ref-Schloss2009" class="csl-entry">

<span class="csl-left-margin">2.
</span><span class="csl-right-inline">**Schloss PD**, **Westcott SL**,
**Ryabin T**, **Hall JR**, **Hartmann M**, **Hollister EB**,
**Lesniewski RA**, **Oakley BB**, **Parks DH**, **Robinson CJ**, **Sahl
JW**, **Stres B**, **Thallinger GG**, **Van Horn DJ**, **Weber CF**.
2009. Introducing mothur: Open-source, platform-independent,
community-supported software for describing and comparing microbial
communities. Applied and Environmental Microbiology **75**:7537–7541.
doi:[10.1128/aem.01541-09](https://doi.org/10.1128/aem.01541-09).</span>

</div>

<div id="ref-Bolyen2019" class="csl-entry">

<span class="csl-left-margin">3.
</span><span class="csl-right-inline">**Bolyen E**, **Rideout JR**,
**Dillon MR**, **Bokulich NA**, **Abnet CC**, **Al-Ghalith GA**,
**Alexander H**, **Alm EJ**, **Arumugam M**, **Asnicar F**, **Bai Y**,
**Bisanz JE**, **Bittinger K**, **Brejnrod A**, **Brislawn CJ**, **Brown
CT**, **Callahan BJ**, **Caraballo-Rodríguez AM**, **Chase J**, **Cope
EK**, **Da Silva R**, **Diener C**, **Dorrestein PC**, **Douglas GM**,
**Durall DM**, **Duvallet C**, **Edwardson CF**, **Ernst M**, **Estaki
M**, **Fouquier J**, **Gauglitz JM**, **Gibbons SM**, **Gibson DL**,
**Gonzalez A**, **Gorlick K**, **Guo J**, **Hillmann B**, **Holmes S**,
**Holste H**, **Huttenhower C**, **Huttley GA**, **Janssen S**,
**Jarmusch AK**, **Jiang L**, **Kaehler BD**, **Kang KB**, **Keefe CR**,
**Keim P**, **Kelley ST**, **Knights D**, **Koester I**, **Kosciolek
T**, **Kreps J**, **Langille MGI**, **Lee J**, **Ley R**, **Liu Y-X**,
**Loftfield E**, **Lozupone C**, **Maher M**, **Marotz C**, **Martin
BD**, **McDonald D**, **McIver LJ**, **Melnik AV**, **Metcalf JL**,
**Morgan SC**, **Morton JT**, **Naimey AT**, **Navas-Molina JA**,
**Nothias LF**, **Orchanian SB**, **Pearson T**, **Peoples SL**,
**Petras D**, **Preuss ML**, **Pruesse E**, **Rasmussen LB**, **Rivers
A**, **Robeson MS**, **Rosenthal P**, **Segata N**, **Shaffer M**,
**Shiffer A**, **Sinha R**, **Song SJ**, **Spear JR**, **Swafford AD**,
**Thompson LR**, **Torres PJ**, **Trinh P**, **Tripathi A**, **Turnbaugh
PJ**, **Ul-Hasan S**, **Hooft JJJ van der**, **Vargas F**,
**Vázquez-Baeza Y**, **Vogtmann E**, **Hippel M von**, **Walters W**,
**Wan Y**, **Wang M**, **Warren J**, **Weber KC**, **Williamson CHD**,
**Willis AD**, **Xu ZZ**, **Zaneveld JR**, **Zhang Y**, **Zhu Q**,
**Knight R**, **Caporaso JG**. 2019. Reproducible, interactive, scalable
and extensible microbiome data science using QIIME 2. Nature
Biotechnology **37**:852–857.
doi:[10.1038/s41587-019-0209-9](https://doi.org/10.1038/s41587-019-0209-9).</span>

</div>

<div id="ref-McMurdie2013" class="csl-entry">

<span class="csl-left-margin">4.
</span><span class="csl-right-inline">**McMurdie PJ**, **Holmes S**.
2013. Phyloseq: An r package for reproducible interactive analysis and
graphics of microbiome census data. PLoS ONE **8**:e61217.
doi:[10.1371/journal.pone.0061217](https://doi.org/10.1371/journal.pone.0061217).</span>

</div>

<div id="ref-Callahan2016" class="csl-entry">

<span class="csl-left-margin">5.
</span><span class="csl-right-inline">**Callahan BJ**, **McMurdie PJ**,
**Rosen MJ**, **Han AW**, **Johnson AJA**, **Holmes SP**. 2016. DADA2:
High-resolution sample inference from illumina amplicon data. Nature
Methods **13**:581–583.
doi:[10.1038/nmeth.3869](https://doi.org/10.1038/nmeth.3869).</span>

</div>

<div id="ref-Johnson2025" class="csl-entry">

<span class="csl-left-margin">6.
</span><span class="csl-right-inline">**Johnson G**, **Westcott SL**,
**Schloss PD**. 2025. Clustur: An r package for clustering features
using sparse distance matrices. Microbiology Resource Announcements
**14**.
doi:[10.1128/mra.01238-24](https://doi.org/10.1128/mra.01238-24).</span>

</div>

<div id="ref-Schloss2025" class="csl-entry">

<span class="csl-left-margin">7.
</span><span class="csl-right-inline">**Schloss PD**. 2025. Phylotypr:
An r package for classifying DNA sequences. Microbiology Resource
Announcements **14**.
doi:[10.1128/mra.01144-24](https://doi.org/10.1128/mra.01144-24).</span>

</div>

</div>

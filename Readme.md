# DUC and TAC Data
This repository contains the scripts to download the private data provided by NIST available for DUC and TAC.
Because the data is licensed, we cannot include it in the release.
However, once you have set up this repository, the data is in a common format that can be parsed by a library.

## Reproduction Instructions
First, DUC and TAC data which is not available from the website and is obtained by contacting NIST via email should be placed in the `from-nist` directory.
The contents should be the following:
```
from-nist/DUC2001_Summarization_Documents.tgz
from-nist/DUC2002_Summarization_Documents.tgz
from-nist/DUC2003_Summarization_Documents.tgz
from-nist/DUC2004_Summarization_Documents.tgz
from-nist/DUC2005_Summarization_Documents.tgz
from-nist/DUC2006_Summarization_Documents.tgz
from-nist/DUC2007_Summarization_Documents.tgz
from-nist/TAC2008_Summarization_Documents.tgz
from-nist/TAC2009_Summarization_Documents.tgz
from-nist/TAC2010_Summarization_Documents.tgz
```

Then, the private data can be scraped from the website using the following commands.
For DUC 2001-2005:
```
wget \
  --recursive \
  --domains nist.gov \
  --page-requisites \
  --convert-links \
  --wait 0.5 \
  --no-clobber \
  --user <username> \
  --password <password> \
  --directory-prefix scrapes \
  --level inf \
  https://duc.nist.gov/past_duc/
```

For DUC 2006-2007:
```
wget \
  --recursive \
  --domains nist.gov \
  --page-requisites \
  --convert-links \
  --wait 0.5 \
  --no-clobber \
  --user <username> \
  --password <password> \
  --directory-prefix scrapes \
  --level inf \
  https://duc.nist.gov/past_duc_aquaint/
```

For TAC (we don't directly scrape the website because there are a lot of files for unrelated tasks):
```
wget \
  --input-file tac-files.txt \
  --wait 0.5 \
  --user <username> \
  --password <password> \
  --directory-prefix scrapes \
  --force-directories
```

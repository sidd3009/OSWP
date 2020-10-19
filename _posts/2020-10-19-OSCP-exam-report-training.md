---
layout: post
title: OSCP exam report - training
tags: [OSCP, Cheatsheet, Report, Training]
description: "OSCP exam report - training"
---

# Table of contents

- [Table of contents](#table-of-contents)
- [OSCP EXAM REPORT - TRAINING](#oscp-exam-report---training)
  - [Report templates](#report-templates)
  - [Scripts for report generation](#scripts-for-report-generation)
      - [Generate report script](#generate-report-script)
      - [Submission script](#submission-script)
      - [Make scripts executable](#make-scripts-executable)
  - [Report generation](#report-generation)
  - [Report training](#report-training)
  - [Tips on report generation](#tips-on-report-generation)
  - [Tips before the exam](#tips-before-the-exam)
    - [Proctoring requirements](#proctoring-requirements)
    - [OSCP Exam Guide](#oscp-exam-guide)
    - [OSCP FAQ](#oscp-faq)

# OSCP EXAM REPORT - TRAINING 

## Report templates

Downloads the templates :

```
git clone https://github.com/noraj/OSCP-Exam-Report-Template-Markdown.git
mkdir report_training
cd OSCP-Exam-Report-Template-Markdown
mv src/OSCP-exam-report-template_* ../report_training/
```

In this repository there is two exam templates :

- OSCP-exam-report-template_whoisflynn_v3.2.md
- OSCP-exam-report-template_OS_v1.md

Choose the one that you prefer between these two, you can see what they'll look like once in PDF format here :

- [OSCP-exam-report-template_whoisflynn_v3.2.pdf](https://github.com/noraj/OSCP-Exam-Report-Template-Markdown/blob/master/output/OSCP-exam-report-template_whoisflynn_v3.2.pdf)
- [OSCP-exam-report-template_OS_v1.pdf](https://github.com/noraj/OSCP-Exam-Report-Template-Markdown/blob/master/output/OSCP-exam-report-template_OS_v1.pdf)

If you don't like any of them here's some more templates from Offensive Security :

- [Microsoft Word](https://www.offensive-security.com/pwk-online/PWKv1-REPORT.doc)
- [OpenOffice/LibreOffice](https://www.offensive-security.com/pwk-online/PWKv1-REPORT.odt)

For my part I choose **OSCP-exam-report-template_whoisflynn_v3.2.md**, so any training will be done with this one.

## Scripts for report generation

#### Generate report script

This script is for the report generation in PDF from markdown.

```bash
# generate_report.sh

#!/bin/bash

if [ "$#" -ne 2 ]; then
    echo "usage: $0 <input.md> <output.pdf>"
    exit
fi

# if this machine does not have the template in place, put it there!
if [ ! -e /usr/share/pandoc/data/templates/eisvogel.latex ]
then
    sudo cp eisvogel.latex /usr/share/pandoc/data/templates/
fi

pandoc $1 -o $2 \
--from markdown+yaml_metadata_block+raw_html \
--template eisvogel \
--table-of-contents \
--toc-depth 6 \
--number-sections \
--top-level-division=chapter \
--highlight-style tango

if [ $? -eq 0 ]
then
    evince $2
fi
```

#### Submission script

This script is to generate the password protected **.7z**, once your report is finish. I commented the LAB_REPORT part of the script because I did not do it.

```bash
# make_submission.sh

#!/bin/bash

OSID="XXXXX"
EXAM_REPORT="OSCP-OS-$OSID-Exam-Report.pdf"
# LAB_REPORT="OSCP-OS-$OSID-Lab-Report.pdf"
ZIP_PACKAGE="OSCP-OS-$OSID-Exam-Report.7z"

echo "Generating exam report..."
./generate_report.sh ../exam/OSCP_exam_report.md $EXAM_REPORT

# echo "Generating lab report..."
# ./generate_report.sh lab_report.md $LAB_REPORT

echo "Creating 7z package..."
# 7z a $ZIP_PACKAGE -pOS-$OSID $EXAM_REPORT $LAB_REPORT
7z a $ZIP_PACKAGE -pOS-$OSID $EXAM_REPORT
```

#### Make scripts executable

```bash
chmod +x generate_report.sh make_submission.sh
```

## Report generation



## Report training 





## Tips on report generation



## Tips before the exam

### Proctoring requirements

Follow this tutorial before your exam to install all requirements concerning the proctoring :

- [https://help.offensive-security.com/hc/en-us/articles/360050299352-Proctoring-Tool-Student-Manual](https://help.offensive-security.com/hc/en-us/articles/360050299352-Proctoring-Tool-Student-Manual)

### OSCP Exam Guide

Read the OSCP Exam Guide :

- [https://help.offensive-security.com/hc/en-us/articles/360040165632](https://help.offensive-security.com/hc/en-us/articles/360040165632)

### OSCP FAQ

Have some questions ? Read the OSCP FAQ :

- [https://help.offensive-security.com/hc/en-us/articles/360050164111-OSCP-Certification-Exam-FAQ](https://help.offensive-security.com/hc/en-us/articles/360050164111-OSCP-Certification-Exam-FAQ)
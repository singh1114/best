---
author: ranvirsingh1114
comments: true
date: 2017-06-28 21:15:53+00:00
layout: post
link: https://ranvirsinghprojects.wordpress.com/2017/06/29/updating-the-models/
slug: updating-the-models
title: Updating the models
wordpress_id: 807
categories:
- GSoC-2017
---

Today I was working on another branch to write the code that can fill the database. I scanned some code and saved copied the results to open them in clean JSON format because I wanted to iterate over the results. I used the online the following JSON parser.

[http://json.parser.online.fr/](http://json.parser.online.fr/)

It is a website that shows clean results and you can correctly see what's going on. After checking out the results I found that there was some discrepancy with the database. So I left the work of filling database and started the work on updating the database.


<blockquote>`{"files": [{"licenses": [{"category": "Permissive", "start_line": 2358, "short_name": "MIT License", "spdx_url": "https://spdx.org/licenses/MIT", "text_url": "http://opensource.org/licenses/mit-license.php", "spdx_license_key": "MIT", "homepage_url": "http://opensource.org/licenses/mit-license.php", "score": 10.0, "end_line": 2358, "key": "mit", "owner": "MIT", "dejacode_url": "https://enterprise.dejacode.com/urn/urn:dje:license:mit", "matched_rule": {"licenses": ["mit"], "license_choice": false, "identifier": "mit_14.RULE"}}, {"category": "Permissive", "start_line": 2532, "short_name": "MIT License", "spdx_url": "https://spdx.org/licenses/MIT", "text_url": "http://opensource.org/licenses/mit-license.php", "spdx_license_key": "MIT", "homepage_url": "http://opensource.org/licenses/mit-license.php", "score": 97.6, "end_line": 2547, "key": "mit", "owner": "MIT", "dejacode_url": "https://enterprise.dejacode.com/urn/urn:dje:license:mit", "matched_rule": {"licenses": ["mit"], "license_choice": false, "identifier": "mit.LICENSE"}}], "path": "URL/5", "packages": [], "scan_errors": [], "copyrights": [{"end_line": 2542, "holders": ["GitHub Inc."], "start_line": 2530, "statements": ["Copyright (c) 2011-2017 GitHub Inc."], "authors": []}, {"end_line": 2588, "holders": [], "start_line": 2582, "statements": ["(c) 2017 span title"], "authors": []}]}], "scancode_notice": "Generated with ScanCode and provided on an \"AS IS\" BASIS, WITHOUT WARRANTIES\nOR CONDITIONS OF ANY KIND, either express or implied. No content created from\nScanCode should be considered or used as legal advice. Consult an Attorney\nfor any legal advice.\nScanCode is a free software code scanning tool from nexB Inc. and others.\nVisit https://github.com/nexB/scancode-toolkit/ for support and download.", "scancode_version": "2.0.0rc3", "files_count": 1, "scancode_options": {"--format": "json", "--ignore": [], "--license": true, "--package": true, "--license-score": 0, "--copyright": true}}`</blockquote>


This is the JSON result that helped me to create the changes in the database.

Following is the commit related to the change in the database.

[https://github.com/singh1114/scancode-server/commit/de5a93a08741f1150ab3fbaa7b57b82f2bc5054a](https://github.com/singh1114/scancode-server/commit/de5a93a08741f1150ab3fbaa7b57b82f2bc5054a)

After this, I went back to work on filling the database. I will be able to push something tomorrow. It is a tough task to keep everything. If I wrote some bad code then it is going to be very hard to debug.

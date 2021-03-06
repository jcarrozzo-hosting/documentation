---
title: AWS CMK Deleted or Scheduled for Deletion
kind: documentation
type: security_rules
disable_edit: true
src_link: https://docs.datadoghq.com/integrations/amazon_cloudtrail/
src_img: /images/integrations_logos/amazon_cloudtrail.png
security: compliance
framework: cis
control: cis-3.7
source: cloudtrail
scope: kms

aliases:
- 432-8db-b8b
---

## Overview

### Goal
Detect when a CMK is deleted or scheduled for deletion.

### Strategy
This rule lets you monitor these CloudTrail API calls to detect if an attacker is deleting CMKs:
* [DisableKey][1]
* [ScheduleKeyDeletion][2]

### Triage & Response
1. Determine which user in your organization owns the API key that made this API call.
2. Contact the user to see if they intended to make this API call.
3. If the user did not make the API call:
 * Rotate the credentials.
 * Investigate if the same credentials made other unauthorized API calls.

[1]: https://docs.aws.amazon.com/kms/latest/APIReference/API_DisableKey.html
[2]: https://docs.aws.amazon.com/kms/latest/APIReference/API_ScheduleKeyDeletion.html

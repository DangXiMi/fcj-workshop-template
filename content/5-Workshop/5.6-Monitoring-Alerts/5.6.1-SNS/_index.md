---
title: "SNS Email Alerts"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.6.1. </b> "
---

1. **SNS → Topics → Create topic** (Standard).
2. **Create subscription** → Protocol **Email** → enter your address.
3. Confirm the subscription from the email inbox (status must be **Confirmed**).

{{% notice info %}}
A "publish succeeded" log does not guarantee delivery. SNS only emails **confirmed** subscriptions. If no email arrives, check that the subscription status is Confirmed, not PendingConfirmation.
{{% /notice %}}

Test with **Publish message**, then test end-to-end by uploading a batch that contains high-risk students and confirming the summary email arrives.

![SNS alert email]( /fcj-workshop-template/images/5-Workshop/5.6-Monitoring/sns-email.png)
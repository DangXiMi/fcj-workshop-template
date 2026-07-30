---
title: "Automated Email Alerts with AWS SNS"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---


## Introduction

An important requirement of the project was to send immediate alerts to lecturers when students are predicted as "High Risk". Instead of manually checking the database, I used AWS SNS to send real-time email alerts. In the batch prediction system, SNS is used to send summary emails after the entire CSV file is processed.

## What is Amazon SNS?

SNS is AWS's pub/sub messaging service. It allows you to send notifications to multiple subscribers (email, SMS, HTTP endpoints, or other AWS services) instantly. I used SNS with the Email protocol to send alerts to lecturers.

## Why I Chose It?

I needed a simple and reliable way to send emails without having to build a custom email sending system. SNS provides this feature out-of-the-box, integrates easily with Lambda, and has a free tier of 1,000 emails per month.

## Issue Encountered

I created the topic and subscription successfully, but I didn't receive any emails. Checking the console showed the status "Pending confirmation".

## How I Fixed It

SNS requires email confirmation before sending notifications. I forgot to click the confirmation link in my inbox. After confirming, everything worked perfectly.

## How I Implemented It

### 1.Create Notification Channel with SNS

I created an SNS Topic to act as the intermediary receiving notifications from the system. This topic is responsible for distributing alerts to registered subscribers.

### 2.Connect Notification Recipients

I configured an email subscription for the lecturer. After subscribing, the email needs to be confirmed before SNS can send notifications.

### 3.Grant Lambda Permission to Send Notifications

I configured IAM permissions so Lambda can publish messages to the SNS Topic after completing the prediction process.

### 4.Integrate SNS into the Workflow

After Lambda finishes processing the data and identifies the list of high-risk students, the system creates a summary notification and sends it via SNS.

### 5.Send Automatic Alerts

SNS receives the message from Lambda and automatically sends the email to the lecturer, making student risk monitoring completely hands-off.
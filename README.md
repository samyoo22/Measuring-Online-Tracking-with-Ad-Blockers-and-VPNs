# Measuring Online Tracking with Ad Blockers and VPNs

This repository contains the code and experimental artifacts for a web privacy measurement study titled **"Measuring Online Tracking with Ad Blockers and VPNs."** The project empirically evaluates how different privacy tools and configurations affect online tracking behavior in the Chrome browser.

## 📌 Project Overview

Modern websites rely heavily on third-party trackers that collect user data via cookies, JavaScript APIs, fingerprinting, and cookie syncing. In response, users often deploy Virtual Private Networks (VPNs) and ad blockers to enhance their privacy — but the actual effectiveness of these tools in real-world browsing is not always clear.

This project measures and compares online tracking across four browsing modes:

- **Vanilla** – no VPN, no ad blocker  
- **VPN only** – VPN enabled, no ad blocker  
- **Ad blocker only** – ad blocker enabled, no VPN  
- **VPN + ad blocker** – both protections enabled

We focus on how these configurations change the volume and nature of tracking-related activity in practice.

## 🔬 Experimental Setup

- **Browser:** Google Chrome (latest stable version during experiments)  
- **Websites:** 540 domains sampled from the Tranco top sites list  
- **Tracking data collection:** DuckDuckGo Tracker Radar Collector  
- **Privacy tools:**
  - **VPNs**
    - NordVPN (GUI-based client)
    - ProtonVPN (CLI-based client)
  - **Ad blocker**
    - uBlock Origin (default settings)

For each browsing mode and VPN setup, we automate visits to the selected websites and record:

- Third-party HTTP(S) requests  
- Cookie setting and access events  
- JavaScript API calls related to tracking and fingerprinting  
- Fingerprinting attempts  
- Cookie syncing pairs across third-party domains  

The experimental environment is carefully controlled: each run uses a fresh browser instance with caches, cookies, and history cleared between conditions to avoid cross-contamination.

## 📊 Key Findings

- **VPNs and ad blockers provide complementary protection.**  
  VPNs primarily reduce network-level tracking (e.g., third-party requests and some cookie exchanges), while ad blockers excel at blocking ad and tracker domains at the browser level.

- **Ad blockers alone significantly reduce cookies and script-based tracking.**  
  uBlock Origin, even with default settings, substantially lowers the number of cookies and JavaScript API calls associated with tracking.

- **VPNs alone can meaningfully reduce tracking but are not sufficient.**  
  Both NordVPN (GUI) and ProtonVPN (CLI) reduce third-party requests and cookie syncing, but do not fully prevent browser-level techniques such as fingerprinting.

- **The combination of VPN + ad blocker achieves the strongest overall protection.**  
  Using both layers together yields the lowest levels of third-party requests, cookies, JavaScript API calls, and cookie syncing, demonstrating the value of multi-layered defenses.

- **VPN implementation details matter.**  
  We observe notable differences between GUI-based and CLI-based VPN deployments, suggesting that routing behavior, background services, and client design can influence privacy outcomes.

## 🧰 Tools & Technologies

- Chrome web browser  
- DuckDuckGo Tracker Radar Collector  
- uBlock Origin (browser-based ad and tracker blocker)  
- NordVPN (GUI client)  
- ProtonVPN (CLI client)  
- Supporting scripts for automation, crawling, and data analysis

## 🧾 Paper

The full write-up is provided in:

- **`Measuring Online Tracking with Ad Blockers and VPNs.pdf`**

Please see the paper for detailed methodology, statistical analysis, and additional plots (e.g., distributions of third-party requests, cookie counts, JavaScript API calls, fingerprinting ratios, and cookie syncing pairs) across all experimental conditions.

## ⚠️ Ethical & Practical Notes

This research is a **measurement study**, not a product or commercial VPN review.  
All crawling targeted publicly accessible websites, followed ethical web measurement practices, and did not collect any sensitive personal user data. The results highlight that:

> There is no single “magic” privacy tool — robust privacy requires **multiple defensive layers**, combining VPNs with high-quality browser-based protections such as ad and tracker blockers.

---
layout: default
---

**AVEDroid** is a repo to share our artifacts of out studies on Android vulnerability evolution.

## Abstract

The Android ecosystem today is a growing universe of a few billions devices, hundreds of millions of users and millions of applications targeting a wide range of activities where sensitive information is collected and processed. Security of communication and privacy of data are thus of utmost importance in application development. Yet, regularly, there are reports of successful attacks targeting Android users. While some of those attacks exploit vulnerabilities in the Android OS, others directly concern application-level code written by a large pool of developers with varying experience. Recently, a number of studies have investigated this phenomenon, focusing however only on a specific vulnerability type appearing in apps, and based on only a snapshot of the situation at a given time. Thus, the community is still lacking comprehensive studies exploring how vulnerabilities have evolved over time, and how they evolve in a single app across developer updates. Our work fills this gap by leveraging a data stream of 5 million app packages to re-construct versioned lineages of Android apps on which we apply state-of-the-art vulnerability finding tools, to study which types of vulnerabilities are present, how they are introduced in app code, where they are located, and whether they foreshadow malware. Our findings and study artifacts constitute a tangible knowledge to the community. It could be leveraged by developers to focus verification tasks, and by researchers to drive vulnerability discovery and repair research efforts. 

## Android App Lineage

As we defined, an app **lineage** is a **consecutive** series of version of apks of an Android application.

### Construction of Lineages

* _Base Dataset_: [Androzoo](https://androzoo.uni.lu/) which is a growing collection of Android applications.

* _App ID_: App name from the Manifest file of apks. APKs with same ID will be the candidate versions of a lineage.

* _App Certificate_: Certificate is used to distinguish apks from same developer.

* _App Market_: Based on Androzoo metadata, lineages will only consider apks from
the same market.

* _App Version_: APKs of different versions of a lineage will be ordered by their **version code** in the Manifest.

* _Limitation_: Only lineages contain no less than 10 versions were considered to avoid toy apps.

### Statistics and Example

* Number of lineages: 28,564
* Number of APKs: 465,037
* Median of lineage size: 13
* Maximum of lineage size: 172

Example of lineage:

    com.lskjg.shgu.shiwang.kongj
      27294E32E7D3458EDEBED41F31FD982102E2554E872CF63892E70485B8A16678 6 anzhi 10112101 2013-11-27 17:10:16
      19C56A664623494EA7E15446CDB43AB8078F7620684D9A1D871EA3FD72AFA3EB 0 anzhi 10112102 2013-12-04 12:09:10
      C94E5529FE63325E4DFB5048C673D0624A8173D6C6781CC7C3C8C07789C8DA24 7 anzhi 10112104 2013-12-17 11:27:34
      5165A5F9EEEDDB6899AEE4AE1244412B29A1CB6B463916BAAF78CADCDE666D86 6 anzhi 10112106 2013-12-27 13:34:34
      80E1D507B2EB1BD840B02EA3E6A107126B76107C8CBC353F516F0B9B1071F661 9 anzhi 10112107 2013-12-31 14:11:10
      6C15B45ABFC4C7B34E7E8313CA39AA14DA6DC7D1949F1AF7A3E67C4634FDF232 15 anzhi 10112108 2014-01-03 09:39:28
      11CAA201134FB9BDF2FDEE15C9CF1FCF85A18227F456028198B7A5F87ABB9247 15 anzhi 10112109 2014-01-07 12:00:26
      8660B0794C481AFED3DC8C906E6D2EAD894913C3691643BCA81465B28F8C79BA 16 anzhi 10112110 2014-01-10 12:21:34
      0C9E11EDEC186780BD2277D652A06BF1D6003BF4759AD34B533E03A158F7AF74 10 anzhi 10112111 2014-01-17 15:07:18
      DC4C315C062779C8465AEF371C7A7946AAA89964935720A214A81F522C8D65EA 10 anzhi 10112112 2014-01-23 14:02:28
      3D785866639F234CCF4ECB7A0AE90DE3A4D1D7636C394604095BA9D461C64304 0 anzhi 10112113 2014-02-18 14:10:42
      8137EECFA59FB3C34B256B8E29D117264AD5ECF0A1C07E3B2100C0D97138280A 10 anzhi 10112129 2014-07-16 11:55:22

First line is the App ID (App name) and followings are the sorted versions of this lineage. For each version line, it shows hash, AV positive from [VirusTotal](https://www.virustotal.com/), market, version code and dex date.

### Resource Sharing

The lineage list will be shared after the decision of relevant paper has been made.

## Scanning and Raw Result

For our research, we stand on three state-of-the-art scanners which are:

* **FlowDroid**: a highly reputable framework for static taint analysis.
* **AndroBugs**: first presented at the BlackHat security conference and is notably credited in the security hall of fame of companies such as FaceBook, eBay, Twitter, etc.
* **IC3**: a state-of-the-art static analyzer focused on resolving the target values in intent message objects used for inter-component communication.

### Limitations and Statistics

Because FlowDroid and IC3 are heavy in terms of resource consumption. Also, some of the apks cannot be successfully analyzed by some of the scanner. For each scanner, the quantity of collected result are different and some of the lineages are missing results for some versions.

* FlowDroid
  * Scanned # of completed lineages: 37,736 apks of 3357 lineages
  * Scanned total # of APKs: 223,474

* IC3
  * Scanned # of completed lineages: 30,042 apks of 2048 lineages
  * Scanned total # of APKs: 72,983

* AndroBugs
  * Scanned # of completed lineages: 454,799 apks of 27,974 lineages
  * Scanned total # of APKs: 458,814

### Raw Scanning Result
The scanning result will be shared after the decision of relevant paper has been made.

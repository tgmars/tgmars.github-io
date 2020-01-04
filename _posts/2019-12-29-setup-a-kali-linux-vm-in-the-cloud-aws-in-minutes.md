---
title: (Draft) Setup a Kali Linux VM in the cloud (AWS) in minutes!
categories:
  - Blog
tags:
  - Cloud
  - AWS
  - Penetration testing
  - Kali
---

Doing a CTF and in need of some extra power? Only got access to limited processing and can't afford the resources to spin up another VM? Have a look at using some cloud compute to supplement your efforts. 

This guide is designed for a total newcomer to AWS. If you already have a VPC and keypair, go [here](https://aws.amazon.com/marketplace/pp/B01M26MMTT) and get cracking!
If you don't, follow along below.

### Setup
- Create an AWS account and verify payment details.
- Go to the [Kali Linux AMI subscription page](https://aws.amazon.com/marketplace/pp/B01M26MMTT)
- Subscribe, then continue to configuration
- Keep the default configuration values, at the time of writing this, they were the only options available. Proceed to 'launch'.
- Select the appropriate dropdowns, shown in the screenshots below: 
  - Action
  - Instance Size (Offensive Security recommend a t2.medium instance with 4GB RAM and 2 virtual cores, but increase it as required) 
  - VPC, create one if required
  - Subnet, create one if required
  - Security group. Create this based on Offensive Security's recommendations. SSH access is the only connection method, you need to modify this for more access than terminal only.
  - Keypair
![Launch page config](https://github.com/tgmars/tgmars.github.io/blob/master/assets/images/launch-shot-part-one.png?raw=true)
![Launch page config](https://github.com/tgmars/tgmars.github.io/blob/master/assets/images/launch-shot-part-two.png?raw=true)

### Connecting
Next, connect to your instance. Amazon provide instructions for whichever method you desire. 
Go to your: **EC2 dashboard > instances > (your kail EC2 instance) > right click > Instance State > Start**

Login with whichever account is specified in the AMI usage instructions, at the time of publish this was **'ec2-user'**

Kick off a ``` sudo apt update && apt dist-upgrade ```

### Strengths & Weaknesses

| Strengths        | Weaknesses           |
| ------------- |-------------|
| Quick to establish      | IO bottleneck | 
| Cheaper than a new box      | Reliance on internet access      | 
| Use only what's required | Extra config required for GUI access (Burp)      |  
| Scalable |  |

### Further additions 

From here, you can install xrdp on Kali and open up 3389 in your security settings for remote desktop access to the EC2 instance. 

Enjoy!

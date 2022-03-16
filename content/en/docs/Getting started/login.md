---
categories: ["Document"]
tags: ["Bayes", "tutorial", "docs"] 
title: "Access to the Cluster"
linkTitle: "Access to the Cluster"
weight: 3
---

## For Linux and macOS User

The user who are using this two operating system, we recommand you to access the cluster via **Terminal**:
* For Linux user: press `CTRL + ALT + T` or click `Terminal`
* FOr macOS user: go to *LaunchPad* and then type `Terminal`

Continue with the assumption in [Quick Start #Access to the System]({{< ref "quick_start.md#access-to-the-system" >}})

```bash
ssh user_name@hpc.uicstat.com
```

If you can see the output below, it means that you have successfully access the cluster's control node.

```bash
Welcome to UIC-STAT Bayes Cluster (USBC)
#     ___          ___          ___          ___#
#    /  /\        /  /\        /  /\        /  /\#
#   /  /:/       /  /::\      /  /::\      /  /::\#
#  /  /:/       /__/:/\:\    /  /:/\:\    /  /:/\:\#
# /  /:/       _\_ \:\ \:\  /  /::\ \:\  /  /:/  \:\#
#/__/:/     /\/__/\ \:\ \:\/__/:/\:\_\:|/__/:/ \  \:\#
#\  \:\    /:/\  \:\ \:\_\/\  \:\ \:\/:/\  \:\  \__\/#
# \  \:\  /:/  \  \:\_\:\   \  \:\_\::/  \  \:\#
#  \  \:\/:/    \  \:\/:/    \  \:\/:/    \  \:\#
#   \  \::/      \  \::/      \__\::/      \  \:\#
#    \__\/        \__\/           ~~        \__\/#

 * Documentation:       https://uicstat.com/wiki/
 * Web UI:       	https://hpc.uicstat.com:8443/
 * Support Maintenance: bayes@uicstat.com

Date and time             = Sun Mar 13 23:38:36 CST 2022
Release                   = Ubuntu 20.04.4 LTS
Kernel                    = 5.4.0-92-generic GNU/Linux

Last login: Sat Mar 12 22:40:25 2022 from 172.16.231.10
```

After successfully logging in, the path is your personal Home folder, and the absolute path is `/Storage2030005000/home/user_name`. You can access and modify all the contents of the personal folder.

* When you want to log out of the workstation, execute the following command `exit` or just press `CTRL+D`.
* If you log in for the first time, the system will force you to change the password. Be sure to set a more complicated password, and then log in again after the modification.
* If you want to change the password again, use the following command passwd. Similarly, no characters are displayed in the terminal input area when you are changing your password.

## For Windows User

Since the operations on the cluster are mostly based on Linux, if the same or similar operations can be used under Windows, it will bring great convenience to users. We provide several ways for you to use the cluster under Windows as follows: 

* <u>For Windows 10 and above</u>, you can use CMD/Powershell with SSH 
* <u>FOr Windows 8 and below</u> you can choose one of these recommanded tools:
  * [puTTY](https://documentation.help/PuTTY/)
  * [MobaXterm](https://mobaxterm.mobatek.net/documentation.html)

## Set Two-Factor Authentication (2FA)

Simply using a password to verify the security factor is not enough, because anyone who knows your password can use it to log in to your account. The role of 2FA is to allow the user to authorize access to his account if he needs to complete two verification methods at the same time. Similar is MFA (multi-step verification. Although more authentication methods will increase security, it will also bring tedious login process, which will affect the user experience.

The server has enabled the 2FA, login using account password + one-time verification code. The following is the configuration method.

1. Download an App: the UIC VPN is also need a token to login, you can use the app (ndkey 宁顿令牌) to be your 2FA client validator.
2. Server Account Configuration: the server uses the google-authenticator module to implement 2FA for SSH. Configure server 2FA to use commands:
    ```bash
    google-authenticator
    ```
    This command will generate a secret key under the server account. During the generation process, you will be asked a series of questions. It is recommended to read it carefully. Personally, I recommend all of them you can just input y. After the first question, a command line window displays a QR code. At this point, take out your phone to open ndkey, select “Add Account” or just press “+” and scan the code. After successfully scanning the code, you can see that ndkey will continue to generate six-digit verification codes, and each verification code will expire after 30s.

3. Test: after the configration, you can just open a new windows for a test:
    ```bash
    $ ssh user_name@hpc.uicstat.com
    $ Password:                   # << input your original password
    $ Verification code:          # << input your validation code on your phone
    ```

{{% alert title="" color="warning" %}}
1. After the server account is generated and configured, the secret key will be stored in the .google_authenticator file under HOME. If you want to close 2FA, delete this file. You can also back up this file to your local.
2. No internet connection is required to use 2FA. The 2FA code is generated based on the time, as long as the server time and the phone time are consistent.
3. If you access to the cluster via SSH key for authentication instead of password authentication, 2FA is not required (regardless of whether the server is configured). This setting is based on the assumption that the local private key is trusted.
4. If you lose your 2FA key, please contact the administrator to unbind your 2FA token.
{{% /alert %}}
---
title: How I set up new machines | For development
date: '2019-12-13 20:58:00 +0000'
published: true
image: 'https://i.imgur.com/ZYkt1Yf.jpg'
tags:
  - discuss
  - programming
  - webdev
  - career
categories:
  - discuss
  - programming
  - webdev
  - career
---
Losing access to your ssh key is one of the most dreadful situations for a developer. You will spend your full day creating the new ssh key getting the access to all machines back after you create this new ssh key.

![How I set up new machines](https://i.imgur.com/ZYkt1Yf.jpg "How I set up new machines")

## Creating a config for handling access to all the boxes

Working from my current company, I have access to a lot of boxes(EC2s). I have created a sample config file so that I keep which key is being used to access that particular box.

You can add something like this to your `~/.ssh/config` file.

```bash
Host stage
    User ubuntu
    HostName 10.X.X.X
Host stage-job-box
    User ubuntu
    HostName 172.X.X.X
    IdentityFile ~/new.pem
Host my-project
    User ubuntu
    HostName 13.X.X.X
Host my-project-jobs
    User ubuntu
    HostName 3.X.X.X
```

By default, it uses `id_rsa.pem` file to connect to the boxes unless you specify other `IdentityFile` with the path of the `private` key file.

Finally, you can ssh into the boxes using the command,

`ssh stage`

## Prologue (I have been using the same ssh key since this long)

I have been using the same ssh key for a while now. In between this time, I have faced a few challenges of changing jobs, SSD crashing a few times and many more.

Even after all those situations, the ssh key that I have used has never changed.

## How I have been using the same ssh key?

So, I have an old laptop that I keep at my place which contains the ssh key which I use for almost all the purposes.

**Note**: I do have one more layer of security which involves VPN being connected to connect everything related to my current organization.

Whenever I get a new machine, I get back to the same machine and `ssh` into this old machine and get all of the required data from that machine using a combination of `ssh` and `scp`(Secure Copy).

## Allowing ssh into Ubuntu Device

For `ssh`ing into any machine, you need to open the port 22 of that machine. As that machine is a ubuntu machine,

The simplest way is to install OpenSSH onto the Ubuntu machine. Use the following command in Ubuntu.

`sudo apt install openssh-server -y`

While in the ubuntu machine try to run `ifconfig` to find out the `IP` of the machine on which you are on. Make sure that both of the machines are on the same wifi.

Once you are get the `IP` of the machine that you are looking for, find the `scp` command that suites you. One of my friend has written a [good post for SCP commands](https://sharmapacific.in/securely-transfer-files-from-slash-to-a-remote-server-using-scp/). We will use one of those commands to get the file from that machine to my machine.

`scp prashant@192.168.0.114:~/Desktop/ranvir.png ~/Desktop/.`

![SCP files using another device](https://i.imgur.com/w9AkV79.jpg "SCP files using another device")

This will get the file from the given machine and dump the file in the `Desktop` directory.

## Allowing ssh into MAC machine

Something similar is applied to MAC devices as well. For allowing ssh into MAC devices you have to allow `remote login` on the device which you want to access. You can find the setting in `preferences -> sharing`.

![Allowing remote login in MAC](https://i.imgur.com/banssOS.jpg "Allowing remote login in MAC")

After this, you can `ssh` into the machine and `scp` into the new device to get the required files.

Hope you liked this post. Please subscribe to the weekly newsletter by sharing your email.

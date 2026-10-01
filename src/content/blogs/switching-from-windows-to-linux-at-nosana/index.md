---
category: "blog"
title: "Your GPU Is Ready to Earn. Here's How to Switch from Windows to Linux and Host on Nosana"
description: "Nosana GPU hosting runs on Linux. Learn why we moved away from Windows, what your RTX 4090 or RTX 5090 can earn, and how to dual-boot Ubuntu without giving up Windows."
thumbnail: "./assets/thumbnail.jpeg"
createdAt: "2026-10-01"
tags:
  - "news"
---

Developers on Nosana need more RTX 4090 and RTX 5090 GPUs than the network currently has. Many of those GPUs are already out there, sitting in gaming PCs and workstations around the world. For a lot of their owners, the only thing standing between that hardware and real earnings is the operating system: Nosana hosting runs on Linux, and their PC runs Windows.

This post explains why Nosana is Linux only, what your GPU can earn, and how to switch without giving up Windows. If you hosted with us on Windows before, this post is for you too.

## Why Nosana Hosting Runs on Linux

Nosana used to support Windows hosts. To make that work, the Nosana node ran inside <a href="https://learn.microsoft.com/en-us/windows/wsl/about" target="_blank" rel="noopener noreferrer">WSL2 (Windows Subsystem for Linux)</a>, which is a Linux environment running on top of Windows.

In practice, that extra layer caused problems. GPU access through WSL was harder to set up and less reliable. Bugs showed up that only happened on Windows, and every Windows update could break something new. Keeping Windows hosts working took a large share of our engineering time, and hosts still ran into issues.

Native Linux was simply better. The node talks to the GPU directly, workloads run faster, and hosts stay online more reliably. So we made the decision to sunset Windows support and focus on Linux.

That decision matters for hosts. On Nosana, **uptime is what earns you money**. A host that stays online gets more jobs, qualifies for incentives, and has a better chance of being promoted to Premium markets. Linux gives you the most stable foundation for that.

In this article we will go through the necessary steps to dual-boot Windows and Linux, so you can earn with your GPU on the Nosana network. So first let's figure out how much you can earn with your GPU and afterward go through the Linux Ubuntu install guide.

## What Your GPU Can Earn

Your earnings depend on your GPU, how many hours it is online and how many customer jobs it receives. Here are the current rates in the Premium markets for RTX 4090 and RTX 5090 GPUs:

|                                        | RTX 4090       | RTX 5090       |
| -------------------------------------- | -------------- | -------------- |
| Market rate                            | $0.36 per hour | $0.45 per hour |
| Earnings at full utilization (30 days) | ~$262          | ~$327          |
| Campaign incentive per qualifying day  | ~$1.75         | ~$2.18         |
| Campaign incentive (30 days)           | ~$52           | ~$65           |

_Rates as of October 1, 2026. Market rates can change. Earnings are paid in NOS._

<!-- TODO: confirm the campaign incentive is calculated at the GPU's market rate -->

<a href="https://nosana.com/gpu-providers/" target="_blank" rel="noopener noreferrer">Estimate your earnings with the calculator</a>

### The RTX 4090 and RTX 5090 Campaign

Until **November 17**, eligible RTX 4090 and RTX 5090 hosts receive an extra incentive equal to **20% daily utilization**. That is the same as being paid for 4.8 hours of work every day, **on top of** what you earn from real customer jobs.

To qualify, your host must:

- Use an NVIDIA RTX 4090 or RTX 5090
- Be registered and verified on the Nosana network
- Stay online for **at least 85% of each day**

If your uptime falls below 85% on a given day, you don't receive the incentive for that day. The campaign is open to both new and existing hosts, but spaces are limited.

Every day your GPU isn't connected is a day of incentives you won't get back. The sooner you switch, the more of the campaign you can use.

<a href="https://nosana.com/blog/rtx-4090-5090-gpu-provider-campaign/" target="_blank" rel="noopener noreferrer">Read the full campaign details</a>

## You Don't Have to Give up Windows

Switching to Linux doesn't mean wiping your PC. With a **dual-boot** setup, Windows and Ubuntu live side by side on the same machine. When you turn on your PC, you choose which one to start.

For hosting, we recommend this setup:

- **Ubuntu is the default.** Your PC starts in Ubuntu and the Nosana node runs automatically.
- **Windows is there when you need it.** Want to play a game or use a Windows-only app? Restart and pick Windows from the menu.
- **Back to hosting when you're done.** Restart again and you're back in Ubuntu.

There is one trade-off to keep in mind. While your PC is in Windows, your host is offline. To meet the campaign's 85% uptime requirement, your PC can be in Windows or switched off for at most about **3.5 hours a day**. If you game for an evening, that's fine. If you game all day, you'll miss the incentive for that day.

If you have a spare PC or want the most uptime, you can also run Ubuntu on its own. Dual-boot is the easiest way to start if your GPU lives in your main PC.

## What the Switch Looks Like

You don't need to be a Linux expert. Most of the setup happens through graphical installers, and the terminal steps are copy and paste. Plan for about one to two hours.

1. **Prepare Windows.** Back up your files, save your <a href="https://support.microsoft.com/en-us/windows/find-your-bitlocker-recovery-key-6b71ad27-0b89-ea08-f143-056f5ab347d6" target="_blank" rel="noopener noreferrer">BitLocker recovery key</a> if you use it, and turn off Fast Startup.
2. **Make space for Ubuntu.** Add a second SSD (the simplest option) or free up at least 256GB on your current drive. Check that your PC meets the <a href="https://learn.nosana.com/hosts/grid.html#hardware-requirements" target="_blank" rel="noopener noreferrer">hardware requirements</a>.
3. **Create a bootable USB.** <a href="https://ubuntu.com/download/desktop" target="_blank" rel="noopener noreferrer">Download Ubuntu 26.04 LTS</a> and write it to a USB stick with <a href="https://rufus.ie/en/" target="_blank" rel="noopener noreferrer">Rufus</a> or <a href="https://etcher.balena.io/" target="_blank" rel="noopener noreferrer">balenaEtcher</a>.
4. **Install Ubuntu alongside Windows.** Boot from the USB and choose to install Ubuntu next to Windows. Ubuntu's <a href="https://ubuntu.com/tutorials/install-ubuntu-desktop" target="_blank" rel="noopener noreferrer">installation tutorial</a> walks through each installer screen.
5. **Install your NVIDIA drivers.** Ubuntu can <a href="https://ubuntu.com/server/docs/how-to/graphics/install-nvidia-drivers/" target="_blank" rel="noopener noreferrer">install the recommended driver</a> for your GPU with a single command.
6. **Install Docker and the NVIDIA Container Toolkit.** <a href="https://docs.docker.com/engine/install/ubuntu/" target="_blank" rel="noopener noreferrer">Docker</a> and the <a href="https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html" target="_blank" rel="noopener noreferrer">NVIDIA Container Toolkit</a> let Nosana run AI workloads on your GPU.
7. **Start the Nosana node.** <a href="https://learn.nosana.com/hosts/grid-run.html#join-the-grid" target="_blank" rel="noopener noreferrer">Run one command</a> to register your host and connect to the network.

Our step-by-step guide covers each of these steps in detail, including commands and fixes for common problems.

## Switching from Windows: Dual-Boot Ubuntu for Nosana Hosting

Nosana GPU hosting runs on native Linux only. Windows and WSL2 are no longer supported. If your GPU is in a Windows PC, this guide walks you through installing **Ubuntu 26.04 LTS** alongside Windows, so you keep Windows for gaming and everyday use and boot into Ubuntu to host on Nosana.

By the end of this guide you will have:

- Ubuntu 26.04 LTS installed next to Windows, set as the default boot option
- NVIDIA drivers, Docker, and the NVIDIA Container Toolkit installed
- The Nosana node running and registered on the Grid

## What You Need

- A PC with a <a href="https://learn.nosana.com/hosts/grid.html#hardware-requirements" target="_blank" rel="noopener noreferrer">supported NVIDIA GPU</a> that meets the hardware requirements (12GB+ RAM, 256GB+ NVMe SSD for Ubuntu, 100 Mb/s down / 50 Mb/s up)
- A USB stick of **8GB or more** (it will be erased)
- **256GB or more of free disk space.** A second SSD just for Ubuntu is the safest and simplest option. Shrinking your Windows drive also works.
- About 1–2 hours

## Step 1: Prepare Windows

### Already Hosted on Windows with WSL?

Welcome back. You can move your existing host and wallet to your new Ubuntu install, but **we recommend starting with a new wallet**. A fresh key on a fresh, native Linux setup is the cleanest start.

Before you remove WSL, make sure you have a backup of your old node key (`nosana_key.json`). You'll need it to access any funds in that wallet. [The setup guide](https://learn.nosana.com/hosts/grid-run.html#running-the-host-1) explains where to find it and how to move it if you decide to keep your existing wallet.

### Back up Your Data

Partitioning is safe when done carefully, but mistakes can erase data. Back up anything important to an external drive or cloud storage before continuing.

### Save Your BitLocker Recovery Key

If your Windows drive is encrypted with BitLocker (common on Windows 11), changing boot settings can trigger a recovery-key prompt. Find and save your key first:

- Go to <a href="https://account.microsoft.com/devices/recoverykey" target="_blank" rel="noopener noreferrer">account.microsoft.com/devices/recoverykey</a>, or
- Open **Command Prompt (Admin)** and run:

```powershell
manage-bde -protectors -get C:
```

Write the 48-digit recovery password down somewhere **off this PC**.

### Turn off Fast Startup

Fast Startup leaves the Windows drive in a half-hibernated state, which can cause problems for dual-boot.

1. Open **Control Panel → Power Options → Choose what the power buttons do**
2. Click **Change settings that are currently unavailable**
3. Uncheck **Turn on fast startup** and save

### Check That Windows Uses UEFI

Press `Win + R`, run `msinfo32`, and check that **BIOS Mode** says **UEFI**. Almost all modern PCs do. If it says _Legacy_, ask for help in <a href="https://nosana.com/discord" target="_blank" rel="noopener noreferrer">Discord</a> before continuing.

## Step 2: Make Space for Ubuntu

Choose **one** of the options below.

### Option a: Use a Second Drive (Recommended)

Install a second SSD of 256GB or more. You'll pick it during the Ubuntu install, and Windows stays untouched.

### Option B: Shrink Your Windows Drive

1. Press `Win + X` and open **Disk Management**
2. Right-click your Windows drive (`C:`) and choose **Shrink Volume**
3. Enter the amount to shrink in MB. For 256GB, enter `262144`
4. Leave the new space as **Unallocated**. Do not create a partition. The Ubuntu installer will use it

## Step 3: Create a Bootable Ubuntu USB

1. Download **Ubuntu 26.04 LTS Desktop** from <a href="https://ubuntu.com/download/desktop" target="_blank" rel="noopener noreferrer">ubuntu.com/download/desktop</a>
2. Download <a href="https://rufus.ie" target="_blank" rel="noopener noreferrer">Rufus</a> (or <a href="https://etcher.balena.io" target="_blank" rel="noopener noreferrer">balenaEtcher</a>)
3. In Rufus, select your USB stick and the Ubuntu `.iso` file, set **Partition scheme** to **GPT**, and click **Start**

## Step 4: Boot from the USB

The easiest way from Windows:

1. Open **Settings → System → Recovery**
2. Next to **Advanced startup**, click **Restart now**
3. Choose **Use a device** and select your USB stick

Alternatively, restart and press your motherboard's boot-menu key while the PC starts (often `F12`, `F11`, `F8` or `Esc`).

When the Ubuntu menu appears, choose **Try or Install Ubuntu**.

> **Secure Boot**
>
> You can leave Secure Boot enabled. Ubuntu supports it. When you install the NVIDIA drivers, you will be asked to set a password and enroll a key (MOK) on the next reboot. See Ubuntu's <a href="https://ubuntu.com/server/docs/how-to/graphics/install-nvidia-drivers/" target="_blank" rel="noopener noreferrer">NVIDIA driver guide</a> for details.

## Step 5: Install Ubuntu Alongside Windows

Follow the installer. At these screens, pay attention:

- **Applications and updates:** check **Install third-party software for graphics and Wi-Fi hardware**. This installs the NVIDIA driver during setup.
- **Disk setup:**
  - **Option A (second drive):** choose **Erase disk and install Ubuntu**, then make sure you select the **empty second drive**. Check the drive size and model carefully. Selecting your Windows drive here will erase it.
  - **Option B (shrunk drive):** choose **Install Ubuntu alongside Windows Boot Manager**. The installer will use the unallocated space.
- **Account:** create your user and password.

When the installer finishes, remove the USB stick and restart.

## Step 6: Make Ubuntu the Default

After restarting you should see the **GRUB** menu, which lists Ubuntu and Windows Boot Manager. Ubuntu is selected by default.

**If your PC boots straight into Windows**, open your BIOS/UEFI settings (usually `Del` or `F2` at startup) and move **Ubuntu** to the top of the boot order.

## Step 7: Install and Run the Nosana Host

Ubuntu is installed, so the last step is getting your GPU onto the network. Nosana's <a href="https://learn.nosana.com/hosts/grid-run.html" target="_blank" rel="noopener noreferrer">Running the Host guide</a> covers everything:

- **NVIDIA drivers and the NVIDIA Container Toolkit**, so AI workloads can use your GPU
- **Docker**, which runs the Nosana node
- **The start command**, which checks your setup, benchmarks your hardware and registers your host

Once your host is online, connect your wallet at <a href="https://host.nosana.com" target="_blank" rel="noopener noreferrer">host.nosana.com</a> to track its uptime and earnings.

## Common Questions

**Can I still play games?**
Yes. Restart into Windows whenever you want to play. Many games also run on Linux through Steam and Proton. Check <a href="https://www.protondb.com/" target="_blank" rel="noopener noreferrer">ProtonDB</a> to see how well your games run.

**Is installing Linux risky?**
Dual-booting is safe when you follow the steps carefully and back up your data first. Using a second SSD for Ubuntu is the safest option, because your Windows drive stays untouched.

**Do I need to know the Linux terminal?**
Only a little. The guide gives you every command to copy and paste, and our community in <a href="https://nosana.com/discord" target="_blank" rel="noopener noreferrer">Discord</a> is ready to help if you get stuck. Running into an error? Check the <a href="https://learn.nosana.com/hosts/troubleshoot.html" target="_blank" rel="noopener noreferrer">troubleshooting guide</a>.

**Which Ubuntu version should I use?**
<a href="https://releases.ubuntu.com/26.04/" target="_blank" rel="noopener noreferrer">Ubuntu 26.04 LTS</a>, the latest long-term support release.

**Where can I see my uptime and earnings?**
Connect your wallet on <a href="https://host.nosana.com" target="_blank" rel="noopener noreferrer">host.nosana.com</a> to see your host's status, uptime and earnings.

## Put Your GPU to Work

Your RTX 4090 or RTX 5090 can power real AI workloads for developers around the world, and earn you money while it does. The switch to Linux takes an afternoon, Windows stays on your PC, and the campaign incentive runs until November 17.

Set up Ubuntu, start the node and bring your GPU online.

<a href="https://nosana.com/gpu-providers/" target="_blank" rel="noopener noreferrer">Become a Nosana GPU provider</a>

Stuck during setup? Ask our community in <a href="https://nosana.com/discord" target="_blank" rel="noopener noreferrer">Discord</a>. We're happy to help.

## Useful Links

- <a href="https://nosana.com/gpu-providers/" target="_blank" rel="noopener noreferrer">GPU Provider page and earnings calculator</a>
- <a href="https://nosana.com/blog/rtx-4090-5090-gpu-provider-campaign/" target="_blank" rel="noopener noreferrer">RTX 4090 and RTX 5090 campaign details</a>
- <a href="https://learn.nosana.com/hosts/grid-run.html" target="_blank" rel="noopener noreferrer">Running the Nosana Host guide</a>
- <a href="https://learn.nosana.com/hosts/grid.html" target="_blank" rel="noopener noreferrer">GPU host documentation</a>
- <a href="https://host.nosana.com" target="_blank" rel="noopener noreferrer">Host dashboard</a>
- <a href="https://explore.nosana.com" target="_blank" rel="noopener noreferrer">Nosana Explorer: markets and queues</a>
- <a href="https://nosana.com/discord" target="_blank" rel="noopener noreferrer">Join the Discord</a>
- <a href="https://nosana.com/twitter/" target="_blank" rel="noopener noreferrer">Follow us on X</a>

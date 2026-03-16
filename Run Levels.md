# Linux Run Levels and Startup/Shutdown Sequence Cheat Sheet

## Run Levels (SysVinit)
Run levels define the **state of a Linux system** and determine which **services are running**.

| Run Level | Description |
|-----------|-------------|
| 0 | Halt / Shutdown system |
| 1 | Single-user mode (maintenance, root only) |
| 2 | Multi-user mode (no networking, rarely used) |
| 3 | Multi-user mode with networking (CLI) |
| 4 | Custom / user-defined |
| 5 | Multi-user mode with GUI |
| 6 | Reboot |

Check current run level: runlevel

Change run level: init 3 , telinit 5

## systemd Target Equivalent
Modern Linux systems use **systemd targets** instead of run levels.

| Runlevel | systemd Target |
|----------|----------------|
| 0 | poweroff.target |
| 1 | rescue.target |
| 2 | multi-user.target |
| 3 | multi-user.target |
| 4 | multi-user.target |
| 5 | graphical.target |
| 6 | reboot.target |

Check default target: systemctl get-default  
Set CLI mode: sudo systemctl set-default multi-user.target  
Set GUI mode: sudo systemctl set-default graphical.target  
Switch temporarily: sudo systemctl isolate multi-user.target

## Linux Startup (Boot) Sequence

Power ON → BIOS/UEFI → Bootloader (GRUB) → Linux Kernel → systemd/init (PID 1) → Start Services → Login Prompt / GUI

### Boot Steps

BIOS / UEFI  
- Initializes hardware  
- Performs POST  
- Selects boot device  

Bootloader (GRUB)  
- Loads Linux kernel  
- Loads initramfs  
- Provides OS selection menu  

GRUB configuration file: /boot/grub/grub.cfg

Kernel Initialization  
- Detect hardware  
- Load drivers  
- Mount root filesystem  
- Start first process (PID 1)

Check PID 1 process: ps -p 1

systemd / init  
- First userspace process  
- Starts system services  
- Manages targets and runlevels  

Service directories:  
/etc/systemd/system  
/usr/lib/systemd/system

Service Startup Examples  
- Networking  
- SSH  
- Cron  
- Logging  
- Display manager

Login Stage  
CLI login → tty1  
GUI login → display manager (GDM, SDDM, LightDM)

## Linux Shutdown Sequence

User shutdown command → systemd receives signal → stop services → unmount filesystems → terminate processes → sync disks → power off or reboot

Shutdown immediately: sudo shutdown now  
Shutdown after 10 minutes: sudo shutdown +10  
Reboot system: sudo reboot  
Power off system: sudo poweroff  
Cancel shutdown: sudo shutdown -c

## Important systemd Commands

| Command | Purpose |
|--------|---------|
| systemctl | Manage services |
| systemctl status service | Check service status |
| systemctl start service | Start service |
| systemctl stop service | Stop service |
| systemctl enable service | Enable at boot |
| systemctl disable service | Disable at boot |

Example: systemctl status ssh

## Quick Boot Flow

Power ON → BIOS/UEFI → GRUB → Kernel → systemd (PID 1) → Services → Login
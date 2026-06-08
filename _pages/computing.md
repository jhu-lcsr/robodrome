---
permalink: /documentation/computing/
title: "Computing Resources"
sidebar:
  nav: "docs"
---

## Network setup
You can connect to the WiFi network with SSID `stieff-mocap` to recieve messages from the Optitrack system. The system is set to multicast from a Windows machine running Motive at `192.168.0.92`. Please do not change the system to Unicast as this will prevent multiple users from recieving messages simultaneously.

You can use the [MOCAP4ROS2](https://github.com/orgs/MOCAP4ROS2-Project/repositories) packages to automatically convert the native [NatNet](https://optitrack.com/software/natnet-sdk) messages to ROS2 messages.

## Adding Rigid Bodies
You can add Rigid Bodies using the Motive instance running on the Mocap Windows PC physically located in the space. Observe the following guidelines:
- Motive will automatically give new Rigid Bodies a unique ID, do not change this to avoid conflicting with existing rigid bodies
- Never delete an existing rigid body that you did not create yourself

## ROS_DOMAIN_ID
If you are connected to the Stieff LAN, it is important to deconflict your ROS_DOMAIN_ID before launching any ROS nodes so that messages across experimental setups do not conflict. Refer to the whiteboard in the room for which ROS_DOMAIN_IDs are in use, and write down your ROS_DOMAIN_ID to reserve it. 

It is also possible to operate ROS in localhost only mode to prevent messages from being broadcasted across the LAN. Set ROS_LOCALHOST_ONLY=1 if you don't have a multi-device setup.

## IP Addresses
Please set your devices to DHCP (dynamic IP) and allow the router to serve your device an IP. If you need a static IP, contact a router admin. Static IP's should be set from the router to ensure deconfliction.

## Router Administration

Please contact a member of AIRO or ACE lab if you need to do any router administration. This includes:
- Port fowarding
- Static IP Reservation
- Remote access

Router Admin Contacts:
- Ashwin Gupta (agupt139@jh.edu)
- Rahul Nunna (rnunna1@jh.edu)
- Sriram Kodey (skodey1@jh.edu)

## mDNS
mDNS is a LAN UDP multicast DNS service that is in use by default on most Linux devices. Use of mDNS is highly recommended as it alleviates the need for static IPs. Machines are accessible at `<hostname>.local`. E.g. to `ssh` a device named `kalman` one can `ssh kalman.local` without ever knowing it's local IP.

You can discover hostnames with nmap `nmap -sn 192.168.0.*`.
# Windows Network Policy Server & Unifi WiFi

Using Unifi Network Application 7.3.76 and Windows server 2016 Standard Connected to MS Active Directory


# Windows server setup

Login and open server manager and navigate to Add Roles and Features

Tick the boxes below that are highlighted

![](./images/nps-1.png)

When Here tick the following

![](./images/nps-2.png)

Tick the box thats highlighted

![](./images/nps-3.png)

### Once done just hit install and it all should install without needing a restart


## Windows Firewall
Follow the following images below


![](./images/nps-4.webp)

![](./images/nps-5.webp)
![](./images/nps-6.webp)
![](./images/nps-7.png)
![](./images/nps-8.png)
![](./images/nps-9.png)
![](./images/nps-10.png)

## Windows CA
Follow the images below


![](./images/ca-1.webp)
![](./images/ca-2.webp)
![](./images/ca-3.webp)
![](./images/ca-4.webp)
![](./images/ca-5.webp)
![](./images/ca-6.webp)
![](./images/ca-7.webp)
![](./images/ca-8.webp)
![](./images/ca-9.webp)
![](./images/ca-10.webp)
![](./images/ca-11.webp)
![](./images/ca-12.webp)

## NPS configuration
Configuring NPS for Radius Auth


# Copy and paste this box below when it comes up in plain text and save it to note pad, You will need this for later

![](./images/nps-13.png)

# Select the Template you made earlier
![](./images/nps-12.png)

Select The highlighted option in the image

![](./images/nps-14.png)

You can use a custom group like i have, since its a group that gives you access to most of my applications or just use "Domain Users"

![](./images/nps-15.png)

No Configuration Required here

![](./images/nps-16.png)

Hit Finish

![](./images/nps-17.png)

# GPO for Ad clients (optional)


Create the GPO in the USERS folder or where you store your users in AD

![](./images/gpo-1.png)
![](./images/gpo-2.png)

Computer Configuration > Windows Settings > Security Settings > Public Key Policies 

double click Certificate Services Client Enrollment and fill out the as the image blow is

![](./images/gpo-3.png)
![](./images/gpo-4.png)

Expand Public Key policies and right click Automatic certificate request settings and click new automatic certificate request

![](./images/gpo-5.png)

Click next

![](./images/gpo-6.png)

Make sure you select Computer

![](./images/gpo-7.png)

Click finish and your done!

![](./images/gpo-8.png)

# Unifi Setup

This is pretty straight forward

The Shared Secret is the string you copied earlier into a text file

Keep the ports at default 1812 for auth servers and 1813 for accounting (this is not needed but helps for later troubleshooting)

Goto Settings, Profiles and Create New Radius Profile
![](./images/unifi-1.png)

Set the name to something useful, Assigned VLAN support is there its just not needed for this, Type the IP of your NPS server and enter the port 1812 for the auth server and the Shared Key is from earlier

Same for the accounting server 

![](./images/unifi-2.png)

For your Wifi Settings you will need to change from WPA-personal to WPA-Enterprise and select the Profile we made just before, Make sure to Require PMF, this helps with connecting clients and so they dont have issues

![](./images/unifi-3.png)

Source: https://patrickdomingues.com/2021/10/27/how-to-configure-windows-server-and-unifi-controller-for-radius-wifi-access/

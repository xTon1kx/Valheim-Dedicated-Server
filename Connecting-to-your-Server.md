While ValheimServerGUI takes care of most of the server setup for you, you'll still need to tweak a couple of settings on your home network in order for other players to be able to connect to your PC. This guide will cover some of the common issues you might run into while trying to get your friends to connect to your PC.

Consider the following scenario: You are running a Valheim Dedicated Server on your PC, and your friend wants to connect to your PC so you can both play on the same world. Imagine this using the following highly-detailed diagram.

```
          Step 1                     Step 2                                               Step 3
            |                          |                                                    |
[Your PC] <---- [Your PC's Firewall] <---- [Your Router] <---- ( THE INTERNET ) <---- ... <---- [Friend's PC]
```

## Step 1 - Allow Valheim to communicate through Your PC's Firewall

A firewall essentially blocks all internet-bound communication from applications that you have not authorized. You need to make an exception to allow communication from `valheim_server.exe` to pass through your PC's firewall. If you're using Windows Defender, you should get a prompt from Windows asking you to authorize this when you start your server for the first time. Make sure that both Public and Private networks are checked, to avoid any complications.



If you want to make sure that your firewall exception is in place, search the Start menu in Windows 10 for **"Allow an app through Windows Firewall"**. If an exception for `valheim_server` does not exist, you can click **"Allow another app..."** and browse for it here.

## Step 2 - Telling Your Router how to find Your PC

Your router already knows how to find your PC, right? Well, yes. But when you're hosting a server, you want to make sure of two things:

1. Your router always looks at the **same address** to find your PC, every time.
2. Your router sends all incoming traffic directed to the **Valheim port** straight to your PC.

So with that in mind, let me show you how I would set this up on my home network (using a Linksys WRT1900AC router), and hopefully you can adapt this to fit your own network.

### Setting up a Static IP Address

Normally, your router will assign your PC (or any device on your home network) an **arbitrary internal IP address** each time it connects. These usually look like `192.168.X.X` or `10.X.X.X`, depending on your router.

But we want to make sure your router assigns the **same IP address** to your computer every time you connect. This is called a **Static IP Address** or **DHCP Reservation**, and virtually every modern router should support this.

1. Navigate to your router's settings page at `192.168.1.1` (this may also be `10.0.0.1` or something else depending on your router)
2. Enter your router's admin password.
3. Go to Connectivity > Local Network > DHCP Reservations.
4. Find your PC in the list, and select it to "Add a DHCP Reservation". In this example, you can see I reserved the internal IP address `192.168.1.192` for my PC.



### Setting up Port Forwarding

(WIP)
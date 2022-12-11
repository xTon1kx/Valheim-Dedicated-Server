## If you have Crossplay enabled...

...then you don't need to perform any of the steps outlined below! Enabling crossplay will route all of your server's traffic through a 3rd-party provider (PlayFab). Instead of setting up port-forwarding and sharing an IP address, all you need to do is share a 6-digit **Invite Code**. 

ValheimServerGUI will display your server's Invite Code on the Server Details tab as soon as it's available. Each time you restart your server, the Invite Code will change. However, once a player joins with an Invite Code, that server will be saved in their server list in Valheim itself, so they shouldn't need to input the new code.

I would suggest enabling Crossplay and sharing the Invite Code if you just want to get started quickly, even if everyone is playing on PC. However, if you're experiencing networking issues (like disconnects or lag), then you may want to have everyone connect via IP address instead. In that case, read on!

## Sharing your Server without Crossplay

While ValheimServerGUI takes care of most of the server setup for you, you'll still need to tweak a couple of settings on your home network in order for other players to be able to connect to your PC. This guide will cover some of the common issues you might run into while trying to get your friends to connect to your PC.

Consider the following scenario: You are running a Valheim Dedicated Server on your PC, and your friend wants to connect to your PC so you can both play on the same world. Imagine this using the following highly-detailed diagram.

```
          Step 1                     Step 2                                               Step 3
            |                          |                                                    |
[Your PC] <---- [Your PC's Firewall] <---- [Your Router] <---- ( THE INTERNET ) <---- ... <---- [Friend's PC]
```

## Step 1 - Allow Valheim to communicate through Your PC's Firewall

A firewall essentially blocks all internet-bound communication from applications that you have not authorized. You need to make an exception to allow communication from `valheim_server.exe` to pass through your PC's firewall. If you're using Windows Defender, you should get a prompt from Windows asking you to authorize this when you start your server for the first time. Make sure that both Public and Private networks are checked, to avoid any complications.

![](https://raw.githubusercontent.com/runeberry/ValheimServerGUI/main/img/firewall-1.png)

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
3. Go to **Connectivity > Local Network > DHCP Reservations**.
4. Find your PC in the list, and select it to **"Add a DHCP Reservation"**. In this example, you can see I reserved the internal IP address `192.168.1.192` for my PC.

![](https://raw.githubusercontent.com/runeberry/ValheimServerGUI/main/img/router-1.png)

### Setting up Port Forwarding

As I mentioned before, this step will vary greatly depending on your router. I would recommend finding your router on [PortForward.com](https://portforward.com/) for specific instructions. But here's how I handled it on my router:

1. From within your router's settings page, go to **Security > Apps & Gaming > Port Range Forwarding**.
2. You'll need to select your ports and an internal IP address to route them to.
  * For Valheim, you will need 2 ports forwarded. **2456-2457** are the default ports, but this may differ if you're using a different port in ValheimServerGUI. For example, if you're running your server on port 9500, you'll need to forward ports 9500-9501.
  * Then, you'll need to enter the internal IP address you reserved from the previous step.

![](https://raw.githubusercontent.com/runeberry/ValheimServerGUI/main/img/router-2.png)

After you've done this, all incoming traffic directed to the Valheim server ports will now automatically be directed to your computer. Hooray, the hard part is done!

## Step 3 - Telling Your Friend's PC how to find Your PC

Okay, great. You've got everything set up, now how do your friends outside your home connect to your server? They won't be able to find those internal IP addresses we talked about before, because those only work within your home network.

If you're running a **Community Server**, then your Server Name should show up in the Join Game tab within Valheim shortly after you start your server from your PC. Note that it might take a few minutes to show up the first time, and you may need to refresh the list a couple of times.

If you're not running a Community Server, then the only way to connect to your server is to **"Join by IP"**. You'll need to give your friends your **external IP address** for them to connect to. This is assigned by your ISP (Comcast, Verizon, etc.), and the easiest way to find it is to visit whatsmyip.com.

Let's say, for example, that whatsmyip.com says my external IP address is `100.2.3.4`. My friends would be able to connect to my server by joining:
* `100.2.3.4` if I'm using running my server on the default port (2456). You can omit the port from your IP address if you're using the default.
* `100.2.3.4:9500` if I were running my server on port 9500.

**VERY IMPORTANT NOTE:** If you're running your server from basic residential internet, your ISP may change your external IP address at any time, without notice! Keep this in mind, and check back on whatsmyip.com to see if it's changed!

**TIP:** To retain your "host advantage", you should always connect to `127.0.0.1` if you're hosting your server on the same PC that you're playing Valheim on. This special address works on all networks and will always loop back to your own computer without ever hitting the internet, giving you the best possible connection!
# DNS cache

{% hint style="info" %}
It is likely that the DNS record for your local API has been cached by your computer. 
{% endhint %}

To clear the DNS cache, follow the instructions for your operating system:

* [MacOS](dns-cache.md#macos)
* [Microsoft Windows 8 \(or above\)](dns-cache.md#microsoft-windows-8-or-above)
* [Microsoft Windows 7](dns-cache.md#microsoft-windows-7)
* [Microsoft Windows XP, 2000, or Vista](dns-cache.md#microsoft-windows-xp-2000-or-vista)

## **MacOS**

Open the terminal and paste the command below:

```bash
sudo killall -HUP mDNSResponder;sudo killall mDNSResponderHelper;sudo dscacheutil -flushcache
```

## **Microsoft Windows 8 \(Or above\)**

1. Select **Win + X** to open the **WinX menu**.
2. Right-click **Command Prompt &gt; Run as Administrator**.
3. Type **ipconfig /flushdns** and press **Enter**.

## **Microsoft Windows 7**

1. Click the **Start** Menu.
2. Type **CMD** in the Search Box.
3. Right-click **Command Prompt &gt; Run as Administrator**.
4. Type **ipconfig /flushdns** and press **Enter**.

## **Microsoft Windows XP, 2000, Or Vista**

1. Select **Win + R** to open the **Run... Dialog**.
2. Type **ipconfig /flushdns** and press **Enter**.


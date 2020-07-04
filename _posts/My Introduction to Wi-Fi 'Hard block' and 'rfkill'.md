---
title: "My Introduction to Wi-Fi 'Hard block' and 'rfkill'"
date: 2020-07-26T15:34:30-04:00
categories:
  - blog
  - launch
tags:
  - Wi-Fi Hard Block
  - rfkill
---

  While I was adjusting the brightness of my laptop, my internet suddenly got disconnected.  I checked router and Wi-Fi connection, they were perfectly fine,  I noticed Wi-Fi symbol disappeared from the drop-down menu, even the settings showed no options to turn it 'on'  and the notification said '**No Wi-Fi Adapter Found**' as shown in the screen shot below : 



![pic 1](https://user-images.githubusercontent.com/42797168/86515763-07b5f500-be39-11ea-8de8-df6503c4a7f6.png)

Surmising an issue in the Wi-Fi driver, I removed the exisiting Wi-Fi packages using  _'apt'_ & _'purge'_ tools and then re-installed them, but couldn't find any change!!

I then checked the list of pci buses on my system using _'lspci'_ command and  realised  “Network Bus’’ was missing. 

With my collegue’s intervention I came across _‘rfkill’_ tool..

**_'rfkill'_** - is a tool that gives an interface to know the status, activate and deactivate the radio transmittors in a computer.
It is mainly associated with wireless tramsittors in the system like 'Wi-Fi' , 'Bluetooth' and Mobile Broadband Devices .

When these devices are deactivated they fall into **'soft block'** ( a state in which the device can be re-activated using software) **or**  **'hard block'** ( a state in which the device cannot be re-activated using a software ) 

( References:
 https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/power_management_guide/rfkill

https://linux.die.net/man/1/rfkill )

Using the command _''rfkill list''_  I found that the wireless LAN was **hard blocked** and as understood hard block cannot be unblocked using software...

As mentioned in the beginning of my writeup,  I remembered I was adjusting the brightness using keyboard buttons (Function +F12) supposing this action might have blocked Wi-FI I tried it again but no luck...

Then I tried '**Function + Prtscr**' ( ‘PrtScr’ has a transmittor symbol on it)  and finally it worked!!!

 Looking back at my initial action I might accidentally stroked ‘PrtScr’ key (which is right beside F12) while holding 'Function (Fn)' key

It is important to be vigilant of the actions and keyboard strokes you give while using the keyboard otherwise we may end up triggering changes in hardware setup!!!!
```c
#Sample code highlighting
#include <stdio.h>

int main()
{
    printf("Code hightlishting is supported\n");
    
    int 0;
}
```

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]:    https://jekyllrb.com/docs/home
[jekyll-gh]:      https://github.com/jekyll/jekyll
[jekyll-talk]:    https://talk.jekyllrb.com/
[pvjournal]:      https://pvjournal.github.io/
[project-vikram]: https://projectvikram.github.io/

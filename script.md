##### pull screen

``` bash
    adb shell screencap -p /sdcard/1.png
    adb shell pull /sdcard/1.png .
```

##### adb input events

* **adb shell input tap 300 700** – Inputs a tap event at the specific coordinates in pixels. In this case, 300 is the x value and 700 is the y value.
* **adb shell input swipe 540 1600 540 100 1500** – Inputs a swipe gesture starting at a set of coordinates, ending at another set of coordinates. In this case, 540 is the start x value, 1600 is the start y value, 540 is the end x value, 100 is the end y value, and 1500 is the time in milliseconds the swipe will take. On both a physical device and the emulator I have found that swipe inputs that are under 1500 milliseconds produce inconsistent results. This is important because when chaining multiple inputs together (more on this below), if one of them is off, the whole chain is broken.
* **adb shell input text 'Leon'** – Inputs text.
* **adb shell input keyevent 66** – Inputs enter.
* **adb shell input keyevent 19** – Inputs a D-pad up event, useful for changing the focus to a different view.
* **adb shell input keyevent 20** – Inputs a D-pad down event, useful for changing the focus to a different view.
* **adb shell input keyevent 21** – Inputs a D-pad left, useful for changing the focus to a different view.
* **adb shell input keyevent 22** – Inputs a D-pad right event, useful for changing the focus to a different view.



#### some data

1. place general
   (470,480),(360,580),(400,700)
2. begin combat
   (950,1000)
3. press OK
   (950,700)
4. auto 
   (1845,235)
5.  retry
   (790,770)


#### full scripts

```
    adb shell screencap -p /sdcard/1.png
    adb shell pull /sdcard/1.png .
```

``` bash
    //place generals
    adb shell input tap 470 480
    adb shell input tap 360 580
    adb shell input tap 400 700

    //begin
    adb shell input tap 950 1000

    //press OK
    adb shell input tap 950 700

    //auto battle
    adb shell input tap 1845 235

    // wait for battle
    sleep 30

    // retry
    adb shell input tap 790 770
    // tap again
    adb shell input tap 790 770
```
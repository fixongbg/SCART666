# SCART666
This is modified version of the included vga666 overlay which excludes pin 18, 19, leaving them to be available for PWM audio while using the SCART666 adapter.

# Instructions
Boot up your Rpi. Use the console line or SSH and type:

    sudo apt-get update

    sudo apt-get install -y git

    git clone https://github.com/WiringPi/WiringPi.git

    cd WiringPi

    sudo ./build

....wait for the compiling to be done. Then type:
 
    git clone https://github.com/fix-ON/SCART666.git

    cd SCART666

    sudo cp scart666.dtbo /boot/overlays/

# Configuration
Type the following:

    sudo raspi-config:

Choose `Advanced Options > Audio > Force 3.5mm (headphone) jack >`
Press ENTER. 

Go down to `Finish` > Press `ENTER`.

When your back in the console, type:

    sudo alsamixer

Press the `Up arrow key` until the volume is at MAX (db gain: 4.00).

Press `ESC` to exit (settings will be saved automatically).

Almost done, just type: 

    sudo shutdown -h now (this will turn off your Rpi). 

Wait until your Rpi is completely off, then take out the SD-card and connect it to your computer. 
In the root of your SD-card there's a file called `config.txt`. Inside that text file, add this to the bottom of all the text: tills din Rpi har stängts av och ta ut minneskortet. 
 
    dtoverlay=pwm-2chan,pin=18,func=2,pin2=19,func2=2
    dtoverlay=scart666
    enable_dpi_lcd=1
    display_default_lcd=1
    dpi_output_format=6
    dpi_group=2
    dpi_mode=87
    hdmi_timings=320 1 16 30 34 240 1 2 3 22 0 0 0 60 0 6400000 1

Eject your SD-card and put it back into the Rpi.

Connect the SCART666 adapter to the Rpi and hook up all the necessary cables to your TV/Monitor.

Turn on the Rpi and you should get a 240p picture! 

If you want, you can do a audio test by typing:
sudo aplay /usr/share/sounds/alsa/Front_Center.wav

You'll here a voice saying "Front Center". 

You're all set! Enjoy your SCART666 adapter. 

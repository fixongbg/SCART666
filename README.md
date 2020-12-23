# SCART666
This is modified version of the included vga666 overlay which excludes pin 18, 19, leaving them to be available for PWM audio while using the SCART666 adapter.


Boot up your Rpi or use SSH and type: 

 sudo apt-get install -y git

             git clone https://github.com/WiringPi/WiringPi.git

             cd WiringPi

             sudo ./build

....wait for compiling to be done.
 

git clone https://github.com/fix-ON/SCART666.git

cd SCART666
sudo cp scart666.dtbo /boot/overlays/
sudo raspi-config:
	Välj Advanced Options > Audio > Force 3.5mm (headphone) jack > 
Tryck ENTER. 
Gå ner till Finish > Tryck ENTER.
Tillbaka i konsolen skriver vi sudo alsamixer
Tryck på uppåtpilen tills volymen är på max (db gain: 4.00)
Tryck ESC för att avsluta (inställningarna sparas automatiskt).
sudo shutdown -h now (Detta kommer stänga av din Raspberry Pi)
Vänta tills din Rpi har stängts av och ta ut minneskortet. 
Sätt i minneskortet i datorn. Gå in på minneskortet och öppna config.txt.
Kopiera och klistra in detta längst ner under all text:
 
dtoverlay=pwm-2chan,pin=18,func=2,pin2=19,func2=2
dtoverlay=scart666
enable_dpi_lcd=1
display_default_lcd=1
dpi_output_format=6
dpi_group=2
dpi_mode=87
hdmi_timings=320 1 16 30 34 240 1 2 3 22 0 0 0 60 0 6400000 1
Sätt minneskortet i din Rpi igen.
Koppla på SCART666 över din Rpi om du inte redan gjort det.
Koppla in den till TV’n och starta upp din Rpi.
Du bör nu se din Rpi boota upp i 240p upplösning eller liknande. 
Om du vill kan du göra ett ljudtest: 
sudo aplay /usr/share/sounds/alsa/Front_Center.wav
Du bör höra en kvinnoröst som säger “Front Center”. 
Annars är allting klart! Njut nu av din Rpi i RGB med ljud via SCART. 
 
Har du några problem eller frågor? 
Tveka in på att maila contact@fix-ON.se

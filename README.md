![LoRaHAM_Pi](https://github.com/LoRaHAM/LoRaHAM_Pi/blob/main/LoRaHAM_logo.png?raw=true)

# LoRaHAM_Voice (english) - Speech over LoRa (Codec 2)

LoRaHAM_Voice is a software for the LoRaHAM_Pi hardware upgrade project and LoRaHAM modules for amateur radio operators, enabling high-power LoRa operation with long range on a single-board computer. The daemon is a device driver that allows users (without any hardware programming knowledge) to easily operate the system.

First code for the LoRaHAM Pi hardware | https://www.loraham.de/produkt/loraham-pi/

U need an Audio-Adapter with Microphone and Speaker or an BT-Headset! Not all Headsets will support bei RPi OS. Plantronics ML18 works, EOTE14 not (both tested)

<img src="https://github.com/LoRaHAM/LoRaHAM_Pi/blob/main/LoRaHAM_P1_3.jpg" alt="LoRaHAM_Pi" width="300" height="auto"><img src="https://github.com/LoRaHAM/LoRaHAM_Ressources/blob/main/LoRaHAM_Cartridge_for_pi500.png" alt="LoRaHAM Cartridge" width="300" height="auto">

* Raspberry Pi 3/4/5
* Raspbian Image on RPi
* LoRaHAM_Daemon | https://github.com/LoRaHAM/LoRaHAM_Daemon

# Need follow parts on the Raspberry Pi image:

    sudo apt update
    sudo apt install libcodec2-dev -y
    sudo apt install libasound2-dev -y
    sudo apt install libgtk-3-dev -y
    sudo apt install libncurses5-dev -y
     
    git clone https://github.com/LoRaHAM/LoRaHAM_Voice ~/LoRaHAM/voice


# Compile instruction
loraham_voice:

    cd ~/LoRaHAM/voice
    gcc -o loraham_voice loraham_voice.c `pkg-config --cflags --libs gtk+-3.0` -lcodec2 -lasound -lncurses -lpthread -lm


# Use instructions:
1. first run the LoRaHAM Daemon because this is the interface between hardware (LoRaHAM_Pi HAT or LoRaHAM Cartridge) and users programm
2. then the LoRaHAM Voice 

1. ./loraham_daemon
2. ./loraham_voice

Daemon can also run as real daemon (parameter -d):
1. ./loraham_daemon -d

if you dont run loraham_daemon as a daemon, you see all traffic on your terminal!

Voice options:

     ./loraham_voice        (Auto: GUI wenn DISPLAY gesetzt)
     ./loraham_voice --cli   (CLI erzwingen)
     ./loraham_voice --gui   (GUI erzwingen)
 
Example:

     ./loraham_voice 
 
# Background information
loraham_voice uses 4 IPC (inter process communication) UNIX-Sockets for two LoRa-Bands:

    - DATA868_SOCKET "/tmp/lora868.sock"
    - DATA433_SOCKET "/tmp/lora433.sock"
    - CONF868_SOCKET "/tmp/loraconf868.sock"
    - CONF433_SOCKET "/tmp/loraconf433.sock"
    
After start, you will see an overview of usable audio devices. 
Use "pulse" for pulse-audio

# Warnings
This code is provided at your own risk and responsibility. This code is experimental.
For radio amateur or laboratory use only.

# Credits and license

    Copyright (c) 2020-2026 Alexander Walter
    Licensed under GPL v3 (text)
    Maintained by Alexander Walter 
    
This project is licensed under **GNU GPL v3** with additional commercial restrictions:

    * **Private & Hobby:** Use is free of charge. Modifications must be reported to the author (via Pull Request).
    * **Commercial:** Any use in a business environment or for profit is **prohibited without a paid commercial license**.
    * **Redistribution:** Binaries may only be distributed alongside the full source code.
    * **Liability:** Software is provided "as is". The author is not liable for any damages.
 
         ******************************************************************************
         * Copyright (C) 2026  [LoRaHAM / Alexander Walter]
         * * LICENSE: GNU General Public License v3 (GPLv3) with the following terms:
         * 1. PRIVATE/HOBBY: Free use, modification, and redistribution for non-commercial
         * purposes is permitted.
         * 2. COMMERCIAL: Commercial or business use is STRICTLY PROHIBITED unless a
         * written license is obtained from the author for a fee (Dual-Licensing).
         * [CONTACT: loraham.de Email Contact]
         * 3. CODE MAINTENANCE: Any modifications to this code must be reported to the
         * author (preferably via Pull Request on GitHub).
         * 4. REDISTRIBUTION: Binaries may only be distributed alongside the full
         * source code (Copyleft).
         * * --- DISCLAIMER OF WARRANTY & LIMITATION OF LIABILITY ---
         * THIS SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
         * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
         * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
         * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
         * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
         * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
         * THE SOFTWARE. THE ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE
         * PROGRAM IS WITH THE USER.
     ******************************************************************************


![LoRaHAM_Pi](https://github.com/LoRaHAM/LoRaHAM_Pi/blob/main/LoRaHAM_logo.png?raw=true)

# LoRaHAM_Voice (deutsch) - Speech over LoRa (Codec 2)

LoRaHAM_Voice ist eine Software für das LoRaHAM_Pi-Hardware-Upgrade-Projekt und LoRaHAM-Module für Funkamateure, die einen leistungsstarken LoRa-Betrieb mit großer Reichweite auf einem Einplatinencomputer ermöglicht. Der Daemon ist ein Gerätetreiber, der es Benutzern (ohne jegliche Kenntnisse in der Hardwareprogrammierung) ermöglicht, das System einfach zu bedienen.

Erster Code für die LoRaHAM Pi Hardware | https://www.loraham.de/produkt/loraham-pi/

<img src="https://github.com/LoRaHAM/LoRaHAM_Pi/blob/main/LoRaHAM_P1_3.jpg" alt="LoRaHAM_Pi" width="300" height="auto"><img src="https://github.com/LoRaHAM/LoRaHAM_Ressources/blob/main/LoRaHAM_Cartridge_for_pi500.png" alt="LoRaHAM Cartridge" width="300" height="auto">

* Raspberry Pi 3/4/5
* Raspbian Image auf RPi
* LoRaHAM_Daemon | https://github.com/LoRaHAM/LoRaHAM_Daemon
 
    
# Anderenfalls werden folgende Pakete auf dem Raspberry Pi Image benötigt:

    sudo apt update
    sudo apt install libcodec2-dev -y
    sudo apt install libasound2-dev -y
    sudo apt install libgtk-3-dev -y
    sudo apt install libncurses5-dev -y
     
    git clone https://github.com/LoRaHAM/LoRaHAM_Voice ~/LoRaHAM/voice
    

# Kompilieranweisung
loraham_voice:

    cd ~/LoRaHAM/voice
    gcc -o loraham_voice loraham_voice.c `pkg-config --cflags --libs gtk+-3.0` -lcodec2 -lasound -lncurses -lpthread -lm

    
# Bedienungsanleitung:
1. Zuerst den LoRaHAM Daemon starten, da dies die Schnittstelle zwischen der Hardware (LoRaHAM_Pi HAT oder LoRaHAM Cartridge) und dem Benutzerprogramm ist.
2. Dann das LoRaHAM Voice 

1. ./loraham_daemon
2. ./loraham_voice

Daemon kann auch als echter Daemon laufen (Parameter -d):

1. ./loraham_daemon -d

Wenn Sie loraham_daemon nicht als Daemon ausführen, sehen Sie den gesamten Datenverkehr in Ihrem Terminal!

Voice Optionen:

     ./loraham_voice        (Auto: GUI wenn DISPLAY gesetzt)
     ./loraham_voice --cli   (CLI erzwingen)
     ./loraham_voice --gui   (GUI erzwingen)

Beispiel:

     ./loraham_voice
 
# Hintergrundinformationen
loraham_voice verwendet 4 IPC (Inter-Process Communication) UNIX-Sockets für zwei LoRa-Bänder:

    - DATA868_SOCKET "/tmp/lora868.sock"
    - DATA433_SOCKET "/tmp/lora433.sock"
    - CONF868_SOCKET "/tmp/loraconf868.sock"
    - CONF433_SOCKET "/tmp/loraconf433.sock"
    

# Warnungen
Dieser Code wird auf eigenes Risiko und eigene Verantwortung zur Verfügung gestellt. Dieser Code ist experimentell.
Er ist nur für Funkamateure oder Labore geeignet.

# Credits und Lizenz

    Copyright (c) 2020-2025 Alexander Walter
    Licensed under GPL v3 (text)
    Maintained by Alexander Walter 
    
Dieses Projekt ist unter der **GNU GPL v3** lizenziert, jedoch mit spezifischen Bedingungen für die kommerzielle Nutzung:
    
    * **Privat & Hobby:** Die Nutzung ist kostenlos. Änderungen müssen dem Urheber mitgeteilt werden (via Pull Request).
    * **Kommerziell:** Jede Nutzung in einem geschäftlichen Umfeld oder zur Gewinnerzielung ist **genehmigungspflichtig und kostenpflichtig**. 
    * **Weitergabe:** Binärdateien dürfen nur zusammen mit dem Quellcode verbreitet werden.
    * **Haftung:** Die Software wird "wie besehen" bereitgestellt. Der Urheber übernimmt keine Haftung für Schäden.
        
        ******************************************************************************
         * Copyright (C) 2026 [LoRaHAM / Alexander Walter]
         * * LIZENZ: GNU General Public License v3 (GPLv3) mit den folgenden Bedingungen:
         * 1. PRIVAT/HOBBY: Die freie Nutzung, Änderung und Weiterverbreitung für 
         * nicht-kommerzielle Zwecke ist gestattet.
         * 2. KOMMERZIELL: Die kommerzielle oder geschäftliche Nutzung ist STRENGSTENS 
         * UNTERSAGT, sofern keine schriftliche Lizenz vom Autor gegen Gebühr erworben 
         * wurde (Dual-Licensing).
         * [KONTAKT: loraham.de E-Mail Kontakt]
         * 3. CODE-PFLEGE: Jegliche Änderungen an diesem Code müssen dem Autor gemeldet 
         * werden (vorzugsweise via Pull Request auf GitHub).
         * 4. WEITERVERBREITUNG: Binärdateien dürfen nur zusammen mit dem vollständigen 
         * Quellcode verbreitet werden (Copyleft).
         * * --- GEWÄHRLEISTUNGSAUSSCHLUSS & HAFTUNGSBESCHRÄNKUNG ---
         * DIESE SOFTWARE WIRD "WIE BESEHEN" (AS IS) ZUR VERFÜGUNG GESTELLT, OHNE 
         * JEGLICHE AUSDRÜCKLICHE ODER STILLSCHWEIGENDE GEWÄHRLEISTUNG, EINSCHLIESSLICH, 
         * ABER NICHT BESCHRÄNKT AUF DIE GEWÄHRLEISTUNG DER MARKTGÄNGIGKEIT, DER EIGNUNG 
         * FÜR EINEM BESTIMMTEN ZWECK UND DER NICHTVERLETZUNG VON RECHTEN DRITTER. 
         * IN KEINEM FALL SIND DIE AUTOREN ODER URHEBERRECHTSINHABER HAFTBAR FÜR 
         * ANSPRÜCHE, SCHÄDEN ODER ANDERE VERPFLICHTUNGEN, OB AUS VERTRAG, UNERLAUBTER 
         * HANDLUNG ODER ANDERWEITIG, DIE AUS ODER IM ZUSAMMENHANG MIT DER SOFTWARE 
         * ODER DER NUTZUNG ODER ANDEREN GESCHÄFTEN MIT DER SOFTWARE ENTSTEHEN. 
         * DAS GESAMTE RISIKO HINSICHTLICH DER QUALITÄT UND LEISTUNG DES PROGRAMMS 
         * LIEGT BEIM NUTZER.
     ******************************************************************************

# AK90Guide
YOUR MILEAGE MAY VARY - Here I wrote a simple guide of how I managed to write a key to my EWS3 for my 1999 BMW. Information about the AK90 tool and software is hit or miss, and I struggled in the past and could not make it work.
Apparently there are units that don't have an internal speaker and some do, these seem to be the ones with higher success rate. Mine has no speaker, but I managed to make it work in the end

## Setup

1. I used a Windows XP virtual machine. I could not get the software to run on a Windows 7 netbook, probably because it's a stripped down version of the OS
2. Install the AK90+ software and the included CP2102 drivers.
   - Not confirmed whether this depends on the hardware. Units with a CH9102 USB chip may need CH9102 drivers instead.
3. In the software, select your EEPROM model, then open **EWS Picture** to see the included connection pictures.

## Power the EWS module externally

My AK90 unit (no internal speaker) did not power the EEPROM. Without external power, reads failed, but then I realized that there was a picture included which said to power the EWS module if it could not be read. Here is how to power it:

- EWS connector **pin 9** to GND
- EWS connector **pin 10** to +12 V

Make sure the grounds of the AK90 and the power supply are connected.

## Read the EWS

1. Read the EWS several times, and save the .BIN files. To be extra careful, compare the outputs to make sure they are the same.
2. Check that the VIN and mileage are the same on every read.
3. Read the warning about the **2D47J** EEPROM/mask before continuing.
4. Proceed with **Read EWS**.

## Write the key

1. Click **Write key**.
2. Select an **unused key slot** in the EWS.
3. New transponders show **"unknown key type"** when read before writing. I think this is normal until the key data is written.
4. If writing fails, retry several times and change the transponder's position on the coil. In my case it eventually wrote and verified successfully.

## Verify

1. Click **Test key**.
2. It should show the VIN, the mileage and the key number you chose.

## Save to the EWS

1. Again making sure the connection to the EEPROM is solid, click **Write EWS** to write the updated data to the EWS EEPROM.

## Tips

- Keep the original dump (read and compare multiple times) as a backup before writing.
- If key reading or the connection fails, check the COM port and driver first.

I hope this can be of help to someone that found the same issues I did. I actually bought the programmer several years ago, disconnected the EWS module without disconnecting the car's battery and probably triggered a safe mode of the EWS system, and the car did not start anymore. After a few days of panic I disconnected the battery for some other reason and when I connected it back the car started working again. Because of this scare, I stopped trying, also because I'm usually the only driver of my car.
But a few days ago, my dad accidentally grabbed my keys and I found myself stuck at home and late for an appointment. This and the years of experience convinced me to attempt to do it again, and fortunately this time I could make the programmer work

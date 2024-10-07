# ESP BFF Manual

In deze manual leg ik je uit hoe je met twee ESP's data kan uitwisselen zonder directe verbinding

## Stap 1: Maak een Adafruit IO account aan

- Maak een account aan bij Adafruit IO via deze link (als je die niet al hebt):
https://io.adafruit.com/

## Stap 2: Maak een feed aan in AdafruitIO:

- Bovenin de navbar klik je op feeds  
- Hierna klik je op **+ new feed** en geef je het een naam  

## Stap 4: Kopieer je username en API key

- Klik op je nieuwe feed en ga hier naar jhet gele sleuteltje rechts bovenin naast New Device  
  ![image](https://github.com/user-attachments/assets/3dc5630d-2dec-4407-9020-368a99355c22)

- Sla deze info op, je hebt dit nodig voor in de code zometeen  
- We hebben de **Username** en **Active Key** nodig
  ![Screenshot 2024-10-07 160131](https://github.com/user-attachments/assets/8dba5030-448e-4445-a42b-4cb64b57598d)


## Stap 5: Sluit de knop en Ledstrip aan op de ESP's

- We gebruiken uiteraard twee ESP's voor dit project. We beginnen met de ESP met de knop:
    - Sluit de 'S' (signal) aan op pin 4 van je ESP, de '-' op GND (Ground) van je ESP en de middelste is de voeding dus sluit deze aan op de 3V3 (3.3 Volt) pin op je ESP  
      ![image](https://github.com/user-attachments/assets/0626c2b8-9003-4d1d-8c57-dcf5c04ef09a)
- En voor de andere ESP:
    - Sluit de DIN ook aan op pin 4 van je ESP, de '+5v' op je 3V3 pin op je ESP en de GND aan de GND uiteraard  

## Stap 5: Maak een nieuw project aan (Visual Studio Code met PlatformIO)

> Let Op! Doe deze stap twee keer voor de twee verschillende stukken code, een voor de reciever en een voor de ESP met de Button

- Klik op **+ New Project** in PlatformIO.

<img width="1272" alt="Screenshot 2024-10-03 at 11 23 44" src="https://github.com/user-attachments/assets/12b5b11b-4910-489f-ac8b-dd324f0749a0">

- Selecteer je ESP32 board, bijvoorbeeld **esp32dev module** zoals de screenshot hieronder.
- Druk op **Finish** om het project aan te maken.

## Stap 6: Update je `platformio.ini` bestand voor de libraries (en de serial monitor snelheid)

- Voeg `monitor_speed = 115200` toe om de snelheid van de seriële monitor in te stellen.
- Voeg de juiste **lib_deps** toe zodat PlatformIO de benodigde libraries installeert. Voor dit project gebruiken we:
   Door dit bestand aan te passen weet PlatformIo precies wat het nodig heeft en installeert het de jusite libraries en andere benodigdheden. Als je      een foute library hebt toegevoegd, dan haal je dit uit je **lib_deps** en dan verwijderd PlatformIO dit ook weer automatisch bij de build.
- Na deze stap moet je `plaformio.ini` er zo uitzien:
  
  
## Stap 5: De code

- Open het bestand **main.cpp** in je projectmap. Deze vind je in je **src** folder.
- Vervang de huidige inhoud met de code die beschikbaar is in deze repository, in het bestand genaamd `main.cpp`. Je kunt dit gewoon kopiëren en plakken in je eigen project (of je kunt deze repository overnemen/clonen).
- We hebben twee codes nodig en je moet dit ook twee keer uploaden dus naar twee verschillende ESP32's. In dit geval hebben we een normale, waar je de knop aansluit, en een 'reciever' waar je de LEDstrip aansluit. Check dit dat je de goede code naar elke ESP upload zie stap hieronder (eentje met de reciever code, de ander met de button code)

## Stap 5: Uploaden maar!

- Build en upload je code naar je ESP32 door op de **Upload** knop te drukken in Visual Studio Code.
- Druk hiervoor eerst op het vinkje om je project te compileren, en daarna op het pijltje om het naar je ESP te sturen (zie de screenshot hieronder). Let erop dat als je serial monitor `connecting....` zegt (klik hiervoor op het stekkertje in de onderste balk, zie screenshot hieronder) dan moet je eventjes de **boot** knop van je esp ingedrukt houden zodat je ESP in de juiste boot stand staat om je code te kunnen ontvangen.
  
<img width="433" alt="Screenshot 2024-10-03 at 11 10 00" src="https://github.com/user-attachments/assets/65afddb0-e101-4d0e-a809-56a30a5e2bfa">  

- Nogmaals deze stap doe je met beide ESP's en bij de ene upload je de **Button** code en de andere upload je de **Reciever** code.

## Stap 9: Testen maar!

Als je nu op de knop drukt van je ESP die we net hebben aangesloten, dan zie je dat er bij de andere ESP de ledstrip gaat branden, zonder enige directe verbinding. Ook kan je dit volgen via je feed in AdafruitIO

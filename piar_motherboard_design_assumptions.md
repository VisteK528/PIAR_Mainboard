# Inteligentny Dystrybutor do wody - motherboard założenia

## Główne założenia
1. Wykorzystanie mikrokontolera ESP32-C6-WROOM-1 jako głównego modułu sterującego oraz do komunikacji z aplikacją przez WiFi.
2. Zasilanie z +12V poprzez gniazdo DC (do pracy z pompką i zaworem) oraz +5V z USB-C do samej logiki.
3. Programowanie poprzez złącze USB-C.
4. Możliwość sterowania silnikiem DC (pompką) zasilanym z +12V z poziomu MCU z wykorzystaniem sygnału PWM.
5. Możliwość sterowania elektrozaworem zasilanym z +12V (binarnie).
6. Możliwość sterowania adresowalnymi diodami led z wykorzystaniem interfejsu one wire.
7. Możliwość podłączenia zewnętrznego zasilacza z wykorzystaniem magistrali I2C.
8. Możliwość podłączenia dwóch modułów NFC z wykorzystaniem magistrali SPI.
9. Możliwość nalania wody po przyciśnięciu zewnętrznego przycisku.

## System zasilania
Zgodnie z założeniem (2.) moduł zasilany jest poprzez gniazdo DC jack napięciem +12V. 

Zasilanie to jest rozdzielane na 3 części:
- +12V dla pompki oraz elektrozaworu (max. 1.5A)
- +5V dla adresowalnych diod LED (max. 0.5A)
- +3.3V - (max. 0.7A)
    - MCU - (max. 0.4A)
    - 2x PN532 - (max. 0.3A)
    - Inne - (max. 0.2A)

W sumie zużycie przez poszczególne komponenty wyniesie 2.7A (bez uwzględnienia strat na konwersji napięcia).

Do zmiany napięcia z +12V na +5V wykorzystana zostanie przetwornica LMR33630 (Texas Instruments) o maksymalnym prądzie wyjściowym 3A.

Do zamiany napięcia z +5V wykorzystany zostanie stabilizator liniowy LD29150DT33R (ST Microelectronics) o maksymalnym prądzie wyjściowym 1.5A.


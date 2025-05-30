# Dalmierz laserowy

## Podstawowe informacje

Autor: Krzysztof Płonka 

Data: 07.06.2024 Miejsce: Kraków

### Założenia techniczne:

> 1\. Pomiar odległości z zakresu 0.2 \[m\] – 5 \[m\] 

> 2\. Dobra dokładność(\<0.5 \[cm\])

> 3\. Łatwa oraz intuicyjna obsługa

> 4\. Możliwość łączności bezprzewodowej 

> 5\. Niska cena(cena komercyjna~400 zł) 

> 6\. Kompaktowość

>7\. Długi czas życia na baterii(co najmniej 7 dni)

### Warunki pracy oraz użytkowania

Urządzenie przeznaczone jest do pracy w warunkach takich jak:
>- Budowy

> - Remonty domów mieszkalnych

> - Prace konstrukcyjne, hobbystyczne

Dalmierz jest odporny na wstrząsy, upadki z niewielkiej wysokości oraz
zapylenie.

Poglądowy schemat blokowy

![image](https://github.com/user-attachments/assets/94a0d0fa-1719-4c3d-a049-ed7732ea3088)

Szczegółowy schemat blokowy

![image](https://github.com/user-attachments/assets/b3385fdf-a1fb-4aea-882e-cca114592a5f)

## Elementy składowe układu:

### Mikrokontroler: STM32WB35CCU6A • Cechy:

> • Obsługa Bluetooth • Energooszczędny

> • Niska cena oraz duża dostępność • Integrated SMPS
>
> • Niezbędne interfejsy(SPI, I2C)
>
> • Mała obudowa z dostępem do wyjść(UFQFPN-48)

### Sensor BME280 • Cechy

> • Kompaktowy(mały rozmiar)
>
> • Kompleksowy(jedno urządzenie zapewnia pomiar 3 parametrów) • Tani
>
> • Popularny(łatwo dostępny)
>
> • Prosta obsługa(I2C – istnieje też możliwość komunikacji przez SPI)

### Stabilizator AOZ1280 • Cechy

> • Tani
>
> • Kompaktowy
>
> • Prosty do zaimplementowania w układzie

### Oscylator(wyspecyfikowane przez producenta) • HSE: 32MHz - NX2016_32M

> • LSE: 32.768 kHz - NX2012_32K768

## Budowa układu – opis blokowy układu

### Blok „STM32WB35CCUxA” – układ zawierający mikrokontroler STM32 pokazujący jego integrację z pozostałymi elementami układu

![image](https://github.com/user-attachments/assets/322ddef8-f4fd-4fc4-a45b-7013f13621d2)

### Blok „RF and Antenna block” – blok odpowiedzialny za obwód anteny – dopasowanie impedancyjne, filtrowanie sygnału oraz możliwość fizycznej realizacji anteny potrzebnej do Bluetooth.
> Układ M830520 – ceramic chip antenna – antena 2.4GHZ przeznaczona min. Do Bluetooth

> DLF162500LT – filtr dolno - przepustowy

![image](https://github.com/user-attachments/assets/5f892e76-a78e-443e-88aa-8b4ded7bd489)

### Blok „Power supply ” – blok odpowiedzialny za dostarczenie zasilania 3.3 V

![image](https://github.com/user-attachments/assets/062ce85e-df08-4d21-be1d-04f14b0dee11)

### Blok „BME280” – blok odpowiedzialny za prawidłową komunikację oraz polaryzację i filtrację napięcia zasilania do sensora BME280

![image](https://github.com/user-attachments/assets/25bed0db-99bd-4289-ab59-d1b26f9ba32c)

### Inne bloki układowe zapewniające złącza niezbędne do podłączenia peryferiów (LCD OLED, lasera, przycisków oraz złącze SWD) oraz obwód kontroli stanu naładowania baterii.

![image](https://github.com/user-attachments/assets/c4683929-51e4-4070-bcfa-ae8e0c73e7f2)

## Symulacje

Podczas budowy układu podjęto próbę zaprojektowania układu
przeznaczonego do sterowania diodą laserową. Poniższe wyniki symulacji
są jednak tylko przybliżonym przedstawieniem faktycznego układu
ponieważ, producenci nie udostępniają modeli symulacyjnych diod
laserowych a baza wiedzy na ten temat jest stosunkowo ciężko dostępna. W
poniższym schemacie użyto zastępczo diody LED.
Zaprojektowany obwód:

![image](https://github.com/user-attachments/assets/1b6bffd3-2bf5-4401-9c6f-7a099efe968d)

Na poniższej ilustracji przedstawiono wyniki sygnału wejściowego(pochodzącego mikrokontrolera) oraz prądu diody(docelowo lasera)

![image](https://github.com/user-attachments/assets/769df599-d546-4ff2-ab32-0d99156f2f5d)

Na poniższej ilustracji przedstawiono jakość zboczy sygnałów z poprzedniego slajdu.

![image](https://github.com/user-attachments/assets/3b02beb0-c7da-452e-9e37-104e33a7f9f4)

Na poniższej ilustracji przedstawiono charakterystyki poboru prądu zarówno z zasilania(niebieski przebieg) oraz z portu sterującego(zielony przebieg).

![image](https://github.com/user-attachments/assets/67715dc0-20f0-4a63-8000-75afeefb2115)

## Layout – projektowanie PCB.

Firma która docelowo miałaby podjąć się fabrykacji układu to PCBWAY, a
co za tym idzie wszystkie reguły projektowe zaczerpnięto właśnie z
strony wyżej wymienionego producenta.

Stackup płytki wraz z jego właściwościami przedstawiono poniżej

![image](https://github.com/user-attachments/assets/50158e05-8953-492a-a647-8bc09b9b6ac5)

Zaprojektowany layout PCB:

![image](https://github.com/user-attachments/assets/7bbb16bc-4780-4ec8-b525-c53ea812499e)

Zaprojektowany układ składa się z 4 warstw(opis od góry do dołu):

> - warstwa 1 – warstwa sygnałowa oraz masy

> - warstwa 2 – warstwa masy - GND

> - warstwa 3 – warstwa zasilania – VDD 

> - Warstwa 4 – warstwa sygnałowa

Wygląd – 3D – widok od góry

![image](https://github.com/user-attachments/assets/80e22e23-a1c5-4fc3-85bc-b2756eabacef)

Wygląd -3D – widok od dołu

![image](https://github.com/user-attachments/assets/95af478c-1bd0-40d2-9a97-e5ff640d0085)

### Opis PCB:
![image](https://github.com/user-attachments/assets/2a0e8175-f4e4-4420-9492-b029c650dc57)
 
### Gerbery:

![image](https://github.com/user-attachments/assets/5ff91ae6-563d-4916-96eb-a2c0502009bd)


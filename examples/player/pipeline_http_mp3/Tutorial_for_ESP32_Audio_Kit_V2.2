# Uruchomienie projektu `pipeline_http_mp3` na ESP32 Audio Kit V2.2 (ESP32-A1S + ES8388)

## Wstęp

Płytka ESP32 Audio Kit V2.2 występuje w kilku wersjach sprzętowych. Mój egzemplarz zawiera moduł ESP32-A1S, kodek audio ES8388, dwa wzmacniacze NS4150, 4 MB Flash i 8 MB PSRAM.

Celem było uruchomienie przykładu `pipeline_http_mp3` z pakietu ESP-ADF, który pobiera plik MP3 przez Wi-Fi i odtwarza go przez kodek ES8388.

## Środowisko

Zainstalowane zostały:

* ESP-IDF v5.5.4
* ESP-ADF v2.8
* Python dostarczony przez Espressif
* Narzędzie `idf.py`

Sprawdzenie wersji:

```bat
idf.py --version
git -C C:\Users\barto\esp-adf describe --tags
```

## Ustalenie typu płytki

Wykonano skaner I2C:

```cpp
Wire.begin(33, 32);
```

Znalezione zostało urządzenie:

```text
FOUND 0x10
```

Adres ten odpowiada kodekowi ES8388 używającemu adresacji 7-bitowej.

## Konfiguracja płytki w ESP-ADF

W przykładzie:

```text
esp-adf/examples/player/pipeline_http_mp3
```

wybrano płytkę:

```text
ESP32-Lyrat V4.2
```

Piny okazały się zgodne z ESP32 Audio Kit V2.2:

| Funkcja | GPIO |
| ------- | ---: |
| SDA     |   33 |
| SCL     |   32 |
| MCLK    |    0 |
| BCLK    |   27 |
| LRCK    |   25 |
| DOUT    |   26 |
| DIN     |   35 |

## Brak dźwięku

Mimo poprawnej inicjalizacji:

* kodek ES8388 odpowiadał,
* MP3 było dekodowane,
* Wi-Fi działało,

na głośnikach panowała całkowita cisza.

Przyczyną okazało się niewłączenie wzmacniacza audio NS4150.

## Rozwiązanie

Należy ustawić GPIO21 w stan wysoki:

```c
gpio_reset_pin(GPIO_NUM_21);
gpio_set_direction(GPIO_NUM_21, GPIO_MODE_OUTPUT);
gpio_set_level(GPIO_NUM_21, 1);
```

lub w Arduino:

```cpp
pinMode(21, OUTPUT);
digitalWrite(21, HIGH);
```

GPIO21 pełni funkcję:

```text
PA_ENABLE
```

i włącza wzmacniacze mocy.

Kod został dodany na początku funkcji:

```c
void app_main(void)
```

w pliku:

```text
examples/player/pipeline_http_mp3/main/play_http_mp3_example.c
```

## Konfiguracja Wi-Fi

Przykład `pipeline_http_mp3` pobiera muzykę z Internetu, dlatego konieczne jest skonfigurowanie sieci Wi-Fi:

```bash
idf.py menuconfig
```

Następnie:

```text
Example Configuration -->
    WiFi SSID
    WiFi Password
```

Po zapisaniu konfiguracji wykonujemy:

```bash
idf.py build
idf.py flash monitor
```

## Wynik

Po:

1. ustawieniu GPIO21 = HIGH,
2. skonfigurowaniu Wi-Fi,
3. wgraniu przykładu `pipeline_http_mp3`,

płytka poprawnie:

* łączy się z Wi-Fi,
* pobiera plik MP3,
* dekoduje dźwięk,
* odtwarza muzykę przez kodek ES8388.

## Podsumowanie

Ostatecznie ustalono, że używana płytka to:

* ESP32 Audio Kit V2.2
* Moduł ESP32-A1S
* Kodek ES8388
* 2× wzmacniacz NS4150
* 4 MB Flash
* 8 MB PSRAM

Najważniejszym krokiem, nieopisanym w standardowym przykładzie ESP-ADF, było ręczne włączenie wzmacniacza poprzez ustawienie GPIO21 w stan wysoki.

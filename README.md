# smarthome-ble-tracker
aka BT-Tracker: Wewnątrzbudynkowy system lokalizacji BLE z ESP32

![BT-Tracker Logo]([docs/images/bt_tracker_logo.png](https://avatars.githubusercontent.com/u/153299163?s=400&u=d6d96e79405711cc57ec8d7b0f0e2f7fe290a14e&v=4))  (Zastąp to linkiem do swojego logo)

**BT-Tracker** to *System lokalizacji urządzenia Bluetooth Low Energy (BLE) w czasie rzeczywistym*. Wykorzystuje sieć pięciu urządzeń ESP32 jako węzłów pomiarowych, multilaterację, filtrację oraz uczenie maszynowe do korekty określania pozycji.

## :sparkles: Funkcje

*   **Precyzyjna lokalizacja BLE:** Wykorzystuje RSSI oraz multilaterację do  określania pozycji.
*   **Sieć ESP32:** Oparty na urządzeniach ESP32-C3 jako węzły pomiarowe.
*   **Zaawansowana filtracja:** Filtr Kalmana i filtr medianowy dla poprawy dokładności.
*   **Uczenie maszynowe:**  Modele uczenia maszynowego [SOON] korygują błędy i zwiększają precyzję.
*   **Adaptacyjna kalibracja:** Automatycznie dostosowuje parametry systemu do specyfiki środowiska.
*   **Interfejs graficzny (GUI):** Interfejs w Pythonie do sterowania, wizualizacji i monitorowania.
*   **Komunikacja MQTT/HTTP:** Przesył danych między ESP32 a serwerem.
*   **Dynamiczne identyfikatory urządzeń:** Adres MAC każdego ESP32 jako id.
*   **Trajektoria ruchu:** Wyświetlanie historii ruchu śledzonego urządzenia (wykres/mapa).
*   **Wykres RSSI:**  Monitorowanie RSSI w czasie rzeczywistym dla każdego trackera.

## :gear: Architektura

![System Architecture](docs/images/system_architecture.png)

System składa się z trzech głównych komponentów:

1.  **Węzły ESP32 (Trackerzy):**

    *   Skanują sygnały BLE i mierzą RSSI.
    *   Wstępnie filtrują dane.
    *   Wysyłają dane do serwera.

2.  **Serwer centralny:**

    *   Odbiera dane RSSI od trackerów.
    *   Wykonuje obliczenia multilateracji.
    *   Filtry i modele uczenia maszynowego.
    *   Udostępnia dane do interfejsu graficznego.

3.  **Interfejs graficzny (GUI):**

    *   Umożliwia sterowanie systemem i konfigurację parametrów.
    *   Wyświetla pozycje trackerów i śledzonego urządzenia na mapie.
    *   Wyświetla wykresy RSSI i trajektorię ruchu.
    *   Prezentuje logi i komunikaty systemowe.



## :arrow_down: Instalacja

1.  **Wymagania:**

    *   Python 3.6+
    *   ESP32-C3 Super Mini (najlepiej 5 szt.)
    *   Biblioteki Python (zobacz `requirements.txt`)


2.  **Instalacja bibliotek Python:**

    ```bash
    pip install -r requirements.txt
    ```

3.  **Konfiguracja ESP32:**

    *   Skonfiguruj Wi-Fi na każdym ESP32.
    *   Skonfiguruj adres MAC śledzonego urządzenia.
    *   Wgraj kod do ESP32 (przykładowy kod dostępny w katalogu `esp32/`).

4.  **Konfiguracja serwera:**

    *   Skonfiguruj adresy IP i porty dla MQTT/HTTP.
    *   Skonfiguruj pozycje trackerów (x, y) w pliku konfiguracyjnym.

5.  **Uruchomienie GUI:**

    ```bash
    python gui/main.py
    ```

## :rocket: Użycie

1.  Uruchom wszystkie węzły ESP32.
2.  Uruchom serwer centralny.
3.  Uruchom interfejs graficzny.
4.  Skonfiguruj parametry (txPower, n, interwał skanowania) w GUI.
5.  Kliknij "Start" w GUI, aby rozpocząć śledzenie.
6.  Monitoruj pozycję urządzenia BLE na mapie w GUI.

## :hammer: Konfiguracja

Plik `config.ini` zawiera konfigurację dla serwera centralnego i GUI.  Przykładowe ustawienia:

```ini
[server]
mqtt_broker = mqtt.example.com
mqtt_port = 1883
http_port = 8000

[trackers]
tracker1_x = 0
tracker1_y = 0
tracker2_x = 5
tracker2_y = 0
...
```
:camera: Przykładowe zrzuty ekranu
![alt text](docs/images/gui_screenshot.png)
(Zastąp to linkiem do zrzutu ekranu GUI)
:exclamation: Problemy i rozwiązania
Zakłócenia sygnału RSSI:
Upewnij się, że węzły ESP32 są umieszczone w optymalnych miejscach.
Skalibruj system w docelowym środowisku.
Wypróbuj różne algorytmy filtracji.
Brak połączenia Wi-Fi:
Sprawdź połączenie Wi-Fi na każdym ESP32.
Upewnij się, że serwer jest dostępny.
Niska dokładność:
Skalibruj parametry txPower i n.
Zbierz dane treningowe i wytrenuj model uczenia maszynowego.
Zoptymalizuj algorytm multilateracji.
:handshake: Współpraca
Zapraszamy do zgłaszania uwag, propozycji i poprawek. Utwórz issue lub pull request!
:trophy: Autorzy
YOUR_NAME
:page_facing_up: Licencja
Ten projekt jest udostępniany na licencji MIT License.
:link: Linki
Dokumentacja: LINK_DO_DOKUMENTACJI (Utwórz dokumentację i dodaj link)
Demo: LINK_DO_DEMO (Jeśli masz demo)

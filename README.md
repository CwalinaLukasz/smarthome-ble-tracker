# smarthome-ble-tracker
# BT-Tracker: Precyzyjny System Lokalizacji BLE z ESP32

[![GitHub Stars](https://img.shields.io/github/stars/YOUR_USERNAME/BT-Tracker?style=social)](https://github.com/YOUR_USERNAME/BT-Tracker)
[![GitHub Forks](https://img.shields.io/github/forks/YOUR_USERNAME/BT-Tracker?style=social)](https://github.com/YOUR_USERNAME/BT-Tracker)
[![GitHub Issues](https://img.shields.io/github/issues/YOUR_USERNAME/BT-Tracker)](https://github.com/YOUR_USERNAME/BT-Tracker/issues)
[![GitHub License](https://img.shields.io/github/license/YOUR_USERNAME/BT-Tracker)](https://github.com/YOUR_USERNAME/BT-Tracker/blob/main/LICENSE)

![BT-Tracker Logo](docs/images/bt_tracker_logo.png)  (Zastąp to linkiem do swojego logo)

**BT-Tracker** to zaawansowany system lokalizacji urządzenia Bluetooth Low Energy (BLE) w czasie rzeczywistym. Wykorzystuje sieć pięciu urządzeń ESP32 jako węzłów pomiarowych, multilaterację, zaawansowaną filtrację i uczenie maszynowe, aby zapewnić precyzyjne i niezawodne określanie pozycji. Idealny do zastosowań Smart Home, śledzenia zasobów, i wielu innych.

## :sparkles: Funkcje

*   **Precyzyjna lokalizacja BLE:** Wykorzystuje RSSI i multilaterację do dokładnego określania pozycji.
*   **Sieć ESP32:** Oparty na pięciu urządzeniach ESP32-C3 Super Mini, działających jako węzły pomiarowe.
*   **Zaawansowana filtracja:** Filtr Kalmana i filtr medianowy eliminują zakłócenia i poprawiają dokładność.
*   **Uczenie maszynowe:**  Modele uczenia maszynowego (np. regresja liniowa, lasy losowe) korygują błędy i zwiększają precyzję.
*   **Adaptacyjna kalibracja:** Automatycznie dostosowuje parametry systemu do specyfiki środowiska.
*   **Interfejs graficzny (GUI):** Intuicyjny interfejs w Pythonie do sterowania, wizualizacji i monitorowania.
*   **Komunikacja MQTT/HTTP:** Elastyczny i niezawodny przesył danych między ESP32 a serwerem.
*   **Dynamiczne identyfikatory urządzeń:** Wykorzystanie adresu MAC każdego ESP32 jako unikalnego identyfikatora.
*   **Trajektoria ruchu:** Wyświetlanie historii ruchu śledzonego urządzenia.
*   **Wykres RSSI:**  Monitorowanie siły sygnału w czasie rzeczywistym dla każdego trackera.

## :gear: Architektura

System składa się z trzech głównych komponentów:

1.  **Węzły ESP32 (Trackerzy):**

    *   Skanują sygnały BLE i mierzą RSSI.
    *   Wstępnie filtrują dane za pomocą filtru Kalmana.
    *   Wysyłają dane do serwera przez MQTT lub HTTP w formacie JSON.

2.  **Serwer centralny:**

    *   Odbiera dane RSSI od trackerów.
    *   Wykonuje obliczenia multilateracji.
    *   Stosuje filtry i modele uczenia maszynowego.
    *   Udostępnia dane do interfejsu graficznego.

3.  **Interfejs graficzny (GUI):**

    *   Umożliwia sterowanie systemem i konfigurację parametrów.
    *   Wyświetla pozycje trackerów i śledzonego urządzenia na mapie.
    *   Wyświetla wykresy RSSI i trajektorię ruchu.
    *   Prezentuje logi i komunikaty systemowe.

![System Architecture](docs/images/system_architecture.png) (Zastąp to linkiem do diagramu architektury)

## :arrow_down: Instalacja

1.  **Wymagania:**

    *   Python 3.6+
    *   ESP32-C3 Super Mini (5 szt.)
    *   Biblioteki Python (zobacz `requirements.txt`)
    *   Broker MQTT (opcjonalny, jeśli używasz MQTT)

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

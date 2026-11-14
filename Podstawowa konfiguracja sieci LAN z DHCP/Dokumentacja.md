
<div align="center">

# 🌐 Cisco Packet Tracer – Laboratoria Sieciowe

### Sprawozdanie nr 01: Podstawowa sieć LAN z serwerem DHCP i Wi-Fi

![Cisco](https://img.shields.io/badge/Cisco-Packet_Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![Network](https://img.shields.io/badge/Topologia-LAN_%2B_WLAN-2EA44F?style=for-the-badge)
![Protocol](https://img.shields.io/badge/Usługi-DHCP_%7C_ICMP_%7C_WPA2-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status_Badań-Zakończone_Sukcesem-brightgreen?style=for-the-badge)

</div>

<br>

> [!NOTE]
> Repozytorium zawiera dokumentację oraz zrzuty ekranu z praktycznych ćwiczeń (labów) realizowanych w środowisku **Cisco Packet Tracer**. Każdy projekt prezentuje krok po kroku budowę topologii, proces konfiguracji urządzeń sieciowych oraz wyniki przeprowadzonych testów łączności (badań).

---

## 📑 Spis treści

- [📌 Opis i założenia projektu](#-opis-i-założenia-projektu)
- [🗺️ Parametry i architektura sieci](#️-parametry-i-architektura-sieci)
- [🖼️ Topologia sieci](#️-topologia-sieci)
- [🔬 Opis i wyniki badań (Testy)](#-opis-i-wyniki-badań-testy)
  - [1. Weryfikacja automatycznego przydzielania adresów (DHCP)](#1-weryfikacja-automatycznego-przydzielania-adresów-dhcp)
  - [2. Badanie łączności z drukarką sieciową (Statyczne IP)](#2-badanie-łączności-z-drukarką-sieciową-statyczne-ip)
  - [3. Weryfikacja komunikacji między podsieciami (Wi-Fi ↔ LAN)](#3-weryfikacja-komunikacji-między-podsieciami-wi-fi--lan)

---

## 📌 Opis i założenia projektu

Celem ćwiczenia było zaprojektowanie i uruchomienie symulacji sieci dla małego biura. Projekt zakładał podział infrastruktury na dwa odizolowane od siebie segmenty – **sieć przewodową** dla stacji roboczych i drukarki oraz **sieć bezprzewodową** dla urządzeń mobilnych, aby zwiększyć bezpieczeństwo lokalnych zasobów.

W ramach konfiguracji główny router (**Cisco 2911**) został skonfigurowany jako bramka domyślna dla obu podsieci oraz jako serwer **DHCP** automatycznie przydzielający adresację IP klientom. Dla drukarki sieciowej zastosowano **adresację statyczną** spoza puli DHCP, aby zagwarantować jej stałą dostępność w sieci.

---

## 🗺️ Parametry i architektura sieci

| Segment sieci | Podsieć / Maska | Bramka domyślna | Przydział adresów | Urządzenia w segmencie |
| :--- | :--- | :--- | :--- | :--- |
| **🔌 Sieć przewodowa (LAN)** | `192.168.1.0/24` | `192.168.1.1` | Dynamiczny (`DHCP`) + Statyczny | 3× PC, 1× Drukarka (`192.168.1.100`) |
| **📶 Sieć bezprzewodowa (Wi-Fi)** | `192.168.2.0/24` | `192.168.2.1` | Dynamiczny (`DHCP`) | 1× Laptop (`WPC300N`, `WPA2-Personal`) |

---

## 🖼️ Topologia sieci

<div align="center">

![Topologia sieci LAN i Wi-Fi](sciezka/do/zdjecia_topologii.png)

*<sub><b>Rys. 1.</b> Schemat połączeń w programie Cisco Packet Tracer przedstawiający podział na sieć przewodową (po lewej) oraz bezprzewodową (po prawej).</sub>*

</div>

---

## 🔬 Opis i wyniki badań (Testy)

### 1. Weryfikacja automatycznego przydzielania adresów (DHCP)

> [!TIP]
> **Cel badania:** Sprawdzenie, czy router poprawnie rozgłasza pule adresowe `wiredLAN` oraz `wirelessLAN` i czy urządzenia końcowe otrzymują właściwe parametry sieciowe (adres IP, maskę podsieci oraz bramkę domyślną).

* **Przebieg i wynik:** Wszystkie trzy komputery PC podłączone do przełącznika poprawnie pobrały adresy z zakresu `192.168.1.x` z bramką `192.168.1.1`. Laptop po zamontowaniu modułu `WPC300N` i uwierzytelnieniu w sieci Wi-Fi (`WPA2-Personal`) otrzymał adres z puli `192.168.2.x` z bramką `192.168.2.1`.

<div align="center">

![Wynik DHCP na komputerze](sciezka/do/zdjecia_dhcp.png)

*<sub><b>Rys. 2.</b> Poprawne pobranie konfiguracji sieciowej z serwera DHCP na stacji roboczej.</sub>*

</div>

---

### 2. Badanie łączności z drukarką sieciową (Statyczne IP)

> [!TIP]
> **Cel badania:** Drukarce przypisano na stałe adres `192.168.1.100`. Z poziomu wiersza poleceń (*Command Prompt*) na komputerze PC wykonano test komunikacji za pomocą protokołu ICMP (`ping 192.168.1.100`), aby potwierdzić poprawność routingu i dostępność urządzenia w sieci lokalnej.

* **Przebieg i wynik:** Test zakończył się pełnym sukcesem (**0% utraconych pakietów**). Drukarka odpowiada na zapytania ze wszystkich urządzeń w sieci.

<div align="center">

![Wynik polecenia ping](sciezka/do/zdjecia_ping.png)

*<sub><b>Rys. 3.</b> Rezultat polecenia ping potwierdzający poprawną komunikację z drukarką sieciową.</sub>*

</div>

---

### 3. Weryfikacja komunikacji między podsieciami (Wi-Fi ↔ LAN)

> [!TIP]
> **Cel badania:** Przeprowadzono test przesyłania pakietów (symulacja `PDU` / polecenie `ping`) pomiędzy laptopem w sieci bezprzewodowej (`192.168.2.0/24`) a komputerem w sieci przewodowej (`192.168.1.0/24`), aby sprawdzić działanie routingu na routerze Cisco 2911.

* **Przebieg i wynik:** Po pierwszym pakiecie `ARP` wymiana danych przebiegła bez zakłóceń. Oba segmenty sieci komunikują się ze sobą poprawnie za pośrednictwem bramek domyślnych.

<div align="center">

![Test komunikacji między sieciami](sciezka/do/zdjecia_pdu.png)

*<sub><b>Rys. 4.</b> Status "Successful" w panelu symulacji potwierdzający prawidłowy przepływ pakietów między siecią bezprzewodową a przewodową.</sub>*

</div>

---

<div align="center">

⬅️ **[Powrót do głównego katalogu projektów](../README.md)**

</div>

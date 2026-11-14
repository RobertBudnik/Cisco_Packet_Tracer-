# 🌐 Cisco Packet Tracer – Laboratorium 01
### Podstawowa sieć LAN z serwerem DHCP i Wi-Fi

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco_Packet_Tracer-v8.2+-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)
![DHCP](https://img.shields.io/badge/Protokół-DHCP-2EA44F?style=for-the-badge)
![Wi-Fi](https://img.shields.io/badge/Sieć-Wi--Fi_WPA2-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Ukończono-success?style=for-the-badge)

> Repo stanowi sprawozdanie z ćwiczenia laboratoryjnego obejmującego projektowanie, segmentację oraz testy łączności w małej sieci biurowej.

---

## 📌 Opis i założenia projektu

Celem ćwiczenia było zaprojektowanie i uruchomienie symulacji sieci dla małego biura. Projekt zakładał podział infrastruktury na **dwa odizolowane od siebie segmenty** – sieć przewodową dla stacji roboczych i drukarki oraz sieć bezprzewodową dla urządzeń mobilnych, aby zwiększyć bezpieczeństwo lokalnych zasobów.

> [!NOTE]
> Główny router (**Cisco 2911**) pełni rolę bramki domyślnej dla obu podsieci oraz serwera **DHCP** automatycznie przydzielającego adresację IP klientom. Dla drukarki sieciowej zastosowano adresację statyczną spoza puli DHCP, aby zagwarantować jej stałą dostępność w sieci.

### 📊 Schemat adresacji i segmentacji

| Segment sieci | Podsieć / Maska | Bramka domyślna | Sposób adresacji | Podłączone urządzenia |
| :--- | :--- | :--- | :--- | :--- |
| **Wired LAN** *(Przewodowa)* | `192.168.1.0/24` | `192.168.1.1` | DHCP + Statyczne IP | 3x PC, 1x Drukarka sieciowa |
| **Wireless LAN** *(Wi-Fi)* | `192.168.2.0/24` | `192.168.2.1` | DHCP | 1x Laptop (moduł `WPC300N`) |

---

## 🖼️ Topologia sieci

![Topologia sieci LAN i Wi-Fi](images/topologia.png)

*Rys. 1. Schemat połączeń w programie Cisco Packet Tracer przedstawiający podział na sieć przewodową (po lewej) oraz bezprzewodową (po prawej).*

---

## 🔬 Opis i wyniki badań

### 1. Weryfikacja automatycznego przydzielania adresów (DHCP)

* **Cel badania:** Sprawdzenie, czy router poprawnie rozgłasza pule adresowe `wiredLAN` oraz `wirelessLAN` i czy urządzenia końcowe otrzymują właściwe parametry sieciowe (adres IP, maskę podsieci oraz bramkę domyślną).
* **Przebieg i wynik:** Wszystkie trzy komputery PC podłączone do przełącznika poprawnie pobrały adresy z zakresu `192.168.1.x` z bramką `192.168.1.1`. Laptop po zamontowaniu modułu `WPC300N` i uwierzytelnieniu w sieci Wi-Fi (`WPA2-Personal`) otrzymał adres z puli `192.168.2.x` z bramką `192.168.2.1`.

![Wynik DHCP na komputerze](images/dhcp.png)

*Rys. 2. Poprawne pobranie konfiguracji sieciowej z serwera DHCP na stacji roboczej.*

---

### 2. Badanie łączności z drukarką sieciową (Statyczne IP)

* **Cel badania:** Weryfikacja dostępności drukarki ze stałym adresem IP (`192.168.1.100`) z poziomu stacji roboczych w sieci lokalnej.
* **Przebieg i wynik:** Z poziomu wiersza poleceń (*Command Prompt*) na komputerze PC wykonano test komunikacji za pomocą protokołu ICMP (`ping 192.168.1.100`). Test zakończył się pełnym sukcesem (**0% utraconych pakietów**).

![Wynik polecenia ping](images/ping.png)

*Rys. 3. Rezultat polecenia ping potwierdzający poprawną komunikację z drukarką sieciową.*

---

### 3. Weryfikacja komunikacji między podsieciami (Wi-Fi ↔ LAN)

* **Cel badania:** Sprawdzenie działania routingu na routerze Cisco 2911 pomiędzy dwoma odseparowanymi segmentami sieci.
* **Przebieg i wynik:** Przeprowadzono test przesyłania pakietów (symulacja PDU / polecenie `ping`) pomiędzy laptopem w sieci bezprzewodowej (`192.168.2.0/24`) a komputerem w sieci przewodowej (`192.168.1.0/24`). Po pierwszym pakiecie ARP wymiana danych przebiegła bez zakłóceń.

![Test komunikacji między sieciami](images/pdu.png)

*Rys. 4. Status "Successful" w panelu symulacji potwierdzający prawidłowy przepływ pakietów między siecią bezprzewodową a przewodową.*

---

> [!TIP]
> **Wskazówka do repozytorium:** Upewnij się, że Twoje zrzuty ekranu znajdują się w podfolderze `images/` i nazywają się dokładnie tak, jak w linkach powyżej (`topologia.png`, `dhcp.png`, `ping.png`, `pdu.png`), aby GitHub automatycznie je wyświetlił.

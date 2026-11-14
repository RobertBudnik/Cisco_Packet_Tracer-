[g_wny_plik_readme_repozytorium (1).md](https://github.com/user-attachments/files/34860957/g_wny_plik_readme_repozytorium.1.md)
<div align="center">

# 🌐 Cisco Packet Tracer
### Dokumentacja Badań i Projektów Sieciowych

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco_Packet_Tracer-8.2%2B-049FD9?style=for-the-badge&logo=cisco&logoColor=white)
![Networking](https://img.shields.io/badge/Networking-Lab_Reports-2EA44F?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Aktywny_Rozwój-orange?style=for-the-badge)

</div>

---

> [!NOTE]
> Repozytorium stanowi zbiór sprawozdań, analiz oraz dokumentacji wizualnej z ćwiczeń laboratoryjnych realizowanych w środowisku **Cisco Packet Tracer**. Każdy folder odpowiada osobnemu zagadnieniu sieciowemu i zawiera opis założeń projektowych, zrzuty ekranu topologii oraz szczegółowe wyniki przeprowadzonych badań łączności i poprawności konfiguracji.

---

## 🎯 Cel repozytorium

Głównym celem tego zbioru jest udokumentowanie praktycznego działania protokołów i urządzeń sieciowych w kontrolowanym środowisku symulacyjnym. Zamiast surowych plików konfiguracyjnych, każdy projekt skupia się na trzech filarach:

* 📐 **Analizie architektury sieci** – doborze odpowiednich urządzeń, okablowania oraz podziale na podsieci.
* 🖼️ **Dokumentacji wizualnej** – zrzutach ekranu przedstawiających schematy połączeń oraz stan interfejsów.
* 🔬 **Opisie badań i testów** – weryfikacji działania usług (m.in. `DHCP`, routing, komunikacja bezprzewodowa) za pomocą narzędzi diagnostycznych (`ping`, symulacja pakietów `PDU`).

---

## 📁 Katalog projektów (Spis sprawozdań)

Poniżej znajduje się lista zrealizowanych laboratoriów. Kliknięcie w nazwę projektu przeniesie Cię bezpośrednio do folderu ze szczegółowym opisem badań oraz galerią zrzutów ekranu.

| Nr | Projekt / Sprawozdanie | Zakres badań | Przeprowadzone testy | Status |
| :---: | :--- | :--- | :--- | :---: |
| **01** | [**Podstawowa sieć LAN z serwerem DHCP i Wi-Fi**](./01-basic-lan-dhcp/) | Projektowanie małej sieci biurowej z podziałem na segment przewodowy (`192.168.1.0/24`) oraz bezprzewodowy (`192.168.2.0/24`). | Weryfikacja automatycznego przydzielania adresów IP przez serwer DHCP (Cisco 2911), badanie dostępności drukarki ze statycznym IP oraz testy komunikacji między sieciami (`Wi-Fi ↔ LAN`). | ✅ Ukończono |
| **02** | *Kolejny projekt w przygotowaniu...* | *Miejsce na krótki opis założeń kolejnego laboratorium (np. konfiguracja sieci VLAN i routingu między nimi).* | *Opis głównych testów weryfikacyjnych.* | 🚧 W trakcie |

---

## 🗂️ Organizacja folderów

Każdy projekt w repozytorium posiada ujednoliconą strukturę, ułatwiającą nawigację i przeglądanie wyników badań:

```text
cisco-packet-tracer-labs/
├── 📄 README.md                  # Główny opis repozytorium i spis projektów (ten plik)
├── 📁 01-basic-lan-dhcp/         # Folder pierwszego sprawozdania
│   ├── 📄 README.md              # Szczegółowy opis projektu, przebieg badań i wyniki
│   └── 🖼️ images/                # Zrzuty ekranu (topologia, wyniki poleceń ping, DHCP)
└── 📁 02-kolejny-projekt/        # Miejsce na następne laboratorium
    ├── 📄 README.md
    └── 🖼️ images/
```

---

## 🛠️ Środowisko badawcze

Wszystkie przedstawione w repozytorium symulacje, pomiary oraz testy przepływu pakietów zostały wykonane przy użyciu oprogramowania **Cisco Packet Tracer** (wersja `8.2` lub nowsza) z wykorzystaniem wirtualnych odpowiedników rzeczywistego sprzętu sieciowego:

* **Routery:** seria Cisco `2911`
* **Przełączniki warstwy dostępowej:** seria Cisco `2960`
* **Sieci bezprzewodowe:** punkty dostępowe Wi-Fi (`Linksys WRT300N`) oraz moduły bezprzewodowe (`WPC300N`)

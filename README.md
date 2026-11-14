🌐 Cisco Packet Tracer – Dokumentacja Badań i Projektów Sieciowych
Repozytorium stanowi zbiór sprawozdań, analiz oraz dokumentacji wizualnej z ćwiczeń laboratoryjnych realizowanych w środowisku Cisco Packet Tracer. Każdy folder w tym repozytorium odpowiada osobnemu zagadnieniu sieciowemu i zawiera opis założeń projektowych, zrzuty ekranu topologii oraz szczegółowe wyniki przeprowadzonych badań łączności i poprawności konfiguracji.

🎯 Cel repozytorium
Głównym celem tego zbioru jest udokumentowanie praktycznego działania protokołów i urządzeń sieciowych w kontrolowanym środowisku symulacyjnym. Zamiast surowych plików konfiguracyjnych, każdy projekt skupia się na:
Analizie architektury sieci – doborze odpowiednich urządzeń, okablowania oraz podziale na podsieci.
Dokumentacji wizualnej – zrzutach ekranu przedstawiających schematy połączeń oraz stan interfejsów.
Opisie badań i testów – weryfikacji działania usług (m.in. DHCP, routing, komunikacja bezprzewodowa) za pomocą narzędzi diagnostycznych (ping, symulacja pakietów PDU).

📁 Katalog projektów (Spis sprawozdań)
Poniżej znajduje się lista zrealizowanych laboratoriów. Kliknięcie w nazwę projektu przeniesie Cię do folderu ze szczegółowym opisem badań oraz galerią zrzutów ekranu.
01. Podstawowa sieć LAN z serwerem DHCP i Wi-Fi
Zakres badań: Projektowanie małej sieci biurowej z podziałem na segment przewodowy (192.168.1.0/24) oraz bezprzewodowy (192.168.2.0/24).
Przeprowadzone testy: Weryfikacja automatycznego przydzielania adresów IP przez serwer DHCP na routerze Cisco 2911, badanie dostępności drukarki ze statycznym adresem IP oraz testy komunikacji między sieciami (Wi-Fi ↔ LAN).
02. Kolejny projekt w przygotowaniu...
Zakres badań: Miejsce na krótki opis założeń kolejnego laboratorium (np. konfiguracja sieci VLAN i routingu między nimi).
Przeprowadzone testy: Opis głównych testów weryfikacyjnych.

🗂️ Organizacja folderów
Każdy projekt w repozytorium posiada ujednoliconą strukturę, ułatwiającą przeglądanie wyników badań:
cisco-packet-tracer-labs/
├── README.md                  # Główny opis repozytorium i spis projektów (ten plik)
├── 01-basic-lan-dhcp/         # Folder pierwszego sprawozdania
│   ├── README.md              # Szczegółowy opis projektu, przebieg badań i wyniki
│   └── images/                # Zrzuty ekranu (topologia, wyniki poleceń ping, DHCP)
└── 02-kolejny-projekt/        # Miejsce na następne laboratorium
    ├── README.md
    └── images/

🛠️ Środowisko badawcze
Wszystkie przedstawione w repozytorium symulacje, pomiary oraz testy przepływu pakietów zostały wykonane przy użyciu oprogramowania Cisco Packet Tracer (wersja 8.2 lub nowsza) z wykorzystaniem wirtualnych odpowiedników rzeczywistego sprzętu sieciowego (routery serii 2911, przełączniki warstwy dostępowej 2960 oraz punkty dostępowe Wi-Fi).

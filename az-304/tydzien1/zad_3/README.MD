zad 3

Ponieważ już poznałeś nieco model ról, model polityk, model subskrypcji, napisz krótki dokument, najlepiej w punktach, w którym:
opiszesz krótko jak działa IT w firmie - najważniejsze rzeczy

Dział IT w większych organizacjach podzielony jest kilka- kilkanaście jednostek zajmujących się konkretnymi tematami takimi jak: 
* System, IaaS Compute and Storage
* Network and Unified Communication
* Application Development and Integration Platforms
* Data Management and Data Platforms
* Application Security and Data Protection
* Data&Analytics/BI
* Digital Workspace
* Service desk


przygotujesz krótki podział mgmt group oraz subksrypcji z uzasadnieniem dlaczego tak to chcesz budować

* Grupa zarządzająca główna
  * grupy zarządzające administracyjne dotyczące platformy (zarządzenie siecią, zarządzanie zasobami, zarządzanie tożsamościami)
    * osobne subskrypcje dla każdego obszaru zarządzania
  * grupy zarządzające aplikacje korporacyjne dla poszczególnych działów (HR, etc.) 
    * osobne management group dla każdego działu
    * osobne subskrypcje dla każdego systemu
  * grupa zarządzająca sandbox’y 
    * osobne subskrypcje dla poszczególnych aplikacji 
  * grupa zarządzająca automatyzacja


przygotujesz krótki opis ról, które chcesz by występowały w organizajci z krótkim opisem zadań każdej z nich

SysOps - role związane z obsługą infrastruktury serwerowo-systemowej, np:
* Virtual Machines administrator 
* Storage Account Contributor administrator
* Backup Contributor
* CosmosDB  / SQL DB Operator
NetOps - role związane z siecią i obsługa sieci: 
* Network Contributor
SecOps – role związane z bezpieczeństwem np
* Key Vault Administrator
* Monitoring Contributor
* Security Admin
DevOps
* Azure K8s Admin
* Logic App Operator/Contributor
Funkcyjne dla działów które korzystają z konkretnych aplikacji/systemów.

przygotujesz krótki opis wybranych polityk, które są dla Ciebie najważniejsze. uzasdnij swój wybór

* Organizacyjne, jako zwiększające poziom organizacji i czytelności zasobów w firmie
  * Konwencja nazewnicza – wymuszenie stosowania konwencji nazewniczej dla zasobów w Azure
* Ograniczające koszty, jako polityki które trzymają koszty w ryzach, blokując przypadkowe lub nieświadome wybieranie drogich zasobów których organizacja nie potrzebuje
  * Ograniczenie użycia określonych zasobów – wykluczenie zasobów lub rozmiarów pewnych zasobów (VM, storage) które organizacja nie będzie korzystała np. ze względu na wysokie koszty
  * Wykluczenie lokalizacji których organizacja nie będzie korzystać
* Zapewniające podstawowe bezpieczeństwo środowiska. Zapewnienie bezpieczeństwa jest kluczowym kryterium w każdej firmie, 
  * Audyt szyfrowanie dysków – bezpieczeństwo danych musi być zapewnione od samego początku stworzenia VM
  * Wymuszenie instalacja rozszerzenie antymalware – podobnie jak wyżej, podstawowe zasady bezpieczeństwa
  * Weryfikacja czy usługi które są zbędne nie są zainstalowane 
  * Audyt włączenia Azure Backup do VM 
  * Weryfikacja zainstalowanych pożądanych usług 

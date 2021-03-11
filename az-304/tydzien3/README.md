## Zadanie domowe

Zaprojektuj system, który pozwoli na obsłużenie komunikacji z systemów monitorujących system produkcji żywności. Klient posiada serwery on-premises, które zbierają dane z systemów Scada (systemy do monitorowania procesów automatyki) znajdujących się lokalizacjach klienta. Aktualne rozwiązanie jest w stanie publikować dane wykorzystując API Kafki. System zbiera dwa rodzaje komunikatów - dane telemetryczne oraz dane na temat cyklu życia urządzeń. Encje telemetryczne są JSON’ami o rozmiarze do 4 KB i są generowane z częstotliwością 5 Hz. Dane dotyczące cyklu życia urządzenia są encjami przekazywanych w formacie JSON, które mają rozmiar 2 KB i są generowane w momencie pojawienia się odpowiedniego zdarzenia na urządzeniu.

## Wymagania użytkownika

1. Dostęp do danych telemetrycznych w czasie rzeczywistym w postaci dedykowanej wizualizacji lub raportu.

2. Informacje w trybie rzeczywistym na temat przyjścia danych dotyczących cyklu życia urządzenia, przesyłane w postaci e-maila dla obsługi.

3. Możliwość podpięcia dowolnego serwisu, wystawionego w kontenerze pod przychodzący strumień danych (np. Aplikacje subskrybującą się na dane telemetryczne z unikalnym widokiem na dane), które zwrócą przetworzone dane i umieszczą w dedykowanym topicu, z którego aplikacje z warstwy prezentacji będą w stanie odczytać przetworzone dane i zaprezentować użytkownikowi.

4. W warstwie prezentacji danych znajdzie się baza relacyjna oraz aplikacja webowa osadzona w usłudze PaaS.

5. Dostęp dla firm zewnętrznych będzie zrealizowany za pomocą API, które będzie w bezpieczny sposób udostępnione na zewnątrz

W ramach prac zaprojektuj rozwiązanie oraz stwórz proste PoC (proof of concept) pokazujące możliwości działania tego systemu.


![alt text](https://github.com/mzdzioch/szkolachmury/blob/main/az-304/tydzien3/Szkola%20chmury%20AZ-304%20Event%20Driven.png)

## #TYDZIEŃ5.1 
„Dla każdego typu Storage, którego się nauczyłeś w czasie kursu (min. 4 typy) dobierz dwa dobre i jedno złe zastosowanie. Chciałbym byś zweryfikował różne możliwości składowania danych w Azure i opowiedział, kiedy i do czego te możliwości możesz wykorzystać.”

#### Odpowiedź:
Azure Blob 
 * Dobre zastosowanie: przechowywanie zdjęć sprzedawanych produktów, streaming video reklamujących produkt, przechowywanie dokumentacji np. instrukcji, regulaminów itp. , przechowywanie backup
 * Złe zastosowanie: pliki współdzielone

Azure File
 * Dobre zastosowanie: pliki do współdzielenia z innymi użytkownikami, 
 * Złe zastosowanie: przechowywanie plików video

Azure Queue 
 * Dobre zastosowanie: aplikacja budowana w stylu „decoupled”, wymiana danych z systemami partnerów, integracja z innymi systemami wewnętrznymi
 * Złe zastosowanie: Musimy mieć zagwarantowany porządek wiadomości „FIFO”

Azure Table
 * Dobre zastosowanie: zapisywanie danych w prostych tabelach które nie potrzebują klucza obcego, wykonywania złożonych zapytań, np. przechowywanie logów czy danych diagnostycznych
 * Złe zastosowanie: potrzebujemy relacji pomiędzy tabelami w bazie danych, wykonywania zaawansowanych zapytań


## #TYDZIEŃ5.2
„Wymień jeden dobry i jeden zły przykład wykorzystania StorSimple w swojej organizacji. Napisz, kiedy i w jakich scenariuszach się sprawdzi, a kiedy nie.”

#### Odpowiedź:

Dobre:
Archiwum, Disk-based backup, SharePoint, serwer plików

Złe zastosowanie: 
Real time application, baza danych wysokiej wydajności





## #TYDZIEŃ5.3
„Liczymy Koszty :). Umówmy się. Twój system backupu (nie ma znaczenia jaki) składuje 1TB nowych danych każdego dnia. Wykorzystujesz oczywiście Azure do tej operacji i chcesz dane składować jak najtaniej. Przez dwa lata nie kasujesz zebranych danych. Po dwóch latach na próbę odtwarzasz dane z ostatniego dnia każdego roku. Po 3 roku kasujesz dane, zebrane w roku pierwszym.

 * Ile łącznie wygenerujesz kosztów w ramach tej usługi, jeśli rozważymy pełny, 6 letni okres jej działania.
 * Rozważ różne aspekty i różne możliwości usług i pokaż jako algorytm liczenia przyjąłeś.


#### Odpowiedź:

Założenia:
* Składujemy backup na Azure Storage
* Backup: 
  * Dziennie: 1TB 
  * Miesięcznie: 30 TB
  * Rocznie: 365 TB
* Czas trwania: 6 lat
* Retencja 3 lata, po 3 latach usuwamy to co starsze
* 1 miesiąc = 30 dni, 1 Rok = 365 dni

Ilość wygenerowanych danych:
Rok 1: 365 TB
Rok 2: 730 TB
Rok 3: 1095 TB 
Rok 4: 1095 TB (po roku 3 usuwamy dane z roku 1)
Rok 5: 1095 TB (po roku 4 usuwamy dane z roku 2)
Rok 6: 1095 TB (po roku 5 usuwamy dane z roku 3)

Wygenerowane koszty:

Założenia:
* Cena za 1TB = 1,84 USD miesięcznie zaczerpnięta z kalkulatora Azure przy poniższych parametrach:
  * Region: West Europe
  * Typ: Magazyn blob storage
  * Warstwa wydajności: Standard
  * Type konta magazynu: Ogólnego przeznaczenia, V2
  * Nadmiarowość: LRS
  * Warstwa dostępu: Archiwum
  * Wszelkie operacje zapisu/odczytu nie są brane pod uwagę przy wyliczeniu kosztu składowania 1TB


Rok 1: 2340 TB x 1,84 USD = 4'305,60 USD\
Rok 2: (12 x 360 TB + 2340 TB) x 1,84 USD =  12'254,40 USD\
Rok 3: (12 x 2 x 360 TB + 2340 TB) x 1,84 USD = 20'203,20 USD\
Rok 4: (12 x 2 x 360 TB + 2340 TB) x 1,84 USD = 20'203,20 USD\
Rok 5: (12 x 2 x 360 TB + 2340 TB) x 1,84 USD = 20'203,20 USD\
Rok 6: (12 x 2 x 360 TB + 2340 TB) x 1,84 USD = 20'203,20 USD\

Wyjaśnienie: 

W roku 1, płacimy za przechowywane dane w nastęujący sposób:

Miesiąc 1: 30 TB x 1,84 USD

Miesiąc 2: 60 TB x 1,84 USD

Miesiąc 2: 90 TB x 1,84 USD

(...)

Miesiąc 12: 360 TB x 1,84 USD

Z sumy ciągów wyliczamy ilość jednostek TB za które płacimy w ciągu roku 12 x (30 + 360)/2 = 2340TB

W roku 2, płacimy za każdy miesiąc przechowywania danych zebranych w 1 roku i inkrementalnie przyrastającymi danymi w ciągu roku 2 czyli 2340 TB

W roku 3, podobnie jak w roku 2 tylko płacimy za dane zebrane z dwóch ostatnich lat czyli za 2x360TB plus dane inkrementalne w ciągu roku 3 czyli 2340 TB. 



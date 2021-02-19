## #TYDZIE�5.1 
�Dla ka�dego typu Storage, kt�rego si� nauczy�e� w czasie kursu (min. 4 typy) dobierz dwa dobre i jedno z�e zastosowanie. Chcia�bym by� zweryfikowa� r�ne mo�liwo�ci sk�adowania danych w Azure i opowiedzia�, kiedy i do czego te mo�liwo�ci mo�esz wykorzysta�.�

#### Odpowied�
Azure Blob 
 * Dobre zastosowanie: przechowywanie zdj�� sprzedawanych produkt�w, streaming video reklamuj�cych produkt, przechowywanie dokumentacji np. instrukcji, regulamin�w itp. , przechowywanie backup
 * Z�e zastosowanie: pliki wsp�dzielone
Azure File
 * Dobre zastosowanie: pliki do wsp�dzielenia z innymi u�ytkownikami, 
 * Z�e zastosowanie: przechowywanie plik�w video
Azure Queue 
 * Dobre zastosowanie: aplikacja budowana w stylu �decoupled�, wymiana danych z systemami partner�w, integracja z innymi systemami wewn�trznymi
 * Z�e zastosowanie: Musimy mie� zagwarantowany porz�dek wiadomo�ci �FIFO�
Azure Table
 * Dobre zastosowanie: zapisywanie danych w prostych tabelach kt�re nie potrzebuj� klucza obcego, wykonywania z�o�onych zapyta�, np. przechowywanie log�w czy danych diagnostycznych
 * Z�e zastosowanie: potrzebujemy relacji pomi�dzy tabelami w bazie danych, wykonywania zaawansowanych zapyta�


## #TYDZIE�5.2
�Wymie� jeden dobry i jeden z�y przyk�ad wykorzystania StorSimple w swojej organizacji. Napisz, kiedy i w jakich scenariuszach si� sprawdzi, a kiedy nie.�

Dobre:
Archiwum, Disk-based backup, SharePoint, serwer plik�w

Z�e zastosowanie: 
Real time application, baza danych wysokiej wydajno�ci


#### Odpowied�


## #TYDZIE�5.3
�Liczymy Koszty :). Um�wmy si�. Tw�j system backupu (nie ma znaczenia jaki) sk�aduje 1TB nowych danych ka�dego dnia. Wykorzystujesz oczywi�cie Azure do tej operacji i chcesz dane sk�adowa� jak najtaniej. Przez dwa lata nie kasujesz zebranych danych. Po dw�ch latach na pr�b� odtwarzasz dane z ostatniego dnia ka�dego roku. Po 3 roku kasujesz dane, zebrane w roku pierwszym.

 * Ile ��cznie wygenerujesz koszt�w w ramach tej us�ugi, je�li rozwa�ymy pe�ny, 6 letni okres jej dzia�ania.
 * Rozwa� r�ne aspekty i r�ne mo�liwo�ci us�ug i poka� jako algorytm liczenia przyj��e�.


#### Odpowied�

Za�o�enia:
* Sk�adujemy backup na Azure Storage
* Backup: 
  * Dziennie: 1TB 
  * Miesi�cznie: 30 TB
  * Rocznie: 365 TB
* Czas trwania: 6 lat
* Retencja 3 lata, po 3 latach usuwamy to co starsze
* 1 miesi�c = 30 dni, 1 Rok = 365 dni

Ilo�� wygenerowanych danych:
Rok 1: 365 TB
Rok 2: 730 TB
Rok 3: 1095 TB 
Rok 4: 1095 TB (po roku 3 usuwamy dane z roku 1)
Rok 5: 1095 TB (po roku 4 usuwamy dane z roku 2)
Rok 6: 1095 TB (po roku 5 usuwamy dane z roku 3)

Wygenerowane koszty:
Za�o�enia:
 * Cena za 1TB = 55,3 USD miesi�cznie zaczerpni�ta z kalkulatora Azure przy poni�szych parametrach:
  * Region: West Europe
  * Typ: Magazyn blob storage
  * Warstwa wydajno�ci: Standard
  * Type konta magazynu: Og�lnego przeznaczenia, V2
  * Nadmiarowo��: LRS
  * Warstwa dost�pu: Archiwum
  * Wszelkie operacje zapisu/odczytu nie s� brane pod uwag� przy wyliczeniu kosztu sk�adowania 1TB

Rok 1: 2340 TB x 55,3 USD = 129'402 USD
Rok 2: (12 x 360 TB + 2340 TB) x 55,3 USD = 368'298 USD 
Rok 3: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD
Rok 4: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD
Rok 5: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD
Rok 6: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD

Wyja�nienie: 
W roku 1, p�acimy za przechowywane dane w nast�uj�cy spos�b:
Miesi�c 1: 30 TB x 55,3 USD
Miesi�c 2: 60 TB x 55,3 USD
Miesi�c 2: 90 TB x 55,3 USD
(...)
Miesi�c 12: 360 TB x 55,3 USD

Z sumy ci�g�w wyliczamy ilo�� jednostek TB za kt�re p�acimy w ci�gu roku 12 x (30 + 360)/2 = 2340TB

W roku 2, p�acimy za ka�dy miesi�c przechowywania danych zebranych w 1 roku i  inkrementalnie przyrastaj�cymi danym w ci�gu roku 2 czyli 2340 TB

W roku 3, podobnie jak w roku 2 tylko p�acimy za dane zebrane z dw�ch ostatnich lat czyli za 2x360TB plus dane inkrementalne w ci�gu roku 3 czyli 2340 TB. 

Op�acalnie by�oby rozwa�y� u�ycie storage zarezerwanego z g�ry na 6 lat (2 razy po 3 lata) z ilo�ci� 11PB. Wygl�da �e wysz�oby taniej. 
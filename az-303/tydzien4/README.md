## #TYDZIEÑ5.1 
„Dla ka¿dego typu Storage, którego siê nauczy³eœ w czasie kursu (min. 4 typy) dobierz dwa dobre i jedno z³e zastosowanie. Chcia³bym byœ zweryfikowa³ ró¿ne mo¿liwoœci sk³adowania danych w Azure i opowiedzia³, kiedy i do czego te mo¿liwoœci mo¿esz wykorzystaæ.”

#### OdpowiedŸ
Azure Blob 
 * Dobre zastosowanie: przechowywanie zdjêæ sprzedawanych produktów, streaming video reklamuj¹cych produkt, przechowywanie dokumentacji np. instrukcji, regulaminów itp. , przechowywanie backup
 * Z³e zastosowanie: pliki wspó³dzielone
Azure File
 * Dobre zastosowanie: pliki do wspó³dzielenia z innymi u¿ytkownikami, 
 * Z³e zastosowanie: przechowywanie plików video
Azure Queue 
 * Dobre zastosowanie: aplikacja budowana w stylu „decoupled”, wymiana danych z systemami partnerów, integracja z innymi systemami wewnêtrznymi
 * Z³e zastosowanie: Musimy mieæ zagwarantowany porz¹dek wiadomoœci „FIFO”
Azure Table
 * Dobre zastosowanie: zapisywanie danych w prostych tabelach które nie potrzebuj¹ klucza obcego, wykonywania z³o¿onych zapytañ, np. przechowywanie logów czy danych diagnostycznych
 * Z³e zastosowanie: potrzebujemy relacji pomiêdzy tabelami w bazie danych, wykonywania zaawansowanych zapytañ


## #TYDZIEÑ5.2
„Wymieñ jeden dobry i jeden z³y przyk³ad wykorzystania StorSimple w swojej organizacji. Napisz, kiedy i w jakich scenariuszach siê sprawdzi, a kiedy nie.”

Dobre:
Archiwum, Disk-based backup, SharePoint, serwer plików

Z³e zastosowanie: 
Real time application, baza danych wysokiej wydajnoœci


#### OdpowiedŸ


## #TYDZIEÑ5.3
„Liczymy Koszty :). Umówmy siê. Twój system backupu (nie ma znaczenia jaki) sk³aduje 1TB nowych danych ka¿dego dnia. Wykorzystujesz oczywiœcie Azure do tej operacji i chcesz dane sk³adowaæ jak najtaniej. Przez dwa lata nie kasujesz zebranych danych. Po dwóch latach na próbê odtwarzasz dane z ostatniego dnia ka¿dego roku. Po 3 roku kasujesz dane, zebrane w roku pierwszym.

 * Ile ³¹cznie wygenerujesz kosztów w ramach tej us³ugi, jeœli rozwa¿ymy pe³ny, 6 letni okres jej dzia³ania.
 * Rozwa¿ ró¿ne aspekty i ró¿ne mo¿liwoœci us³ug i poka¿ jako algorytm liczenia przyj¹³eœ.


#### OdpowiedŸ

Za³o¿enia:
* Sk³adujemy backup na Azure Storage
* Backup: 
  * Dziennie: 1TB 
  * Miesiêcznie: 30 TB
  * Rocznie: 365 TB
* Czas trwania: 6 lat
* Retencja 3 lata, po 3 latach usuwamy to co starsze
* 1 miesi¹c = 30 dni, 1 Rok = 365 dni

Iloœæ wygenerowanych danych:
Rok 1: 365 TB
Rok 2: 730 TB
Rok 3: 1095 TB 
Rok 4: 1095 TB (po roku 3 usuwamy dane z roku 1)
Rok 5: 1095 TB (po roku 4 usuwamy dane z roku 2)
Rok 6: 1095 TB (po roku 5 usuwamy dane z roku 3)

Wygenerowane koszty:
Za³o¿enia:
 * Cena za 1TB = 55,3 USD miesiêcznie zaczerpniêta z kalkulatora Azure przy poni¿szych parametrach:
  * Region: West Europe
  * Typ: Magazyn blob storage
  * Warstwa wydajnoœci: Standard
  * Type konta magazynu: Ogólnego przeznaczenia, V2
  * Nadmiarowoœæ: LRS
  * Warstwa dostêpu: Archiwum
  * Wszelkie operacje zapisu/odczytu nie s¹ brane pod uwagê przy wyliczeniu kosztu sk³adowania 1TB

Rok 1: 2340 TB x 55,3 USD = 129'402 USD
Rok 2: (12 x 360 TB + 2340 TB) x 55,3 USD = 368'298 USD 
Rok 3: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD
Rok 4: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD
Rok 5: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD
Rok 6: (12 x 2 x 360 TB + 2340 TB) x 55,3 USD = 607'194 USD

Wyjaœnienie: 
W roku 1, p³acimy za przechowywane dane w nastêuj¹cy sposób:
Miesi¹c 1: 30 TB x 55,3 USD
Miesi¹c 2: 60 TB x 55,3 USD
Miesi¹c 2: 90 TB x 55,3 USD
(...)
Miesi¹c 12: 360 TB x 55,3 USD

Z sumy ci¹gów wyliczamy iloœæ jednostek TB za które p³acimy w ci¹gu roku 12 x (30 + 360)/2 = 2340TB

W roku 2, p³acimy za ka¿dy miesi¹c przechowywania danych zebranych w 1 roku i  inkrementalnie przyrastaj¹cymi danym w ci¹gu roku 2 czyli 2340 TB

W roku 3, podobnie jak w roku 2 tylko p³acimy za dane zebrane z dwóch ostatnich lat czyli za 2x360TB plus dane inkrementalne w ci¹gu roku 3 czyli 2340 TB. 

Op³acalnie by³oby rozwa¿yæ u¿ycie storage zarezerwanego z góry na 6 lat (2 razy po 3 lata) z iloœci¹ 11PB. Wygl¹da ¿e wysz³oby taniej. 
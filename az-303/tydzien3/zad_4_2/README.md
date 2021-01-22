## #TYDZIEN4.2
„Poprzez Azure Monitor zacznij monitorować dyski, CPU, Memory, a następnie podłącz maszyny do Log Analytics. Zacznij zbierać dane takie jak eventy z logu Apliacation oraz System. Postaraj się utworzyć własne dashboardy, w których pokazywane będą zbierane dane ze zdarzeń oraz danych performansowych (zachęcamy też do popatrzenia na inne dane i tego co da się osiągnąć dzięki Log Analytics w kwestii bezpieczeństwa. Proszę podziel się swoimi wnioskami!)

#### Odpowiedź
Po skonfigurowaniu Windows Event logs w menu Data, Azure Monitor zbiera eventy odpowiednie wybrany w ustawieniach. 

![alt text](https://github.com/mzdzioch/szkolachmury/blob/main/az-303/tydzien3/zad_4_2/loganalytics.JPG?raw=true)

Wtenczas Azure Monitors pozwala wizualizować dane telemetryczne takie jak brakujące update'y (krytyczne, zwykłe, związane z bezpieczeństwem), nieudane logowanie do Windows,  wykrycia złośliwego opgrowamowania, responsywność, błędy, dostępność maszyn, zużycie cpu, pamięci, dysków, etc. Do analizy z pomocą przychodzą prekonfigurowane zapytania albo zdefiniowanie właśnego zapytania. Widoki możemy przydpiąć do dashboardu.    

# zad 2) 

## Spróbuj stworzyć 3 nowe role i sprawdź ich działanie tworząc 3 urzytkowników dla potrzeb testów:

Uwaga: rola domyślnie nie może nic ponad to, co opisano niżej. A więc rola SecurityEng może tylko tworzyć zapytania i nic ponad to.

#### a) Rola: ProjectOwner:
może zarządzać usługami Virtual Machines, Azure Kubernetes Services, Storage Account
nie może modfikować usług sieciowych (Microsoft.Network)
nie może modyfikować usługi Azure Log Analytics

#### b) Rola: SecurityManager
może modyfikować: Azure Security Center, Azure Log Analytics
nie może tworzyć: Azure Security Center, Azure Log Analytics
może tworzyć alerty

#### c) Rola: SecurityEng
może: tworzyć zapytania w ramach Azure Log Analytics

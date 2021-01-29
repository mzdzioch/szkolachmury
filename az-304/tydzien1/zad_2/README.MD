2) Spróbuj stworzyæ 3 nowe role i sprawdŸ ich dzia³anie tworz¹c 3 urzytkowników dla potrzeb testów:

Uwaga: rola domyœlnie nie mo¿e nic ponad to, co opisano ni¿ej. A wiêc rola SecurityEng mo¿e tylko tworzyæ zapytania i nic ponad to.

a) Rola: ProjectOwner:
mo¿e zarz¹dzaæ us³ugami Virtual Machines, Azure Kubernetes Services, Storage Account
nie mo¿e modfikowaæ us³ug sieciowych (Microsoft.Network)
nie mo¿e modyfikowaæ us³ugi Azure Log Analytics

b) Rola: SecurityManager
mo¿e modyfikowaæ: Azure Security Center, Azure Log Analytics
nie mo¿e tworzyæ: Azure Security Center, Azure Log Analytics
mo¿e tworzyæ alerty

c) Rola: SecurityEng
mo¿e: tworzyæ zapytania w ramach Azure Log Analytics
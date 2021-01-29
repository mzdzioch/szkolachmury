# zad 1) 

## Spróbuj utworzyć zestaw polityk, które spełniają następujące oczekiwania i zapisz swoje wymiki prac:

* politka zabrania stworznia konta typu Azure Storage, które umożliwia dostępu z tzw. Public Endpoints
* polityka zabrania tworzenia serwerów Azure SQL, dostępnych publicznie
* polityka zabrania tworzenia zasobów, które nie mają Tag’u o nazwie Project
* polityka zabrania tworzenia zasobów, które nie mają Tag’u o nazwie Owner i którego zawartość nie zawiera maila np. w domenie chmurowisko.pl. Czyli tag Owner o wartości michal@chmurowisko.pl jest OK. ale tag o wartości michal@chmurowiskolab.com już nie
* polityka wymusza by każda stworzona maszyna była od razu podłączona do usługi Azure Log Analytics, które będzie parameterem polityki

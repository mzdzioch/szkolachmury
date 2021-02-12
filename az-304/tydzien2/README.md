![alt text](https://github.com/mzdzioch/szkolachmury/blob/main/az-304/tydzien2/szkola%20chmury%20AZ-304.png)

* DR
  * Main Site w West Europe oraz Backup Site w North Europe. West Europe jest optymalnym punktem na mapie Azure na główny site ze względu niskie opóźnienia dla połączeń z oddziałów Polski i Holandii.
  

* Połączenia zewnętrzne
 * Ruch z połączeń z internetu filtrowanych jest przez firewall'e skonfigurowane z load balance'erem aby zapewnić wysoką dostępności oraz rozłożyć obciążenie. Wydzielona siec może służyć jako rozbudowę pod DMZ
 * HQ, DC1/DC2 z Polski oraz oddziały lokalne połączone poprzez VPN IPsec do VPN Gateway'ów. Zastanowiłbym się nad użyciem Virtual WAN aby elastycznie podpinać kolejne oddziały z innych krajów oraz zarządzać połączeniami, natomiast nie wiem jak zachowuje się Virtual WAN w przypadku failover do site'u zapasowego.Z drugiej strony VPN Gateway też nie ma opcji przerzucenia ruchu do backup site w razie awarii site'u głównego :) 
  

* Topologia sieci
 * Zarówno połączenia z on-prem jak i z zewnątrz są zbudowane w konfiguracji hub-and-spoke. VNet'y dmz-int-vnet oraz dmz-ext-vnet jako hub, natomiast aplikacyjne jako spoke.


* Segmentacja
 * Każda aplikacja w rozbiciu na PROD, DEV i TEST w osobnych VNET-ach. 
 * W ramach jednej sieci VNET aplikacja podzielona na 6 warstw: firewall, front-end, api-management, backend, AKS oraz data 
 * Na każdym subnet'cie podpięty jest NSG oraz routing table  
 * RT wskazuje na ruch do firewall, firewall jest odpowiedzialny za inspekcje i kontrole ruchu w ramach i do VNET


*  

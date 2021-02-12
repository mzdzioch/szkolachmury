![alt text](https://github.com/mzdzioch/szkolachmury/blob/main/az-304/tydzien2/szkola%20chmury%20AZ-304.png)

* DR
  * Main Site w West Europe oraz Backup Site w North Europe. West Europe jest optymalnym punktem na mapie Azure na główny site ze względu niskie opóźnienia dla połączeń z oddziałów Polski i Holandii.
  

* Połączenia zewnętrzne
  * Ruch z połączeń z internetu filtrowanych jest przez firewall'e skonfigurowane z load balance'erem aby zapewnić wysoką dostępność oraz rozłożyć obciążenie. VENT z firewall'ami może służyć rozbudowę pod DMZ. Połączenia z internetu dystrybuowane przez Traffic Manager skonfigurowany aby przerzucić ruch na site zapasowy w przypadku awarii site'u głównego
  * HQ z Holandii, DC1/DC2 z Polski oraz oddziały lokalne połączone poprzez VPN IPsec do VPN Gateway'ów. Zastanowiłbym się nad użyciem Virtual WAN aby elastycznie podpinać kolejne oddziały z innych krajów oraz zarządzać połączeniami, natomiast nie wiem jak zachowuje się Virtual WAN w przypadku failover'u do site'u zapasowego.Z drugiej strony VPN Gateway też nie ma opcji przerzucenia ruchu do backup site w razie awarii site'u głównego :) Także nie jestem pewny zastowowanego rozwiązania 
  

* Topologia sieci
  * Zarówno połączenia z on-prem jak i z zewnątrz są zbudowane w konfiguracji hub-and-spoke. VNet'y dmz-int-vnet oraz dmz-ext-vnet jako hub, natomiast aplikacyjne jako spoke. Połączenie VNET peering pomiędzy Hub and spoke'ami.


* Segmentacja
  * Każda aplikacja w rozbiciu na PROD, DEV i TEST w osobnych VNET-ach. 
  * W ramach jednej sieci VNET aplikacja podzielona na 6 warstw: firewall, front-end, api-management, backend, AKS oraz data 
  * Na każdym subnet'cie podpięty jest NSG oraz routing table  
  * RT wskazuje na ruch do firewall, firewall jest odpowiedzialny za inspekcje i kontrole ruchu w ramach i do VNET
  * Proponuje aby każdy subnet miał zakres sieci /24

* Monitoring i Security
  * Użyłbym dostępnych narzędzi Network Watcher, Azure Monitor oraz Azure Sentinel jako SIEM zlokalizowane w dmz-ext-vnet oraz dmz-int-vnet do diagnozowania, analizy i monitoringu ruchu sieciowego 
  
* Strefa przesiadkowa
  * W obu lokalizacjach dedykowany serwer wystawiony z publicznym IP i zabezpieczony NSG

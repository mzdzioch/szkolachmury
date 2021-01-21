## #TYDZIEN4.3
„Włącz dla maszyn Just-in-time (JIT) i zweryfikuj jakie zmiany nastąpiły na NSG oraz jak możesz zarządzać dostępem do maszyn. Dla utworzonych wcześniej maszyn wdróż usługę Azure Bastion, powyłączaj na VMkach Public IP. Podłącz się za pomocą Azure Basion do VM, opowiedz o plusach i minusach usługi”

#### Odpowiedź
Po włączeniu JIT nastąpiło dodanie reguły "deny" na NSG dla portów:
- 22 — SSH
- 3389 — RDP
- 5985 — WinRM
- 5986 — WinRM

Dostęp jest włączany po wcześniejszym wybraniu żądania dostępu który automatycznie wrzuca na określony czas regułę "allow" z wyższym priorytetem i żądanym portem.


Usługę Bastion bardzo szybko się konfiguruje, jest ciekawą alternatywą dla połączenia RDP i przyszłościową dla połączeń remote desktop do systemu Windows ze względu na połaczenie przez przeglądarkę internetową. Dobre rozwiązanie dla organizacji które chciałyby zrezygnować z dodatkowego serwera Jump jeśli nie będzie zbyt częstych połączeń gdyż połączenia są rozliczane czasowo oraz za przesył.

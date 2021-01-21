## #TYDZIEN4.1 
„Przeanalizuj proszę Azure Security i zainstaluj Endpoint protection na wcześniej utworzonych Vmkach. Przejrzyj usługę Azure Security Center oraz poszukaj opcję rekomendacji pod względem spełniania regulacji - Regulatory Compliance PCI DSS. W miarę możliwości postaraj się wdrożyć dane rekomendacje i podziel się swoimi wnioskami!”

#### Odpowiedź
Sama koncepcja posiadania skoncentrowanej i ujednoliconej na bezpieczeństwie usługi jaką jest Azure Security Center z pewnością to zaleta Azure. W jednym miejscu mamy pełny wachlarz niezbędnych rzeczy - od podstawowych rekomendacji gwarantujących bezpieczeństwo środowisk, poprzez wdrażanie wszelkiej maści regulacji czy też analizy realnych zagrożeń na które wystawione jest środowisko. 
Wracając do samego ćwiczenia, wdrażanie regulacji PCI DSS (i inncyh) w Azure Security Center jest o tyle prostsze dzięki dokładnym opisom przy każdym punkcie regulacji. Z minusów wymieniłbym długi czas oczekiwania aż skanowanie uwględni naniesione zmiany. Ponoć 24 godziny, jednak w moim przypadku - a chciałem wszystkie zmiany wdrożyć - trwało czasem kilka dni zanim skanowanie przełknęło zmiany. Podejrzewam, że jest to związane z rodzajem subskrybcji jaką posiadam (w moim pzypadku trial). Np. długo czekałem na zmianę statusu ustawień "Firewall" maszyny Windows oraz "System Audit Policies" w GPO. "System Audit Policy" status wciąż nie zmienił się - wydaje się być ustawione poprawnie zgodnie z rekomendacjami. W przypadku punktów dotyczących "Firewall" po kilku dniach analizy/skanowania, pozostawione zostały dwa punkty z których jeden jest rozbieżny w opisie. Skan podaje poniżej. Inne punkty z GPO przeszły skanowanie z różnym czasem zmiany statusu. 

Poniżej na liście rekomendowana zmiana na "No", poczym wyświetlając szczegóły jest jednak zmiana na "Yes". Patrząc na expected values "1", to jednak chyba na "No" ma być ustawione. 

![alt text](https://github.com/mzdzioch/szkolachmury/blob/main/az-303/tydzien3/zad_4_1/firewall_compliance.JPG?raw=true)
![alt text](https://github.com/mzdzioch/szkolachmury/blob/main/az-303/tydzien3/zad_4_1/firewall_point.JPG?raw=true)

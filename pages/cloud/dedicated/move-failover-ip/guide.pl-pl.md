---
title:  Przenieś IP Failover
excerpt: Dowiedz się, jak przenieść IP Failover z Panelu klienta lub poprzez API OVHcloud
slug: ip-fo-move
section: Sieć & IP
order: 7
---

**Ostatnia aktualizacja z dnia 12-03-2021**

## Wprowadzenie

IP Failover mogą być przenoszone między Twoimi usługami. Chodzi o to, aby nie tracić reputacji i lepszego pozycjonowania Twoich aplikacji i systemów.
Technologia ta pozwala na wymianę adresów IP między poszczególnymi rozwiązaniami w czasie krótszym niż jedna minuta, praktycznie bez przerwy w dostępie do Twoich użytkowników. Mechanizm ten może być wykorzystywany w trakcie migracji usługi, podczas przenoszenia projektów ze środowiska programistycznego do środowiska produkcyjnego i przełączania usług na serwer backup w przypadku usterki.

**Dowiedz się, jak przenieść adres IP Failover z Panelu klienta OVHcloud lub poprzez API OVHcloud**

## Wymagania początkowe

- Posiadanie [serwera dedykowanego](https://www.ovhcloud.com/pl/bare-metal/){.external} w Panelu klienta
- Posiadanie [adresu IP Failover](https://www.ovhcloud.com/pl/bare-metal/ip/)
- Dostęp do [panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl){.external}.

## W praktyce

> [!primary]
> IP Failover nie może być przenoszone między strefami. Na przykład adres IP zlokalizowany w centrum danych SBG może zostać przeniesiony do GRA lub RBX, ale nie może zostać przeniesiony do BHS

### Przenieś IP w Panelu klienta OVHcloud

Zaloguj się do [Panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pl/&ovhSubsidiary=pl), kliknij menu `Bare Metal Cloud`{.action}, a następnie sekcję `IP`{.action} w dolnej części kolumny po lewej stronie.

![Panelu klienta](images/manager01.png){.thumbnail}

W rozwijanym menu "Service" możesz wybrać tylko adresy IP Failover.

Kliknij przycisk `...`{.action} po prawej stronie przenoszonego adresu IP, a następnie `Przenieś IP failover`{.action}.

![Panelu klienta](images/manager02.png){.thumbnail}

W menu, które się wyświetla wybierz usługę, do której chcesz przenieść adres IP.

Kliknij `Dalej`{.action}, a następnie `Zatwierdź`{.action}.

![Panelu klienta](images/manager03.png){.thumbnail}

### Przeniesienie IP przez API

Zaloguj się na stronie WWW [API OVHcloud](https://api.ovh.com/).

Najpierw należy sprawdzić, czy adres IP może zostać przeniesiony.
<br>Aby sprawdzić, czy IP może zostać przeniesione na jeden z Twoich serwerów dedykowanych, wywołaj następujące połączenie:

> [!api]
>
> @api {GET} /dedicated/server/{serviceName}/ipCanBeMovedTo
>

- `serviceName`: numer serwera dedykowanego docelowego
- `ip`: adres IP Fail Over do przeniesienia

Aby przenieść adres IP, użyj następującego połączenia:

> [!api]
>
> @api {POST} /dedicated/server/{serviceName}/ipMove
>

- `serviceName`: numer serwera dedykowanego docelowego
- `ip`: adres IP Fail Over do przeniesienia

## Sprawdź również

Dołącz do społeczności naszych użytkowników na stronie<https://community.ovh.com/en/>.

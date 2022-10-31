---
title: 'Domain mit DNSSEC sichern'
excerpt: 'Schützen Sie Ihre Domain mit DNSSEC vor Cache Poisoning'
slug: sichern_sie_ihre_domain_mit_dnssec_ab
legacy_guide_number: g609
section: 'Sicherheit'
order: 01
---

**Stand 19.06.2019**

## Ziel

Auf DNS-Servern wird die DNS-Konfiguration von Domains gespeichert. Diese Konfiguration wird üblicherweise dazu verwendet, Ihre Domain mit dem oder den Servern zu verbinden, auf denen Ihre Website oder E-Mail-Adressen gehostet werden. In den letzten Jahren haben Hacker Cache-Poisoning-Methoden für DNS-Server entwickelt, um den Traffic zu anderen Servern umzuleiten. Es gibt ein Verfahren, um Ihre Domain hiervor zu schützen: DNSSEC.

**Hier erfahren Sie, wie Sie DNSSEC für Ihre Domain aktivieren, um sie vor Cache Poisoning zu schützen.**  
Um zu verstehen, wie dieses Verfahren funktioniert, lesen Sie folgende Seite: „[DNSSEC verstehen](https://www.ovhcloud.com/de/domains/dnssec/){.external}“

## Voraussetzungen

- Sie besitzen eine bei OVHcloud registrierte Domain.
- Die betreffende Domain hat eine mit DNSSEC kompatible Endung.
- Sie sind in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} eingeloggt und befinden sich im Bereich `Web Cloud`{.action}.


## In der praktischen Anwendung

DNSSEC kann auf zwei Arten aktiviert werden:

- **Wenn Ihre Domain DNS-Server von OVHcloud verwendet**, kann DNSSEC mit einem Klick über Ihr Kundencenter aktiviert werden.

- **Wenn Ihre Domain nicht die OVHcloud DNS-Server verwendet**, informieren Sie sich für die Vorgehensweise bei dem Anbieter, der die DNS-Konfiguration Ihrer Domain verwaltet. Wenn Sie die Konfiguration selbst verwalten, muss DNSSEC manuell von Ihnen installiert werden. Ist das der Fall, nutzen Sie bitte die Dokumentation im Internet.

> [!primary]
>
> Um zu überprüfen, ob Ihre Domain die OVHcloud DNS-Konfiguration verwendet, gehen Sie in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} zur entsprechenden Domain und anschließend auf den Tab `DNS-Server`{.action}.
>

### Schritt 1: Auf die Domainverwaltung zugreifen

Um zu beginnen, loggen Sie sich zunächst in Ihrem [OVHcloud Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} ein und gehen Sie im Bereich `Web Cloud`{.action} auf `Domainnamen`{.action} und wählen Sie die betreffende Domain aus der Liste aus.

Die geöffnete Seite zeigt die allgemeinen Informationen der Domain. 

### Schritt 2: DNSSEC-Dienst Ihrer Domain verwalten

Im Tab `Allgemeine Informationen`{.action} können Sie den Status der DNSSEC-Aktivierung für Ihre Domain überprüfen.

Den Status finden Sie unter „Sicherheit“ und „Sichere Delegation (DNSSEC)“.

![DNSSEC](images/activate-dnssec-step2.png){.thumbnail}

Indem Sie den Aktivierungsbutton verschieben, können Sie DNSSEC für Ihre Domain aktivieren bzw. deaktivieren. Es öffnet sich ein neues Fenster zur Bestätigung der Änderung.

![DNSSEC](images/activate-dnssec-step3.png){.thumbnail}

### Schritt 3: Durchführung der Aktivierung bzw. Deaktivierung abwarten

Die Aktivierung bzw. Deaktivierung von DNSSEC für Ihre Domain kann bis zu 24 Stunden dauern. 

## Weiterführende Informationen

Für den Austausch mit unserer User Community gehen Sie auf <https://community.ovh.com/en/>.

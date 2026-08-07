# Certification Practice Statement (CPS)

**Signature Root CA der GrowVolution e.V. — LibreSign**

|                       |                                                                                                                       |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------|
| Dokumententyp         | Certification Practice Statement                                                                                      |
| Betreiber der CA      | GrowVolution e.V.                                                                                                     |
| Anschrift             | Schöninger Straße 17, 38173 Sickte, Deutschland                                                                       |
| Registergericht       | Amtsgericht Braunschweig, VR 202639                                                                                   |
| Vertretungsberechtigt | 1. Vorsitzender, 2. Vorsitzender                                                                                      |
| Betreibende Stelle    | Verwaltungseinheit Digital Infrastructure (DI)                                                                        |
| CA-Subject            | CN = Signature Root CA, O = GrowVolution e.V., OU = Digital Infrastracuture, C = DE, ST = Lower Saxony, L = Brunswick |
| Version               | 1.0                                                                                                                   |
| Stand                 | 07.08.2026                                                                                                            |
| Inkrafttreten         | 07.08.2026                                                                                                            |
| Kontakt               | admin@growvolution.org                                                                                                |
| Veröffentlichung      | https://github.com/GrowVolution/GrowVolution_e.V./tree/main/cps/de/libresign.md                                       |

---

## 1. Einleitung

### 1.1 Überblick

Dieses Certification Practice Statement (CPS) beschreibt die Verfahren, nach denen die GrowVolution e.V. (nachfolgend „der Verein") die von ihr betriebene Zertifizierungsstelle „Signature Root CA" betreibt und Signaturzertifikate für natürliche Personen ausstellt, verwaltet und widerruft.

Die Signature Root CA dient ausschließlich der Erstellung **fortgeschrittener elektronischer Signaturen (FES)** im Sinne von Art. 3 Nr. 11 i.V.m. Art. 26 der Verordnung (EU) Nr. 910/2014 (eIDAS-VO) auf Dokumenten, die über die vom Verein betriebene Instanz von Nextcloud/LibreSign verarbeitet werden.

### 1.2 Abgrenzung: kein qualifizierter Vertrauensdienst

Der Verein ist **kein qualifizierter Vertrauensdiensteanbieter (QTSP)** im Sinne von Art. 3 Nr. 20 eIDAS-VO. Die Signature Root CA ist nicht in der EU Trusted List gelistet, unterliegt keiner Konformitätsbewertung nach Art. 20/21 eIDAS-VO und keiner Aufsicht durch die Bundesnetzagentur. Es werden keine qualifizierten Zertifikate ausgestellt und keine qualifizierten elektronischen Signaturerstellungseinheiten (QSCD) eingesetzt.

Die mit dieser CA erzeugten Signaturen sind daher **keine qualifizierten elektronischen Signaturen (QES)** und ersetzen nicht die gesetzlich angeordnete Schriftform nach § 126 BGB (vgl. § 126a BGB). Rechtsgeschäfte, die eine notarielle Beurkundung oder Beglaubigung erfordern, werden über die dafür vorgesehenen Verfahren abgewickelt und sind vom Anwendungsbereich dieses CPS ausgenommen.

Nach Art. 25 Abs. 1 eIDAS-VO darf einer elektronischen Signatur die Rechtswirkung und die Zulässigkeit als Beweismittel in Gerichtsverfahren nicht allein deshalb abgesprochen werden, weil sie nicht die Anforderungen an qualifizierte elektronische Signaturen erfüllt.

### 1.3 Teilnehmer der PKI

| Rolle                      | Beschreibung                                                                                                     |
|----------------------------|------------------------------------------------------------------------------------------------------------------|
| Zertifizierungsstelle (CA) | GrowVolution e.V., betrieben durch die Verwaltungseinheit Digital Infrastructure (DI)                            |
| Registrierungsstelle (RA)  | Digital Infrastructure (DI)                                                                                      |
| Zertifikatsinhaber         | Natürliche Personen mit Benutzerkonto in der Vereinscloud, deren Identität nach Abschnitt 3.2 festgestellt wurde |
| Signaturanfordernde        | Mitglieder der Gruppe `NC_Signatures`                                                                            |
| Vertrauende Dritte         | Empfänger signierter Dokumente                                                                                   |

### 1.4 Anwendungsbereich

Zulässig ist die Verwendung der ausgestellten Zertifikate zur Signatur von Dokumenten im Rahmen der Vereinstätigkeit und der Rechtsbeziehungen des Vereins zu Mitgliedern, Vertragspartnern und Dritten.

Unzulässig ist insbesondere die Verwendung für TLS-/Server-Authentifizierung, Code Signing, E-Mail-Verschlüsselung, die Ausstellung von Sub-CAs an Dritte sowie jede Verwendung außerhalb der vom Verein betriebenen Signaturplattform.

### 1.5 Verwaltung des CPS

Dieses CPS wird vom Vorstand verabschiedet und geändert. Die Überwachung und Sicherstellung der Einhaltung obliegt der Verwaltungseinheit Digital Infrastructure (DI). Änderungen werden versioniert; die jeweils gültige Fassung wird nach Abschnitt 2 veröffentlicht. Rückfragen und Meldungen sind an admin@growvolution.org zu richten.

---

## 2. Veröffentlichung und Verzeichnisdienst

Die jeweils gültige Fassung dieses CPS wird im öffentlichen Repository des Vereins veröffentlicht:
`https://github.com/GrowVolution/GrowVolution_e.V./tree/main/cps/de/libresign.md` (englische Fassung unter `/cps/en/libresign.md`).

Das Zertifikat der Signature Root CA wird **nicht** über eine eigenständige URL bereitgestellt. Stattdessen enthält jedes über die Plattform signierte Dokument einen Footer mit Validierungslink und QR-Code. Über diesen Link sind sämtliche Informationen zur Zertifikatskette sowie der Sperrstatus (CRL) einsehbar. Die Prüfung einer Signatur erfolgt damit dokumentgebunden.

Vertrauende Dritte werden ausdrücklich darauf hingewiesen, dass das Root-Zertifikat **nicht** in öffentlichen Trust Stores enthalten ist. Eine Signaturprüfung außerhalb des Validierungsdienstes setzt eine manuelle Vertrauensentscheidung zugunsten dieses Root-Zertifikats voraus.

---

## 3. Identifizierung und Authentifizierung

### 3.1 Namensregeln

Zertifikate werden auf den bürgerlichen Namen der natürlichen Person ausgestellt, ergänzt um deren im Verzeichnisdienst hinterlegte E-Mail-Adresse. Pseudonyme werden nicht ausgestellt. Die Eindeutigkeit der Zuordnung von Subject-DN zu einer natürlichen Person innerhalb der PKI wird durch DI sichergestellt.

### 3.2 Identitätsprüfung bei Erstregistrierung

Vor Ausstellung eines Signaturzertifikats wird die Identität der antragstellenden Person auf geeignete Weise festgestellt. Als geeignet gelten insbesondere:

1. Sichtung eines gültigen amtlichen Lichtbildausweises (persönlich oder in einem beaufsichtigten Video-Verfahren),
2. die im Rahmen des Mitgliedschaftsverfahrens erfolgte Identitätsfeststellung,
3. Verfahren gleichwertiger Zuverlässigkeit wie PostIDENT.

Das gewählte Verfahren, das Datum der Feststellung und die feststellende Person werden dokumentiert und nach Abschnitt 5.4 aufbewahrt.

Signaturanfragen werden erst ausgelöst, nachdem die Eindeutigkeit der Identität der anzufragenden Person verifiziert wurde. Signaturanfragen können ausschließlich an Personen gerichtet werden, die über ein Benutzerkonto in der Vereinscloud verfügen.

### 3.3 Berechtigung zur Anforderung von Signaturen

Signaturen können ausschließlich von Mitgliedern der Gruppe `NC_Signatures` angefordert werden. Die Aufnahme in diese Gruppe setzt eine vorherige Unterweisung über die Anforderungen dieses CPS voraus, insbesondere über die Pflicht zur Verifizierung der Identität der anzufragenden Person vor Auslösung einer Signaturanfrage.

### 3.4 Authentifizierung bei Signaturerstellung

Die Auslösung einer Signatur erfordert kumulativ zwei Faktoren:

1. **Erster Faktor:** authentifizierter Zugang zur Vereinscloud über den zentralen Single-Sign-On-Dienst des Vereins,
2. **Zweiter Faktor:** Eingabe des ausschließlich dem Zertifikatsinhaber bekannten Signaturpassworts, mit dem der private Schlüssel geschützt ist.

Das Signaturpasswort wird ausschließlich zur Ver- bzw. Entschlüsselung des privaten Schlüssels des Inhabers verwendet und nicht im Klartext gespeichert. Es ist weder aus dem Schlüsselmaterial noch aus dem Zertifikat ableitbar. Der Verein kennt das Signaturpasswort nicht und kann es nicht wiederherstellen; eine Signaturerstellung ohne dieses Passwort ist technisch ausgeschlossen.

---

## 4. Betriebliche Anforderungen im Lebenszyklus

### 4.1 Antrag und Ausstellung

Der Antrag erfolgt durch die natürliche Person über die Signaturplattform. Nach positiver Identitätsprüfung nach Abschnitt 3.2 wird das Schlüsselpaar erzeugt und das Zertifikat durch die Signature Root CA ausgestellt. Die Ausstellung wird protokolliert.

### 4.2 Schlüsselerzeugung des Zertifikatsinhabers

Das Schlüsselpaar wird im Rahmen des Ausstellungsprozesses erzeugt; der private Schlüssel wird unmittelbar mit dem vom Inhaber gesetzten Signaturpasswort verschlüsselt abgelegt. Der Zertifikatsinhaber ist verpflichtet, das Signaturpasswort geheim zu halten und nicht an Dritte weiterzugeben.

### 4.3 Gültigkeitsdauern

| Zertifikatstyp        | Gültigkeit |
|-----------------------|------------|
| Signature Root CA     | 10 Jahre   |
| Endanwenderzertifikat | 1 Jahr     |

### 4.4 Erneuerung

Eine Erneuerung erfolgt durch Neuausstellung. Bei unveränderten Identitätsdaten und weiterhin bestehendem Benutzerkonto kann auf eine erneute vollständige Identitätsprüfung verzichtet werden, sofern die letzte Feststellung nicht länger als 7 Jahre zurückliegt. Die Frist orientiert sich an der regelmäßigen Gültigkeitsdauer deutscher Personalausweise.

### 4.5 Widerruf (Revocation)

Ein Zertifikat wird unverzüglich widerrufen, wenn:

- der Zertifikatsinhaber dies beantragt,
- Anhaltspunkte für eine Kompromittierung des privaten Schlüssels oder des Signaturpassworts bestehen,
- die im Zertifikat enthaltenen Angaben unrichtig geworden sind,
- das Benutzerkonto des Inhabers deaktiviert wird oder die zugrunde liegende Beziehung zum Verein endet,
- ein Verstoß gegen dieses CPS festgestellt wird.

Widerrufsanträge sind an admin@growvolution.org zu richten. Antragsberechtigt sind der Zertifikatsinhaber sowie der Vorstand. Die Durchführung obliegt DI.

Die Signaturplattform führt eine eigene Sperrliste (CRL). Diese ist administrativ zugänglich; für vertrauende Dritte ist der Sperrstatus über den Validierungslink des jeweiligen Dokuments (Abschnitt 2) einsehbar. Ein öffentlicher CRL-Verteilpunkt außerhalb dieses Validierungsdienstes wird nicht betrieben.

### 4.6 Signaturformat und Integritätssicherung

Signaturen werden so mit den signierten Daten verknüpft, dass jede nachträgliche Veränderung der Daten erkennbar ist (Art. 26 lit. d eIDAS-VO). Als Signaturverfahren kommt RSA mit SHA-512 zum Einsatz.

---

## 5. Organisatorische Sicherheitsmaßnahmen

### 5.1 Verantwortlichkeit

Der Verein trägt als eigene Rechtspersönlichkeit die Verantwortung für den Betrieb der Signature Root CA sowie für die Feststellung und Eindeutigkeit der den Signaturen zugrunde liegenden Identitäten.

Die Gesamtverantwortung und die rechtliche Haftung liegen beim Vorstand. Der operative Betrieb — Betrieb und Pflege des Vereinsnetzwerks, Verwaltung der Root CA, Identitätsfeststellung, Ausstellung und Widerruf von Zertifikaten sowie die Überwachung der Einhaltung dieses CPS — obliegt vollständig der vom Vorstand mandatierten Verwaltungseinheit Digital Infrastructure (DI).

### 5.2 Rollen und Zugriffskontrolle

Administrativer Zugriff auf die CA-Funktionen der Signaturplattform ist auf DI beschränkt. Der Zugang zur Plattform erfolgt über den zentralen SSO-Dienst mit Mehrfaktor-Authentifizierung. Privilegierter Zugriff auf die zugrunde liegende Serverinfrastruktur (SSH, Container-Verwaltung) ist auf den benannten Ansprechpartner von DI beschränkt.

**Hinweis zur Rollentrennung:** Der privilegierte Infrastrukturzugriff ist derzeit auf eine Person konzentriert. Eine Trennung von Ausstellungs- und Kontrollfunktion ist organisatorisch nicht abgebildet; die Kompensation erfolgt über die lückenlose Protokollierung und Alarmierung nach Abschnitt 5.3.

### 5.3 Protokollierung und Alarmierung

- Sämtliche Zugriffe auf die Serverinfrastruktur werden mittels `auditd` protokolliert; jede unter erhöhten Rechten ausgeführte Aktion ist nachvollziehbar.
- Jeder SSH-Verbindungsaufbau löst automatisiert eine Benachrichtigung in die Administrationsgruppe auf dem vereinseigenen Matrix-Server (Synapse) aus. Der Verein betreibt diesen Dienst selbst und hat insoweit vollständige Datenhoheit.
- Protokolliert werden ferner: Ausstellung, Erneuerung und Widerruf von Zertifikaten, administrative Eingriffe in die CA-Konfiguration sowie Signaturvorgänge einschließlich Zeitstempel und beteiligter Konten.

### 5.4 Aufbewahrung

Registrierungsunterlagen, Protokolldaten und ausgestellte Zertifikate werden für 10 Jahre nach Ablauf des jeweiligen Zertifikats aufbewahrt. Die Verarbeitung personenbezogener Daten erfolgt nach Maßgabe der Datenschutzordnung des Vereins.

### 5.5 Beendigung des CA-Betriebs

Bei Einstellung des Betriebs werden alle ausgestellten Zertifikate widerrufen, die Zertifikatsinhaber und bekannte vertrauende Dritte informiert und die Protokolldaten für die Dauer der Aufbewahrungsfrist gesichert.

---

## 6. Technische Sicherheitsmaßnahmen

### 6.1 Schlüsselerzeugung der CA

Das Schlüsselpaar der Signature Root CA wurde über die Verwaltungsoberfläche der Signaturkomponente (LibreSign) innerhalb der vom Verein selbst betriebenen Nextcloud-Instanz erzeugt. Aus diesem Root-Schlüssel werden die Signaturzertifikate der Zertifikatsinhaber abgeleitet.

### 6.2 Schutz des privaten CA-Schlüssels

Der private Schlüssel der Signature Root CA wird serverseitig innerhalb der vom Verein selbst betriebenen Clusterinfrastruktur gespeichert. Es kommt **keine** Hardware-Sicherheitseinheit (HSM) und keine QSCD zum Einsatz. Der Schlüssel liegt damit im Zugriffsbereich der Systemadministration; hieraus folgt, dass die Vertrauenswürdigkeit der CA maßgeblich von den organisatorischen und protokollarischen Maßnahmen nach Abschnitt 5 getragen wird.

Folgende Maßnahmen sichern den Schlüssel ab:

- Speicherung auf einem dedizierten Knoten der Vereinsinfrastruktur; das Schlüsselmaterial verlässt diesen Knoten im Regelbetrieb nicht.
- Beschränkung des privilegierten Zugriffs (SSH, Container-Verwaltung) auf den benannten Ansprechpartner von DI.
- Vollständige Auditierung aller Zugriffe (`auditd`) und automatisierte Alarmierung bei SSH-Verbindungsaufbau (Abschnitt 5.3).
- Automatisierte lokale Sicherung des Datenbestands mittels Borg im 7-Tage-Intervall. Die Sicherungen unterliegen denselben Zugriffsbeschränkungen wie das Produktivsystem.

Detailangaben zu Hostnamen, Netzadressen und Ablagepfaden werden aus Sicherheitsgründen nicht veröffentlicht; sie sind in der internen Systemdokumentation von DI hinterlegt.

### 6.3 Schutz der privaten Schlüssel der Zertifikatsinhaber

Private Schlüssel der Zertifikatsinhaber sind zwingend mit einem nur dem Inhaber bekannten Signaturpasswort verschlüsselt. Das Passwort wird nicht persistiert und ist aus dem verschlüsselten Schlüsselmaterial nicht ableitbar. Eine Signaturerstellung durch den Betreiber ohne Mitwirkung des Inhabers ist ausgeschlossen. Bei Verlust des Signaturpassworts ist keine Wiederherstellung möglich; das betroffene Zertifikat ist nach Abschnitt 4.5 zu widerrufen und neu auszustellen.

### 6.4 Kryptographische Parameter

| Parameter            | Wert                                    |
|----------------------|-----------------------------------------|
| Schlüsselalgorithmus | RSA                                     |
| Signaturalgorithmus  | `sha512WithRSAEncryption` (RSA-SHA-512) |
| Hashverfahren        | SHA-512                                 |

---

## 7. Zertifikatsprofile

Dieser Abschnitt dokumentiert, welche Felder und Erweiterungen die ausgestellten Zertifikate enthalten, damit vertrauende Dritte eine Signatur technisch prüfen können.

### 7.1 Root-Zertifikat

| Feld                     | Wert                                                         |
|--------------------------|--------------------------------------------------------------|
| Common Name (CN)         | Signature Root CA                                            |
| Organization (O)         | GrowVolution e.V.                                            |
| Organizational Unit (OU) | Digital Infrastracuture, libresign-ca-id:jbi0cxmc0h_g:11_e:o |
| Country (C)              | DE                                                           |
| State (ST)               | Lower Saxony                                                 |
| Locality (L)             | Brunswick                                                    |
| Signaturalgorithmus      | sha512WithRSAEncryption                                      |
| Gültigkeit               | 10 Jahre ab Ausstellung                                      |
| Basic Constraints        | CA:TRUE                                                      |

### 7.2 Endanwenderzertifikat

| Feld                | Wert                                                         |
|---------------------|--------------------------------------------------------------|
| Subject             | Bürgerlicher Name und E-Mail-Adresse des Zertifikatsinhabers |
| Issuer              | CN = Signature Root CA, O = GrowVolution e.V.                |
| Signaturalgorithmus | sha512WithRSAEncryption                                      |
| Gültigkeit          | 1 Jahr ab Ausstellung                                        |
| Basic Constraints   | CA:FALSE                                                     |
| Key Usage           | digitalSignature, nonRepudiation (contentCommitment)         |

---

## 8. Konformitätsprüfung

Eine externe Konformitätsbewertung nach Art. 20/21 eIDAS-VO findet nicht statt und ist für nicht-qualifizierte Vertrauensdienste nicht erforderlich.

DI überprüft die Einhaltung dieses CPS einmal jährlich und dokumentiert das Ergebnis. Der Prüfbericht wird dem Vorstand vorgelegt. Gegenstand der Prüfung sind mindestens: Bestand und Gültigkeit ausgestellter Zertifikate, Vollständigkeit der Registrierungsdokumentation, Auswertung der Zugriffsprotokolle sowie die Funktionsfähigkeit von Sperrverfahren und Validierungsdienst.

---

## 9. Rechtliche Bestimmungen

### 9.1 Erfüllung der Anforderungen an FES

| Anforderung (Art. 26 eIDAS-VO)                                              | Umsetzung                                                                                                                                       |
|-----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| lit. a — eindeutige Zuordnung zum Unterzeichner                             | Ausstellung personengebundener Zertifikate an eindeutig identifizierte natürliche Personen (Abschnitte 3.1, 3.2)                                |
| lit. b — Identifizierung des Unterzeichners ermöglicht                      | Dokumentierte Identitätsfeststellung vor Ausstellung; Name und E-Mail-Adresse im Zertifikat (Abschnitt 3.2)                                     |
| lit. c — Erstellung mit Daten unter alleiniger Kontrolle des Unterzeichners | Zwingendes, nur dem Inhaber bekanntes und nicht ableitbares Signaturpasswort als zweiter Faktor zusätzlich zum SSO-Zugang (Abschnitte 3.4, 6.3) |
| lit. d — Verknüpfung, die nachträgliche Änderungen erkennbar macht          | Kryptographische Bindung der Signatur an das Dokument mittels RSA-SHA-512 (Abschnitt 4.6)                                                       |

### 9.2 Pflichten der Zertifikatsinhaber

Zertifikatsinhaber sind verpflichtet, das Signaturpasswort geheim zu halten, den Verlust oder den Verdacht einer Kompromittierung unverzüglich an admin@growvolution.org zu melden und Zertifikate nur im Rahmen des Anwendungsbereichs nach Abschnitt 1.4 zu verwenden.

### 9.3 Haftung

Der Verein haftet nach den allgemeinen gesetzlichen Vorschriften; die Gesamtverantwortung trägt der Vorstand. Eine Haftung für Schäden aus der Verwendung von Signaturen außerhalb des Anwendungsbereichs nach Abschnitt 1.4 sowie aus einer Verletzung der Pflichten nach Abschnitt 9.2 ist ausgeschlossen, soweit gesetzlich zulässig. Die Haftungsprivilegierung nach Art. 13 eIDAS-VO für qualifizierte Vertrauensdienste findet keine Anwendung.

### 9.4 Datenschutz

Die Verarbeitung personenbezogener Daten im Rahmen des CA-Betriebs richtet sich nach der DSGVO und der Datenschutzordnung des Vereins.

### 9.5 Anwendbares Recht und Gerichtsstand

Es gilt das Recht der Bundesrepublik Deutschland. Gerichtsstand ist der Sitz des Vereins, soweit ein solcher zulässig vereinbart werden kann; im Übrigen gelten die gesetzlichen Gerichtsstände.

---

## Änderungshistorie

| Version | Datum      | Änderung    |
|---------|------------|-------------|
| 1.0     | 07.08.2026 | Erstfassung |
---
title: Obsługuje instrukcji w języku Visual Basic 6.0 | Dokumentacja firmy Microsoft
ms.date: 08/28/2017
ms.technology: devlang-vb
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.workload:
- paulyuk
ms.openlocfilehash: cc55dec5960717e3807602bc76031f7502ec90c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Obsługuje instrukcji w języku Visual Basic 6.0 w systemie Windows


## <a name="executive-summary"></a>Streszczenie

Zespół programu Visual Basic przywiązuje dużą wagę do "Ją po prostu działa" zgodność aplikacji Visual Basic 6.0 na następujących obsługiwanych systemów operacyjnych Windows: 

- Windows 10
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 R2 w tym
- Windows Server 2008 R2 w tym

Celem zespołu Visual Basic jest, że aplikacje Visual Basic 6.0 nadal działać w obsługiwanych wersjach systemu Windows. Zgodnie z opisem w tym dokumencie, środowisko uruchomieniowe Visual Basic 6.0 core będą obsługiwane dla pełnej okres istnienia obsługiwanych wersji systemu Windows, czyli pięciu lat. dostępne podstawowe wsparcie następuje pięciu lat. rozszerzonej pomocy technicznej (http://support.microsoft.com/gp/lifepolicy). Na pasku pomocy technicznej będzie ograniczony do poważnych regresji i ważnych kwestiach dotyczących zabezpieczeń dla istniejących aplikacji.

## <a name="technical-summary"></a>Podsumowanie informacji technicznych

Visual Basic 6.0 składa się z tych kluczy materiałów:
- Visual Basic 6.0 IDE (Integrated Development Environment).
- Środowisko uruchomieniowe Visual Basic 6.0: biblioteki podstawowej i aparat wykonywania używane do uruchamiania aplikacji VB w wersji 6.0.
- Pliki rozszerzone środowiska uruchomieniowego języka Visual Basic 6.0: wybrane pliki OCX formantu ActiveX, biblioteki i narzędzia wysyłki na nośnikach programu IDE i jako wersji online.

## <a name="the-visual-basic-60-ide"></a>Visual Basic 6.0 IDE

Środowiska IDE programu Visual Basic 6.0 nie jest już obsługiwany począwszy od 8 kwietnia 2008. Ponadto zespoły zarówno systemu Windows, jak i Visual Basic zostały przetestowane Visual Basic 6.0 IDE na Windows Vista, Windows 7, Windows Server 2008, Windows 8 i Windows 8.1 do zrozumienia i ograniczenia (jeśli są one) problemy ze zgodnością w 32-bitowych wersjach systemu Windows (patrz [64-bitowym systemie Windows](#62-bit-windows) sekcji poniżej, aby uzyskać więcej informacji na temat 64-bitowym). Zawiadomienie nie powoduje zmiany zasad pomocy technicznej dla IDE.

## <a name="the-visual-basic-60-runtime"></a>Środowisko uruchomieniowe Visual Basic 6.0

Środowisko uruchomieniowe Visual Basic 6.0 jest zdefiniowany jako skompilowane pliki binarne oryginalnie uwzględnione na liście ponownej dystrybucji dla programu Visual Basic 6.0. Pliki te zostały oznaczone jako dystrybucyjnego w oryginalnej licencji Visual Basic 6.0. Pliki te przykłady biblioteki wykonawczej programu Visual Basic 6.0 (`msvbvm60.dll`), kontrolek (tj. `msflxgrd.ocx`) oraz środowisko uruchomieniowe obsługi plików dla innych głównych obszarów funkcjonalnych (np. MDAC).

Środowisko wykonawcze jest podzielone na trzy grupy:

- Obsługiwane pliki środowiska uruchomieniowego — wysyłania w systemie operacyjnym

   Pliki środowiska uruchomieniowego klucza Visual Basic 6.0, używane w większości scenariuszy aplikacji jest dostarczany w i obsługiwane przez czas ich istnienia obsługiwanych wersji systemu Windows. Ten cykl życia jest pięciu lat. dostępne podstawowe wsparcie i pięciu lat. wsparcia dodatkowego z czas, który jest dostarczany z danej wersji systemu Windows. Pliki te zostały przetestowane na zgodność jako część testów aplikacji Visual Basic 6.0 działających w obsługiwanych wersjach systemu Windows. 

   > [!NOTE]
   > Wymagania pakietu redystrybucyjnego dla aplikacji zawierające te pliki należy niemal identyczne i wszystkich obsługiwanych wersjach systemu Windows zawiera listę niemal identyczne plików. Najważniejsza różnica co oznacza, że `TriEdit.dll` został usunięty z systemu Windows Vista i nowszych wersjach.

- Obsługiwane pliki środowiska uruchomieniowego — — rozszerzone pliki do rozprowadzania z aplikacji

   Ta lista rozszerzonej składa się z klucza formantów, biblioteki i narzędzia, które są zainstalowane na komputerze dewelopera z nośnika programu IDE lub z witryny Microsoft.com. Zazwyczaj VB6 IDE tych kontrolek na komputerze dewelopera domyślnie instalowany. Deweloper nadal musi wykonać ponowną dystrybucję tych plików z aplikacji. Obsługiwane wersje plików jest dostępna online w Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927).

- Pliki środowiska uruchomieniowego nieobsługiwane

   Niektóre pliki albo spada poza podstawowe obsługują lub nigdy nie zostały dołączone jako część pakietu redystrybucyjnego środowiska uruchomieniowego (np., zostały uwzględnione w `\Tools` folderze na nośniku IDE do obsługi starszych aplikacji VB4/VB5 lub były formanty innych firm). Te pliki nie są obsługiwane w systemie Windows; Zamiast tego są one objęte niezależnie od umowy pomocy technicznej ma zastosowanie do nośnika, które zostały dołączone. Oznacza to udzielania żadnych gwarancji dotyczących pomocy technicznej i obsługi. W niektórych przypadkach nowsze wersje biblioteki te są obsługiwane. Poniżej znajdują się szczegółowe informacje o zgodności z poprzednimi wersjami lub migracji do obsługiwanych wersji.

Aby szczegółowych informacji na temat plików znajdujących się w każdej grupie pomocy technicznej, zobacz [definicji środowiska uruchomieniowego](#runtime-definition) poniższej sekcji.

## <a name="the-visual-basic-60-support-lifetime"></a>Cykl życia pomocy technicznej programu Visual Basic 6.0

Obsługa i/lub wysyłania pliki binarne środowiska wykonawczego Visual Basic 6.0 w obsługiwanych wersjach systemu Windows nie zmienia zasady udzielania pomocy technicznej dla środowiska IDE programu Visual Basic 6.0 lub programu Visual Studio 6.0 IDE jako całość. Przenieść tych produktów poza obowiązuje wsparcie 8 kwietnia 2008 roku.

Szczegółowe informacje o cyklu pomocy technicznej produktów firmy Microsoft można znaleźć w folderze http://support.microsoft.com/gp/lifepolicy. W ramach tego cyklu pomocy technicznej firma Microsoft będzie obsługuje środowisko uruchomieniowe Visual Basic 6.0 w obsługiwanych wersjach systemu Windows przez czas ich istnienia obsługi tych systemów operacyjnych. Oznacza to, na przykład obsługiwane w systemie Windows Server 2003 do czerwca, 2008, aby uzyskać wsparcie podstawowe i czerwca 2013 rozszerzonej pomocy technicznej środowisko uruchomieniowe Visual Basic 6.0.
Więcej szczegółów na cykl pomocy technicznej lub Aby uzyskać informacje na temat dodatkowe opcje pomocy technicznej, można znaleźć pod adresem naszą stronę pomocy technicznej w http://www.microsoft.com/support.

## <a name="64-bit-windows"></a>64-bitowego systemu Windows

Pliki środowiska uruchomieniowego Visual Basic 6.0 jest 32-bitowych. Pliki te są dostarczane w 64-bitowych systemów operacyjnych Windows wymienionej w tabeli poniżej. 32-bitowe VB6 aplikacje i składniki są obsługiwane w środowisku emulacji WOW tylko. składniki 32-bitowe muszą być również obsługiwane w procesach 32-bitowej aplikacji.

Środowiska IDE programu Visual Basic 6.0 nigdy nie jest dostępne w natywnych 64-bitowej wersji, nie ma obsługiwanego IDE 32-bitowych na 64-bitowym systemie Windows. Programowanie VB6 na 64-bitowego systemu Windows lub dowolnej natywnego architekturze niż 32-bitowych nie jest i nie jest obsługiwana.

## <a name="windows-7"></a>Windows 7

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows 7. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 w systemie Windows 7.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w systemie Windows 7 dla okresu istnienia systemu operacyjnego. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji.

## <a name="windows-81"></a>Windows 8.1

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows 8.1. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 na Windows 8.1.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w Windows 8.1 przez czas ich istnienia systemu operacyjnego. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji. Deweloperzy można traktować jako takie same jak w systemie Windows 7 artykułu pomocy technicznej dla Windows 8.1.

## <a name="windows-10"></a>Windows 10

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows 10. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 w systemie Windows 10.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w systemie Windows 10 dla okresu istnienia systemu operacyjnego. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji. Deweloperzy można traktować jako takie same jak Windows 8.1 artykułu pomocy technicznej dla systemu Windows 10.

## <a name="windows-server-2008"></a>Windows Server 2008

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows Server 2008. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 w systemie Windows Server 2008.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w systemie Windows Server 2008 dla okresu istnienia systemu operacyjnego. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji.

## <a name="windows-server-2008-r2"></a>Windows Server 2008 z dodatkiem R2

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows Server 2008 R2. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 w systemie Windows Server 2008 R2.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w systemie Windows Server 2008 R2 dla systemu operacyjnego przez czas ich istnienia. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji. Deweloperzy można traktować jako takie same, podobnie jak w przypadku systemu Windows Server 2008 artykułu pomocy technicznej dla systemu Windows Server 2008 R2.

## <a name="windows-server-2012"></a>Windows Server 2012

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows Server 2012. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 w systemie Windows Server 2012.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w systemie Windows Server 2012 dla okresu istnienia systemu operacyjnego. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji. Deweloperzy można traktować jako takie same, podobnie jak w przypadku systemu Windows Server 2008 R2 artykułu pomocy technicznej dla systemu Windows Server 2012.

## <a name="windows-server-2012-r2"></a>Windows Server 2012 z dodatkiem R2

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows Server 2012 R2. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 w systemie Windows Server 2012 R2.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w systemie Windows Server 2012 R2 dla systemu operacyjnego przez czas ich istnienia. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji. Deweloperzy można traktować jako takie same, podobnie jak w przypadku systemu Windows Server 2012 artykułu pomocy technicznej dla systemu Windows Server 2012 R2.

## <a name="windows-server-2016"></a>Windows Server 2016

Od początkowej wersji to stwierdzenie została wydana systemu operacyjnego Windows Server 2016. Ten dokument został zaktualizowany wyjaśnienie pomocy technicznej firmy Microsoft dla VB6 w systemie Windows Server 2016.

Środowisko uruchomieniowe VB6 wyśle i będą obsługiwane w systemie Windows Server 2016 przez czas ich istnienia systemu operacyjnego. Pliki środowiska uruchomieniowego Visual Basic 6.0 w dalszym ciągu można tylko 32-bitowe i wszystkie składniki muszą być obsługiwane w procesach 32-bitowej aplikacji. Deweloperzy można traktować artykuł pomocy technicznej dla systemu Windows Server 2016 jako takie same, podobnie jak w przypadku systemu Windows Server 2012 R2.

## <a name="supported-windows-operating-system-versions"></a>Obsługiwane wersje systemu operacyjnego Windows

Ta sekcja zawiera dodatkowe informacje dotyczące systemów operacyjnych, które oferują obsługę VB6 pewnego poziomu. 

|System operacyjny Windows|VB6 Obsługiwane środowiska wykonawczego</br>Pliki wysyłania w systemie Windows obsługują?|VB6 Obsługiwane Rutime</br>Rozszerzone pliki</br>do rozprowadzania z aplikacji obsługuje?| VB6 IDE obsługuje?|
|---|---|---|---|
|Windows 10, wszystkie wersje 32-bitowe|Tak *|Tak *|Nie|
|Windows 10, wszystkie wersje 64-bitowe (tylko WOW)|Tak * </br> działa tylko w WOW aplikacje 32-bitowych|Tak* </br> działa tylko w WOW aplikacje 32-bitowych|Nie|
|Windows 8.1, wszystkie wersje 32-bitowe|Tak *|Tak *|Nie|
| Windows 8.1, wszystkie wersje 64-bitowe (tylko WOW)|Tak * </br> działa tylko w WOW aplikacje 32-bitowych|Tak* </br> działa tylko w WOW aplikacje 32-bitowych|Nie|
|Wszystkie wersje 32-bitowe systemu Windows 7|Tak *|Tak *|Nie|
|Windows 7, wszystkie wersje 64-bitowe (tylko WOW)|Tak * </br> działa tylko w WOW aplikacje 32-bitowych|Tak * </br> działa tylko w WOW aplikacje 32-bitowych|Nie|
|Windows Server 2016, wszystkie wersje 64-bitowe (tylko WOW)|Tak* </br> działa tylko w WOW aplikacje 32-bitowych|Tak* </br> działa tylko w WOW aplikacje 32-bitowych|Nie|
|Wszystkie 64-bitowych (tylko WOW) dla systemu Windows Server 2012 R2<br>Windows Server 2012, wszystkie wersje 64-bitowe (tylko WOW)|Tak* </br> działa tylko w WOW aplikacje 32-bitowych|Tak* </br> działa tylko w WOW aplikacje 32-bitowych|Nie|
|Windows Server 2008 R2, x64 wszystkie wersje (tylko WOW)</br>Windows Server 2008, x64 wszystkie wersje (tylko WOW)|Tak * </br> działa tylko w WOW aplikacje 32-bitowych|Tak * </br> działa tylko w WOW aplikacje 32-bitowych|Nie|
|Windows Server 2008, wszystkie wersje 32-bitowe|Tak *|Tak *|Nie|


> [!NOTE]
> &#42;Obsługa środowiska uruchomieniowego VB6 jest ograniczona przez cykl pomocy technicznej systemu Windows.  Na przykład jeśli docelowy system operacyjny jest objęte wsparciem dodatkowym, VB6 nie może mieć wyższego poziomu wsparcia niż wsparciem dodatkowym.  [Systemu Windows obsługuje cyklu życia faktów dotyczących](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet) zawiera cykl życia dodatkowe informacje o bieżących i poprzednich wersjach systemu Windows.

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Użycie środowiska wykonawczego Visual Basic 6.0 wewnątrz VBA i pakietu Office

Visual Basic for Applications lub VBA, to technologia różne najczęściej używanych aplikacji automatyzacji i makra wewnątrz innych aplikacji, najczęściej w aplikacji Microsoft Office. VBA jest dostarczana jako część pakietu Office i w związku z tym obsługę VBA podlega zasadom obsługi pakietu Office. Jednak istnieją sytuacje, w którym VBA służy do wywołania lub udostępniać pliki binarne środowiska wykonawczego Visual Basic 6.0 i kontrolek. W takich przypadkach Visual Basic 6.0 obsługiwane pliki środowiska uruchomieniowego w systemie operacyjnym i listy rozszerzone również są obsługiwane, gdy są używane wewnątrz obsługiwanym środowisku VBA.

Dla VB6 Runtime ― scenariusze obsługiwane wewnątrz VBA należy spełnić wszystkie następujące:

- Wersja systemu operacyjnego hosta dla środowisko uruchomieniowe VB nadal jest obsługiwany.
- Wersja hosta pakietu Office dla VBA nadal jest obsługiwany.
- Pliki środowiska uruchomieniowego zagrożona nadal są obsługiwane.

## <a name="visual-basic-script-vbscript"></a>Skrypt Visual Basic (VBScript)

Skrypt VBScript jest związana z Visual Basic 6.0 i niniejszych pomocy technicznej. Jednak VBScript jest obecnie wysyłania jako część systemu Windows 7, Windows 8.1, Windows 10, Windows Server 2008 R2, Windows Server 2012 R2 i Windows Server 2016 w tym w tym i podlega cykl pomocy technicznej systemu operacyjnego.

## <a name="third-party-components"></a>Składników innych firm

Microsoft nie może zapewnić obsługę dla składników innych firm, takich jak OCX/formantów. Zachęcamy klientów, skontaktuj się z dostawcą kontrolki, aby uzyskać więcej informacji na temat obsługi tych składników.

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Zgłaszanie problemów z aplikacji VB 6.0 uruchomionych w systemie Windows

Deweloperzy planowane jest używanie Visual Basic 6.0 z jednym z listy systemów operacyjnych Windows należy zainstalować tego systemu operacyjnego i rozpoczęcie testowania zgodności aplikacji przy użyciu oryginalnego testów akceptacyjnych aplikacji.

Jeśli napotkasz problem z aplikacji Visual Basic 6.0 uruchomionej na jednym z systemów operacyjnych Windows wymienionych wykonaj inne kanały normalne pomocy technicznej, aby zgłosić problem.

## <a name="supported-and-shipping-in-windows"></a>Obsługiwane i wysyłanie w systemie Windows

| | | | |
|---|---|---|---|
|atl.dll|         msadcor.dll|     msorcl32.dll|   ole2.dll|
|asycfilt.dll|    msadcs.dll|      msvbvm60.dll|   ole32.dll|
|comcat.dll|      msadds.dll|      msvcirt.dll|    oleaut32.dll|
|compobj.dll|     msaddsr.dll|     msvcrt.dll|     oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    msvcrt40.dll|   oledb32.dll|
|dcomcnfg.exe|    msado15.dll|     mtxdm.dll|      oledb32r.dll|
|dllhost.exe|     msador15.dll|    mtxoci.dll|     oledlg.dll|
|ds16gt.dll|      msadrh15.dll|    odbc16gt.dll|   Olepro32.dll|
|ds32gt.dll|      mscpxl32.dll|    odbc32.dll|     Olethk32.dll|
|expsrv.dll|      msdadc.dll|      odbc32gt.dll|   regsvr32.exe|
|hh.exe|          msdaenum.dll|    odbcad32.exe|   rpcns4.dll|
|hhctrl.ocx|      msdaer.dll|      odbccp32.cpl|   rpcrt4.dll|
|imagehlp.dll|    msdaora.dll|     odbccp32.dll|   scrrun.dll|
|iprop.dll|       msdaosp.dll|     odbccr32.dll|   secur32.dll|
|ITIRCL.dll|      msdaprst.dll|    odbccu32.dll|   simpdata.tlb|
|ITSS.dll|        msdaps.dll|      odbcint.dll|    sqloledb.dll|
|mfc40.dll|       msdasc.dll|      odbcji32.dll|   sqlsrv32.dll|
|mfc42.dll|       msdasql.dll|     odbcjt32.dll|   stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    odbctrac.dll|   stdole32.tlb|
|msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    vbajet32.dll|
|msadcf.dll|      msdfmap.dll|     odfox32.dll|    vfpodbc.dll|
|msadcfr.dll|     msdfmap.ini|     odpdx32.dll|                |
|msadco.dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>Pliki środowiska uruchomieniowego obsługiwanych do rozprowadzania z aplikacji

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |msstdfmt.dll| 
|comct332.ocx |mscdrun.dll  |msflxgrd.ocx  |msstkprp.dll| 
|comctl32.ocx |mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|comdlg32.ocx |mscomct2.ocx |mshtmpgr.dll  |mswinsck.ocx| 
|dbadapt.dll  |mscomctl.ocx |msinet.ocx    |picclp32.ocx| 
|dbgrid32.ocx |mscomm32.ocx |msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |msdatgrd.ocx |msmask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>Obsługiwane, ale obsługiwane i zgodny uaktualnienia lub aktualizacje są dostępne

| | | | |
|---|---|---|---|
|dao350.dll|   msexch35.dll| msjter35.dll| Msrepl35.dll|
|mdac_typ.exe| msexcl35.dll| msjtor35.dll| mstext35.dll|
|mschart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>Pliki środowiska uruchomieniowego nieobsługiwane

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  rdocurs.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   vbar332.dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  visdata.exe|
|autmgr32.exe| ciscnfg.exe|  rpcss.exe|     vsdbflex.srg|
|autprx32.dll| olecnv32.dll| dbmsshrn.dll|  threed32.ocx|
|racmgr32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  windbver.exe|  tlbinf32.dll|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   triedit.dll|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>Lokalizacja plików binarnych z pomocy technicznej

Następujące pliki binarne są niezbędne do obsługi aplikacji Visual Basic 6.0 uruchomionych na zlokalizowane wersje systemu operacyjnego Windows. Są obsługiwane, ale nie są wysyłane w systemie Windows. Pliki te są wymagane do wysłania z ustawień aplikacji.

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>Pliki środowiska uruchomieniowego obsługiwanych do rozprowadzania z aplikacji

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|


---
title: Kody błędów dla aplikacji środowiska wykonawczego systemu Windows przy użyciu języka JavaScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/10/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- JavaScript, Windows Runtime error codes
- VS.WebClient.Help.APPHOST9601
- VS.WebClient.Help.APPHOST9602
- VS.WebClient.Help.APPHOST9603
- VS.WebClient.Help.APPHOST9604
- VS.WebClient.Help.APPHOST9605
- VS.WebClient.Help.APPHOST9606
- VS.WebClient.Help.APPHOST9607
- VS.WebClient.Help.APPHOST9608
- VS.WebClient.Help.APPHOST9610
- VS.WebClient.Help.APPHOST9611
- VS.WebClient.Help.APPHOST9613
- VS.WebClient.Help.APPHOST9614
- VS.WebClient.Help.APPHOST9615
- VS.WebClient.Help.APPHOST9616
- VS.WebClient.Help.APPHOST9617
- VS.WebClient.Help.APPHOST9618
- VS.WebClient.Help.APPHOST9619
- VS.WebClient.Help.APPHOST9620
- VS.WebClient.Help.APPHOST9623
- VS.WebClient.Help.APPHOST9624
- VS.WebClient.Help.APPHOST9626
ms.assetid: 4c6d4e90-602a-4b56-ae74-3458929da442
caps.latest.revision: 1
author: erikadoyle
ms.author: edoyle
manager: jken
ms.openlocfilehash: 89b91a3246d0a6e2980459c2c35c7361168bccd4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792247"
---
# <a name="error-codes-for-windows-runtime-apps-using-javascript"></a>Kody błędów dla aplikacji środowiska wykonawczego systemu Windows przy użyciu języka JavaScript
Poniżej przedstawiono kody błędów, wyświetlane przez konsolę programu Microsoft Visual Studio podczas opracowywania aplikacji środowiska wykonawczego systemu Windows przy użyciu języka JavaScript.
  
Błąd | Uwagi
----- | -------
APPHOST9601: "nie można załadować *remoteURI*. Aplikacji nie można załadować zawartości sieci web do zdalnego w kontekście lokalnego." | Aby uzyskać więcej informacji na temat dozwolonych w kontekście sieci web, zobacz [funkcje i ograniczenia dotyczące przez kontekst](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9602: "" javascript: "jest nieprawidłową wartością atrybutu i zostaną zignorowane. Nie używaj "javascript:" identyfikatorów URI w kontekście lokalnego. " | Ze względów bezpieczeństwa nie można użyć "javascript:" identyfikatorów URI w kontekście lokalnego. Aby uzyskać więcej informacji na temat dozwolonych w kontekście lokalnego, zobacz [funkcje i ograniczenia dotyczące przez kontekst](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9603: "nie można załadować wtyczki ActiveX, który ma identyfikator klasy *classID*.  Aplikacji nie można załadować kontrolki ActiveX." | Aplikacje środowiska wykonawczego systemu Windows przy użyciu języka JavaScript nie obsługują niestandardowych ActiveXcontrols firmy Microsoft. Formantu interfejsu użytkownika, należy użyć formantu standardowe sieci web, Biblioteka formantów, lub utworzyć własne kontrolki niestandardowej. Jeśli zachodzi potrzeba wykonania niestandardowej logiki, należy utworzyć niestandardowego obiektu środowiska wykonawczego systemu Windows. Informacje o innych różnic, HTML, CSS i JavaScript, zobacz [funkcji HTML, CSS i JavaScript i różnice](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9604: "nie można przejść do *uri* ponieważ używa kodowania nieprawidłowy znak.  Aplikację można przechodzić tylko do plików z kodowaniem UTF8." | HTML, JavaScript i CSS dostęp do środowiska wykonawczego systemu Windows musi być zakodowany jako Format transformacji 8-bitową Unicode (UTF-8). Informacje o innych różnic, HTML, CSS i JavaScript, zobacz [funkcji HTML, CSS i JavaScript i różnice](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465380.aspx).
APPHOST9605: "nie można przejść do *targetURI* z *sourceURI* ponieważ miejsce docelowe URI w wyższych strefę zabezpieczeń. Nie można nawigować ze strefy z niższych zabezpieczeń do strefy z wyższy poziom zabezpieczeń chyba że w przypadku przechodzenia do lokalny kontekst identyfikatora URI, z kontekstu identyfikatora URI sieci web i Lokalny kontekst identyfikatora URI został zarejestrowany za pomocą metody MSApp.addPublicLocalApplicationUri." | Aby uzyskać więcej informacji, zobacz [MSApp.addPublicLocalApplicationUri](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465759.aspx).
APPHOST9606: "nie można załadować *uri* ponieważ używa połączenia HTTP i ma element meta ms https połączenia — tylko. Tylko połączenia HTTPS są dozwolone, gdy używasz element meta ms https połączenia — tylko. Użyj połączenia HTTPS lub, jeśli nie ma potrzeby bezpiecznego połączenia, Usuń meta element." | Aby uzyskać więcej informacji, zobacz [sposobu wymagać połączenia HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9607: "aplikacji nie mogą być uruchamiane w identyfikatorze URI *uri* z powodu tego błędu: *failureCode*." | Brak zasobów lub nieprawidłowy plik są typowe przyczyny tego błędu.
APPHOST9608: "aplikacji nie można przejść do o: pustej strony z powodu tego błędu: *errorCode*." | 
APPHOST9610: "aplikacja napotkał błąd podczas przygotowywania do przejścia do strony błędu niestandardowego: *errorCode*." |
APPHOST9611: "aplikacji nie można przejść do strony błędu niestandardowego z powodu tego błędu: *errorCode*." |
APPHOST9613: "aplikacji nie można przejść do * identyfikator uri * z powodu tego błędu: *errorCode*." | 
APPHOST9614: "dokumentu w ramce żądany *requestedDocMode* tryb doc, ale system wymusza *currentDocMode* tryb dokumentu. Element iframe użyje *currentDocMode* tryb dokumentu. " | Aby uzyskać więcej informacji na temat wyświetlania zawartości sieci web do zdalnego, zobacz [jak połączyć, aby zewnętrzne strony sieci web](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9615: "aplikacja nie może pobrać pliku w *uri* ponieważ został wywołany programowo poza kontekstem lokalnego." | Występuje, gdy zawartość w kontekście sieci web próbuje programowo pobierania pliku.
APPHOST9616: "tego identyfikatora URI nie można użyć używanie funkcji geolokalizacji interfejsów API.  Używanie funkcji Geolokalizacji interfejsy API mogą być wywoływane tylko z identyfikatorem URI, który jest częścią pakietu lub znajduje się w elemencie ApplicationContentUris manifestu." | Aby uzyskać więcej informacji na temat dozwolonych w kontekście sieci web, zobacz [funkcje i ograniczenia dotyczące przez kontekst](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9617: "tego identyfikatora URI nie można używać interfejsów API schowka.  Interfejsy API Schowka można wywołać tylko z identyfikatorem URI, który jest częścią pakietu lub znajduje się w elemencie ApplicationContentUris manifestu." | Aby uzyskać więcej informacji na temat dozwolonych w kontekście sieci web, zobacz [funkcje i ograniczenia dotyczące przez kontekst](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9618: "tego identyfikatora URI nie można użyć window.close.  Metoda window.close można wywołać tylko z pakietów zawartości, która została załadowana z ms-appx schemat identyfikatora URI." | Aby uzyskać więcej informacji na temat dozwolonych w kontekście sieci web, zobacz [funkcje i ograniczenia dotyczące przez kontekst](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465373.aspx).
APPHOST9619: "aplikacji nie można przejść do *uri* ponieważ strony w kontekście sieci web nie może być aplikacji najwyższego poziomu dokumentu. Załadować stronę w trybie iframe." | Nie można nawigować strony najwyższego poziomu do zdalnej strony sieci web, ale aplikacji można wyświetlić strony sieci web w [iframe](https://msdn.microsoft.com/en-us/library/ms535258(v=vs.85).aspx). Aby uzyskać więcej informacji na temat wyświetlania zawartości sieci web do zdalnego, zobacz [jak połączyć, aby zewnętrzne strony sieci web](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh780594.aspx).
APPHOST9620: "Ta aplikacja została zamknięta, ponieważ on połączeń HTTP i ma element meta ms https połączenia — tylko. Tylko połączenia HTTPS są dozwolone, gdy używasz element meta ms https połączenia — tylko. Użyj połączenia HTTPS lub, jeśli nie wymaga bezpiecznego połączenia, Usuń meta element." | Aby uzyskać więcej informacji, zobacz [sposobu wymagać połączenia HTTPS](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh452771.aspx).
APPHOST9623: "nie można rozpoznać aplikacji *adres url* z powodu tego błędu: *errorCode*." | Typową przyczyną tego błędu jest Brak pliku.  
APPHOST9624: "aplikacji nie można użyć skryptu, aby załadować *adres url* adres url, ponieważ adres url Uruchamia inną aplikację. Tylko bezpośredniej interakcji użytkownika można uruchomić innej aplikacji." | Aplikacji nie można bezpośrednio uruchomić inne aplikacje. Jeśli aplikacja korzysta pewnych kontrakty można uruchomić inne aplikacje przez użytkownika. Aby uzyskać więcej informacji, zobacz [kontrakty aplikacji i rozszerzenia](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh464906.aspx).
APPHOST9626: "bezpośrednie odwołanie do pliku zasobów `ms-appx://1d33240b-0b00-40e4-a416-a4750c48787f/ja-jp\images\logo.scale-140.png` został wykryty. To odwołanie powoduje, że błędy, gdy jest używany poza środowiskiem debugowania." | Ze względu na ścieżce `logo.scale-140.png`, ten plik PNG jest traktowany jako zasób zlokalizowanych przyczyną błędu w tym zlokalizowanych zasobów nie może odwoływać się bezpośrednio. Zobacz [Globalizowanie aplikacji (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/xaml/hh465006.aspx) Jeśli zamierzasz używać tego pliku jako zasób języka. W przeciwnym razie spróbuj, zmiana nazwy katalogu powodować problemy.
  
## <a name="see-also"></a>Zobacz też  
 [W języku JavaScript za pomocą środowiska wykonawczego systemu Windows](../jswinrt/using-the-windows-runtime-in-javascript.md)
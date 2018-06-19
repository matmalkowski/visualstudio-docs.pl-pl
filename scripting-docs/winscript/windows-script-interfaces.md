---
title: Interfejsy skryptów systemu Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 200a1ac1bf273e2515e1e17b6f83c2020ff9884d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796498"
---
# <a name="windows-script-interfaces"></a>Interfejsy skryptów systemu Windows
Interfejsy skryptów systemu Windows firmy Microsoft zapewnia możliwości aplikacji, aby dodać skryptów i automatyzacji OLE. Wykonywanie skryptów hosty, które zależą od skryptów systemu Windows umożliwia aparatów skryptów z wielu źródeł i dostawców Zarządzanie skryptów między składnikami. Implementacja sam skrypt — języka, składni, trwałym formacie, model wykonania itd. — pozostało do dostawcy skryptu.  
  
 Dokumentacja skryptów systemu Windows jest podzielony na następujące sekcje:  
  
 [Hosty skryptów systemu Windows](../winscript/windows-script-hosts.md)  
  
 [Aparaty skryptów systemu Windows](../winscript/windows-script-engines.md)  
  
 [Przegląd debugowania aktywnego skryptu](../winscript/active-script-debugging-overview.md)  
  
 [Przegląd profilowania aktywnego skryptu](../winscript/active-script-profiling-overview.md)  
  
 [Odwołania skryptów systemu Windows](../winscript/reference/windows-script-interfaces-reference.md)  
  
## <a name="windows-script-background"></a>Tło skryptu systemu Windows  
 Interfejsy skryptów systemu Windows można podzielić na dwie kategorie: hosty skryptów systemu Windows i aparaty skryptów systemu Windows. Host tworzy aparat skryptów i wywołania na aparacie uruchamiania skryptów. Przykłady hosty skryptów systemu Windows:  
  
-   Microsoft Internet Explorer  
  
-   Narzędzia do tworzenia Internet  
  
-   Powłoka  
  
 Aparaty skryptów systemu Windows mogą być opracowane dla dowolnego języka lub w środowisku, w tym:  
  
-   Microsoft Visual Basic Scripting Edition (VBScript)  
  
-   Perl  
  
-   Lisp  
  
 Aby zapewnić możliwie najbardziej elastyczne implementacja hosta, znajduje się automatyzacji OLE otoki dla skryptu systemu Windows. Hosta, który używa tego obiektu otoki można utworzyć wystąpienia aparatu skryptów nie ma jednak stopień kontroli nad przestrzeń nazw środowiska wykonawczego, trwałości modelu i który będzie używany skryptu systemu Windows bezpośrednio.  
  
 Projekt Windows Script izoluje elementów interfejsu wymagane tylko w środowisku tworzenia pakietów administracyjnych, aby hosty nonauthoring (takie jak przeglądarki i przeglądarki) i aparatów skryptów (na przykład VBScript) mogą być przechowywane lightweight.  
  
## <a name="windows-script-basic-architecture"></a>Podstawowa architektura skryptu systemu Windows  
 Na poniższej ilustracji przedstawiono interakcje między hostem skryptów systemu Windows i aparat skryptu systemu Windows.  
  
 Etapy interakcji między hostem a aparatu są podane poniżej.  
  
1.  Tworzenie projektu. Host ładuje projekt lub dokumentu. (Ten krok nie jest konkretnym do skryptu systemu Windows, ale został tu zawarty, aby informacje były kompletne).  
  
2.  Utwórz aparat skryptów systemu Windows. Wywołania hosta `CoCreateInstance` Aby utworzyć nowy aparat skryptu systemu Windows, określając identyfikator klasy (CLSID) z określonego aparatu skryptów do użycia. Na przykład przeglądarki HTML programu Internet Explorer otrzymuje identyfikator klasy aparat skryptów za pomocą identyfikatora CLSID = atrybutu HTML \<obiektu > tagu.  
  
3.  Ładowanie skryptu. Jeśli utrwalone zawartość skryptu host wywołuje aparat skryptu `IPersist*::Load` metoda ze źródłem jego skrypt zbioru magazynu, strumienia lub właściwości. W przeciwnym razie host używa `IPersist*::InitNew` lub [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metodę, aby utworzyć skrypt wartości null. Host, który obsługuje skrypt jako tekst można używać [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) ze źródłem tekst skryptu, aparat skryptów po wywołaniu `IActiveScriptParse::InitNew`.  
  
4.  Dodaj nazwanych elementów. Dla każdego najwyższego poziomu o nazwie elementu (takich jak strony i formularze) zaimportowane do przestrzeni nazw aparat skryptów, wymaga hosta [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) metodę w celu utworzenia wpisu w przestrzeni nazw przez aparat. Ten krok nie jest konieczne, jeśli elementy najwyższego poziomu o nazwie jest już częścią programu trwały stan skrypt ładowane w kroku 3. Host nie używa `IActiveScript::AddNamedItem` można dodać podpoziomu o nazwie elementy (takie jak kontrolki na stronie HTML); zamiast aparat pośrednio uzyskuje podpoziomu elementów z elementów najwyższego poziomu przy użyciu hosta `ITypeInfo` i `IDispatch` interfejsów.  
  
5.  Uruchom skrypt. Host powoduje, że aparat uruchomienia skryptu przez ustawienie flagi SCRIPTSTATE_CONNECTED w [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) metody. To wywołanie prawdopodobnie przeprowadziłby wszelkich skryptów aparatu konstrukcji pracy, w tym statycznych powiązanie, Podłączanie do zdarzeń (patrz poniżej) i wykonywanie kodu, w sposób podobny do skryptową `main()` funkcji.  
  
6.  Pobierz informacje o elementach. Zawsze musi aparat skryptu do skojarzenia z elementem najwyższego poziomu, symbol wywołuje [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) metodę, która zwraca informacje na temat danego elementu.  
  
7.  Podpinanie zdarzeń. Przed uruchomieniem skryptu rzeczywiste, aparat skryptów łączy się zdarzenia odpowiednich obiektów za pomocą `IConnectionPoint` interfejsu.  
  
8.  Wywoływanie właściwości i metody. Jak skrypt jest uruchamiany, aparat skryptów realizuje odwołań do właściwości i metod do nazwanych obiektów za pomocą `IDispatch::Invoke` lub innych standardowych mechanizmów powiązanie OLE.  
  
## <a name="windows-script-terms"></a>Warunki skryptu systemu Windows  
 Ta lista zawiera definicje terminów związanych z skryptów używanych w tym dokumencie.  
  
|Termin|Definicja|  
|----------|----------------|  
|Kod obiektu|Wystąpienia utworzone przez aparat skryptów, który jest skojarzony z elementem nazwanego, takich jak modułu formularza w języku Visual Basic lub klasę C++ skojarzone z nazwanego elementu. Najlepiej jest obiekt OLE składnika modelu COM (Object), który obsługuje automatyzacji OLE, więc hosta lub innego podmiotu niż skryptu można manipulować obiektu kodu.|  
|Element o nazwie|Obiekt OLE COM (najlepiej jedną, która obsługuje automatyzacji OLE) czy hosta uzna interesujące do skryptu. Przykładami strony HTML i przeglądarki w przeglądarce sieci Web, dokumentów i okien dialogowych w programie Microsoft Word.|  
|Skrypt|Dane, które tworzy program, który uruchamia aparatu skryptów. Skrypt może być ciągłe danych pliku wykonywalnego, łącznie z fragmentów tekstu, bloki `pcode`, a nawet kody bajtów wykonywalnego komputera. Host ładuje skrypt do aparatu skryptów za pomocą jednego z `IPersist*` interfejsów lub za pomocą [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsu.|  
|Aparat skryptów|Obiekt OLE, który przetwarza skryptów. Aparat skryptów implementuje [IActiveScript](../winscript/reference/iactivescript.md) i, opcjonalnie, [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsów.|  
|Host skryptów|Aplikacja lub program, który jest właścicielem aparat skryptów systemu Windows. Implementuje hosta [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) i, opcjonalnie, [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) interfejsów.|  
|Skryptlet|Część skryptu, który pobiera dołączony do obiektu za pomocą [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsu. Łączny kolekcja skryptlety jest skrypt.|  
|Język skryptów|Język jest skrypt napisane (VBScript, na przykład) i semantyka tego języka.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy skryptów systemu Windows](../winscript/windows-script-interfaces.md)
---
title: "Aparaty skryptów systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2191b8e76e2b96d05633156d09a08b5416faae90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="windows-script-engines"></a>Aparaty skryptów systemu Windows
Aby zaimplementować aparat skryptów systemu Windows firmy Microsoft, Utwórz obiekt OLE COM, który obsługuje następujące interfejsy.  
  
|||  
|-|-|  
|Interface|Opis|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Zapewnia podstawowe możliwości obsługi skryptów. Wymagana jest implementacja tego interfejsu.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Umożliwia dodawanie tekstu skryptu, obliczać wyrażeń i tak dalej. Implementację tego interfejsu jest opcjonalna. Jednak jeśli nie jest zaimplementowana, aparat skryptu musi implementować jeden z interfejsów IPersist * aby załadować skryptu.|  
|IPersist *|Zapewnia obsługę trwałości. Wymagana jest implementacja co najmniej jeden z następujących interfejsów, jeśli [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) nie jest zaimplementowana.<br /><br /> IPersistStorage: Zapewnia obsługę danych = {url} atrybut w tagu OBJECT.<br /><br /> IPersistStreamInit: Zapewnia obsługę taka sama jak `IPersistStorage` oraz danych = "strumień bajtów zakodowany ciąg" atrybut w tagu OBJECT.<br /><br /> IPersistPropertyBag: Zapewnia obsługę PARAM = atrybut w tagu OBJECT.|  
  
> [!NOTE]
>  Istnieje możliwość, że aparat skryptów będą nigdy nie zobowiązane do zapisania lub przywrócenia stanu skryptu, za pośrednictwem `IPersist*`. Zamiast tego [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) jest używany przez wywołanie metody [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) Aby utworzyć skrypt puste, następnie skryptlety są dodawane i podłączone do zdarzeń o [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md) i dodaje się kod ogólne [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Niemniej jednak aparat skryptów pełni zaimplementować co najmniej jeden `IPersist*` interfejs (najlepiej `IPersistStreamInit`), ponieważ inne aplikacje hosta spróbuj wprowadzić korzystać z nich.  
  
 W poniższych sekcjach opisano Implementowanie aparatu skryptów systemu Windows bardziej szczegółowo.  
  
 Zobacz [odwołania skryptów systemu Windows](../winscript/reference/windows-script-interfaces-reference.md) Aby uzyskać więcej informacji.  
  
## <a name="registry-standard"></a>Standard rejestru  
 Aparat skryptów systemu Windows można zidentyfikować przy użyciu identyfikatorów kategorii. Skrypt Windows definiuje obecnie dwóch identyfikatorów kategorii.  
  
|||  
|-|-|  
|Kategoria|Opis|  
|CATID_ActiveScript|Wskazuje, że identyfikatorów klasy (CLSID) aparaty skryptów systemu Windows, które obsługują co najmniej [IActiveScript](../winscript/reference/iactivescript.md) interfejsu i mechanizmu stanu trwałego ( `IPersistStorage`, `IPersistStreamInit`, lub IPersistPropertyBag interface).|  
|CATID_ActiveScriptParse|Wskazuje, że CLSID aparaty skryptów systemu Windows, które obsługują co najmniej [IActiveScript](../winscript/reference/iactivescript.md) i [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsów.|  
  
 Mimo że [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) nie jest mechanizm trwałości wartość true, obsługuje on [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metodę, która jest funkcjonalnym odpowiednikiem `IPersist*::InitNew`.  
  
## <a name="script-engine-states"></a>Stany aparatu skryptu  
 W dowolnym momencie aparat skryptów systemu Windows może być jeden z kilku stanów.  
  
|||  
|-|-|  
|Stan|Opis|  
|nie zainicjalizowano|Skrypt nie został zainicjowany lub ładowane przy użyciu interfejsu IPersist * lub nie ma [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejs zestaw. Aparat skryptów zazwyczaj nie jest używany z tego stanu do momentu załadowania skryptu.|  
|zainicjowana|Skrypt został zainicjowany z `IPersist*` interfejsu i ma [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu zestawu, ale nie jest podłączony do obiektów hosta i wychwytywanie zdarzeń. Należy pamiętać, że ten stan po prostu oznacza, że `IPersist*::Load`, `IPersist*::InitNew`, lub [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metoda została zakończona oraz że [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) została wywołana metoda. Aparat nie może uruchomić kod w tym trybie. Kod, który hosta przekazuje do niego za pośrednictwem kolejek aparat [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) metody i wykonuje kod po przechodzenia do stan uruchomienia.<br /><br /> Ponieważ języki mogą mieć różne powszechnie semantykę, aparatów skryptów nie są wymagane do obsługi tej zmiany stanu. Silniki obsługujące [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) — metoda jednak musi obsługiwać ten proces przejścia stanu. Hosty muszą przygotować tego przejścia i podejmij odpowiednią akcję: Zwolnij bieżącego aparatu skryptów, Utwórz nowy aparat skryptów i wywołania `IPersist*::Load`, `IPersist*::InitNew`, lub [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (i prawdopodobnie także wywołać [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). Optymalizacja powyższych kroków można rozważyć użycie ten proces przejścia. Zauważ, że wszystkie informacje o nazwach elementów o nazwie uzyskał aparat skryptów i informacje o typie o nazwie elementy opisujące pozostaje ważny.<br /><br /> Ponieważ języków różnią Definiowanie dokładnego semantyka ten proces przejścia jest trudne. Co najmniej aparat skryptów musi odłączyć od wszystkich zdarzeń i zwolnij wszystkie wskaźniki SCRIPTINFO_IUNKNOWN można uzyskać przez wywołanie [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) metody. Aparat ponownie uzyskać te wskaźniki po ponownym uruchomieniu skryptu. Aparat skryptów powinny również przywrócić skrypt początkowy stan, który jest odpowiedni dla języka. Skrypt VBScript, na przykład resetuje wszystkie zmienne i zachowuje dowolny kod dynamicznie dodawany przez wywołanie [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) z SCRIPTTEXT_ISPERSISTENT Flaga. Inne języki trzeba zachować bieżące wartości (na przykład Lisp, ponieważ nie istnieje żadne separację kodu/danych) lub zresetować do dobrze znanego stanu (dotyczy to również języków ze zmiennymi statycznie zainicjowane).<br /><br /> Należy pamiętać, że przejście do stan uruchomienia powinny mieć tej samej semantyki (to znaczy powinien dawać aparat skryptów w takim samym stanie) jako wywoływania IPersist*::Save zapisać aparat skryptów, a następnie wywołując IPersist\*:: aparat obciążenia, aby załadować nowy skryptów; te akcje powinny mieć tej samej semantyki jako [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md). Skryptów, które jeszcze nie obsługuje IActiveScript::Clone lub `IPersist*` starannie rozważyć sposób przejścia do stan uruchomienia zachowania w przypadku, dzięki czemu takie przejście nie naruszyłoby powyższe warunki, jeśli IActiveScript::Clone lub `IPersist*` później dodano obsługę.<br /><br /> Podczas tego przejścia na stan uruchomienia aparatu skryptów spowoduje rozłączenie wychwytywanie zdarzeń po odpowiednich destruktory i tak dalej, są wykonywane w skrypcie. Aby uniknąć tych destruktory wykonywane, host może najpierw przenieść skrypt w stanie rozłączenia przed przejściem w stan uruchomienia.<br /><br /> Użyj [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) na zakończenie działania, aby anulować uruchomiony wątek skryptu bez oczekiwania na bieżącym zdarzeń i itd.|  
|Rozpoczęto|Przejście z stanie zainicjowania na stan uruchomienia powoduje, że aparat do wykonania kodu, który został umieszczony w stanie zainicjowania. Aparat może uruchomić kod znajduje się w stanie uruchomienia, ale nie jest podłączony do żadnych zdarzeń dodane za pośrednictwem [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) metody. Aparat może uruchomić kod, wywołując interfejs IDispatch uzyskane z [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) metody, lub przez wywołanie metody [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Istnieje możliwość tego dalsze inicjowania tła (progresywnego obciążenia) jest nadal uruchomione i że wywołania [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) metody z ustawioną flagą SCRIPTSTATE_CONNECTED może spowodować skryptu, aby zablokować przed zakończeniem inicjowania.|  
|połączone|Skrypt jest załadowany i połączony wychwytywanie zdarzeń z obiektami hostów. Jeśli jest to przejście ze stanu zainicjowane, aparat skryptów powinny przejście za pośrednictwem stan uruchomienia, wykonywanie niezbędne działania przed wprowadzanie stan połączenia i nawiązywania połączenia z zdarzenia.|  
|odłączony|Skrypt jest załadowany i ma stan czasu wykonywania, ale jest tymczasowo odłączone od wychwytywanie zdarzeń z obiektami hostów. Można to zrobić albo logicznie (Ignorowanie zdarzeń odebranych) lub fizycznie (wywołanie IConnectionPoint::Unadvise w punktach odpowiedniego połączenia). Jeśli jest to przejście ze stanu zainicjowane, aparat skryptów powinny przejście za pośrednictwem stan uruchomienia, wykonywania przed wejściem w stanie rozłączenia odpowiednie działania. Wychwytywanie zdarzeń, które są w toku zostały zakończone przed zmianą stanu (Użyj [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) anulować uruchomiony wątek skryptu). Ten stan jest różnią się od zainicjowane przejście do ten stan nie powoduje, że skrypt zresetować, stan czasu wykonywania skryptu nie jest resetowany i nie została wykonana procedura inicjowania skryptu.|  
|zamknięte|Skrypt został zamknięty. Aparat skryptów już nie działa i zwraca informacje o błędach dla większości metod.|  
  
 Poniższa ilustracja przedstawia relacje między różnymi stanami aparatu skryptów i przedstawia metody, które powodują przejść z jednego stanu do innego.  
  
 Na poniższej ilustracji przedstawiono akcje, że aparat skryptów jest wykonywane podczas różnych przejścia stanu.  
  
## <a name="scripting-engine-threading"></a>Wątkowość aparatu skryptów  
 Ponieważ aparat skryptów systemu Windows mogą być używane w wielu środowiskach, należy zachować jak najbardziej elastyczny model jego wykonania. Na przykład na serwerze hosta może być konieczne zachować wielowątkowych projektu podczas wydajne przy użyciu skryptu systemu Windows. W tym samym czasie hosta, który nie korzysta z wątków, takie jak typowa aplikacja, nie powinny obciążać z wątków zarządzania. Windows Script osiąga tej równowagi przez ograniczenie sposoby bezwątkowe aparat skryptów można wywołania zwrotnego na hoście zwalniania hosty z tym obciążenia.  
  
 Aparaty skryptów używane na serwerach zwykle są zaimplementowane jako wolny wątkowość obiektów COM. Oznacza to, że metody [IActiveScript](../winscript/reference/iactivescript.md) interfejsu i skojarzone interfejsy może zostać wywołana z dowolnego wątku w procesie, bez przekazywanie. (Niestety, oznacza to również czy aparat skryptów muszą zostać zaimplementowane jako serwer w procesie, ponieważ OLE nie obsługuje obecnie międzyprocesowej kierowanie obiekty bezwątkowe.) Synchronizacja jest odpowiedzialny aparat skryptów. Dla skryptów, które nie są współużytkowane wewnętrznie lub modeli języka, które nie są wielowątkowe synchronizacji można tak proste, jak serializacji dostęp do aparatu skryptów z obiektu mutex. Oczywiście niektórych metod, takich jak [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md), nie powinien podlegać serializacji w ten sposób, dzięki czemu można przerywać działanie skryptu zablokowane z innego wątku.  
  
 Fakt który [IActiveScript](../winscript/reference/iactivescript.md) jest zwykle bezwątkowe zazwyczaj oznacza, że [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejs i model obiektu hosta powinien być bezwątkowe również. Może to być implementacji hosta bardzo trudne, szczególnie w typowych przypadkach, gdy host jest jednowątkowy aplikacji systemu Windows z formantami ActiveX jednowątkowe lub modelu typu apartment w jego modelu obiektów. Z tego powodu następujące ograniczenia są umieszczane na używanie aparatu skryptów [IActiveScriptSite](../winscript/reference/iactivescriptsite.md):  
  
 Skrypt lokacji zawsze jest wywoływana w kontekście wątku hosta. Oznacza to, skryptów aparatu nigdy nie lokacji skryptu w kontekście wątku utworzony przez aparat skryptów, ale tylko za pomocą skryptów aparatu metodę, która została wywołana z hosta przy użyciu wywołania [IActiveScript](../winscript/reference/iactivescript.md) i jego pochodne za pośrednictwem obiektu dyspozytora narażonych aparatu skryptów, za pomocą komunikatów systemu Windows lub z źródłem zdarzeń w modelu obiektu hosta.  
  
 W kontekście wątku proste metody kontroli stanu lokacji skrypt nigdy nie jest wywoływana z (na przykład [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) metody) lub z [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy skryptów systemu Windows](../winscript/windows-script-interfaces.md)
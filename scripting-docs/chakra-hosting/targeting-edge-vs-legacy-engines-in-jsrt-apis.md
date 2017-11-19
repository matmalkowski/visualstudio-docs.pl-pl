---
title: Projektowanie dla programu Edge a Starsze aparaty w interfejsach API JsRT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbc7df6c-0bc9-48f5-b9ad-b9ed31c42f92
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50947cbd619f086daecc1e09f88a4b238a36ee41
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="targeting-edge-vs-legacy-engines-in-jsrt-apis"></a>Projektowanie dla programu Edge a Starsze aparaty w interfejsach API JsRT
Począwszy od systemu Windows 10, jedną ze zmian, które wprowadziliśmy Chakra (aparat JavaScript), który jest wyrównywana z systemu Windows 10 przeglądarki strategii obsłużyć nowy aparat renderowania krawędzi, służy do obsługi dwóch różnych aparaty Chakra:  
  
-   Aparat Chakra stary (nazywane również *starszego aparatu* lub jscript9.dll poniżej) jest dostarczany z i obsługuje program Internet Explorer 11. Ten aparat jest zablokowane w czasie i zostaną całkowicie zmienione od wydania systemu Win8.1/IE11.  
  
-   Nowy aparat Chakra (nazywane również *aparat krawędzi* lub chakra.dll poniżej) jest dostarczany z i obsługuje Nowa przeglądarka w systemie Windows 10, Microsoft Edge. Ten aparat będą stale aktualizowane i będzie obsługiwać "życia" [krawędzi](http://blogs.msdn.com/b/ie/archive/2014/11/11/living-on-the-edge-our-next-step-in-interoperability.aspx) aparatu. Życia krawędzi aparat oznacza, że w przeciwieństwie do starszego aparatu aparat krawędzi czy nie przeniesieniu dowolnej formy versioning funkcja skryptu do uczestnictwa w.  
  
 Podczas tworzenia aplikacji za pomocą języka JavaScript środowiska uruchomieniowego hostingu (JsRT) interfejsu API, można wybrać objęcie starszych lub aparat krawędzi.  
  
-   Jeśli potrzebujesz wyróżnić zgodności z poprzednimi wersjami istniejących aplikacji, cel starszego aparatu.  
  
-   Jeśli chcesz, aby aplikacja należy do przodu wyszukiwania i obsługę nowych JavaScript funkcji jako są wydawane (na przykład jest używany język ECMAScript 6), celem aparat krawędzi.  
  
 Ten temat zawiera szczegółowe informacje, które opisują sposób pod kątem aparatów inny.  
  
## <a name="target-your-preferred-version"></a>Docelowa preferowanych wersji  
 Podczas tworzenia aplikacji, można wybrać wersję JsRT, obsługujący aparat Edge lub starszego aparatu. Można wybrać wersję JsRT zgodnie z wytycznymi powyższych. Aby uwzględnić te różnice, wprowadzono następujące zmiany do `JsCreateRuntime`, `JsCreateContext`, i `JsStartDebugging`.  
  
 Dla `JsCreateRuntime`:  
  
-   Jeśli celem starszego aparatu `JsRuntimeVersionEdge` wartość wyliczenia jest przestarzały i sugeruje wiadomości przy użyciu `JsRuntimeVersionInternetExplorer11` wartość zmiennej.  
  
-   Gdy aparat krawędzi, parametr wersji jest pominięte `JsCreateRuntime` funkcji.  
  
    ```cpp  
    JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
    ```  
  
 Aby uzyskać `JsCreateContext` i `JsStartDebugging`:  
  
-   Jeśli celem starszego aparatu `IDebugApplication` interfejs jest używany do dostarczania własnego-remote metody debugowania. Na potrzeby debugowania, `JsCreateContext` i `JsStartDebugging` funkcje pobierać `IDebugApplication` jako parametr.  
  
-   Gdy aparat krawędzi `IDebugApplication` interfejs jest przestarzały. Chakra aparat umożliwia macierzystego i debugowanie możliwości za pomocą debugera programu Visual Studio bez konieczności stosowania skryptu `IDebugApplication` od użytkownika. Interfejs nie jest już parametr `JsCreateContext` i `JsStartDebugging` w związku z tym.  
  
 Podpisy dla poprzedniego interfejsów API w starszego aparatu są następujące:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsRuntimeVersion version, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, IDebugApplication *debugApplication, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging(IDebugApplication *debugApplication);  
```  
  
 Podpisy dla poprzedniego interfejsów API w aparacie krawędzi są następujące:  
  
```cpp  
JsErrorCode JsCreateRuntime(JsRuntimeAttributes attributes, JsThreadServiceCallback callback, _Out_ JsRuntimeHandle* runtime);  
  
JsErrorCode JsCreateContext(JsRuntimeHandle runtime, JsContextRef *newContext);  
  
JsErrorCode JsStartDebugging();  
```  
  
## <a name="compile-for-your-preferred-version-using-visual-c"></a>Kompiluj dla używanej wersji preferowanym języku Visual C++  
 Korzystając z języka Visual C++, importowanie JsRT API przez dołączenie nagłówka jsrt.h i upewnij się, że ten jsrt.lib jest umieszczona na liście plików wejściowych konsolidatora:  
  
```cpp  
#include <jsrt.h>  
```  
  
 ![Dodawanie jsrt.lib jako plik wejściowy konsolidatora](../chakra-hosting/media/js-chakra.png "JS_Chakra_")  
  
 Jeśli chcesz przeanalizować dane binarne aparat krawędzi, musisz zdefiniować makro `USE_EDGEMODE_JSRT` przed dołączeniem jsrt.h, a zamiast łączenie przed jsrt.lib, należy połączyć przed chakrart.lib:  
  
```cpp  
#define USE_EDGEMODE_JSRT  
#include <jsrt.h>  
```  
  
 ![Dodawanie chakrart.lib jako plik wejściowy konsolidatora](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting_")  
  
 Jeśli zaczynasz nową aplikację, możesz teraz przystąpić do rozpocząć pisanie kodu do interfejsu API JsRT.  
  
## <a name="compile-for-your-preferred-version-using-net"></a>Kompiluj preferowanych wersji przy użyciu platformy .NET  
 Jeśli używasz programu .NET i P/Invoke, należy zmienić Twoje deklaracje interfejsu API JsRT [DllImport] do zaimportowania chakra.dll zamiast jscript9.dll. Ponadto zmieniać definicję `JsCreateRuntime` usunąć `JsRuntimeVersion` parametru, jak i definicja `JsCreateContext` i `JsStartDebugging` do usunięcia `IDebugApplication` parametru.  
  
 Dla starszego aparatu należy użyć poniższego kodu.  
  
```c#  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsRuntimeVersion version,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    IDebugApplication debugApplication,  
    out JsContextRef newContext  
);   
  
[DllImport("jscript9.dll")]  
public static extern JsErrorCode JsStartDebugging(  
    IDebugApplication debugApplication,  
);  
```  
  
 Aparat krawędzi należy użyć poniższego kodu.  
  
```c#  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateRuntime(  
    JsRuntimeAttributes attributes,  
    JsThreadServiceCallback callback,  
    out JsRuntimeSafeHandle runtime  
);  
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsCreateContext(  
    JsRuntimeSafeHandle runtime,  
    out JsContextRef newContext  
);   
  
[DllImport("chakra.dll")]  
public static extern JsErrorCode JsStartDebugging();  
```  
  
> [!CAUTION]
>  Jeśli są ręcznie organizowanie wskaźnik funkcji (takich jak za pomocą metody LoadLibrary/GetProcAddress), jest bardzo istotne, że niemieszanie deklaracje metody, w przeciwnym razie zostanie unbalance stosu, co spowoduje nieprzewidywalne zachowanie, takich jak powoduje aplikacji awarię. Ten sam problem wystąpi, jeśli będą wykonać globalne wyszukiwania i zamieniania wystąpień jscript9.dll w kodzie importu, ponieważ będzie pominięcia `version` parametru usuwane.  
  
## <a name="summary"></a>Podsumowanie  
 W systemie Windows 10 API obsługującego środowisko uruchomieniowe JavaScript jest dzielona na dwie. Te interfejsy API obsługuje teraz "życia" aparat krawędzi, w których możliwości języka zostaną porównane "życia" aparat krawędzi w programie Microsoft Edge. Można wykorzystać te możliwości z pulpitu lub aplikacji ze sklepu, aby utworzyć nowe, ciekawe zastosowania rozszerzenie aplikacji i korzystać z nowoczesnymi umiejętności sieci Web w istniejącej kodzie. Jednak ponieważ występują niewielkie różnice między poprzednich wersji, należy pamiętać o następujących punktów Jeśli Edge lub starszego aparatu.  
  
-   Aplikacja może obsługiwać tylko jedną wersję JsRT jednego procesu.  
  
     Na przykład nie można utworzyć środowiska uruchomieniowego krawędzi aparatu, a następnie runtime starszego aparatu i oczekiwaniom by działała poprawnie, w tym samym procesie. To nie jest obsługiwane i może spowodować nieudokumentowanej zachowanie, np. nie można załadować biblioteki DLL drugiego.  
  
-   Gdy aparat krawędzi, aplikację nieoczekiwanie może uzyskać nowe funkcje, gdy platforma podstawowa zostanie automatycznie zaktualizowana.  
  
     Na przykład tryb Internet Explorer 11 starszej wersji środowiska uruchomieniowego obsługuje deklaracji zmiennej zakresu bloku takich jak `let` i `const`. Jeśli zostały wcześniej standardowego kodu, który miał pracuje w trybie programu Internet Explorer 10, który nie ma reguł zakresu bloku, zachowanie automatyczne przechowywanie wersji aparatu krawędzi mogło uruchomić niepowodzeniem, jeśli platforma automatycznie przeprowadzili uaktualnienie. Musi to być jest brany pod uwagę podczas wybierania który model środowiska uruchomieniowego do użycia. Gdy mamy nadzieję, że docelowych aparat krawędzi, jeśli to możliwe, musi być ostrożność przy używaniu struktury kodu JavaScript, które mogą być nieprawidłowe w przyszłości.  
  
-   JsRT w Sklepie Windows obsługuje tylko przez aparat krawędzi (chakra.dll). Aplikacje, które próbuje połączyć się z dowolnym API JsRT w jscript9.dll zakończy się niepowodzeniem certyfikacji.  
  
-   Jest bardzo istotne, że nie należy mylić deklaracja `JsCreateRuntime`, `JsCreateContext`, i `JsStartDebugging` między jscript9.dll i chakra.dll, ponieważ spowoduje imbalancing stosu.  
  
     Używając C i C++, zostanie wyświetlony błąd konsolidatora, Jeśli spróbujesz użyć deklaracji niewłaściwy tak długo, jak długo wykonywanych nie ekran podobny do wywoływania `LoadLibrary` , a następnie `GetProcAddress`. Deweloperom platformy .NET nie może równie łatwo znaleźć ten problem, dlatego Sprawdź kodu podczas używania tej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Hostowanie środowiska uruchomieniowego JavaScript](../chakra-hosting/javascript-runtime-hosting.md)
---
title: Wyrażenia w debugerze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 063fe4f61e6e3d8e8ed9e54b990029f2cf408e24
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454547"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Wyrażenia w debugerze programu Visual Studio
Debuger programu Visual Studio zawiera ewaluatorów wyrażeń, działające po wprowadzeniu wyrażenia w **QuickWatch** okno dialogowe **czujki** okna, lub **Immediate** okna. Ewaluatory wyrażeń są również w pracy w **punktów przerwania** okno i wielu innych miejscach w debugerze.
  
 Poniższe sekcje zapewniają szczegółowe informacje o wyrażeniach w różnych językach.  
  
## <a name="f-expressions-are-not-supported"></a>F # wyrażenia nie są obsługiwane.  
 F # wyrażenia nie są rozpoznawane. Debugowania kodzie języka F #, musisz przetłumaczyć wyrażenia na składni C# przed wprowadzeniem wyrażeń w debugerze okno lub okno dialogowe. Podczas tłumaczenia wyrażenia z F # na język C#, należy pamiętać, że C# używa `==` operatora, aby sprawdzić pod kątem równości, gdy F # używa jednego `=`.  
  
## <a name="c-expressions"></a>Wyrażenia języka C++  
 Aby dowiedzieć się, jak przy użyciu operatorów kontekstu za pomocą wyrażeń języka C++, zobacz [kontekstu — Operator (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Nieobsługiwane wyrażenia w języku C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Konwersje konstruktory i destruktory  
 Konstruktor ani destruktor nie można wywołać dla obiekt jawnie lub niejawnie. Na przykład poniższe wyrażenie jawnie wywołuje konstruktor i powoduje komunikat o błędzie:  
  
```C++  
my_date( 2, 3, 1985 )  
```  
  
 Nie można wywołać funkcji konwersji, jeśli docelowy konwersji jest klasą. Takie konwersji obejmuje konstrukcji obiektu. Na przykład jeśli `myFraction` jest wystąpieniem `CFraction`, który definiuje operator funkcji konwersji `FixedPoint`, poniższe wyrażenie powoduje wystąpienie błędu:  
  
```C++  
(FixedPoint)myFraction  
```  
  
 Nie można wywołać nowy lub delete — operatory. Na przykład poniższe wyrażenie nie jest obsługiwana:  
  
```C++  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Makra preprocesora  
 Makra preprocesora nie są obsługiwane w debugerze. Na przykład jeśli stałą `VALUE` jest zadeklarowany jako: `#define VALUE 3`, nie można użyć `VALUE` w **czujki** okna. Aby uniknąć tego ograniczenia, należy zastąpić `#define`obiektu z wyliczenia i funkcje, jeśli to możliwe.  
  
### <a name="using-namespace-declarations"></a>za pomocą deklaracji przestrzeni nazw  
 Nie można użyć `using namespace` deklaracji.  Aby uzyskać dostęp do nazwy typu lub zmiennej poza bieżącej przestrzeni nazw, musi być w pełni kwalifikowaną nazwę.  
  
### <a name="anonymous-namespaces"></a>Anonimowe przestrzenie nazw  
 Przestrzenie nazw anonimowe nie są obsługiwane. Jeśli masz następujący kod, nie można dodać `test` do okna czujki:  
  
```C++  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
###  <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Przy użyciu funkcji wewnętrznych debugera do zarządzania stanem  
 Funkcje wewnętrzne debugera zapewniają sposób wywołania pewne funkcje C/C++ w wyrażeniach bez zmiany stanu aplikacji.  
  
 Funkcje wewnętrzne debugera:  
  
-   Zapewniona jest bezpieczne: wykonywanie funkcji wewnętrznej debugera nie spowoduje uszkodzenie jest debugowany proces.  
  
-   Są dozwolone w wszystkie wyrażenia, nawet w scenariuszach, w którym efekty uboczne i obliczanie funkcji nie są dozwolone.  
  
-   Praca w scenariuszach, w których wywołania funkcji regularne nie są możliwe, takich jak debugowania minizrzutu.  
  
 Funkcje wewnętrzne debuger można również ustawić wyrażenia oszacowania wygodniejsze. Na przykład `strncmp(str, "asd")` jest znacznie łatwiejsze do zapisu w warunku punktu przerwania niż `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )  
  
|Obszar|Funkcje wewnętrzne|  
|----------|-------------------------|  
|**Długość ciągu**|strlen —, wcslen —, strnlen — wcsnlen —|  
|**Porównanie ciągów**|strcmp — wcscmp —, stricmp —, _stricmp —, _strcmpi —, wcsicmp —, _wcscmpi, _wcsnicmp —, strncmp —, wcsncmp —, strnicmp —, wcsnicmp —|  
|**Ciąg wyszukiwania**|strchr —, wcschr —, strstr — wcsstr —|  
|**Win32**|Funkcja GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Funkcje te wymagają proces, który jest debugowany działa w systemie Windows 8. Debugowania plików zrzutu generowane z urządzenia z systemem Windows 8 również wymaga programu Visual Studio komputera systemu Windows 8. Jednak przypadku zdalnego debugowania urządzenia z systemem Windows 8, komputerze Visual Studio może być uruchomiony system Windows 7.|  
|**Różne**|__log2<br /><br /> Zwraca dziennik podstawie 2 określona liczba całkowita, zaokrąglona do najbliższej liczby całkowitej niższa.|  
  
## <a name="ccli---unsupported-expressions"></a>C + +/ CLI - nieobsługiwane wyrażenia  
  
-   Rzutowania obejmujących wskaźniki lub zdefiniowanej przez użytkownika rzutowania nie są obsługiwane.  
  
-   Porównanie obiektów i przypisanie nie są obsługiwane.  
  
-   Operatory przeciążone i przeciążonej funkcji nie są obsługiwane.  
  
-   Opakowywanie i rozpakowywanie nie są obsługiwane.  
  
-   `Sizeof` operator nie jest obsługiwany.  
  
## <a name="c---unsupported-expressions"></a>C# — nieobsługiwane wyrażenia  
  
### <a name="dynamic-objects"></a>Obiekty dynamiczne  
 W wyrażeniach debugera, wypełnianych statycznie jako dynamiczny, można używać zmiennych. Jeśli obiekty, które implementują <xref:System.Dynamic.IDynamicMetaObjectProvider> są oceniane w oknie wyrażeń kontrolnych widoku dynamicznego węzeł zostanie dodany. Węzeł widoku dynamicznego pokazuje elementach członkowskich obiektu, ale nie zezwala na edytowanie wartości składników.  
  
 Następujące funkcje obiekty dynamiczne nie są obsługiwane:  
  
-   Złożone operatory `+=`, `-=`, `%=`, `/=`, i `*=`  
  
-   Wiele prezentacji, w tym rzutowania liczbowych i argument typu rzutowania  
  
-   Wywołania metody z więcej niż dwa argumenty  
  
-   Metody pobierające właściwości z więcej niż dwa argumenty  
  
-   Metody ustawiające właściwości z argumentami  
  
-   Przypisywanie do indeksatora  
  
-   Operatory logiczne `&&` i `||`  
  
### <a name="anonymous-methods"></a>Metody anonimowe  
 Tworzenie nowych metod anonimowych nie jest obsługiwane.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - nieobsługiwane wyrażenia  
  
### <a name="dynamic-objects"></a>Obiekty dynamiczne  
 W wyrażeniach debugera, wypełnianych statycznie jako dynamiczny, można używać zmiennych. Jeśli obiekty, które implementują [interfejsu interfejs IDynamicMetaObjectProvider](http://msdn.microsoft.com/Library/e887a72d-ebe2-4253-a7e8-3d8d05154647) są oceniane w oknie wyrażeń kontrolnych widoku dynamicznego węzeł zostanie dodany. Węzeł widoku dynamicznego pokazuje elementach członkowskich obiektu, ale nie zezwala na edytowanie wartości składników.  
  
 Następujące funkcje obiekty dynamiczne nie są obsługiwane:  
  
-   Złożone operatory `+=`, `-=`, `%=`, `/=`, i `*=`  
  
-   Wiele prezentacji, w tym rzutowania liczbowych i argument typu rzutowania  
  
-   Wywołania metody z więcej niż dwa argumenty  
  
-   Metody pobierające właściwości z więcej niż dwa argumenty  
  
-   Metody ustawiające właściwości z argumentami  
  
-   Przypisywanie do indeksatora  
  
-   Operatory logiczne `&&` i `||`  
  
### <a name="local-constants"></a>Stałe lokalnego  
 Stałe lokalnych nie są obsługiwane.  
  
### <a name="import-aliases"></a>Importowanie aliasów  
 Importowanie aliasów nie są obsługiwane.  
  
### <a name="variable-declarations"></a>Deklaracje zmiennej  
 Nie można zadeklarować jawne nowe zmienne w debugerze systemu windows. Jednak można przypisać nowe zmienne niejawne wewnątrz **Immediate** okna. Te zmienne niejawne ograniczone do sesji debugowania i nie są dostępne poza debugerem. Na przykład instrukcja `o = 5` niejawnie tworzy nową zmienną `o` i przypisz jej wartość 5. Takie niejawne zmienne są typu **obiektu** o ile nie można wywnioskować typu przez debuger.  
  
### <a name="unsupported-keywords"></a>Nieobsługiwane słowa kluczowe  
  
-   `AddressOf`  
  
-   `End`  
  
-   `Error`  
  
-   `Exit`  
  
-   `Goto`  
  
-   `On Error`  
  
-   `Resume`  
  
-   `Return`  
  
-   `Select/Case`  
  
-   `Stop`  
  
-   `SyncLock`  
  
-   `Throw`  
  
-   `Try/Catch/Finally`  
  
-   `With`  
  
-   Namespace lub modułu poziomu słów kluczowych, takich jak `End Sub` lub `Module`.  
  
## <a name="see-also"></a>Zobacz też  
 [Specyfikatory formatu w C++](../debugger/format-specifiers-in-cpp.md)   
 [Kontekst — Operator (C++)](../debugger/context-operator-cpp.md)   
 [Specyfikatory formatu w C#](../debugger/format-specifiers-in-csharp.md)   
 [Pseudozmienne](../debugger/pseudovariables.md)
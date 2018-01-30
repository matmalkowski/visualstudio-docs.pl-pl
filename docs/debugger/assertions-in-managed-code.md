---
title: "Potwierdzenia w zarządzanym kodzie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 90e39956f777ddd79fad080d8bb6d13b30d4ccd0
ms.sourcegitcommit: 9a2f937e42305db6e3eaa7aadc235b0ba9aafc83
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="assertions-in-managed-code"></a>Potwierdzenia w zarządzanym kodzie
Moduł potwierdzenie lub `Assert` instrukcji, sprawdza warunek, który jest określony jako argument `Assert` instrukcji. Jeśli warunek jest spełniony, występuje żadna akcja. Gdy warunek jest spełniony, potwierdzenie nie powiedzie się. Jeśli korzystasz z kompilacji debugowania, program wprowadza tryb przerwania.  
  
##  <a name="BKMK_In_this_topic"></a>W tym temacie  
 [Potwierdza w Namespace System.Diagnostics](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Debug.Assert — metoda](#BKMK_The_Debug_Assert_method)  
  
 [Efekty uboczne Debug.Assert](#BKMK_Side_effects_of_Debug_Assert)  
  
 [Wymagania dotyczące debugowania i śledzenia](#BKMK_Trace_and_Debug_Requirements)  
  
 [Assert argumentów](#BKMK_Assert_arguments)  
  
 [Dostosowywanie zachowania Assert](#BKMK_Customizing_Assert_behavior)  
  
 [Ustawienie potwierdzenia w plikach konfiguracji](#BKMK_Setting_assertions_in_configuration_files)  
  
##  <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a>Potwierdza w Namespace System.Diagnostics  
 W języku Visual Basic i Visual C#, można użyć `Assert` metody z albo <xref:System.Diagnostics.Debug> lub <xref:System.Diagnostics.Trace>, które znajdują się w <xref:System.Diagnostics> przestrzeni nazw. <xref:System.Diagnostics.Debug>metody klasy nie znajdują się w wersji programu, nie zwiększyć rozmiar ani zmniejszać szybkość kodu wersji.  
  
 C++ nie obsługuje <xref:System.Diagnostics.Debug> metody klasy. Ten sam efekt można osiągnąć za pomocą <xref:System.Diagnostics.Trace> klasy z kompilacji warunkowej, takich jak `#ifdef DEBUG`... `#endif`.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_Debug_Assert_method"></a>Debug.Assert — metoda  
 Użyj <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metoda za darmo, aby przetestować warunki, które powinny zawierać wartość true, jeśli kod jest poprawny. Na przykład załóżmy, że zostały zapisane Funkcja dzielenia liczby całkowitej. Regułami matematyce dzielnik nigdy nie może być równa zero. Może to testu przy użyciu potwierdzenia:  
  
```VB  
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer  
    Debug.Assert(divisor <> 0)  
    Return CInt(dividend / divisor)  
End Function  
```  
  
```csharp  
int IntegerDivide ( int dividend , int divisor )  
    { Debug.Assert ( divisor != 0 );  
        return ( dividend / divisor ); }  
```  
  
 Uruchom ten kod w debugerze, instrukcja potwierdzenia jest obliczane, ale w wersji, porównanie nie zostało utworzone, więc nie ma żadnych dodatkowych czynności.  
  
 Oto przykład innego. Masz klasy, która implementuje konta bankowego w następujący sposób:  
  
```VB  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Debug.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Debug.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Aby cofnąć pieniędzy z konta chcesz upewnij się, że saldo konta wystarcza do obsługi kwota przygotowywania do wycofania. Potwierdzenie, aby sprawdzić saldo może zapisać:  
  
```VB  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Trace.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Trace.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Należy pamiętać, że wywołań <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metody zniknąć po utworzeniu wersji kodu. Oznacza to, że połączenia, który sprawdza saldo zniknie w wersji. Aby rozwiązać ten problem, należy zastąpić <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> z <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, które nie znika w wersji:  
  
 Wywołuje się <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> narzut dodać do wersji Release, w przeciwieństwie do wywołania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Side_effects_of_Debug_Assert"></a>Efekty uboczne Debug.Assert  
 Jeśli używasz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, upewnij się, że żadnego kodu wewnątrz `Assert` nie zmienia wyniki program, jeśli `Assert` zostanie usunięta. W przeciwnym razie przypadkowego może powodować usterkę, która jest wyświetlana tylko w wersji programu. Należy zachować szczególną ostrożność około potwierdzeń, które zawierają funkcji lub procedury wywołań, taką jak na poniższym przykładzie:  
  
```VB  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```csharp  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 To <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> mogą być wyświetlane na pierwszy rzut oka bezpieczne, ale Załóżmy, że meas funkcja aktualizuje licznik zawsze jest wywoływana. Podczas tworzenia wersji to wywołanie meas została pominięta, dlatego licznik nie zostanie zaktualizowany. To jest przykład funkcji z efektem ubocznym. Wywołanie funkcji, która ma efekty uboczne, eliminując może spowodować usterkę, która jest wyświetlana tylko w wersji. Aby uniknąć tych problemów, nie umieszczaj wywołania funkcji w <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> instrukcji. Zamiast tego użyj zmiennej tymczasowej:  
  
```VB  
temp = meas( i )  
Debug.Assert (temp <> 0)  
```  
  
```csharp  
temp = meas( i );  
Debug.Assert ( temp != 0 );  
```  
  
 Nawet jeśli używasz <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, można nadal unikać umieszczania wywołania funkcji wewnątrz `Assert` instrukcji. Takie połączenia powinny być bezpieczne, ponieważ <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> instrukcji nie są eliminowane w kompilacji wydania. Jednak jeśli takie konstrukcje jako nawyk można uniknąć, jest mniej prawdopodobne do popełnienia błędu, gdy używasz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Trace_and_Debug_Requirements"></a>Wymagania dotyczące debugowania i śledzenia  
 Jeśli utworzysz Twój projekt używający [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kreatorów, symbol śledzenia jest zdefiniowana w konfiguracji zarówno wersji i debugowania. Domyślnie tylko w przypadku kompilacji debugowania jest zdefiniowane symboli debugowania.  
  
 W przeciwnym razie dla <xref:System.Diagnostics.Trace> metody do pracy, program musi mieć jedną z następujących czynności na początku pliku źródłowego:  
  
-   `#Const TRACE = True`w języku Visual Basic  
  
-   `#define TRACE`w programie Visual C# i C++  
  
 Lub program muszą zostać skompilowane z opcją śledzenia:  
  
-   `/d:TRACE=True`w języku Visual Basic  
  
-   `/d:TRACE`w programie Visual C# i C++  
  
 Jeśli musisz użyć metod debugowania w języku C# lub Visual Basic wersji kompilacji, należy zdefiniować symbolu debugowania w wersji konfiguracji.  
  
 C++ nie obsługuje <xref:System.Diagnostics.Debug> metody klasy. Ten sam efekt można osiągnąć za pomocą <xref:System.Diagnostics.Trace> klasy z kompilacji warunkowej, takich jak `#ifdef DEBUG`... `#endif`. Można zdefiniować tych symboli w  **\<projektu > strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Zmienianie ustawienia projektu dla konfiguracji debugowania Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) lub [Zmienianie ustawienia projektu dla języka C lub C++ debugowania konfiguracji](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
##  <a name="BKMK_Assert_arguments"></a>Assert argumentów  
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> potrwać maksymalnie trzech argumentów. Pierwszy argument, który jest wymagany, jest warunek, który chcesz sprawdzić. Jeśli należy wywołać <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> z tylko jednym argumentem `Assert` metoda sprawdza warunek i, jeśli wynik wynosi false, generuje zawartość stosu wywołań do **dane wyjściowe** okna. W poniższym przykładzie przedstawiono <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> i <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>:  
  
```VB  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```csharp  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 Drugi i trzeci argument, jeśli jest obecny, muszą być ciągami. Jeśli należy wywołać <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> z dwóch lub trzech argumentów, pierwszy argument jest warunek. Metoda sprawdza warunek i, jeśli wynik wynosi false, generuje ciąg drugi i trzeci ciągów. W poniższym przykładzie przedstawiono <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> i <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> używana z dwoma argumentami:  
  
```VB  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```csharp  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 W poniższym przykładzie przedstawiono <xref:System.Diagnostics.Debug.Assert%2A> i <xref:System.Diagnostics.Trace.Assert%2A>:  
  
```VB  
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )  
```  
  
```csharp  
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );  
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );   
```  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Customizing_Assert_behavior"></a>Dostosowywanie zachowania Assert  
 Po uruchomieniu aplikacji w tryb interfejsu użytkownika `Assert` metoda Wyświetla **nie powiodła się Asercja** okno dialogowe, gdy warunek nie powiodło się. Akcje występujące po potwierdzenie nie powiedzie się są kontrolowane przez <xref:System.Diagnostics.Debug.Listeners%2A> lub <xref:System.Diagnostics.Trace.Listeners%2A> właściwości.  
  
 Zachowanie danych wyjściowych można dostosować, dodając <xref:System.Diagnostics.TraceListener> do obiektu `Listeners` kolekcji, usuwając <xref:System.Diagnostics.TraceListener> z `Listeners` kolekcji, lub przez zastąpienie <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metody istniejącego `TraceListener` aby stał się zachowywać się inaczej.  
  
 Na przykład można zastąpić <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metody do zapisu do dziennika zdarzeń, zamiast **nie powiodła się Asercja** okno dialogowe.  
  
 Aby dostosować dane wyjściowe w ten sposób, program musi zawierać odbiornik, a musi dziedziczyć z <xref:System.Diagnostics.TraceListener> i zastąp jego <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> metody.  
  
 Aby uzyskać więcej informacji, zobacz [obiektów nasłuchujących śledzenia](/dotnet/framework/debug-trace-profile/trace-listeners).  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Setting_assertions_in_configuration_files"></a>Ustawienie potwierdzenia w plikach konfiguracji  
 Potwierdzenia w pliku konfiguracyjnym programu również można ustawić w kodzie. Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> lub <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Śledzenie i Instrumentacja aplikacji](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)   
 [Porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)   
 [C#, F # i typy projektów Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
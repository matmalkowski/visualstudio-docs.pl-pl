---
title: Pseudovariables | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: "35"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f2bde32d67bb2e106d058c5a9e62801940d3df25
ms.sourcegitcommit: 5d43e9590e2246084670b79269cc9d99124bb3df
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Pseudovariables w debugerze programu Visual Studio
Pseudovariables są warunki, używany do wyświetlania pewne informacje w oknie zmiennej lub **QuickWatch** okno dialogowe. Możesz wprowadzić pseudovariable w taki sam sposób jak wprowadzasz normalnym zmiennej. Pseudovariables zmienne nie są jednak i nazwy zmiennych w programie nie są zgodne.  
  
## <a name="example"></a>Przykład  
 Załóżmy, że pisania aplikacji kodu natywnego i chcesz zobaczyć liczby dojść przydzielone w aplikacji. W **czujki** okna, możesz wprowadzić następujące pseudovariable w **nazwa** kolumny, a następnie naciśnij klawisz Return, aby go ocenić:  
  
```  
$handles  
```  
  
 W kodzie natywnym można użyć pseudovariables przedstawione w tej tabeli:  
  
|Pseudovariable|Funkcja|  
|--------------------|--------------|  
|`$err`|Wyświetla ostatni błąd ustawiona wartość przy użyciu funkcji SetLastError. Wartość, która jest wyświetlana reprezentuje, co będzie zwracany przez funkcję GetLastError.<br /><br /> Użyj `$err,hr` wyświetlić dekodowane formularza tej wartości. Na przykład, jeśli ostatni błąd: 3 `$err,hr` wyświetli`ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Wyświetla liczbę dojść przydzielone w aplikacji.|  
|`$vframe`|Wyświetla adres bieżącej ramki stosu.|  
|`$tid`|Wyświetla identyfikator wątku dla bieżącego wątku.|  
|`$env`|Wyświetla blok środowiska w podglądzie ciągu.|  
|`$cmdline`|Wyświetla ciąg wiersza polecenia, który jest uruchomiony program.|  
|`$pid`|Wyświetla identyfikator procesu.|  
|`$` *registername*<br /><br /> lub<br /><br /> `@` *registername*|Wyświetla zawartość rejestru *registername*.<br /><br /> Zazwyczaj można wyświetlić zawartość rejestru właśnie, wprowadzając nazwę rejestru. Tylko wtedy, należy użyć następującej składni jest, gdy nazwa rejestru overloads nazwę zmiennej. Jeśli nazwa rejestru jest taka sama jak nazwa zmiennej w bieżącym zakresie, debuger interpretuje nazwy jako nazwy zmiennej. Kiedy jest `$` *registername* lub `@` *registername* polega na pod ręką.|  
|`$clk`|Wyświetla czas w cykle zegara.|  
|`$user`|Wyświetla struktury zawierającej informacje o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje o haśle nie jest wyświetlana.|  
|`$exceptionstack`|Wyświetla ślad stosu wyjątku bieżącego środowiska uruchomieniowego systemu Windows. `$ exceptionstack`działa tylko w aplikacji platformy uniwersalnej systemu Windows. `$ exceptionstack`nieobsługiwane wyjątki C++ i KLIKA|  
|`$ReturnValue`|Wyświetla wartość zwracaną przez metodę .NET Framework.|  
  
 W języku C# i Visual Basic można użyć pseudovariables przedstawione w tej tabeli:  
  
|Pseudovariable|Funkcja|  
|--------------------|--------------|  
|`$exception`|Wyświetla informacje o ostatnim wyjątkiem. Jeśli żaden wyjątek wystąpił, obliczenia `$exception` wyświetla komunikat o błędzie.<br /><br /> Języka Visual C# tylko wtedy, gdy Asystenta wyjątków jest wyłączona, `$exception` jest automatycznie dodawany do **zmiennych lokalnych** okna po wystąpieniu wyjątku.|  
|`$user`|Wyświetla struktury zawierającej informacje o koncie dla konta, na którym działa aplikacja. Ze względów bezpieczeństwa informacje o haśle nie jest wyświetlana.|  
  
 W języku Visual Basic można użyć pseudovariables poniższą tabelą:  
  
|Pseudovariable|Funkcja|  
|--------------------|--------------|  
|`$delete`lub`$$delete`|Usuwa Zmienna niejawna, który został utworzony w **Immediate** okna. Składnia jest `$delete,` *zmiennej* lub`$delete,` *zmiennej*`.`|  
|`$objectids`lub`$listobjectids`|Wyświetla wszystkie aktywne identyfikatory obiektów podrzędnych określone wyrażenie. Składnia jest `$objectid,` *wyrażenie* lub`$listobjectids,` *wyrażenia*`.`|  
|`$` *N* `#`|Wyświetla obiekty o identyfikatorze obiektu równa *N*.|  
|`$dynamic`|Wyświetla specjalną **widoku dynamicznego** węzła dla obiekt, który implementuje `IDynamicMetaObjectProvider`. Interfejs. Składnia jest `$dynamic,` *obiektu*. Ta funkcja ma zastosowanie tylko do kodu, który używa .NET Framework w wersji 4.|  
  
## <a name="see-also"></a>Zobacz też  
 [Oglądanie i QuickWatch systemu Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Zmienne systemu Windows](../debugger/debugger-windows.md)
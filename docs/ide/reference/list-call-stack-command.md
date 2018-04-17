---
title: Lista stosu wywołań — polecenie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3b9a0f9c466325d476c01d4acf9b825193fb175
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="list-call-stack-command"></a>Lista stosu wywołań — Polecenie
Wyświetla bieżący stos wywołań.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>Argumenty  
 `index`  
 Opcjonalny. Określa bieżącą ramkę stosu i wyświetla żadnych danych wyjściowych.  
  
## <a name="switches"></a>Przełączniki  
 Każdy przełącznik może być wywoływany przy użyciu jego ukończenia formularza lub krótkich fragmentów.  
  
 / Liczba:`number` [i] / / c:`number`  
 Opcjonalny. Maksymalna liczba stosy wywołań do wyświetlenia. Wartością domyślną jest nieograniczona.  
  
 / ShowTypes:`yes` &#124; `no` [i] / t:`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane typy parametrów. Wartość domyślna to `yes`.  
  
 / ShowNames:`yes` &#124; `no` [i] / n:`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane nazwy parametrów. Wartość domyślna to `yes`.  
  
 / ShowValues:`yes` &#124; `no` [i] / v:`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane wartości parametrów. Wartość domyślna to `yes`.  
  
 / ShowModule:`yes` &#124; `no` [i] / m:`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane nazwy modułu. Wartość domyślna to `yes`.  
  
 / ShowLineOffset:`yes` &#124; `no` [i] /#:`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane przesunięcie wiersza. Wartość domyślna to `no`.  
  
 / ShowByteOffset:`yes` &#124; `no` [i] / b:`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane przesunięcia bajtów. Wartość domyślna to `no`.  
  
 / Pokażjęzyk:`yes` &#124; `no` [i] / l: wyświetlenie`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane w języku. Wartość domyślna to `no`.  
  
 / Uwzględnijwywołaniamiędzywątkami:`yes` &#124; `no` [i] / i:`yes`&#124;`no`  
 Opcjonalny. Określa, czy dołączać wywołania do lub z innych wątków. Wartość domyślna to `no`.  
  
 / ShowExternalCode:`yes`&#124;`no`  
 Opcjonalny. Określa, czy mają być wyświetlane tylko mój kod dla stosu wywołań. Gdy tylko mój kod jest wyłączone, jest wyświetlany cały kod niezwiązany z użytkownikiem. Po włączeniu tylko mój kod kodu innych użytkowników jest wyświetlany jako `[external]` w danych wyjściowych stosu wywołań.  
  
 Wątek:`n`  
 Opcjonalny. Wyświetla stos wywołań dla wątku `n`. Jeśli wątek nie zostanie określony, wyświetla stos wywołań bieżącego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Zmiany wprowadzone do argumentów lub przełączników dotyczą przyszłe wywołania tego polecenia. Jeśli wydawane Debug.ListCallStackby sam Wyświetla cały stos wywołań. Jeśli na przykład określić indeksu  
  
```  
Debug.ListCallStack 2  
```  
  
 następnie bieżącej ramki stosu ustawiono ramki (w tym przypadku drugiej ramki).  
  
 To polecenie za pomocą wstępnie zdefiniowanych aliasem, można również napisać kb. Na przykład można wprowadzić  
  
```  
kb 2  
```  
  
 Aby ustawić bieżącej ramki stosu drugiej ramki.  
  
## <a name="example"></a>Przykład  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Lista dezasemblacji — polecenie](../../ide/reference/list-disassembly-command.md)   
 [Lista wątków — polecenie](../../ide/reference/list-threads-command.md)   
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Find/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
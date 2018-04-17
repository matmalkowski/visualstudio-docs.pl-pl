---
title: Formatversion — zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: Mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1c463f7e3bcd192a7ba217570d9fda051d8d23f9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="formatversion-task"></a>FormatVersion — Zadanie
Dołącza numer poprawki numer wersji.  
  
-   Przypadek #1: Dane wejściowe: wersja =\<Niezdefiniowany >;  Poprawki =\<nieważne >;   Dane wyjściowe: OutputVersion = "1.0.0.0"  
  
-   Przypadek #2: Dane wejściowe: wersja = "1.0.0.*" poprawkę = "5" w danych wyjściowych: OutputVersion = "1.0.0.5"  
  
-   Przypadek #3: Dane wejściowe: wersja = "1.0.0.0" poprawkę =\<nieważne >;  Dane wyjściowe: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `FormatVersion` zadań.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FormatType`|Opcjonalne `String` parametru.<br /><br /> Określa typ formatu.<br /><br /> -"Version" = wersja.<br />-"Path"= replace"." z "_";|  
|`OutputVersion`|Opcjonalne `String` parametru wyjściowego.<br /><br /> Określa wersję danych wyjściowych, zawierającą numer wersji.|  
|`Revision`|Opcjonalne `Int32` parametru.<br /><br /> Określa poprawkę do dołączenia do wersji.|  
|`Version`|Opcjonalne `String` parametru.<br /><br /> Określa ciąg numer wersji do formatowania.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametrów z <xref:Microsoft.Build.Tasks.TaskExtension> dziedziczy klasa, która sama <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrach i ich opisy, zobacz [taskextension — klasa podstawowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
---
title: FormatVersion, zadanie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29f9cae12a66e2b442d6c42032d3f4bf65942127
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37946251"
---
# <a name="formatversion-task"></a>Formatversion — zadanie
Dołącza numer wersji do numeru wersji.  
  
-   Przypadek #1: Dane wejściowe: wersja =\<niezdefiniowana >;  Poprawka =\<nieważne >;   Dane wyjściowe: OutputVersion = "1.0.0.0"  
  
-   Przypadek #2: Dane wejściowe: wersji = poprawkę "1.0.0.*" = "5" w danych wyjściowych: OutputVersion = "1.0.0.5"  
  
-   Przypadek #3: Dane wejściowe: wersja = "1.0.0.0" poprawki =\<nieważne >;  Dane wyjściowe: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `FormatVersion` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`FormatType`|Opcjonalnie `String` parametru.<br /><br /> Określa typ formatu.<br /><br /> -"Wersja" = wersji.<br />-"Path"= Zastąp"." znakiem "_";|  
|`OutputVersion`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa numer wersji danych wyjściowych, który zawiera numer wersji.|  
|`Revision`|Opcjonalnie `Int32` parametru.<br /><br /> Określa poprawkę do dołączenia do wersji.|  
|`Version`|Opcjonalnie `String` parametru.<br /><br /> Określa ciąg numer wersji do sformatowania.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów, które są wymienione w tabeli, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
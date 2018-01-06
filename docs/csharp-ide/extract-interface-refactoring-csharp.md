---
redirect_url: /visualstudio/csharp-ide/refactoring/extract-interface
title: "Wyodrębnij Interface Refaktoryzacja (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Extract Interface
- Extract Interface refactoring operation [C#]
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e3e606a86f5989ca928e0b093b564f997f92a559
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extract-interface-refactoring-c"></a>Refaktoryzacja wyodrębniania interfejsu (C#)
Interfejs wyodrębniania jest operacja refaktoryzacji, która zapewnia prosty sposób utworzyć nowy interfejs z elementów członkowskich, które pochodzą z istniejącej klasy, struktury lub interfejsu.  
  
 Jeśli kilka klienci używają tego samego podzestaw elementów członkowskich z klasy, struktury lub interfejsu, lub wiele klasy, struktury lub interfejsy mają podzestaw elementów członkowskich wspólną, może być warto uwzględnić podzestaw elementów członkowskich w interfejsie. Aby uzyskać więcej informacji o korzystaniu z interfejsów, temacie [interfejsów](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Interfejs wyodrębniania generuje interfejs w nowym pliku i umieszcza kursor na początku nowego pliku. Można określić, które elementy członkowskie można wyodrębnić na nowy interfejs, nazwę nowego interfejsu i nazwę wygenerowanego pliku przy użyciu **wyodrębniania interfejsu** okno dialogowe.  
  
### <a name="to-use-extract-interface"></a>Aby wyodrębnić interfejsu  
  
1.  Utwórz aplikację konsoli o nazwie `ExtractInterface`, a następnie zastąp `Program` następującym kodem  
  
    ```csharp  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Umieść kursor w `MethodB`i kliknij przycisk **wyodrębniania interfejsu** na **Refaktoryzuj** menu.  
  
     **Wyodrębniania interfejsu** zostanie wyświetlone okno dialogowe.  
  
     Możesz także wpisać skrótu klawiaturowego CTRL + R, I do wyświetlenia **wyodrębniania interfejsu** okno dialogowe.  
  
     Też należy kliknąć prawym przyciskiem myszy, wskaż polecenie **Refaktoryzuj**, a następnie kliknij przycisk **wyodrębnić interfejsu** do wyświetlenia **wyodrębnić interfejsu** — okno dialogowe.  
  
3.  Kliknij przycisk **Zaznacz wszystko**.  
  
4.  Kliknij przycisk **OK**.  
  
     Zostanie wyświetlony nowy plik, IProtoA.cs i następujący kod:  
  
    ```csharp  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest dostępna tylko w przypadku, gdy kursor znajduje się w klasy, struktury lub interfejsu, który zawiera elementy członkowskie, które mają zostać wyodrębnione. Gdy kursor znajduje się w tym miejscu, należy wywołać interfejs wyodrębnić operacja refaktoryzacji.  
  
 Po rozpoczęciu procesu wyodrębniania interfejsu klasy lub struktury, Lista zasad i interfejsów jest modyfikowane w celu uwzględnienia nowej nazwy interfejsu. Po rozpoczęciu procesu wyodrębniania interfejsu w interfejsie, Lista zasad i interfejsów nie jest modyfikowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](refactoring-csharp.md)
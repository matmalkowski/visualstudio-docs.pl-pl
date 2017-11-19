---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "Refaktoryzacja usuwania parametrów (C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.remove
dev_langs: CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5e53d813d9b2dcefd2b2d19da2a76b6c0d1f989
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="remove-parameters-refactoring-c"></a>Refaktoryzacja usuwania parametrów (C#)
`Remove Parameters`jest operacja refaktoryzacji, który zapewnia prosty sposób można usunąć parametry z indeksatorów, metod lub obiektów delegowanych. Usuń zmiany parametrów deklaracji; we wszystkich lokalizacjach, gdzie jest wywoływany element członkowski parametr zostaną usunięte, aby uwzględnić nowe oświadczenie.  
  
 Operacja Usuń parametry pierwszy umieszczając kursor na metodę, indeksator lub delegata. Gdy kursor znajduje się w pozycji do wywołania, Usuń `Parameters` operacji, kliknij przycisk **Refaktoryzuj** menu, naciśnij klawisz skrótu klawiaturowego, lub wybierz polecenie z menu skrótów.  
  
> [!NOTE]
>  Nie można usunąć pierwszy parametr metody rozszerzenia.  
  
### <a name="to-remove-parameters"></a>Aby usunąć parametrów  
  
1.  Utwórz aplikację konsoli o nazwie `RemoveParameters`, a następnie zastąp `Program` następującym kodem.  
  
    ```csharp  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Umieść kursor w metodzie `A`, albo w deklaracji metody lub wywołanie metody.  
  
3.  Z **Refaktoryzuj** menu, wybierz opcję **Usuń parametry** do wyświetlenia **Usuń parametry** okno dialogowe.  
  
     Możesz także wpisać skrótu klawiaturowego CTRL + R, V, aby wyświetlić **Usuń parametry** okno dialogowe.  
  
     Również kliknięciu prawym przyciskiem myszy kursora, wskaż polecenie **Refaktoryzuj**, a następnie kliknij przycisk **Usuń parametry** do wyświetlenia **Usuń parametry** okno dialogowe.  
  
4.  Przy użyciu **parametry** pola, umieść kursor na `int i`, a następnie kliknij przycisk **Usuń**.  
  
5.  Kliknij przycisk **OK**.  
  
6.  W **podgląd zmian — Usuń parametry** okno dialogowe, kliknij przycisk **Zastosuj**.  
  
## <a name="remarks"></a>Uwagi  
 Możesz usunąć parametry z deklaracji metody lub wywołanie metody. Umieść kursor w nazwie metody deklaracji ani obiektem delegowanym i wywołać Usuń parametry.  
  
> [!CAUTION]
>  Usuń umożliwia parametrów, aby usunąć parametr, do którego odwołuje się w treści elementu członkowskiego, ale nie usuniesz odwołań do parametru w treści metody. To powodować błędy kompilacji w kodzie. Można jednak użyć **podgląd zmian** okno dialogowe do przeglądania kodu przed wykonaniem operacji refaktoryzacji.  
  
 Parametr usuwany jest modyfikowany podczas wywołania metody, usunięcie parametru spowoduje również usunięcie modyfikacji. Na przykład jeśli wywołanie metody została zmieniona z  
  
```csharp  
MyMethod(param1++, param2);  
```  
  
 na  
  
```csharp  
MyMethod(param2);  
```  
  
 Operacja refaktoryzacji `param1` nie zwiększa się.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](refactoring-csharp.md)
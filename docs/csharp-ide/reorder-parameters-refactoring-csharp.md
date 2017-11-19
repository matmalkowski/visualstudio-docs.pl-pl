---
redirect_url: /visualstudio/csharp-ide/refactoring/change-method-signature
title: "Refaktoryzacja (C#) zmiany kolejności parametrów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.csharp.refactoring.reorder
dev_langs: CSharp
helpviewer_keywords:
- refactoring [C#], Reorder Parameters
- Reorder Parameters refactoring [C#]
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3469e9ae7101c9e180fba5558fce389c6dfcc72d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="reorder-parameters-refactoring-c"></a>Refaktoryzacja zmiany kolejności parametrów (C#)
`Reorder Parameters`jest Visual C# refaktoryzacji operacja, która zapewnia łatwy sposób zmiany kolejności parametrów dla metody, indeksatorów i delegatów. `Reorder Parameters`Zmienia deklaracji, i we wszystkich lokalizacjach, gdzie jest wywoływany element członkowski, parametry są ponownie rozmieszczać, aby odzwierciedlić nową kolejność.  
  
 Aby wykonać `Reorder Parameters` operacji umieścić kursor na lub obok metody, indeksator lub delegata. Gdy kursor znajduje się w miejscu, należy wywołać `Reorder Parameters` operacji, naciskając klawisz skrótu klawiaturowego lub przez kliknięcie przycisku polecenia z menu skrótów.  
  
> [!NOTE]
>  Nie można zmienić kolejności pierwszym parametrem w metodzie rozszerzenia.  
  
### <a name="to-reorder-parameters"></a>Aby zmienić kolejność parametrów  
  
1.  Utwórz bibliotekę klasy o nazwie `ReorderParameters`, a następnie zastąp `Class1` z Poniższy przykładowy kod.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Umieść kursor na `MethodB`, albo w deklaracji metody lub wywołanie metody.  
  
3.  Na **Refaktoryzuj** menu, kliknij przycisk **zmiany kolejności parametrów**.  
  
     **Zmiany kolejności parametrów** zostanie wyświetlone okno dialogowe.  
  
4.  W **zmiany kolejności parametrów** okno dialogowe, wybierz opcję `int i` w **parametry** listy, a następnie kliknij przycisk w dół.  
  
     Alternatywnie możesz przeciągać `int i` po `bool b` w **parametry** listy.  
  
5.  W **zmiany kolejności parametrów** okno dialogowe, kliknij przycisk **OK**.  
  
     Jeśli **podgląd zmian odwołanie** jest zaznaczona opcja **zmiany kolejności parametrów** okno dialogowe **podgląd zmian — zmiany kolejności parametrów** zostanie wyświetlone okno dialogowe. Zapewnia podgląd zmian na liście parametrów dla `MethodB` zarówno podpis, jak i wywołanie metody.  
  
    1.  Jeśli **podgląd zmian — zmiany kolejności parametrów** zostanie wyświetlone okno dialogowe, kliknij przycisk **Zastosuj**.  
  
         W tym przykładzie deklaracji metody i wszystkie metody wywołania witryny `MethodB` zostały zaktualizowane.  
  
## <a name="remarks"></a>Uwagi  
 Można zmienić kolejność parametrów z deklaracji metody lub wywołanie metody. Umieść kursor na lub obok deklaracja metody lub delegata, ale nie w treści.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](refactoring-csharp.md)
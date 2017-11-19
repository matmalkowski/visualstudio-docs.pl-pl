---
title: "Wiele DSLs w jedno rozwiązanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b55d1d5ec8e84c8d16681ffd0ac738291e1bc39d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="multiple-dsls-in-one-solution"></a>Wiele języków DSL w jednym rozwiązaniu
Można spakować DSLs kilka w ramach jednego rozwiązania, dzięki czemu są one zainstalowane ze sobą.  
  
 Kilka technik umożliwia integrację wielu DSLs. Aby uzyskać więcej informacji, zobacz [integrowanie modeli przy użyciu programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) i [porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) i [Dostosowywanie zachowania kopii](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Aby utworzyć więcej niż jeden DSL w tym samym rozwiązaniu  
  
1.  Utwórz dwa lub więcej rozwiązań DSL i projektu VSIX, a następnie dodać wszystkie projekty do jednego rozwiązania.  
  
    -   Aby utworzyć nowy projekt VSIX: W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#**, **rozszerzalności**, **projektu VSIX**.  
  
    -   Utwórz dwa lub więcej rozwiązań DSL w katalog rozwiązania VSIX.  
  
         Dla każdego DSL Otwórz nowe wystąpienie programu Visual Studio. Utwórz nowy DSL i określ tego samego folderu rozwiązania jako rozwiązanie VSIX.  
  
         Upewnij się, tworzenie każdego DSL z rozszerzeniem innej nazwy pliku.  
  
    -   Zmiana nazwy **Dsl** i **DslPackage** projekty, dzięki czemu są one różne. Na przykład: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   W każdym **DslPackage\*\source.extension.tt**, zaktualizuj ten wiersz do poprawnej nazwy projektu Dsl:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   W rozwiązaniu VSIX, Dodaj Dsl * i DslPackage\* projektów.  
  
         Można umieścić w osobnym folderze rozwiązania każdej pary.  
  
2.  Łączenie manifestach VSIX DSLs:  
  
    1.  Otwórz *YourVsixProject***\source.extension.manifest**.  
  
    2.  Dla każdego DSL wybierz **Dodaj zawartość** i dodać:  
  
        -   `Dsl*`projekt jako **składników MEF**  
  
        -   `DslPackage*`projekt jako **składników MEF**  
  
        -   `DslPackage*`projekt jako **pakiet programu VS**  
  
3.  Skompiluj rozwiązanie.  
  
 Wynikowa VSIX zainstaluje zarówno DSLs. Można przetestować je za pomocą F5 lub wdrożyć *YourVsixProject***\bin\Debug\\\*.vsix**.  
  
## <a name="see-also"></a>Zobacz też  
 [Integrowanie modeli przy użyciu programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Porady: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md)
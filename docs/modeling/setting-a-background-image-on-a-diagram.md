---
title: "Ustawienie obraz tła na diagramie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 486ef0391f324ea355dd1ccdfc698c5c0394c1d8
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="setting-a-background-image-on-a-diagram"></a>Ustawienie obrazu tła w diagramie
W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania zestawu SDK, należy określić obrazu tła wygenerowanego projektanta przy użyciu kodu niestandardowego.  
  
## <a name="setting-the-background-image"></a>Ustawienie obrazu tła  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Aby ustawić obraz tła dla wygenerowanego projektanta  
  
1.  Skopiuj plik obrazu, który ma być używany jako tło diagramu do katalogu Dsl\Resources dla bieżącego projektu.  
  
2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy Dsl\Resources folder, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **istniejący element**.  
  
3.  W **Dodaj istniejący element** okno dialogowe, przejdź do folderu Dsl\Resources.  
  
4.  W **pliki typu** kliknij **pliki obrazów**.  
  
5.  Kliknij plik obrazu, który został skopiowany do katalogu, a następnie kliknij przycisk **Dodaj**.  
  
6.  Kliknij prawym przyciskiem myszy Dsl, a następnie kliknij przycisk **właściwości** aby otworzyć okno właściwości projektu Dsl.  
  
7.  Na **zasobów** , kliknij pozycję **ten projekt nie zawiera domyślnego pliku zasobów. Kliknij tutaj, aby go utworzyć.**  
  
8.  Dodaj plik obrazu pliku zasobów przez przeciąganie obrazów z **Eksploratora rozwiązań** do okna zasobów.  
  
9. Otwórz menu Plik, a następnie kliknij opcję, aby zapisać właściwości projektu.  
  
10. Sprawdź, czy plik Dsl\Properties\Resources.resx istnieje i ma pliku Resources.Designer.cs na jego podstawie.  
  
11. Jeśli brakuje Resources.Designer.cs, kliknij plik Resources.resx w **Eksploratora rozwiązań**.  
  
12. W **właściwości** ustaw `Custom Tool` właściwości `ResXFileCodeGenerator`.  
  
13. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt Dsl, wskaż polecenie **Dodaj**i kliknij przycisk **nowy Folder**.  
  
14. Nazwa folderu **niestandardowy**.  
  
15. Kliknij prawym przyciskiem myszy folder niestandardowe, wskaż pozycję **Dodaj**i kliknij przycisk **nowy element**.  
  
16. W **Dodaj nowy element** okna dialogowego, **szablony** kliknij **pliku kodu**.  
  
17. W **nazwa** wpisz `BackgroundImage.cs`i kliknij przycisk **Dodaj**.  
  
18. Skopiuj następujący kod do pliku BackgroundImage.cs dostosowywania przestrzeni nazw, nazwa klasy diagramu i nazwę zasobu dla pliku obrazu.  
  
     Zastąp nazwę klasy częściowej diagram, który jest zdefiniowany w Dsl\GeneratedCode\Diagrams.cs "MyDiagramClass". Można również pobrać poprawną przestrzeń nazw z pliku Dsl\GeneratedCode\Diagrams.cs.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Aby uzyskać więcej informacji na temat dostosowywania model kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie łączników i kształtów](../modeling/defining-shapes-and-connectors.md)   
 [Dostosowywanie pola obrazu i tekstu](../modeling/customizing-text-and-image-fields.md)   
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

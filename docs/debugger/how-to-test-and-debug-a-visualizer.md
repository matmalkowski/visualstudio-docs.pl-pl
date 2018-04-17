---
title: 'Porady: testowanie i debugowanie Wizualizera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6189abf72a8459618a83a4e5b12d5c3edb1b6a52
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Porady: testowanie i debugowanie wizualizera
Raz zostały zapisane wizualizatora, musisz debugowania i testowania go.  
  
 Jednym ze sposobów testu wizualizatora jest zamontowany w programie Visual Studio i wywoływanie go z okna debugera. (Zobacz [porady: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md).) Można to zrobić, należy używać drugie wystąpienie programu Visual Studio do dołączania i debugowania wizualizatora, w którym jest uruchomiony program w pierwszej kolejności debugera.  
  
 Jest prostsze debugowanie wizualizera do uruchomienia wizualizatora sterowniku testu. Wizualizator interfejsów API ułatwiają tworzenie takiego sterownika, która jest wywoływana *wizualizatora programowanie hosta*.  
  
### <a name="to-create-a-visualizer-development-host"></a>Aby utworzyć hosta programowanie wizualizatora  
  
1.  W klasie po stronie debugera obejmują statyczną metodę, która tworzy <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> obiektu i wywołuje metodę jego Pokaż:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Obiekt danych, który ma być wyświetlany w wizualizatora są parametry używane do utworzenia hosta (`objectToVisualize`) i typ klasy po stronie debugera.  
  
2.  Dodaj następującą instrukcję do wywołania `TestShowVisualizer`. Jeśli utworzono z wizualizatora w bibliotece klas, należy utworzyć plik wykonywalny do wywołania biblioteki klas i umieścić to oświadczenie w pliku wykonywalnego:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Aby uzyskać bardziej szczegółowy przykład, zobacz [wskazówki: pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Pisanie wizualizatora w C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Porady: Instalacja programu Visualizer](../debugger/how-to-install-a-visualizer.md)   
 [Utwórz niestandardowe Wizualizatory](../debugger/create-custom-visualizers-of-data.md)
---
title: 'Porady: testowanie i debugowanie Wizualizera | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9972951b1c5064fcc0582909976a234158ea096
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694260"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Porady: testowanie i debugowanie wizualizera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: testowanie i debugowanie Wizualizera](https://docs.microsoft.com/visualstudio/debugger/how-to-test-and-debug-a-visualizer).  
  
Po napisaniu wizualizatora, należy do debugowania i testowania.  
  
 Jednym ze sposobów, aby przetestować Wizualizator jest zamontowany w programie Visual Studio i wywoływania go z okna debugera. (Zobacz [porady: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md).) Jeśli to zrobisz, musisz użyć drugiego wystąpienia programu Visual Studio do dołączenia i debugowanie wizualizatora, w którym jest uruchomiony w pierwszej kolejności debugera.  
  
 Łatwiejsze debugowanie wizualizera jest przeprowadzić wizualizatora sterowniku testu. Wizualizator interfejsów API ułatwiają tworzenie takich sterownika, który jest nazywany *hosta rozwoju Wizualizator*.  
  
### <a name="to-create-a-visualizer-development-host"></a>W celu utworzenia hosta rozwoju wizualizatora  
  
1.  W klasie po stronie debugera zawierają statycznej metody, która tworzy <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost> obiektów i wywołuje swoją metodę show:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Parametry używane do konstruowania hosta jest obiekt danych, który ma być wyświetlany w wizualizatorze (`objectToVisualize`) i typ klasy po stronie debugera.  
  
2.  Dodaj następującą instrukcję, aby wywołać `TestShowVisualizer`. Jeśli Twoje visualizer został utworzony w bibliotece klas, musisz utworzyć plik wykonywalny do wywołania biblioteki klas i umieszczania tej instrukcji w plik wykonywalny:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Aby uzyskać pełniejszy przykład, zobacz [wskazówki: pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Pisanie wizualizatora w języku C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Porady: Instalowanie wizualizatora](../debugger/how-to-install-a-visualizer.md)   
 [Tworzenie niestandardowych Wizualizatorów](../debugger/create-custom-visualizers-of-data.md)




---
title: "Tworzenie niestandardowych widoków danych w debugerze | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 06/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], inspecting programs
- debugger, viewing data
ms.assetid: 13e1105f-f987-402e-9108-ec6ac12be042
caps.latest.revision: "30"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dad9291e60577bd5d6faec557931ac3dcd37c45a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Tworzenie niestandardowych widoków danych w debugerze programu Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugera zawiera różnych narzędzi do sprawdzania i modyfikowania stanu programu. Większość tych funkcji narzędzia tylko w trybie przerwania.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Tworzenie niestandardowych widoków danych w zmiennych systemu windows i etykietki danych
 Duża liczba [debugera systemu windows](../debugger/debugger-windows.md), takich jak **automatycznych** i **czujki** systemu windows, pozwala sprawdzać zmienne podczas debugowania. Można dostosować wyświetlanie typów natywnych i zarządzanych obiektów w oknach zmiennych debugera, a w [etykietek danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Może to być przydatne wyświetlić typy tworzonych w aplikacjach. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych widoków obiektów macierzystych](../debugger/create-custom-views-of-native-objects.md) i [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Utwórz niestandardowe wizualizatory  
 Wizualizatory można wyświetlać zawartość obiektu lub zmienna w znaczący sposób. W debugerze programu Visual Studio wizualizatora odwołuje się do innego systemu windows, które można otworzyć za pomocą ikonę lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikona wizualizatora"). Na przykład można wizualizatora HTML wyświetlić ciąg HTML, jak będą interpretowane i wyświetlania w przeglądarce. Dostępne wizualizatorów etykietek danych, **czujki** okna, **automatycznych** okna, **zmiennych lokalnych** okna, lub **QuickWatch** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [utworzyć niestandardowe wizualizatory](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Okno polecenia](../ide/reference/command-window.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
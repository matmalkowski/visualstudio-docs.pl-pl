---
title: Tworzenie niestandardowych widoków danych w debugerze | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/27/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02bb65aa2b0601315a3f5dec2cc9459af210db3e
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2018
ms.locfileid: "39177675"
---
# <a name="create-custom-views-of-data-in-the-visual-studio-debugger"></a>Tworzenie niestandardowych widoków danych w debugerze programu Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debugera zawiera szereg narzędzi do inspekcji i modyfikacji stanu programu. Większość tych narzędzi działa tylko w trybie przerwania.

## <a name="create-custom-views-of-data-in-variable-windows-and-datatips"></a>Tworzenie niestandardowych widoków danych w oknach zmiennych i etykietki danych
 Wiele [okna debugera](../debugger/debugger-windows.md), takich jak **Autos** i **Obejrzyj** systemu windows, pozwalają na sprawdzanie zmiennych podczas debugowania. Można dostosować wyświetlanie typach natywnych i zarządzanych obiektów w oknach zmiennych debugera, a w [DataTips](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Może to być przydatne wyświetlić typy, utworzonej we własnych aplikacjach. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych widoków obiektów macierzystych](../debugger/create-custom-views-of-native-objects.md) i [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-dot-managed-objects.md).
  
## <a name="create-custom-visualizers"></a>Tworzenie niestandardowych wizualizatorów  
 Wizualizatory umożliwiają wyświetlanie zawartości zmiennej lub obiektu w znaczący sposób. W debugerze programu Visual Studio wizualizatora odnosi się do innego systemu windows, które można otworzyć za pomocą ikony lupy ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ikonę Wizualizator"). Na przykład można użyć wizualizatora HTML do wyświetlenia ciągu HTML, jak byłby interpretowany i wyświetlany w przeglądarce. Dostęp wizualizatorów można uzyskać poprzez DataTips, **Obejrzyj** oknie **Autos** oknie **zmiennych lokalnych** oknie lub **QuickWatch** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych wizualizatorów](../debugger/create-custom-visualizers-of-data.md).
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/getting-started-with-the-debugger.md)   
 [Okno polecenia](../ide/reference/command-window.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)
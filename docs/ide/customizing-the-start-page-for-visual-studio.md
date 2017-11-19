---
title: "Dostosowanie strony początkowej w Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 178c20c9c4c3af8f5252e70ca603cdf8f8335e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>Dostosowanie strony początkowej dla programu Visual Studio
Można dostosować stronę początkową dla programu Visual Studio na kilka sposobów domyślne, takie jak wyświetlanie **Otwórz projekt** okno dialogowe lub otwieranie rozwiązania, które zostały ostatnio załadowane. Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.  

## <a name="customize-the-default-start-page"></a>Dostosowywanie domyślnej strony początkowej  

1.  Na pasku menu wybierz **narzędzia**, **opcje**.  

2.  Rozwiń węzeł **środowiska**, a następnie wybierz pozycję **uruchamiania**.  

3.  W **przy uruchamianiu** listy, wybierz element do dostosowania, które mają.  

## <a name="show-a-custom-start-page"></a>Pokaż niestandardową stronę początkową  

1.  Zainstaluj niestandardową stronę początkową na jeden z następujących sposobów:  

    -   Zainstaluj ją z [galerii programu Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), inna witryna sieci Web lub strony w lokalnym intranecie.  

        Otwórz plik .vsix, który zawiera strona początkowa niestandardowych, lub skopiuj i Wklej pliki strony początkowej w **% USERPROFILE % \My Studio 2017\StartPages** folderu na komputerze.  

    -   Utwórz własną stronę początkową, jeśli zainstalowałeś Visual Studio SDK.  

         Zobacz [Tworzenie niestandardowej strony początkowej](../extensibility/creating-a-custom-start-page.md).  

2.  Na pasku menu wybierz **narzędzia**, **opcje**.  

3.  Rozwiń węzeł **środowiska**, a następnie wybierz pozycję **uruchamiania**.  

4.  W **dostosowanie strony początkowej** wybierz strony, którą chcesz.  

> [!NOTE]
>  Jeśli błąd na niestandardowej stronie początkowej powoduje, że Visual Studio ulega awarii, możesz uruchomić Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby używał domyślnej strony początkowej. Zobacz [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  

## <a name="see-also"></a>Zobacz także  
 [Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)   

---
title: "Zainstaluj strony początkowej niestandardowych lub zmień element startowy w programie Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: ecc22bd23b5b245173321ed3a12379c6fe5622af
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="customize-the-start-page-for-visual-studio"></a>Dostosowanie strony początkowej dla programu Visual Studio

Środowisko uruchamiania dla programu Visual Studio można dostosować na różne sposoby, takie jak wyświetlanie **Otwórz projekt** okno dialogowe lub otwieranie rozwiązania, które zostały ostatnio załadowane. Można także pokazać niestandardową stronę początkową, czyli stronę XAML Windows Presentation Foundation (WPF), która jest uruchamiana w oknie narzędzi i może wykonywać wewnętrzne polecenia Visual Studio.

## <a name="to-change-the-startup-item"></a>Aby zmienić element startowy

1. Na pasku menu wybierz **narzędzia**, **opcje**.

1. Rozwiń węzeł **środowiska**, a następnie wybierz pozycję **uruchamiania**.

1. W **przy uruchamianiu** listy, wybierz element, który będzie wyświetlany po uruchomieniu programu Visual Studio.

## <a name="to-show-a-custom-start-page"></a>Aby wyświetlić niestandardowej strony początkowej

Możesz [utworzyć stronę początkową niestandardowych](../extensibility/creating-a-custom-start-page.md) przy użyciu programu Visual Studio SDK lub użyć innej osobie został już utworzony. Na przykład można znaleźć start niestandardowych stron w [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Aby zainstalować strony początkowej niestandardowych, otwórz plik .vsix lub skopiuj i Wklej pliki stronicowania start do **%USERPROFILE%\Documents\Visual 2017\StartPages w Studio** folderu na komputerze.

### <a name="to-select-which-custom-start-page-to-display"></a>Aby wybrać które strony początkowej niestandardowych do wyświetlenia

1. Na pasku menu wybierz **narzędzia**, **opcje**.

1. Rozwiń węzeł **środowiska**, a następnie wybierz pozycję **uruchamiania**.

1. W **dostosowanie strony początkowej** wybierz strony, którą chcesz.

> [!NOTE]
> Jeśli błąd na niestandardowej stronie początkowej powoduje, że Visual Studio ulega awarii, możesz uruchomić Visual Studio w trybie awaryjnym, a następnie ustawić go tak, aby używał domyślnej strony początkowej. Zobacz [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Zobacz także

[Personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md)

---
title: "Opcje — okno dialogowe (Visual Studio) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b196adf16359c640ba08495b36f4ba428cf8ba48
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="options-dialog-box-visual-studio"></a>Opcje — Okno dialogowe [Visual Studio]
**Opcje** okno dialogowe umożliwia skonfigurowanie zintegrowane środowisko programistyczne (IDE) do własnych potrzeb. Na przykład można założyć domyślną lokalizację zapisywania dla projektów, zmienić domyślny wygląd i zachowanie systemu windows i tworzenie skrótów do często używanych poleceń. Dostępne są także opcje specyficzne dla języka programowania i platform. Dostęp można uzyskać **opcje** z **narzędzia** menu.  
  
> [!NOTE]
>  Opcje dostępne w oknach dialogowych i nazwy i lokalizacje poleceń menu, które zostanie wyświetlone, może się różnić od co to jest opisany w pomocy, w zależności od wersji lub aktywne ustawienia. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="layout-of-the-options-dialog-box"></a>Układ okna dialogowego Opcje  
 **Opcje** okno dialogowe jest podzielony na dwie części: okienka nawigacji po lewej stronie i obszar wyświetlania po prawej stronie. Drzewie w okienku nawigacji zawiera węzły folderów, takich jak środowisko, Edytor tekstu, projekty i rozwiązania i kontroli źródła. Rozwiń węzeł dowolnego folderu, aby wyświetlić listę strony opcji, które zawiera. Po wybraniu węzła dla określonej strony jego opcje są wyświetlane w obszarze.  
  
 Opcje dla funkcji IDE są wyświetlane w okienku nawigacji dopiero funkcji jest ładowany do pamięci. W związku z tym te same opcje mogą nie być wyświetlane po rozpoczęciu nowej sesji wyświetlanej jako zakończonego ostatniego. Podczas tworzenia projektu lub uruchamiania poleceń, które używa określonej aplikacji, węzły odpowiednie opcje są dodawane do okna dialogowego Opcje. Dodać te opcje zostaną następnie pozostają dostępne tak długo, jak funkcja IDE pozostaje w pamięci.  
  
> [!NOTE]
>  Niektóre ustawienia kolekcji zakresu liczbę stron, które są widoczne w okienku nawigacji w oknie dialogowym Opcje. Można wybrać wyświetlić wszystkie strony, wybierając **Pokaż wszystkie ustawienia**.  
  
## <a name="how-options-are-applied"></a>Jak są stosowane opcje  
 Kliknięcie przycisku OK w **opcje** okno dialogowe zapisuje wszystkie ustawienia na wszystkich stronach. Kliknięcie przycisku Anuluj na każdej stronie anuluje wszystkie żądania zmiany, wraz ze wszystkimi dokonaną drugiej **opcje** stron. Niektóre zmiany ustawienia opcji, takich jak te na [czcionki i kolory, środowisko, opcje — Okno dialogowe](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), tylko będzie obowiązywać po zakończeniu zamknij i otwórz ponownie program Visual Studio.  
  
### <a name="show-all-settings"></a>Pokaż wszystkie ustawienia  
 Zaznaczenie lub unselecting **Pokaż wszystkie ustawienia** stosuje wszystkie zmiany wprowadzone w **opcje** okno dialogowe, nawet wtedy, gdy nie ma jeszcze kliknięty **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Dopasowywanie edytora](../../ide/customizing-the-editor.md)
---
title: "Porady: Określanie ikony aplikacji (Visual Basic, C#) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3309b02a50f3f14d166044c2d1cea35bdab3922f
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Porady: określanie ikony aplikacji (Visual Basic, C#)

`Icon` Właściwości dla projektu określa plik ikony (.ico) który będzie wyświetlany dla skompilowanej aplikacji w Eksploratorze plików, a na pasku zadań systemu Windows.

`Icon` Właściwości można uzyskać w **aplikacji** okienku **projektanta projektu**; zawiera listę ikony, które zostały dodane do projektu jako zasoby lub plików zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikona dla aplikacji, można również ustawić `Icon` właściwości każdego **okna** lub **formularza** w aplikacji. Informacje o okna ikony dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.

## <a name="to-specify-an-application-icon"></a>Aby określić ikony aplikacji

1. W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).

1. Na pasku menu wybierz **projektu** > **właściwości**.

1. Gdy **projektanta projektu** zostanie wyświetlone, wybierz **aplikacji** kartę.

1. **(Visual Basic)**  &mdash;w **ikona** listy, wybierz plik ikony (.ico).

    **C#**&mdash;pobliżu **ikona** wybierz  **\<Przeglądaj >** przycisk, a następnie przejdź do lokalizacji pliku ikony, która ma.

## <a name="see-also"></a>Zobacz także

[Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)

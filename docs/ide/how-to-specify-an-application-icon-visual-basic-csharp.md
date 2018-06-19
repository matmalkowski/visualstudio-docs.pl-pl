---
title: 'Porady: Określanie ikony aplikacji (Visual Basic, C#)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8da1de87031db962ede178a742325d9206e808c3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945223"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Porady: Określanie ikony aplikacji (Visual Basic, C#)

`Icon` Właściwości dla projektu określa plik ikony (*.ico*) który będzie wyświetlany dla aplikacji skompilowanych w **Eksploratora plików** i na pasku zadań systemu Windows.

`Icon` Właściwości można uzyskać w **aplikacji** okienku **projektanta projektu**; zawiera listę ikony, które zostały dodane do projektu jako zasoby lub plików zawartości.

> [!NOTE]
> Po ustawieniu właściwości ikona dla aplikacji, można również ustawić `Icon` właściwości każdego **okna** lub **formularza** w aplikacji. Informacje o okna ikony dla aplikacji autonomicznych Windows Presentation Foundation (WPF), zobacz <xref:System.Windows.Window.Icon%2A> właściwości.

## <a name="to-specify-an-application-icon"></a>Aby określić ikony aplikacji

1. W **Eksploratora rozwiązań**, wybierz węzeł projektu (nie **rozwiązania** węzła).

1. Na pasku menu wybierz **projektu** > **właściwości**.

1. Gdy **projektanta projektu** zostanie wyświetlone, wybierz **aplikacji** kartę.

1. **(Visual Basic)**  &mdash;w **ikona** wybierz ikonę (*.ico*) pliku.

    **C#**&mdash;pobliżu **ikona** wybierz  **\<Przeglądaj >** przycisk, a następnie przejdź do lokalizacji pliku ikony, która ma.

## <a name="see-also"></a>Zobacz także

- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
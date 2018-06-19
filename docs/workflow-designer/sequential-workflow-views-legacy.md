---
title: Projektant przepływu pracy — widoki sekwencyjnego przepływu pracy (starsze)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce1217ea629ae0301b72b444161d61db4fe448b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31976022"
---
# <a name="sequential-workflow-views-legacy"></a>Widoki sekwencyjnego przepływu pracy (starsze)

Program Visual Studio 2010 udostępnia starszej wersji projektanta przepływu pracy systemu Windows, który może służyć do docelowego .NET Framework w wersji 3.5 lub WinFX.

Projektant przepływu pracy umożliwia graficznie tworzenie aplikacji systemu Windows Workflow Foundation (WF) przy użyciu znanych interfejsu użytkownika programu Visual Studio. Aplikacje systemu Windows Workflow Foundation (WF) składają się z etapów procesu przepływu pracy nazywane działaniami. Aby utworzyć przepływ pracy, napisz działań na powierzchni projektu przez przeciąganie ich projektanci odpowiednich działań z **przybornika** na powierzchnię projektu.

Po utworzeniu sekwencyjnego przepływu pracy, który jest [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), dostępne są trzy widoki przepływu pracy. Widoki te są dostępne z **przepływu pracy** menu i z menu kontekstowego na powierzchni projektu.

W poniższej tabeli wymieniono nazwę i opis każdego widoku.

|Opcja menu, karta|Opis|
|----------------------|-----------------|
|**Widok sekwencyjnego przepływu pracy**|Kliknij prawym przyciskiem myszy projekt powierzchni i wybierz pozycję **sekwencyjnego przepływu pracy Wyświetl** opcję z menu kontekstowego, aby wyświetlić **sekwencyjnego przepływu pracy** widoku, który zawiera działanie podstawie graficznego Reprezentacja sekwencyjnego przepływu pracy. Lub wybierz **sekwencyjnego przepływu pracy Wyświetl** z **przepływu pracy** menu.|
|**Wyświetl obsługę operacji anulowania**|Kliknij prawym przyciskiem myszy projekt powierzchni i wybierz pozycję **widoku anulowanie obsługi** opcję z menu kontekstowego, aby wyświetlić **sekwencyjnego przepływu pracy** wyświetlić, która zawiera [działania CancellationHandlerActivity ](http://go.microsoft.com/fwlink?LinkID=65050) działania związane z przepływem pracy. Lub wybierz **widoku anulowanie obsługi** z **przepływu pracy** menu.|
|**Program obsługi błędów widoku**|Kliknij prawym przyciskiem myszy projekt powierzchni i wybierz pozycję **obsługi błędów w widoku** opcję z menu kontekstowego, aby wyświetlić **błędów** wyświetlić, która zawiera [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) działania związane z przepływem pracy. Lub wybierz **obsługi błędów w widoku** z **przepływu pracy** menu.|

 Aby uzyskać więcej informacji o podobnych widokach, zobacz [działania widoków (starsze)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>Zobacz także

- [Widoki działania (starsza wersja)](../workflow-designer/activity-views-legacy.md)
- [Tworzenie starszej wersji projektów przepływu pracy](../workflow-designer/creating-legacy-workflow-projects.md)
- [Trybów tworzenia przepływu pracy](http://go.microsoft.com/fwlink?LinkID=65014)
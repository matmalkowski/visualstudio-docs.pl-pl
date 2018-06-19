---
title: Projektant przepływu pracy — działania widoków (starsze)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d3453ecefece93f593c3d4ebbc261e4332815da
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970337"
---
# <a name="activity-views-legacy"></a>Widoki działania (starsze)

Wiele działań dostarczane przez Windows Workflow Foundation (WF), z którego składają się przepływy pracy, ma kilka widoków projektu dostępne w starszych projektanta przepływów pracy systemu Windows. Przeciągnięcie Projektant działań z **przybornika** na powierzchnię projektu, a następnie po wybraniu działania można przełączać się między widokami projektowania przy użyciu **przepływu pracy**menu lub klikając prawym przyciskiem myszy wybrane działanie. Podczas przesuwania wskaźnika nad nazwę wybranego działania listy rozwijanej zbiór kart pojawia się również czy służy do przełączania się między różne widoki.

Każde działanie ma co najmniej jeden widok; jest to domyślny widok wyświetlany podczas przeciągania Projektant działań z **przybornika** na powierzchnię projektu. Widok domyślny to działanie jest dostępne jako **[Typ działania] widoku** opcji menu i karty, na przykład **widoku równoległych**. Większość działań ma dodatkowe widoki i różnych działań może mieć różne widoki. Na przykład [działania TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) działanie ma widoku kompensacji i [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) działanie ma zdarzeń widoku. Wiele działań, które pochodzą z programu Windows Workflow Foundation ma **widoku anulowanie obsługi** i **widoku błędów** projektowaniu widoków do widoku [działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) i [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) skojarzonych z nimi.

W poniższej tabeli wymieniono nazwę i opis każdego widoku.

|Opcja menu, karta|Opis|
|----------------------|-----------------|
|**Widok [Typ działania]**|Wybierz tę opcję menu lub kartę, aby wyświetlić graficzną reprezentację domyślne wybranego działania.|
|**Wyświetl obsługę operacji anulowania**|Wybierz tę opcję menu lub na karcie Widok, aby wyświetlić [działania CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) skojarzonych z wybranym działaniem.|
|**Program obsługi błędów widoku**|Wybierz tę opcję menu lub na karcie Widok, aby wyświetlić [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) skojarzonych z wybranym działaniem.|
|**Widok kompensacji**|Wybierz tę opcję menu lub na karcie Widok, aby wyświetlić [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) skojarzonych z wybranym [działania TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093).|
|**Program obsługi zdarzeń widoku**|Wybierz tę opcję menu lub na karcie Widok, aby wyświetlić [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) skojarzonych z wybranym [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030).|

Informacje o podobnych widoków, zobacz [sekwencyjnego przepływu pracy, widoki (starsze)](../workflow-designer/sequential-workflow-views-legacy.md).

## <a name="see-also"></a>Zobacz także

- [Działania przepływu pracy w starszej wersji](../workflow-designer/legacy-workflow-activities.md)
- [Widoki sekwencyjnego przepływu pracy (starsza wersja)](../workflow-designer/sequential-workflow-views-legacy.md)
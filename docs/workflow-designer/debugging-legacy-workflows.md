---
title: Projektant przepływu pracy — debugowania przepływów pracy starsza wersja
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging
- debugging, workflows
- debugging workflows
ms.assetid: e6097b47-760a-4b30-a92c-ae70cdbda49f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33a8358c5d62b938fc64d608c9b4546ab1745aaa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970380"
---
# <a name="debugging-legacy-workflows"></a>Debugowanie przepływów pracy starsza wersja

Jeśli używasz starszej wersji projektanta przepływów pracy systemu Windows w programie Visual Studio umożliwiające tworzenie aplikacji systemu Windows Workflow Foundation (WF), że target.NET Framework 3.0 lub 3.5 można debugować przepływy pracy, takich jak dowolnego innego programu przez ustawienie punktów przerwania, dołączanie do procesu, i sprawdzeniu wątków i stosu wywołań. Istnieje również możliwość debugowania zdalnego.

> [!NOTE]
> Jeśli wiele wersji programu Visual Studio zostały zainstalowane i odinstalować na komputerze, debugowanie WF3 może zakończyć się niepowodzeniem z jednym z dwóch następujące możliwości:
>
> -   Punkty przerwań nie są osiągane.
> -   Zostanie wyświetlony następujący komunikat:
>
> **Nie można rozpocząć debugowania na serwerze sieci web. Debuger nie jest poprawnie zainstalowany.  Nie można debugować żądanego typu kodu.  Uruchom Instalatora, aby zainstalować lub naprawić debuger.**
>
> W przypadku jednego z tych scenariuszy podczas debugowania środowiska .NET Framework 3.0 lub 3.5 przepływy pracy, wykonaj naprawę instalacji programu Visual Studio.

 Windows Workflow Foundation integruje się z następujących standardowych oknach debugowania programu Visual Studio:

-   **Punkt przerwania**: działa zgodnie z oczekiwaniami, ale Określ działanie dla nazwy funkcji.

-   **Stos wywołań**: zmodyfikowane w celu zapewnienia konspektu działań, które zostały wykonane w wystąpieniu przepływu pracy. Wpisy w **stos wywołań** okna są pierwszy głębokość wyszukiwania wykonywanych działań. Możesz kliknąć dwukrotnie wpis, aby umieścić fokus na działanie wybranego.

-   **Wątki**: zawiera identyfikator wystąpienia wystąpienia przepływu pracy, które jest debugowane.

 Visual Studio dla systemu Windows Workflow Foundation nie obsługuje debugowania następujące funkcje:

-   Warunkowe punkty przerwania na powierzchnię projektanta.

-   QuickWatch.

-   Ustaw następną instrukcję.

-   Uruchom do kursora.

-   Edytuj i Kontynuuj.

-   Debugowanie just in time.

-   Debugowanie w trybie mieszanym.
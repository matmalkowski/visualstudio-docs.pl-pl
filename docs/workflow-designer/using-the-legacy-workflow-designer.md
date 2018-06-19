---
title: Za pomocą projektanta przepływów pracy starsza wersja
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794b52c918eb727fe67d24af209d21403da18475
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975471"
---
# <a name="using-the-legacy-workflow-designer"></a>Za pomocą projektanta przepływów pracy starsza wersja

Starszego podane projektanta przepływów pracy programu Visual Studio 2010 można objęcie .NET Framework w wersji 3.5 lub WinFX.

Jest on dostępny przez wybranie jednej **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okna. Jest domyślną opcją w Visual Studio 2010 **.NET Framework 4** służącym do tworzenia aplikacji systemu Windows Workflow Foundation (WF), przeznaczone dla platformy .NET Framework 4.

Projektant przepływu pracy umożliwia graficznie tworzenie aplikacji systemu Windows Workflow Foundation (WF) przy użyciu znanych interfejsu użytkownika programu Visual Studio. Aplikacje systemu Windows Workflow Foundation (WF) składają się z etapów procesu przepływu pracy nazywane działaniami. Aby utworzyć przepływ pracy, napisz działań na powierzchni projektu przez przeciąganie ich projektanci odpowiednich działań z **przybornika** na powierzchnię projektu.

W poniższej tabeli wymieniono najważniejsze funkcje programu Visual Studio dla systemu Windows Workflow Foundation.

|Funkcja|Opis|
|-------------|-----------------|
|Działanie przeciąganie i upuszczanie|Przeciągnij działania z **przybornika** na powierzchnię projektu, aby utworzyć przepływ pracy.|
|Przeglądarka właściwości|Standardowe **właściwości** okna w programie Visual Studio jest używany do konfigurowania właściwości działania.|
|Powiększenie|Lornetka **poziom powiększenia** ikona znajduje się poniżej pionowy pasek przewijania po prawej stronie powierzchnię projektu. Kliknij Lornetka i wybierz wartość procentową powiększenia spowodować grafikę przepływu pracy, aby powiększyć lub pomniejszyć. Można również użyć **przesuwanie** ikonę lupy kursora opcje można powiększać i pomniejszać.|
|Panoramowanie|**Przesuwanie** ikona, koło, który zawiera cztery krzyżowej strzałki w czterech kierunków, znajduje się poniżej pionowy pasek przewijania po prawej stronie powierzchni projektowej poniżej Lornetka ikonę powiększenia. Po kliknięciu ikony przesuwanie menu podręczne udostępnia następujące opcje kursora:<br /><br /> - **Powiększ** kursora Lupa pozwala powiększać, klikając powierzchnię projektu.<br />- **Pomniejsz** kursora Lupa umożliwia pomniejszyć klikając powierzchnię projektu.<br />- **Narzędzie nawigacji** kursora ręcznie umożliwia "pobrania" i przesunięcia widoku na powierzchni projektu przepływu pracy.<br />- **Domyślne** kursora strzałkę umożliwia przełączenie z innych kursory do kursora strzałkę domyślne.|
|Przewijanie automatycznie|Jeśli masz dużą przepływu pracy, możesz umieścić działania poza widocznych powierzchni projektu. Program Visual Studio umożliwia przeciągnij działanie kierunku krawędzi najbliżej gdzie chcesz umieścić działania powierzchnię projektu. Widok powierzchni projektu automatycznie przewija w tym kierunku.|
|Tagi inteligentne|Działania, które nie został w pełni skonfigurowany lub nie jest prawidłowo skonfigurowane są oznaczone ikoną wykrzyknika. Możesz kliknąć ikonę i wyświetlenie listy rozwijanej potrzeb konfiguracji, które istnieją w działaniu. Następnie można użyć **właściwości** okno, aby skonfigurować odpowiednie działania. Gdy wszystkie właściwości są prawidłowe dla działania, ikona wykrzyknika zniknie.|

## <a name="see-also"></a>Zobacz także

- [Tworzenie przepływów pracy](http://go.microsoft.com/fwlink?LinkID=65010)
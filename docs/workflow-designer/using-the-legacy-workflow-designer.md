---
title: "Za pomocą projektanta przepływów pracy starszego | Dokumentacja firmy Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a042d98019b7f618792f7a9104d262362a4e6e3d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2018
---
# <a name="using-the-legacy-workflow-designer"></a>Za pomocą projektanta przepływów pracy starsza wersja
Starszego [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] dostarczonych przez [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] może służyć do docelowego [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] lub [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Jest on dostępny przez wybranie jednej **.NET Framework 3.0** opcji lub **.NET Framework 3.5** opcji na liście rozwijanej listy w górnej części **nowy projekt** okna. Domyślna opcja [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] jest **.NET Framework 4** używany do tworzenia [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacje, które odnoszą się do [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].

 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Umożliwia tworzenie graficznie [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacji przy użyciu znanych [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfejsu użytkownika. [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] aplikacje składają się z etapów procesu przepływu pracy nazywane działaniami. Aby utworzyć przepływ pracy, napisz działań na powierzchni projektu przez przeciąganie ich projektanci odpowiednich działań z **przybornika** na powierzchnię projektu.

 W poniższej tabeli wymieniono główne funkcje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dla programu Windows Workflow Foundation.

|Funkcja|Opis|
|-------------|-----------------|
|Działanie przeciąganie i upuszczanie|Przeciągnij działania z **przybornika** na powierzchnię projektu, aby utworzyć przepływ pracy.|
|Przeglądarka właściwości|Standardowe **właściwości** okna w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] służy do konfigurowania właściwości działania.|
|Powiększenie|Lornetka **poziom powiększenia** ikona znajduje się poniżej pionowy pasek przewijania po prawej stronie powierzchnię projektu. Kliknij Lornetka i wybierz wartość procentową powiększenia spowodować grafikę przepływu pracy, aby powiększyć lub pomniejszyć. Można również użyć **przesuwanie** ikonę lupy kursora opcje można powiększać i pomniejszać.|
|Panoramowanie|**Przesuwanie** ikona, koło, który zawiera cztery krzyżowej strzałki w czterech kierunków, znajduje się poniżej pionowy pasek przewijania po prawej stronie powierzchni projektowej poniżej Lornetka ikonę powiększenia. Po kliknięciu ikony przesuwanie menu podręczne udostępnia następujące opcje kursora:<br /><br /> - **Powiększ** kursora Lupa pozwala powiększać, klikając powierzchnię projektu.<br />- **Pomniejsz** kursora Lupa umożliwia pomniejszyć klikając powierzchnię projektu.<br />- **Narzędzie nawigacji** kursora ręcznie umożliwia "pobrania" i przesunięcia widoku na powierzchni projektu przepływu pracy.<br />- **Domyślne** kursora strzałkę umożliwia przełączenie z innych kursory do kursora strzałkę domyślne.|
|Przewijanie automatycznie|Jeśli masz dużą przepływu pracy, możesz umieścić działania poza widocznych powierzchni projektu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umożliwia przeciągnij działanie kierunku krawędzi najbliżej gdzie chcesz umieścić działania powierzchnię projektu. Widok powierzchni projektu automatycznie przewija w tym kierunku.|
|Tagi inteligentne|Działania, które nie został w pełni skonfigurowany lub nie jest prawidłowo skonfigurowane są oznaczone ikoną wykrzyknika. Możesz kliknąć ikonę i wyświetlenie listy rozwijanej potrzeb konfiguracji, które istnieją w działaniu. Następnie można użyć **właściwości** okno, aby skonfigurować odpowiednie działania. Gdy wszystkie właściwości są prawidłowe dla działania, ikona wykrzyknika zniknie.|

## <a name="see-also"></a>Zobacz także

- [Tworzenie przepływów pracy](http://go.microsoft.com/fwlink?LinkID=65010)
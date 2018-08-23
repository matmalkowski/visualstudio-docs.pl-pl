---
title: 'Porady: debugowanie XAML za pomocą projektanta przepływu pracy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 07208a51674bffc2fe2a3ad5750daee0e7560fcc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42631130"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Porady: debugowanie XAML za pomocą projektanta przepływu pracy
Przepływy pracy są definiowane zgodnie z XAML. Reprezentacja interfejsu użytkownika przepływu pracy jest oparty na drzewie XAML definiowanie przepływu pracy. Środowisko debugowania jest podobne do debugowania przepływów pracy w programie [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Na przykład podczas debugowania XAML, zmienne lokalne, czujki i wątki w systemie windows działają tak samo jak w [!INCLUDE[wfd2](../includes/wfd2-md.md)] debugowania. Ponadto wyświetlanie stosu wywołań podczas debugowania XAML jest liniowej hierarchiczny widok przepływ wykonania przepływu pracy.  
  
> [!NOTE]
>  XAML dla przepływu pracy znajduje się w tym samym zestawie jako działania, zestawu część nazwy klas nie są uwzględniane. Bez tej części nazwy klas (działanie) XAML nie można załadować w czasie wykonywania. Nie zaleca się zdefiniowanie działania w tej samej przestrzeni nazw jako głównej projektu; w przeciwnym razie XAML będzie trzeba ręcznie modyfikować po edycji w projektancie.  
  
### <a name="to-debug-workflow-xaml"></a>Aby debugować przepływ pracy XAML  
  
1.  Otwórz projekt przepływu pracy lub działania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Ustawianie punktu przerwania działania lub działania, który chcesz debugować, zgodnie z opisem w [porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md).  
  
3.  Kliknij prawym przyciskiem myszy plik .xaml, który zawiera definicję przepływu pracy i wybierz **Wyświetl kod**. Widoczne będą wyświetlane w tym samym wierszu co deklaracja elementu XAML działanie, które można ustawić punkt przerwania w w widoku Projekt punktu przerwania.  
  
4.  Wywoływanie debugera, zgodnie z opisem w [porady: wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Podczas wykonywania kodu osiągną jeden z punktów przerwania, zostanie wyróżniony element XAML skojarzone z tego punktu przerwania. Aby przejść do następnego punktu przerwania, należy użyć **F10** lub **F11** klucza.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Instrukcje: Wywoływanie debugera przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
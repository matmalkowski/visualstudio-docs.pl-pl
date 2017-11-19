---
title: "Porady: debugowanie XAML z projektanta przepływów pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: "8"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: c73e053cc3e3dc53101595f00dcd8fd45da8abd7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Porady: debugowanie XAML z projektanta przepływów pracy
Przepływy pracy są zdefiniowane w języku XAML. Reprezentacja interfejsu użytkownika przepływu pracy jest oparty na drzewie XAML definiujący przepływ pracy. Działanie debugowania jest podobny do debugowania przepływów pracy w [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]. Na przykład podczas debugowania XAML, zmiennych lokalnych, obejrzyj i wątków windows działają tak samo jak w [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] debugowania. Ponadto widoku stosu wywołań podczas debugowania XAML jest liniowej hierarchiczny widok przepływ wykonania przepływu pracy.  
  
> [!NOTE]
>  XAML przepływu pracy znajduje się w tym samym zestawie co działania, zestawu część nazwy klas nie są uwzględniane. Bez tej części nazwy klas (działanie) XAML nie można załadować w czasie wykonywania. Nie zaleca się definiowania działań w tej samej przestrzeni nazw jako głównego projektu; w przeciwnym razie XAML musi być edytowane ręcznie po edycji w projektancie.  
  
### <a name="to-debug-workflow-xaml"></a>Debugowanie XAML przepływu pracy  
  
1.  Otwórz projekt przepływu pracy lub działania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Ustaw punkt przerwania działania lub działania, które chcesz debugować zgodnie z opisem w [porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md).  
  
3.  Kliknij prawym przyciskiem myszy plik .xaml, który zawiera definicję przepływu pracy i wybierz **kod widoku**. Widoczny będzie wyświetlany na tym samym wierszu co deklaracja elementu XAML działania w widoku Projekt można ustawić punktu przerwania na punkt przerwania.  
  
4.  Wywoływanie debugger zgodnie z opisem w [porady: wywoływanie Debugger przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Podczas wykonywania kodu osiągnie jednego z punktów przerwania, zostanie wyróżniony element XAML skojarzone z tego punktu przerwania. Aby przejść do następnego punktu przerwania, należy użyć **F10** lub **F11** klucza.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Ustawianie punktów przerwania w przepływach pracy](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Porady: wywoływanie Debugger przepływu pracy](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
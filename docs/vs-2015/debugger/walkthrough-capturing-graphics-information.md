---
title: 'Wskazówki: Przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de553729d37bb82d1b30c6a142f7e65c983bb1c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42630846"
---
# <a name="walkthrough-capturing-graphics-information"></a>Wskazówki: przechwytywanie informacji graficznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wskazówki: Przechwytywanie informacji graficznych](https://docs.microsoft.com/visualstudio/debugger/graphics/walkthrough-capturing-graphics-information).  
  
W tym instruktażu przedstawiono sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostyki grafiki, aby ręcznie przechwytywać informacje graficzne z aplikacji Direct3D.  
  
 Ten instruktaż ilustruje następujące zadania:  
  
-   Przechwytywanie diagnostyki grafiki do aplikacji  
  
-   Przechwytywanie informacji graficznych  
  
## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Aby korzystać z narzędzi programu Graphics Diagnostics, najpierw musisz przechwytywanie informacji graficznych, która opiera się na. Aby włączyć funkcję przechwytywania, należy użyć **Rozpocznij diagnostykę** polecenie, aby podłączyć Graphics Diagnostics do aplikacji podczas jej uruchamiania.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Aby włączyć funkcję przechwytywania informacji graficznych po projekt lub rozwiązanie jest ładowany  
  
1.  W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], załaduj plik projektu lub rozwiązania, którą chcesz przechwytywać informacje graficzne z aplikacji.  
  
2.  Na pasku narzędzi diagnostyki grafiki, wybierz **Rozpocznij diagnostykę**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Aby włączyć przechwytywanie informacji graficznych bez ładowania projektu lub rozwiązania  
  
1.  Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**. **Otwórz projekt** pojawi się okno dialogowe.  
  
2.  Zamiast pliku projektu lub rozwiązania, należy określić plik wykonywalny aplikacji, który chcesz przechwycić informacje grafiki z, a następnie wybierz **Otwórz**.  
  
3.  Na pasku menu wybierz **debugowania**, **grafiki**, **Rozpocznij diagnostykę**.  
  
 Po uruchomieniu aplikacji i jest renderowanie ramki, możesz przechwytywać informacje graficzne.  
  
#### <a name="to-capture-graphics-information"></a>Do przechwytywania informacji graficznych  
  
-   Na pasku narzędzi diagnostyki grafiki, wybierz **przechwytywania** przycisku. ![Ikona przycisku przechwytywania grafiki](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     —lub—  
  
     Gdy aplikacja w trybie koncentracji uwagi, naciśnij klawisz **klawisza Print Screen**.  
  
 Każdorazowo przechwytywania informacji na temat ramkę, Graphics Diagnostics rejestruje zdarzenia Direct3D i powiązanym stanie i dodaje dane do dziennika grafiki. Nowy dziennik grafiki jest tworzona dla każdej sesji diagnostyki grafiki. Aby uzyskać informacji na temat dzienniki grafiki, zobacz [Przegląd](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Następne kroki  
 W tym instruktażu zademonstrowano, jak przechwytywać informacje graficzne ręcznie. Kolejnym krokiem Rozważ użycie tej opcji:  
  
-   Dowiedz się, jak analizować przechwycone informacje graficzne przy użyciu narzędzi programu Graphics Diagnostics. Zobacz [Przegląd](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przechwytywanie informacji graficznych](../debugger/capturing-graphics-information.md)




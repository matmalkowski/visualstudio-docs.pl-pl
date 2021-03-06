---
title: 'Wskazówki: Przechwytywanie informacji graficznych | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 48f12f6e-57b4-48ec-a145-89fa71a42424
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 037bdbbfb81c36e4f8e4d124801907ca0600aee7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476351"
---
# <a name="walkthrough-capturing-graphics-information"></a>Wskazówki: przechwytywanie informacji graficznych
W tym przewodniku przedstawiono sposób użycia [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagnostyki grafiki do ręcznie przechwytywanie informacji graficznych z aplikacji Direct3D.  
  
 W tym przewodniku przedstawiono te zadania:  
  
-   Przechwytywanie diagnostyki grafiki do aplikacji  
  
-   Przechwytywanie informacji graficznych  
  
## <a name="capturing-graphics-information"></a>Przechwytywanie informacji graficznych  
 Aby korzystać z narzędziami diagnostyki grafiki, należy najpierw przechwytywanie informacji graficznych, która opiera się na. Aby włączyć przechwytywania, należy użyć **Rozpocznij diagnostykę** polecenie, aby utworzenie punktu zaczepienia diagnostyki grafiki do aplikacji podczas jej uruchamiania.  
  
#### <a name="to-enable-the-capture-of-graphics-information-after-a-project-or-solution-is-loaded"></a>Aby włączyć przechwytywanie informacji graficznych po projekt lub rozwiązanie jest załadowany  
  
1.  W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], obciążenia aplikacji, który ma być przechwytywanie informacji graficznych z pliku projektu lub rozwiązania.  
  
2.  Na pasku narzędzi diagnostyki grafiki, wybierz **Rozpocznij diagnostykę**.  
  
#### <a name="to-enable-the-capture-of-graphics-information-without-loading-a-project-or-solution"></a>Aby włączyć przechwytywanie informacji graficznych bez ładowania projektu lub rozwiązania  
  
1.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**. **Otwórz projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Zamiast pliku projektu lub rozwiązania, określ plik wykonywalny dla aplikacji, który ma zostać przechwytywanie informacji graficznych z, a następnie wybierz pozycję **Otwórz**.  
  
3.  Na pasku menu wybierz **debugowania**, **grafiki**, **Rozpocznij diagnostykę**.  
  
 Po uruchomieniu aplikacji i jest renderowanie ramki, można przechwycić informacji graficznych.  
  
#### <a name="to-capture-graphics-information"></a>Aby przechwytywanie informacji graficznych  
  
-   Na pasku narzędzi diagnostyki grafiki, wybierz **przechwytywania** przycisku. ![Ikona przycisku przechwytywania grafiki](media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics")  
  
     —lub—  
  
     Za pomocą aplikacji fokus naciśnij **Print Screen**.  
  
 Zawsze przechwytywanie informacji na temat ramki, diagnostyki grafiki rejestruje zdarzenia Direct3D i skojarzony stan i dodaje dane do dziennika grafiki. Dla każdej sesji diagnostyki grafiki jest tworzony nowy dziennik grafiki. Aby uzyskać informacje o dziennikach grafiki, zobacz [omówienie](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku przedstawiono ręcznie przechwytywanie informacji graficznych. Jako kolejny krok Rozważ użycie tej opcji:  
  
-   Dowiedz się, jak do analizowania informacji przechwyconych grafiki przy użyciu narzędzia diagnostyki grafiki. Zobacz [omówienie](overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przechwytywanie informacji graficznych](capturing-graphics-information.md)
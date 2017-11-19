---
title: "Rozwiązywanie problemów metryki kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: "4"
author: erickson-doug
ms.author: douge
manager: douge
ms.openlocfilehash: 6dde34ce4808f21a90fa9d2e37daf7ed88d4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-code-metrics-issues"></a>Rozwiązywanie problemów związanych z metrykami kodów
Niektóre następujące problemy mogą występować w przypadku zbierać metryki kodu:  
  
-   [Zmiany w obliczeniach złożoności kodu programu Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Zmiany w obliczeniach złożoności kodu programu Visual Studio 2010  
 Dla tej samej funkcji Metryka złożoności kodu obliczana w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] może różnić się od Metryka obliczana na podstawie wcześniejszych wersji [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] w następujących sytuacjach:  
  
-   Funkcja zawiera jeden lub więcej bloki catch. W poprzednich wersjach [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], w obliczeniach nie uwzględniono bloki catch. W [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], złożoność każdy blok catch został dodany do złożoność funkcji.  
  
-   Funkcja zawiera instrukcji switch (Select Case w języku Visual Basic). Kompilator różnice między [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] i wcześniejszych wersjach może wygenerować inny kod MSIL dla niektórych zawierających fall-through przypadków instrukcji switch.  
  
## <a name="see-also"></a>Zobacz też  
 [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
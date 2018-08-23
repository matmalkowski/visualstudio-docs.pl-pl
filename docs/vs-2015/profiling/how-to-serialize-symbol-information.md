---
title: 'Instrukcje: serializacja informacji o symbolach | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04bce9383142ee6916fa7ade50feda072019f530
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42679285"
---
# <a name="how-to-serialize-symbol-information"></a>Porady: serializacja informacji o symbolach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [instrukcje: serializacja informacji o symbolach](https://docs.microsoft.com/visualstudio/profiling/how-to-serialize-symbol-information).  
  
Może wykonywać serializację symboli, które są niezbędne do analizowania aplikacji. Serializacja symbolu dodaje symboli do pliku Vsp. Przez dodawanie informacji o symbolach w pliku Vsp, inne analizowanie raportu dotyczącego wydajności bez uzyskiwania dostępu do oryginalnej symboli. Jeżeli symbole są nie seryjny, konieczne jest posiadanie oryginalnego instrumentowanych .exe i pliki .pdb do analizowania pliku Vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializuj informacje dotyczące symboli  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** zostanie wyświetlone okno dialogowe.  
  
2.  Kliknij przycisk **narzędzia do oceny wydajności**.  
  
3.  W obszarze **ustawienia ogólne**, wybierz opcję **automatycznie serializuj informacje dotyczące symboli**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Porady: odwoływać się do informacji o symbolach Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Porady: zapisywanie analizowane pliki raportu](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)




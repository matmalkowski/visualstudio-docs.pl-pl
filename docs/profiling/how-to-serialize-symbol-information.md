---
title: 'Porady: Serializuj informacje dotyczące symboli | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a86c7171b781f85ae4679209519267adcadcc090
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573313"
---
# <a name="how-to-serialize-symbol-information"></a>Porady: Serializuj informacje dotyczące symboli
Symbole, które muszą mieć do analizowania aplikacji może serializować. Symbol serializacji dodaje symbole. *vsp* pliku. Dodając informacje dotyczące symboli do. *vsp* pliku, inne analizowanie raportu dotyczącego wydajności bez uzyskiwania dostępu do oryginalnego symboli. Symbole nie są serializowane, musisz mieć oryginalne instrumentowany. *exe* i. *PDB* plików do przeanalizowania. *Vsp* pliku.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializuj informacje dotyczące symboli  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** zostanie wyświetlone okno dialogowe.  
  
2.  Kliknij przycisk **narzędzi wydajności**.  
  
3.  W obszarze **ogólne ustawienia**, wybierz pozycję **automatycznie serializuj informacje dotyczące symboli**.  
  
## <a name="see-also"></a>Zobacz także  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Porady: odwołanie do systemu Windows — informacje o symbolach](../profiling/how-to-reference-windows-symbol-information.md)   
 [Porady: zapisywanie przeanalizowane plików raportów](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)
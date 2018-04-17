---
title: 'Porady: Serializuj informacje dotyczące symboli | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: aca984dda2d83b09bfed969f4e5e21a6b6759867
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-serialize-symbol-information"></a>Porady: serializacja informacji o symbolach
Symbole, które muszą mieć do analizowania aplikacji może serializować. Symbol serializacji dodaje symboli do pliku Vsp. Dodanie informacji o symbolach w pliku Vsp, inne analizowanie raportu dotyczącego wydajności bez uzyskiwania dostępu do oryginalnego symboli. Symbole nie są serializowane, musisz oryginalnego instrumentowanych .exe i .pdb, pliki do analizowania pliku Vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Aby automatycznie serializuj informacje dotyczące symboli  
  
1.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** zostanie wyświetlone okno dialogowe.  
  
2.  Kliknij przycisk **narzędzi wydajności**.  
  
3.  W obszarze **ogólne ustawienia**, wybierz pozycję **automatycznie serializuj informacje dotyczące symboli**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Porady: odwołania informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Porady: zapisywanie przeanalizowane plików raportów](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)
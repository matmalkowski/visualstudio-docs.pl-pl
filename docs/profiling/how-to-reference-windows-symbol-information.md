---
title: 'Porady: odwołania informacji o symbolach w systemie Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 198677eb431852d5249684d23ff0dcad025e63af
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572407"
---
# <a name="how-to-reference-windows-symbol-information"></a>Porady: odwołania do informacji o symbolach w systemie Windows
Visual Studio Profiling Tools użyć symbolu (. *PDB*) pliki do rozpoznawania nazw symbolicznych, takich jak funkcja nazw plików binarnych programu. Można wykonaj następujące kroki, aby automatycznie pobrać i zainstalować aktualizację poprawny. *pdb* plików dla wersji systemu Windows na komputerze lokalnym.  
  
> [!NOTE]
>  To ustawienie nie ma wpływu na istniejące raporty. Tylko raporty utworzone po określaniu serwera symboli będzie miał informacji o symbolach.  
  
 Aby uzyskać więcej informacji, zobacz [Określ symbolu (. *PDB*) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera Microsoft symbol server  
  
1.  Utwórz folder zawierający informacje o pliku symboli, takie jak C:\SymbolCache.  
  
2.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** zostanie wyświetlone okno dialogowe.  
  
3.  Rozwiń węzeł **debugowanie** drzewa, a następnie kliknij przycisk **symbole**.  
  
4.  W **symboli (.pdb) lokalizacje**, wybierz pozycję **serwerów symboli firmy Microsoft**  
  
5.  W **pamięci podręcznej symboli z serwera symboli w tym katalogu**, wpisz ścieżkę do folderu, który został utworzony w kroku 1, na przykład:  
  
     **C:\SymbolCache**  
  
     Możesz również kliknąć przycisk wielokropka (**...** ), a następnie wybierz katalog z **przeglądanie w poszukiwaniu folderu** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz także  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)
---
title: 'Porady: odwoływać się do informacji o symbolach Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 385b9e4511c44c02a358eb88471cd8369971ed1c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42695602"
---
# <a name="how-to-reference-windows-symbol-information"></a>Porady: odwołania do informacji o symbolach w systemie Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: informacje o symbolach Windows odwołanie](https://docs.microsoft.com/visualstudio/profiling/how-to-reference-windows-symbol-information).  
  
Visual Studio Profiling Tools umożliwia rozpoznawanie nazw symbolicznych takich jak nazwy funkcji w plikach binarnych program plików symboli (.pdb). Można wykonaj następujące kroki, aby automatycznie Pobierz i zaktualizuj pliki .pdb poprawne dla wersji systemu Windows na komputerze lokalnym.  
  
> [!NOTE]
>  To ustawienie nie wpływa na istniejące raporty. Tylko raporty utworzone po określeniu serwera symboli będzie mieć informacji o symbolach.  
  
 Aby uzyskać więcej informacji, zobacz [Określ symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Aby użyć serwera symboli firmy Microsoft  
  
1.  Tworzenie folderu zawierającego plik informacje o symbolach, takich jak C:\SymbolCache.  
  
2.  Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
     **Opcje** pojawi się okno dialogowe.  
  
3.  Rozwiń **debugowanie** drzewa, a następnie kliknij przycisk **symbole**.  
  
4.  W **symboli (.pdb) lokalizacji**, wybierz opcję **serwery symboli firmy Microsoft**  
  
5.  W **Buforuj symbole z serwera symboli do tego katalogu**, wpisz ścieżkę do folderu, który został utworzony w kroku 1, na przykład:  
  
     **C:\SymbolCache**  
  
     Możesz również kliknąć przycisk wielokropka (**...** ) a następnie wybierz katalog, z **przeglądanie w poszukiwaniu folderu** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: serializacja informacji o symbolach](../profiling/how-to-serialize-symbol-information.md)




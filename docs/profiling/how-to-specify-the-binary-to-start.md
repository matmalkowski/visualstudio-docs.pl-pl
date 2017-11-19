---
title: "Porady: Określanie plików binarnych do uruchomienia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 363ab8f0967ec9a2f8dcdc4e9eb817586e513a8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-specify-the-binary-to-start"></a>Porady: określanie plików binarnych do uruchomienia
Aby profil plików binarnych takich jak biblioteki dll, należy wprowadzić informacje w  **\<docelowy > strony właściwości** okno dialogowe. Te informacje wskazuje, gdzie znaleźć aplikacja wywołująca projektu biblioteki DLL.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Określ plik wykonywalny do uruchomienia  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij przycisk **właściwości**.  
  
2.  W **strony właściwości** okno dialogowe, kliknij przycisk **uruchamianie** właściwości.  
  
3.  Wybierz **zastąpienie właściwości projektu** pole wyboru.  
  
4.  W **pliku wykonywalnego do uruchomienia** tekst Określ lokalizację pliku.  
  
5.  W **argumenty** tekst określ argumenty, które są wymagane do uruchomienia aplikacji.  
  
6.  W **katalog roboczy** tekst Określ lokalizację katalogu.  
  
7.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
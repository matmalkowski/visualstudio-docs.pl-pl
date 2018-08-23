---
title: 'Porady: Określanie plików binarnych do uruchomienia | Dokumentacja firmy Microsoft'
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
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec65dd3a5bcc812ff2f7c42ae4cbbba6080664db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678642"
---
# <a name="how-to-specify-the-binary-to-start"></a>Porady: określanie plików binarnych do uruchomienia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: Określanie plików binarnych do uruchomienia](https://docs.microsoft.com/visualstudio/profiling/how-to-specify-the-binary-to-start).  
  
Do profilu plików binarnych takich jak biblioteki dll, należy wprowadzić informacje w  **\<docelowy > strony właściwości** okno dialogowe. Te informacje wskazują, gdzie znaleźć aplikacji wywołującej projektu DLL.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Określ plik wykonywalny do uruchomienia  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy docelowy plik binarny, a następnie kliknij **właściwości**.  
  
2.  W **stron właściwości** okno dialogowe, kliknij przycisk **Uruchom** właściwości.  
  
3.  Wybierz **zastąpienie właściwości projektu** pole wyboru.  
  
4.  W **pliku wykonywalnego do uruchomienia** tekst pola, określ lokalizację pliku.  
  
5.  W **argumenty** tekstu należy określić argumenty, które są wymagane do uruchamiania aplikacji.  
  
6.  W **katalog roboczy** tekstu określ lokalizację katalogu.  
  
7.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)




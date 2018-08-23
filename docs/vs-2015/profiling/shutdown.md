---
title: Zamknięcie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7e351050859a96ca95c267bdcbe34ee19e7f87f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42683838"
---
# <a name="shutdown"></a>Zamykanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [zamknięcia](https://docs.microsoft.com/visualstudio/profiling/shutdown).  
  
**Zamknięcia** opcji oczekuje żadnego obecnie profilowane procesu, aby zakończyć lub odłączyć, a następnie wyłącza profilera i zamyka plik danych profilowania. **Zamknięcia** opcja musi być ostatnie polecenie uruchomienia profilowania.  
  
 Jeśli nie określono parametr limitu czasu, **zamknięcia** opcja będzie czekać w nieskończoność. Jeśli określono parametr limitu czasu, opcja zwraca po określonej liczbie sekund bez konieczności wyłączania program profilujący lub zamykania pliku danych.  
  
 **Zamknięcia** opcja musi być jedyną opcją, określone w wierszu polecenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### <a name="parameters"></a>Parametry  
 `Timeout`  
 -   (Opcjonalnie) Jeśli zostanie określony, opcja zwraca po określonej liczbie sekund bez konieczności wyłączania program profilujący lub zamykania pliku danych profilowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)




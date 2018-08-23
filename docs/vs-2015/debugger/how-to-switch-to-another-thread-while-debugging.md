---
title: 'Porady: przełączanie na inny wątek w trakcie debugowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c682ddff5fd4dc44fe79fa81c1615362f8121e5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681528"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Porady: przełączanie na inny wątek w trakcie debugowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [porady: przełączanie do innego wątku podczas debugowania](https://docs.microsoft.com/visualstudio/debugger/how-to-switch-to-another-thread-while-debugging).  
  
Podczas debugowania aplikacji wielowątkowych, można użyć jednego z kilku metod, aby przełączyć kontekst z wątku, która odbywała się wcześniej Praca z do innego wątku.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Aby przełączyć się do dowolnego wątku, który pojawia się w oknie wątków  
  
-   Kliknij dwukrotnie wątek.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Aby przełączyć się do wątku w oknie źródła  
  
-   Na lewym marginesie, kliknij prawym przyciskiem myszy wskaźnik wątku, wskaż opcję **przełączyć się do**, a następnie kliknij nazwę tego wątku, do którego chcesz się przełączyć. Menu skrótów pokazuje tylko wątków w tej konkretnej lokalizacji.  
  
     Jeśli pojawiają się wskaźniki nie, kliknij prawym przyciskiem myszy **wątków** okna i sprawdź, czy **Pokaż wątki w źródle** jest zaznaczone.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Aby przełączyć się do wątku w pasku narzędzi debugowania lokalizacji  
  
1.  Na **Lokalizacja debugowania** narzędzi, kliknij przycisk **wątku** pole.  
  
2.  Na liście kliknij wątku, do którego chcesz się przełączyć.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)




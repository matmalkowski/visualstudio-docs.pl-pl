---
title: 'VsgDbg:: ~ VsgDbg (destruktor) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed5e53aee9bed8ee070011de1a44001b910066a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42682797"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [VsgDbg:: ~ VsgDbg (destruktor)](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-tilde-vsgdbg-destructor).  
  
Niszczy wystąpienie `VsgDbg` klasy. Rejestrowana jest aktywnie informacji graficznych, plik dziennika grafiki jest aktualnie finalizowana i zamknąć, a zasoby, które były używane podczas aktywnie przechwytywanie informacji graficznych są zwalniane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VsgDbg::VsgDbg (Konstruktor)](../debugger/vsgdbg-vsgdbg-constructor.md)




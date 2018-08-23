---
title: Kończenie programu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6092e7f393eb973980cfca123264326aa0b2388b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694133"
---
# <a name="terminating-a-program"></a>Kończenie programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [Kończenie programu](https://docs.microsoft.com/visualstudio/extensibility/debugger/terminating-a-program).  
  
Poniżej znajduje się opis przed zakończeniem jednego programu z jednego wątku.  
  
## <a name="termination-process"></a>Zakończenie procesu  
  
1.  Wysyła DE [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) przy użyciu prawidłowego [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  Wysyła DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) przy użyciu prawidłowego [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 IDE przechodzi do trybu projektowania. Aparat debugowania lub wywołania w środowisku uruchomieniowym [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) usunięcie programu z portu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)


---
title: Serwery (zestaw SDK programu Visual Studio) | Dokumentacja firmy Microsoft
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
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e79e5e00bb4708359c19fd6a2ff95c7f31fd1179
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42694339"
---
# <a name="servers-visual-studio-sdk"></a>Serwery (zestaw SDK programu Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [serwerów (Visual Studio SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/servers-visual-studio-sdk).  
  
Pod względem architektury debugera **serwera**:  
  
-   Jest kontenerem portów i dostawcy portów i jest używany do komunikacji portów i dostawcy portów z Menedżer debugowania sesji (SDM) i aparaty debugowania.  
  
-   Można zidentyfikować się według nazwy i wyliczanie jego portów i dostawcy portów.  
  
-   Jest reprezentowany przez [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfejs, który jest implementowane tylko przez program Visual Studio (jedno wystąpienie serwera dla każdego wystąpienia uruchomienia programu Visual Studio).  
  
## <a name="see-also"></a>Zobacz też  
 [Porty](../../extensibility/debugger/ports.md)   
 [Dostawcy portów](../../extensibility/debugger/port-suppliers.md)   
 [Pojęcia dotyczące debugera](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)


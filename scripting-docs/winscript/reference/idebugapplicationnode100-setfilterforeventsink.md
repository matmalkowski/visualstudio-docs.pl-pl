---
title: IDebugApplicationNode100::SetFilterForEventSink | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6db8ea26787427844a92417bf525dba271063cba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Ustawia filtr w przypadku określonego [interfejs IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementacji. Umożliwia on debugera skryptu, aby odfiltrować generowane przez kompilator podrzędnych węzłów aplikacji, dzięki czemu PDM nie będzie wysyłać zdarzenia, gdy są one utworzone lub usunięte. Domyślnie wszystkie węzły będą wysyłane.  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) jest implementowany przez PDM 10.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCookie`  
 Plik cookie filtru.  
  
 `filter`  
 Filtr.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)
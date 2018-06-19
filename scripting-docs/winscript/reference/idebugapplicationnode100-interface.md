---
title: Interfejs IDebugApplicationNode100 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af79614d38ef55776b660329f51931be70b7f52e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793897"
---
# <a name="idebugapplicationnode100-interface"></a>Interfejs IDebugApplicationNode100
`IDebugApplicationNode100` Interfejsu rozszerza funkcjonalność [interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md). Wystąpienie tego interfejsu można uzyskać przez wywołanie metody QueryInterface wykonania [interfejs IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Ten interfejs jest implementowany przez PDM 10.0 i większa. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 `IDebugApplicationNode100` Interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Pobiera dokumentów tekstowych, które są ukryte przez określony filtr.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Określa, czy określony dokument należy do jednego z węzłów podrzędnych tego węzła.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Ustawia filtr w przypadku określonego [interfejs IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementacji. Umożliwia on debugera skryptu, aby odfiltrować generowane przez kompilator podrzędnych węzłów aplikacji tak, aby PDM nie będzie wysyłać zdarzenia, gdy węzły zostały utworzone lub usunięte. Domyślnie wszystkie węzły będą wysyłane.|
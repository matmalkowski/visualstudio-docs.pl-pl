---
title: Interfejs IDebugApplicationNode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 110e04d1c990f1b22f9740d8118a47f485dd041e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793954"
---
# <a name="idebugapplicationnode-interface"></a>Interfejs IDebugApplicationNode
`IDebugApplicationNode` Interfejsu rozszerza funkcjonalność `IDebugDocumentProvider` interfejsu, zapewniając kontekstu w drzewie projektu.  
  
 Oprócz dziedziczone z metody `IDebugDocumentProvider`, `IDebugApplicationNode` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|Wylicza węzłów podrzędnych węzła tej aplikacji.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|Zwraca węzeł nadrzędny tego węzła aplikacji.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|Ustawia dostawcę dokumentu dla tego węzła aplikacji.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|Powoduje, że tej aplikacji zwolnić wszystkie odwołania, a następnie wprowadź nieaktywny.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|Dodaje ten węzeł aplikacji do drzewa określonego projektu.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|Usuwa ten węzeł aplikacji z drzewa projektu.|
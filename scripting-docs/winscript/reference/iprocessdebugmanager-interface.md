---
title: Interfejs IProcessDebugManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IProcessDebugManager interface
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26c97fda6fc8657164e22d51eb041017a6239d98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanager-interface"></a>Interfejs IProcessDebugManager
Podstawowy interfejs do Menedżera debugowania procesu. Ten interfejs można utworzyć, dodać lub usunąć aplikację wirtualną z procesem. Można jej wyliczyć ramek stosu i wątki aplikacji.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IProcessDebugManager` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|Tworzy nowy obiekt aplikacji debugowania dla tej aplikacji.|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|Zwraca domyślny obiekt aplikacji dla bieżącego procesu.|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|Dodaje aplikację do listy Menedżera debugowania maszyny uruchomionych aplikacji.|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|Usuwa z uruchomionym aplikacji listy aplikacji.|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|Tworzy nowy Pomocnik dokumentu debugowania dla tej aplikacji.|
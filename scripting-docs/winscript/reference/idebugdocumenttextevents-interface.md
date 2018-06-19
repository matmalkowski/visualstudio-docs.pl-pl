---
title: Interfejs IDebugDocumentTextEvents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 078cd468b64d30c20f48a3392aa4509ed054fc3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794554"
---
# <a name="idebugdocumenttextevents-interface"></a>Interfejs IDebugDocumentTextEvents
Dostarcza zdarzenia wskazujące zmiany w dokumencie tekstu.  
  
> [!NOTE]
>  Tekst dokumentu zostanie zmieniona, gdy zdarzenia dla tego interfejsu fire. Programy obsługi zdarzeń może pobrać nowego przy użyciu tekstu `IDebugDocumentText` interfejsu.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugDocumentTextEvents` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Wskazuje, że dokument źródłowy został zniszczony i nie jest już prawidłowa|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Wskazuje, czy nowy tekst został dodany do dokumentu|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Wskazuje, czy tekst został usunięty z dokumentu.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Wskazuje, że tekst został zastąpiony.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Wskazuje, czy zmieniono atrybuty tekstu skojarzone z podstawowym zakres pozycji znaku.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Wskazuje, że atrybut dokumentu został zmieniony.|
---
title: IEEVisualizerService::GetValueDisplayStringCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 273dd5e99359f9f175dc6440088254b5219d8b52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Pobiera liczbę ciągi wartości dla określonej właściwości lub pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `displayKind`  
 [in] Wartość z [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) wyliczenia.  
  
 `propertyOrField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfejs, który reprezentuje właściwości lub pola.  
  
 `pcelt`  
 [out] Zwraca liczbę ciągi wartości do wyświetlenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
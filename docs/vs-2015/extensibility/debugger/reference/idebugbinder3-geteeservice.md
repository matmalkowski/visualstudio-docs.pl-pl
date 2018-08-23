---
title: IDebugBinder3::GetEEService | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 706fd4cee9757cf16820f05142ea7ae8529df09f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42696720"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugBinder3::GetEEService](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder3-geteeservice).  
  
Ta metoda zwraca żądanej usługi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vendor`  
 [in] `GUID` dostawcy (wartość null jest dopuszczalne).  
  
 `language`  
 [in] `GUID` języka (wartość null jest dopuszczalne).  
  
 `iid`  
 [in] `IID` usługi do uzyskania.  
  
 `ppService`  
 [out] Interfejs do żądanej usługi.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Przekaż `IID` dla [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interfejsu (`IID_IEEVisualizerServiceProvider`) aby zobaczyć, czy usługa Wizualizator typów jest dostępna. Jeśli tak, można uzyskać Ewaluator wyrażeń [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) wizualizatorów typu obsługiwany przez interfejs. Zobacz [Visualizing i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md) Aby uzyskać szczegółowe informacje.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Wizualizacja i wyświetlanie danych](../../../extensibility/debugger/visualizing-and-viewing-data.md)


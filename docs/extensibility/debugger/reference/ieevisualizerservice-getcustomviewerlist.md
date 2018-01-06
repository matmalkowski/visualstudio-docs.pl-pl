---
title: IEEVisualizerService::GetCustomViewerList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerService::GetCustomViewerList
helpviewer_keywords: IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2ee9ba43e9fcd7de0841d3bde1e3e8865e4503af
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Ta metoda zwraca listę wizualizatorach typu, które zna tej usługi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celtSkip`  
 [in] Liczba wizualizatorów można pominąć.  
  
 `celRequested`  
 [in] Liczba wizualizatorów można pobrać (również określa rozmiar `rgViewers` tablicy).  
  
 `rgViewers`  
 [w, out] Tablica [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktury tak, aby wypełnić.  
  
 `pceltFetched`  
 [out] Liczba wizualizatorów faktycznie pobrany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) przekazuje żądanie do tej metody w ramach wsparcia dla wizualizatorach typu. Jeśli ewaluatora wyrażenia dostarcza również niestandardowe przeglądarki, za pomocą tego samego typu, można dołączyć odpowiednio wypełniony [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktur dla tych przeglądarek niestandardowy do listy. Upewnij się, że [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) odzwierciedla te dodatkowe przeglądarki.  
  
 Zobacz [Podgląd niestandardowe i typ wizualizatora](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) szczegółowe informacje na temat różnic między wizualizatorów i przeglądarki.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
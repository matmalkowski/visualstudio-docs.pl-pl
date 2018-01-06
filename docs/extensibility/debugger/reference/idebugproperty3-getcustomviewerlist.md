---
title: IDebugProperty3::GetCustomViewerList | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::GetCustomViewerList
helpviewer_keywords: IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1cd719891b4c0baec4d143c4a848e0c1d31ad6e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Pobiera listę przeglądarek niestandardowe skojarzone z tą właściwością.  
  
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
 [in] Liczba osób przeglądających można pominąć.  
  
 `celtRequested`  
 [in] Liczba osób przeglądających można pobrać (również określa rozmiar `rgViewers` tablicy).  
  
 `rgViewers`  
 [w, out] Tablica [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) struktury tak, aby wypełnić.  
  
 `pceltFetched`  
 [out] Rzeczywista liczba osób przeglądających zwracane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby obsługiwać wizualizatorach typu, ta metoda przekazuje wywołanie [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) metody. Jeśli ewaluatora wyrażenia obsługuje również podglądy niestandardowe dla tego typu właściwości, ta metoda dołączyć odpowiednie podglądy niestandardowy do listy.  
  
 Zobacz [wizualizatora typu i podglądu niestandardowego](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) szczegółowe informacje na temat różnic między wizualizatorach typu i niestandardowych przeglądarki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę do **CProperty** obiekt ujawniający [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejsu.  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
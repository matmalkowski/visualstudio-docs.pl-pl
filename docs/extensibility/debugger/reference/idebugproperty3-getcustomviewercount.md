---
title: IDebugProperty3::GetCustomViewerCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::GetCustomViewerCount
helpviewer_keywords: IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 720049d864c2124d824a9ac4c5fb905ed4120c3e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
Pobiera liczbę niestandardowych przeglądarek, które mogą być dostępne dla tej właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 [out] Liczba osób przeglądających niestandardowych, które są dostępne dla tej właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Aby zapewnić obsługę wizualizatorach typu, ta metoda przekazuje wywołanie [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) metody. Jeśli ewaluatora wyrażenia obsługuje również podglądy niestandardowe dla tego typu właściwości, ta metoda dodaje do zwrócona wartość liczbę niestandardowych przeglądarki.  
  
 Aby uzyskać szczegółowe informacje na temat różnic między wizualizatorach typu i niestandardowych przeglądarki, zobacz [wizualizatora typu i podglądu niestandardowego](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę do **CProperty** obiekt ujawniający [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) interfejsu.  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Wizualizator typów i przeglądarka niestandardowa](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
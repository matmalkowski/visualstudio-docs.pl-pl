---
title: IDebugBreakpointResolution2::GetBreakpointType | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords: IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c7bd1b12fbad9f70555009eef6774d6f0dc7c028
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
Pobiera typ punktu przerwania reprezentowany przez to rozwiązanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```csharp  
int GetBreakpointType(   
   out enum_ BP_TYPE pBPType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBPType`  
 [out] Zwraca wartość z zakresu od [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) wyliczenia, która określa typ tego punktu przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca E_FAIL, jeśli `bpResLocation` pole w skojarzonej [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) struktura jest nieprawidłowa.  
  
## <a name="remarks"></a>Uwagi  
 Punkt przerwania może być na przykład kodu lub punktu przerwania danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę dla prostego `CDebugBreakpointResolution` obiekt ujawniający [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) interfejsu.  
  
```  
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.    
      if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpResolutionInfo.bpResLocation.bpType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
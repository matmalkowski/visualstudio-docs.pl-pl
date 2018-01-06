---
title: IDebugErrorBreakpointResolution2::GetBreakpointType | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugErrorBreakpointResolution2::GetBreakpointType
helpviewer_keywords: IDebugErrorBreakpointResolution2::GetBreakpointType
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c2ddc100514bf2489d13cb03302734b5dbb66266
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugerrorbreakpointresolution2getbreakpointtype"></a>IDebugErrorBreakpointResolution2::GetBreakpointType
Pobiera typ punktu przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```csharp  
int GetBreakpointType(   
   out enum_BP_TYPE pBPType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBPType`  
 [out] Zwraca wartość z zakresu od [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) wyliczenie opisujące typ punktu przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca typ punktu przerwania, które można powiązać, w związku z tym wymagające zdarzenie błędu punktu przerwania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę dla prostego `CDebugErrorBreakpointResolution` obiekt ujawniający [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) interfejsu.  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.    
      if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;    
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
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
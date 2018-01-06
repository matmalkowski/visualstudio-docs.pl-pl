---
title: IDebugDocumentContext2::GetName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2::GetName
helpviewer_keywords: IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a0350336f9ca13fe4302ada8100912799b326de4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Pobiera nazwę zawiera dokument, który zawiera ten kontekstu dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE gnType,  
   BSTR*        pbstrFileName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrFileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `gnType`  
 [in] Wartość z zakresu od [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) wyliczenie określający typ nazwy do zwrócenia.  
  
 `pbstrFileName`  
 [out] Zwraca nazwę pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda przekazuje zazwyczaj wywołanie [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) metody, chyba że kontekstu dokumentu są zapisywane do przechowywania nazwy dokumentu (jako przykład Pokaż).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób zaimplementować tę metodę dla prostego `CDebugContext` obiekt ujawniający [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu.  
  
```cpp  
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)    
{    
   HRESULT hr;    
  
   // Check for a valid file name argument.    
   if (pbstrFileName)    
   {    
      *pbstrFileName = NULL;    
  
      switch (gnType)    
      {    
         case GN_NAME:    
         case GN_FILENAME:    
         {    
            // Copy the member file name into the local file name.    
            *pbstrFileName = SysAllocString(m_sbstrFileName);    
            // Check for successful copy.    
            hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;    
            break;    
         }    
         default:    
         {    
            hr = E_FAIL;    
            break;    
         }    
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
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
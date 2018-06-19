---
title: IDebugProperty3::GetStringChars | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f7d5430326f57acf686b90f911445cc36dbf02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118248"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Pobiera parametry skojarzone z tą właściwością i zapisuje go w buforze dostarczone przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buflen`  
 [in] Maksymalna liczba znaków, które może przechowywać buforu dostarczone przez użytkownika.  
  
 `rgString`  
 [out] Zwraca ciąg.  
  
 [C++ tylko], `rgString` jest wskaźnikiem do buforu, który odbiera znaki Unicode w ciągu. Bufor musi wynosić co najmniej `buflen` znaki (nie w bajtach) rozmiar.  
  
 `pceltFetched`  
 [out] Gdzie jest zwracana liczba znaków, przechowywane w buforze. (Może być `NULL` w języku C++.)  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W języku C++, należy zadbać, aby mieć pewność, że bufor jest co najmniej `buflen` znaków Unicode. Należy pamiętać, że znaku Unicode 2 bajty.  
  
> [!NOTE]
>  W języku C++ zwracany ciąg nie zawiera znak końcowy null. Jeśli podany, `pceltFetched` określa liczbę znaków w ciągu.  
  
## <a name="example"></a>Przykład  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>Zobacz też  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
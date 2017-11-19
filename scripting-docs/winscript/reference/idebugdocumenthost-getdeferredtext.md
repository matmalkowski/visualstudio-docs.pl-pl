---
title: IDebugDocumentHost::GetDeferredText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ace3bdbfef143a3307d81455788a1e81788cb50b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
Zwraca zakres znaków, które zostały dodane przy użyciu `IDebugDocumentHelper::AddDeferredText` metody w oryginalnym dokumencie hosta.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwTextStartCookie`  
 [in] Zdefiniowane przez hosta pliku cookie, który reprezentuje pozycję początkową tekstu.  
  
 `pcharText`  
 [w, out] Znak buforu tekstu. Ta metoda nie zwraca znaków, jeśli ten parametr ma `NULL`.  
  
 `pstaTextAttr`  
 [w, out] Bufor atrybutu znaków. Ta metoda nie zwraca atrybuty, jeśli ten parametr ma `NULL`.  
  
 `pcNumChars`  
 [w, out] Wskazuje rzeczywistą liczbę znaków/atrybutów zwracanych. Ten parametr musi być ustawiony na zero, przed wywołaniem tej metody.  
  
 `cMaxChars`  
 [in] Maksymalna liczba znaków do zwrócenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Metoda nie jest zaimplementowana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może zwracać `E_NOTIMPL`, jeśli host nie wywołuje `IDebugDocumentHelper::AddDeferredText`.  
  
> [!NOTE]
>  Ta metoda zwraca tekst z oryginalnego dokumentu. Host nie zachować informacje o edycji lub inne zmiany w dokumencie.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [Wyliczenie SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)
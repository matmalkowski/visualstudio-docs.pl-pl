---
title: IDebugDocumentHelper::AddDeferredText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c92909874429075bebc6a1f0a252573d049584e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
Powiadamia pomocnika, że podany tekst jest dostępny, ale nie zawiera znaków.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cChars`  
 [in] Liczba znaków (Unicode) do dodania.  
  
 `dwTextStartCookie`  
 [in] Zdefiniowane przez hosta pliku cookie, który reprezentuje pozycję początkową tekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Metoda nie powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia hosta odroczenia, zapewniając znaków, które można dodać, dopóki nie są potrzebne, umożliwiając pomocnika do generowania dokładne powiadomienia oraz informacje o rozmiarze. `dwTextStartCookie` Parametr jest pliku cookie, zdefiniowany przez hosta, który reprezentuje pozycję początkową tekstu. Kolejne wywołania `IDebugDocumentText::GetText` podać ten plik cookie. Na przykład w przypadku hosta, który reprezentuje tekst w DBCS, plik cookie może być przesunięcia bajtów.  
  
 Zakłada ona, że wywołanie `IDebugDocumentText::GetText` można uzyskać znaki z wielu wywołań `AddDeferredText`. Klasy pomocy może również poprosić o tego samego zakresu znaków odroczonego więcej niż raz.  
  
> [!NOTE]
>  Wywołuje się `AddDeferredText` nie należy łączyć z wywołaniami `AddUnicodeText` lub `AddDBCSText`. W takim przypadku `E_FAIL` jest zwracany.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)
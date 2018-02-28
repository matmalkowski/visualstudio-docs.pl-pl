---
title: IDebugDocumentText::GetText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentText.GetText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetText
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a1006304974fab4959ad6313ffdc26793cdd345
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgettext"></a>IDebugDocumentText::GetText
Pobiera znaki i/lub znak atrybuty skojarzone z pozycji znaku zakresu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 [in] Uruchom lokalizacji pozycji znaku zakresu.  
  
 `pcharText`  
 [w, out] Znak buforu tekstu. Rozmiar buforu musi być wystarczająco duży, aby pomieścić `cMaxChars` znaków. Jeśli ten parametr ma wartość NULL, metoda zwraca znaków.  
  
 `pstaTextAttr`  
 [w, out] Bufor atrybutu znaków. Rozmiar buforu musi być wystarczająco duży, aby pomieścić `cMaxChars` znaków. Jeśli ten parametr ma wartość NULL, metoda zwraca atrybuty.  
  
 `pcNumChars`  
 [w, out] Liczba znaków/atrybutów zwracanych. Ten parametr musi być ustawiony na zero, przed wywołaniem tej metody.  
  
 `cMaxChars`  
 [in] Liczba znaków w zakresie pozycji znaku. Określa również maksymalną liczbę zwracanych znaków.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda pobiera znaki i/lub znak atrybuty skojarzone z pozycji znaku zakresu. Zakres pozycji znaku określono za pomocą pozycji znaku i liczbę znaków.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)   
 [Wyliczenie SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)
---
title: IActiveScriptAuthor::ParseScriptText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analizuje tekst skryptu, dodaje tekst do tworzenia aparatu skryptu i tworzy `IScriptEntry` obiekt, który odpowiada blok skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCode`  
 [in] Tekst skryptu, można przeanalizować.  
  
 `pszItemName`  
 [in] Adres buforu, który zawiera nazwę elementu skojarzone z bloku skryptu.  
  
 `pszDelimiter`  
 [in] Adres ogranicznik zakończenia elementu skryptu bloku. Gdy `pszCode` analizy strumienia tekstu host zazwyczaj używa ogranicznik (na przykład dwa pojedynczy cudzysłów), aby wykryć koniec bloku skryptu. Ustaw ten parametr na wartość NULL, jeśli nie istnieje żadne ogranicznik do identyfikowania koniec bloku skryptu.  
  
 `dwCookie`  
 [in] Zdefiniowane przez aplikację wartość skojarzoną z nowym `IScriptEntry` obiektu.  
  
 `dwFlags`  
 [in] Nie jest używany.  
  
## <a name="return-value"></a>Wartość zwracana  
 `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)
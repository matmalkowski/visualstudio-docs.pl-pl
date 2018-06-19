---
title: IDispError::GetHelpInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17098b4055bb61e9a2f639404edfe2214abc931e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794557"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
Zwraca ścieżkę pliku pomocy i identyfikator kontekstu tematu, który wyjaśni ten błąd, jeśli to możliwe.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrFileName`  
 [out] Ciąg zawierający w pełni kwalifikowana ścieżka do pliku pomocy. Jeśli plik pomocy nie istnieje lub występuje błąd, wartość zwracana jest NULL.  
  
 `pdwContext`  
 [out] Identyfikator kontekstu pomocy dla błędu. Jeśli plik pomocy nie istnieje (Jeśli `pbstrFileName` ma wartość NULL), ten parametr nie ma znaczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_FAIL`|Wystąpił błąd specyficznego dla dostawcy.|  
|`E_INVALIDARG`|`pbstrFileName`lub `pdwContext` została wartość NULL.|  
|`E_OUTOFMEMORY`|Dostawca nie może przydzielić wystarczającej ilości pamięci, do której należy zwrócić ścieżkę pliku pomocy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca ścieżkę pliku pomocy i identyfikator kontekstu tematu, który wyjaśni ten błąd, jeśli to możliwe.  
  
> [!NOTE]
>  Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispError](../../winscript/reference/idisperror-interface.md)
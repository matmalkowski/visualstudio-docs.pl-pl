---
title: IDispError::GetSource | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: IDispError::GetSource
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 922f95206d341773632b84c3922ea3b240d8d1ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idisperrorgetsource"></a>IDispError::GetSource
Zwraca identyfikator programowy zależne od języka dla klasy lub aplikacji, która wywołała błędu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrSource`  
 [out] Ciąg zawierający identyfikator programowy, w postaci `progname.objectname`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana do określenia klasy lub aplikacji, w którym wystąpił wyjątek. Identyfikator programowy mogą być zwracane w języku określonym przez identyfikator ustawień regionalnych (LCID) dostarczony w momencie wywołania.  
  
> [!NOTE]
>  Ta metoda nie jest zaimplementowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDispError](../../winscript/reference/idisperror-interface.md)
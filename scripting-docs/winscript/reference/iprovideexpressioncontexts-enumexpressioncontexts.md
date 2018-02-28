---
title: IProvideExpressionContexts::EnumExpressionContexts | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IProvideExpressionContexts.EnumExpressionContexts
apilocation:
- jscript.dll
helpviewer_keywords:
- IProvideExpressionContexts::EnumExpressionContexts
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c47619fface892e7e0d80141d7d4be53398a356e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iprovideexpressioncontextsenumexpressioncontexts"></a>IProvideExpressionContexts::EnumExpressionContexts
Zwraca moduł wyliczający kontekstów wyrażenie znane przez ten składnik.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppedec`  
 [out] Moduł wyliczający kontekstów wyrażenie znane przez ten składnik.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Menedżer debugowania procesu używa tej metody, aby znaleźć wszystkie konteksty wyrażenia globalnego skojarzone z danym wątku.  
  
> [!NOTE]
>  Ta metoda jest wywoływana z w wątku zainteresowań. Jest czynności, aby zidentyfikować bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)
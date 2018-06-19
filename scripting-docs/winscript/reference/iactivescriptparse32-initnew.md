---
title: IActiveScriptParse32::InitNew | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 31de8258ae13855741c6dd5ca9e4ff2c589e97bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793330"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
Inicjuje aparatu skryptów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` w przypadku powodzenia lub `E_FAIL` Jeśli wystąpił błąd podczas inicjowania.  
  
## <a name="remarks"></a>Uwagi  
 Przed użyciem aparatu skryptów, musi być jedną z następujących metod wywołana: `IPersist*::Load`, `IPersist*::InitNew`, lub `IActiveScriptParse32::InitNew`. Semantyka tej metody są takie same jak `IPersistStreamInit::InitNew`, że ta metoda określa, że aparat skryptów do zainicjowania. Należy pamiętać, że nie można wywołać jednocześnie `IPersist*::InitNew` lub `IActiveScriptParse32::InitNew` i `IPersist*::Load`, ani nie jest prawidłowy do wywołania `IPersist*::InitNew`, `IActiveScriptParse32::InitNew`, lub `IPersist*::Load` więcej niż raz.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)
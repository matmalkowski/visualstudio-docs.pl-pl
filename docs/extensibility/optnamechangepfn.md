---
title: OPTNAMECHANGEPFN | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3ecb80b1ac0b71de935da59d29a3f5c39f85bee
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Jest to określone w wywołaniu funkcji wywołania zwrotnego [SccSetOption](../extensibility/sccsetoption-function.md) (przy użyciu opcji `SCC_OPT_NAMECHANGEPFN`) i jest używany do komunikacji nazwa zmiany wprowadzone przez kontroli źródła wtyczek do środowiska IDE.  
  
## <a name="signature"></a>Podpis  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pvCallerData  
 [in] Wartość użytkownika określonego w poprzednie wywołanie [SccSetOption](../extensibility/sccsetoption-function.md) (przy użyciu opcji `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] Oryginalna nazwa pliku.  
  
 pszNewName  
 [in] Nazwa pliku została zmieniona na.  
  
## <a name="return-value"></a>Wartość zwracana  
 Brak.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik jest zmieniana podczas operacji kontroli źródła, wtyczkę kontroli źródła może powiadomić IDE o zmianie nazwy za pomocą tego wywołania zwrotnego.  
  
 Jeśli środowisko IDE nie obsługuje tego wywołania zwrotnego, nie zostanie wywołany [SccSetOption](../extensibility/sccsetoption-function.md) go określić. Jeśli wtyczka nie obsługuje tego wywołania zwrotnego, będzie zwracać `SCC_E_OPNOTSUPPORTED` z `SccSetOption` działania podczas IDE podejmuje próbę ustawienia wywołania zwrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje wywołania zwrotnego zaimplementowana IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
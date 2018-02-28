---
title: OPTNAMECHANGEPFN | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2d067d5dd150dd026a2bd29a8933e8d9f72222b0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
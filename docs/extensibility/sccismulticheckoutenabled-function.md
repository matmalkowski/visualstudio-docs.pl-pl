---
title: Funkcja SccIsMultiCheckoutEnabled | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af7102a049cd3db072506cbf492799908196df32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="sccismulticheckoutenabled-function"></a>Funkcja SccIsMultiCheckoutEnabled
Ta funkcja sprawdza, czy wtyczkę kontroli źródła umożliwia skonfigurowanie wielu wyewidencjonowania pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Struktura kontekstu wtyczkę kontroli źródła.  
  
 pbMultiCheckout  
 [out] Określa, czy wiele wyewidencjonowania są włączone dla tego projektu (obsługiwanych wiele wyewidencjonowania oznacza różną od zera).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Sprawdzenie powiodło się.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 IDE sprawia, że dwa sprawdza, czy pliki mogą zostać wyewidencjonowane jednocześnie przez więcej niż jednego użytkownika. Po pierwsze system kontroli źródła musi obsługiwać wiele wyewidencjonowania. Wtyczka do kontroli źródła można określić tej możliwości podczas inicjowania podając `SCC_CAP_MULTICHECKOUT`. Następnie drugiego wyboru IDE wywołuje tę funkcję, aby określić, czy bieżący projekt obsługuje wiele wyewidencjonowania. Jeśli wiele wyewidencjonowania są obsługiwane dla wybranego projektu, zwraca sukces wtyczki kodu i ustawia `pbMultiCheckout` do różną od zera (`TRUE`) lub `FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)
---
title: Funkcja SccIsMultiCheckoutEnabled | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b04cd593bd631ba92545901ff289a9f8ed4f1822
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
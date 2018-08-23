---
title: Funkcja SccIsMultiCheckoutEnabled | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11bd525d90f6c593c7a78de5734fa2b2e718c9db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42691662"
---
# <a name="sccismulticheckoutenabled-function"></a>SccIsMultiCheckoutEnabled, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja SccIsMultiCheckoutEnabled](https://docs.microsoft.com/visualstudio/extensibility/sccismulticheckoutenabled-function).  
  
Ta funkcja sprawdza, czy wtyczka do kontroli źródła zezwala na wiele operacji wyewidencjonowania w pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
SCCRTN SccIsMultiCheckoutEnabled(  
   LPVOID pContext,  
   LPBOOL pbMultiCheckout  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Struktura kontekście wtyczki kontroli źródła.  
  
 pbMultiCheckout  
 [out] Określa, czy wiele operacji wyewidencjonowania są włączone dla tego projektu (obsługujące wiele operacji wyewidencjonowania oznacza wartość różną od zera).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Sprawdzanie zakończyło się pomyślnie.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 IDE ułatwia dwóch kontroli, aby określić, jeśli pliki mogą zostać wyewidencjonowane jednocześnie przez więcej niż jednego użytkownika. Po pierwsze system kontroli źródła musi obsługiwać wiele operacji wyewidencjonowania. Wtyczka do kontroli źródła można określić tę możliwość podczas inicjowania, określając `SCC_CAP_MULTICHECKOUT`. Następnie drugiego wyboru IDE wywołuje tę funkcję, aby określić, czy bieżący projekt obsługuje wiele operacji wyewidencjonowania. Jeśli wiele operacji wyewidencjonowania są obsługiwane dla wybranego projektu, wtyczka zwraca Powodzenie kodu i ustawia `pbMultiCheckout` na wartość różną od zera (`TRUE`) lub `FALSE`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła ](../extensibility/source-control-plug-in-api-functions.md)


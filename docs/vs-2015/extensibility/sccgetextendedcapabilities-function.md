---
title: Funkcja SccGetExtendedCapabilities | Dokumentacja firmy Microsoft
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
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 016b44e8dcd8218b8c3fbd569ba6a27b77d9d204
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681351"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja SccGetExtendedCapabilities](https://docs.microsoft.com/visualstudio/extensibility/sccgetextendedcapabilities-function).  
  
Ta funkcja zwraca dodatkowe funkcje obsługiwane przez wtyczka do kontroli źródła.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 lSccExCaps  
 [in] Flaga określająca, rozszerzone możliwości, do których chcesz przetestować (znajdują się w tabeli rozszerzonego kodu możliwości [flagi możliwości](../extensibility/capability-flags.md) dla flag możliwe).  
  
 pbSupported  
 [out] Zwraca wartość różna od zera (`TRUE`), jeśli określona funkcja jest obsługiwana; w przeciwnym razie zwraca wartość zero (`FALSE`).  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Operacja możliwości pobrania została ukończona pomyślnie.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Wystąpił nieznany lub nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana na żądanie; oznacza to, gdy możliwości musi zostać przetestowana, ta metoda jest wywoływana w celu określenia, czy, funkcja jest obsługiwana. Określono tylko jedną flagę w danym momencie.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kody błędów](../extensibility/error-codes.md)   
 [Flagi możliwości](../extensibility/capability-flags.md)


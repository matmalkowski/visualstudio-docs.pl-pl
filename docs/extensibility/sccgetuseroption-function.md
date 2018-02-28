---
title: Funkcja SccGetUserOption | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5c23e1fd5614963d8f52edc019e99287187fd9a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sccgetuseroption-function"></a>Funkcja SccGetUserOption
Ta funkcja pobiera różne opcje specyficzne dla użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pContext  
 [in] Wskaźnik kontekstu wtyczkę kontroli źródła.  
  
 nOption  
 [in] Opcję, aby pobrać (zobacz uwagi możliwe opcje).  
  
 lpVal  
 [out] Wartość skojarzona z opcją.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczkę kontroli źródła tej funkcji może przywrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Opcja została pomyślnie pobrana.|  
|SCC_E_OPNOTSUPPORTED|Opcja nie jest obsługiwana.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższe opcje są obsługiwane przez to polecenie:  
  
|Opcja użytkownika|Opis|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Określa, czy użytkownik chce Wyewidencjonuj lokalną wersję plików. `lpVal`przypisano `SCC_USEROPT_COLV_YES` (użytkownik chce zapoznaj się z lokalnymi plikami) lub `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje API wtyczkę kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kody błędów](../extensibility/error-codes.md)
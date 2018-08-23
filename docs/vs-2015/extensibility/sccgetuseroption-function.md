---
title: Funkcja SccGetUserOption | Dokumentacja firmy Microsoft
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
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 567dbf987887d203a811a1dc965ecd4a472d5641
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681793"
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption, funkcja
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcja SccGetUserOption](https://docs.microsoft.com/visualstudio/extensibility/sccgetuseroption-function).  
  
Ta funkcja pobiera różnorodne opcje specyficzne dla użytkownika.  
  
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
 [in] Wskaźnik kontekście wtyczki kontroli źródła.  
  
 nOption  
 [in] Opcja do pobrania (zobacz uwagi dla możliwych opcji).  
  
 lpVal  
 [out] Wartość skojarzona z opcją.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Opcja został pomyślnie pobrany.|  
|SCC_E_OPNOTSUPPORTED|opcja nie jest obsługiwana.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 Poniższe opcje są obsługiwane przez to polecenie:  
  
|Opcja użytkownika|Opis|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Określa, czy użytkownik chce zapoznaj się z lokalną wersję plików. `lpVal` przypisano `SCC_USEROPT_COLV_YES` (użytkownik chce zapoznaj się z lokalnymi plikami) lub `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [Kody błędów](../extensibility/error-codes.md)


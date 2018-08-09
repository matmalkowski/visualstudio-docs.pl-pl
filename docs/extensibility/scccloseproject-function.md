---
title: Funkcja SccCloseProject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 49d3196fbe2eb6c3bafa1ec234e27072e50a4b7d
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636028"
---
# <a name="scccloseproject-function"></a>Funkcja SccCloseProject
Ta funkcja powoduje zamknięcie projektu oznaczenia końca określonej sesji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
SCCRTN SccCloseProject (  
   LPVOID pvContext  
);  
```  
  
### <a name="parameters"></a>Parametry  
 pvContext  
 Struktura kontekście wtyczki kontroli źródła.  
  
## <a name="return-value"></a>Wartość zwracana  
 Implementacja wtyczki kontroli źródła tej funkcji powinien zwrócić jedną z następujących wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|SCC_OK|Projekt został pomyślnie zamknięty.|  
|SCC_E_PROJNOTOPEN|Projekt nie jest obecnie otwarty.|  
|SCC_E_NOTAUTHORIZED|Użytkownik nie może wykonać tej operacji.|  
|SCC_E_NONSPECIFICERROR|Wystąpił nieokreślony błąd.|  
  
## <a name="remarks"></a>Uwagi  
 [SccOpenProject](../extensibility/sccopenproject-function.md) zawsze jest wywoływany przed tej funkcji. Wywołanie tej funkcji po niej wywołania `SccOpenProject` funkcji lub [SccUninitialize](../extensibility/sccuninitialize-function.md), która całkowicie zakończy połączenie do systemu kontroli źródła.  
  
## <a name="see-also"></a>Zobacz także  
 [Funkcje interfejsu API wtyczki kontroli źródła](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
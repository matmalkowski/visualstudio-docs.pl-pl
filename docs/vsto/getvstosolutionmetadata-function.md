---
title: "Getvstosolutionmetadata — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5caba6e6b42eefccfc9dc520758c7dfbc7346844
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata — funkcja
  Ten interfejs API obsługuje infrastrukturę programu Office i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|Nie używaj.|  
|*ppSolutionInfo*|Nie używaj.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwraca **S_OK**. W przypadku niepowodzenia funkcja zwraca kod błędu.  
  
  
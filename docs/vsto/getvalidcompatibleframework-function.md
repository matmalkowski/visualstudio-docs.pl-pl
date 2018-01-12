---
title: "Getvalidcompatibleframework — funkcja | Dokumentacja firmy Microsoft"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 43056033f6d23eb385609ebaf4d448ebdb2424a8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="getvalidcompatibleframework-function"></a>GetValidCompatibleFramework — funkcja
  Ten interfejs API obsługuje infrastrukturę programu Office i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Nie używaj.|  
|*pbstrValidFrameworkTag*|Nie używaj.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja zakończy się powodzeniem, zwraca **S_OK**. W przypadku niepowodzenia funkcja zwraca kod błędu.  
  
  
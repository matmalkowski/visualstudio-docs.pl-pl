---
title: Ograniczenia długości ciągu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56a76e84c27684d422b6554b22c75d945df4e928
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="restrictions-on-string-lengths"></a>Ograniczenia długości ciągu
Interfejs API dodatku typu Plug-in kontroli źródła ogranicza długości ciągów używanych w różnych funkcji.  
  
## <a name="string-length-values"></a>Wartości długości ciągu  
  
|Stała|Wartość|  
|--------------|-----------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  Długość nie obejmuje Kończenie `null`. Inne stałe z sufiksem "_SIZE" zamiast "_LEN" ma miejsca na zakończenie `null`.  
  
|Stała|Wartość|  
|--------------|-----------|  
|SCC_NAME_SIZE|32|  
|SCC_AUXLABEL_SIZE|32|  
|SCC_USER_SIZE|32|  
|SCC_PRJPATH_SIZE|301|  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)
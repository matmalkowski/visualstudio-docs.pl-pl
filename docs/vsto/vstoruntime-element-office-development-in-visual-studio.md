---
title: "&lt;vstoruntime —&gt; — Element (Office Development w Visual Studio) | Dokumentacja firmy Microsoft"
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
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0d6ac2393a5cfd27b2909fb5a5d63ff0260941e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoruntime —&gt; — Element (Office Development w Visual Studio)
  `vstoRuntime` Elementu `vstav3` przestrzeń nazw zawiera obsługiwanej wersji programu Visual Studio Tools for Office runtime dla konkretnego rozwiązania pakietu Office.  
  
## <a name="syntax"></a>Składnia  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## <a name="elements-and-attributes"></a>Elementy i atrybuty  
 `vstoRuntime` Element jest wymagany i znajduje się w `vstav3` przestrzeni nazw. Jeśli rozwiązania do pakietu Office obsługuje dwie wersje programu Visual Studio Tools dla pakietu Office runtime, występują dwa `vstoRuntime` elementów w manifeście aplikacji.  
  
 `vstoRuntime` Element ma następujące atrybuty.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`release`|Wymagany. Wydanej wersji programu Visual Studio Tools for Office runtime.|  
|`version`|Wymagany. Numer wersji Visual Studio Tools for Office runtime.|  
|`supportUrl`|Opcjonalny. Połącz z lokalizacji instalacji programu Visual Studio Tools for Office runtime.|  
  
 `vstoRuntime`nie ma żadnych elementów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje `vstoRuntime` elementu w manifeście aplikacji dla rozwiązań pakietu Office wdrożone za pomocą [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Ten przykładowy kod jest częścią większego przykładu udostępnionego w [manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Manifesty aplikacji dla rozwiązań pakietu Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesty wdrożenia dla rozwiązań pakietu Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifest aplikacji ClickOnce](/visualstudio/deployment/clickonce-application-manifest)  
  
  
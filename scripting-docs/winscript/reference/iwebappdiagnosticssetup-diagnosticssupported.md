---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5706d868f0096d486629c18c3d700349af92cc92
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Określa, czy diagnostyki są obsługiwane w tej aplikacji. Jeśli [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) została wywołana dla obiekt zawierający implementację tego interfejsu o wartości innej niż NULL [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca `true`. Jeśli nie, zwraca `false` i wywołań [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) zakończyć się niepowodzeniem.  
  
> [!IMPORTANT]
>  [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez PDM v11.0 i większa. Znaleziono w activdbg100.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 Jeśli [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) została wywołana dla obiekt zawierający implementację tego interfejsu o wartości innej niż NULL [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca `true`. Jeśli nie, zwraca `false`i wywołuje w celu [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) zakończyć się niepowodzeniem.
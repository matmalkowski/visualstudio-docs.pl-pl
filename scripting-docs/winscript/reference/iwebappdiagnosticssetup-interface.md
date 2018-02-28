---
title: Interfejs IWebAppDiagnosticsSetup | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interfejs IWebAppDiagnosticsSetup
Ten interfejs jest implementowany przez aplikację do debugowania PDM do tworzenia obiektów COM w procesie, który jest debugowany i włączyć diagnostyki sieci web. Jeśli PDM debugowania aplikacji implementuje obiektu [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), wymaga programu Internet Explorer [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) go po jej utworzeniu i przebiegów w odwołaniu do [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Aplikacja WWA wywołuje [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) i przebiegów w WWA interfejsu IWebApplicationHost zamiast tego. Jeśli [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) została wywołana z wartość inną niż NULL [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca wartość true. Jeśli nie, zwraca wartość false i wywołań [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) zakończyć się niepowodzeniem.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`jest implementowany przez PDM v11.0 lub nowszej. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Ten interfejs udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Pobiera dokumentów tekstowych, które są ukryte przez określony filtr.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Określa, czy określony dokument należy do jednego z węzłów podrzędnych tego węzła.|
---
title: Zmienne kompilacji warunkowej (JavaScript) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional compilation, variables
ms.assetid: d6f9827d-c558-412c-8e68-de04c19c3d9d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 900a44dab0ad418cd2899af6423f78016c90fe2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24788680"
---
# <a name="conditional-compilation-variables-javascript"></a>Zmienne kompilacji warunkowej (JavaScript)
Następujące wstępnie zdefiniowane zmienne są dostępne w kompilacji warunkowej. Jeśli zmienna nie jest **true**, nie jest zdefiniowany i zachowuje się jak `NaN` podczas uzyskiwania dostępu do.  
  
> [!WARNING]
>  Kompilacja warunkowa jest obsługiwana we wszystkich wersjach programu Internet Explorer wcześniejszych niż Internet Explorer 11. Uruchamianie w trybie standardów programu Internet Explorer 11 oraz w [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplikacje, kompilacja warunkowa nie jest obsługiwane.  
  
## <a name="variables"></a>Zmienne  
  
|Zmienna|Opis|  
|--------------|-----------------|  
|@_win32|Wartość true, jeżeli uruchomiono w systemie Win32.|  
|@_win16|Wartość true, jeżeli uruchomiono w systemie Win16.|  
|@_mac|Wartość true, jeżeli uruchomiono w systemie Apple Macintosh.|  
|@_alpha|Wartość true, jeżeli uruchomiono na procesorze DEC Alpha.|  
|@_x86|Wartość true, jeżeli uruchomiono na procesorze Intel.|  
|@_mc680x0|Wartość true, jeżeli uruchomiono na procesorze Motorola 680x0.|  
|@_PowerPC|Wartość true, jeżeli uruchomiono na procesorze PowerPC.|  
|@_jscript|Zawsze true.|  
|@_jscript_build|Zawiera numer kompilacji [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] aparatu skryptów.|  
|@_jscript_version|Zawiera [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] numer wersji w formacie major.minor.|
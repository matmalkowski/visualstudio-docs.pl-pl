---
title: "Iwefdebuggingsupport — interfejs | Dokumentacja firmy Microsoft"
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
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 150c8794fb35ca017be7e0873dc0d1b84ebfc38c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iwefdebuggingsupport-interface"></a>IWefDebuggingSupport — Interfejs
  Zaimplementowany w środowisku debugowania, takiego jak Visual Studio w celu ułatwienia debugowania aplikacji pakietu Office. Aplikacji pakietu Office, takich jak Word czy Excel, uzyskuje dostęp do tego interfejsu z programu Visual Studio, a następnie wywołuje metody interfejsu w niektórych punktach podczas sesji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli wymieniono iwefdebuggingsupport — interfejs definiuje metody.  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[GetAutoInsertExtensions, metoda](../vsto/getautoinsertextensions-method.md)|Pobiera informacje o aplikacjach pakietu Office, które mają być wstawiane automatycznie podczas debugowania.|  
|[SetWefProcessId, metoda](../vsto/setwefprocessid-method.md)|Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).|  
  
  
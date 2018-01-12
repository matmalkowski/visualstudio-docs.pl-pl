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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b132c51e12d553bcd6e722e87c8aeee96be5e5c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
  
  
---
title: Iwefdebuggingsupport — interfejs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 351fb69b99393a10518168f4f9b01efe1f9efaa7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572676"
---
# <a name="iwefdebuggingsupport-interface"></a>Iwefdebuggingsupport — interfejs
  Zaimplementowany w środowisku debugowania, takiego jak Visual Studio w celu ułatwienia debugowania aplikacji pakietu Office. Aplikacji pakietu Office, takich jak Word czy Excel, uzyskuje dostęp do tego interfejsu z programu Visual Studio, a następnie wywołuje metody interfejsu w niektórych punktach podczas sesji debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```csharp 
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
|[GetAutoInsertExtensions — metoda](../vsto/getautoinsertextensions-method.md)|Pobiera informacje o aplikacjach pakietu Office, które mają być wstawiane automatycznie podczas debugowania.|  
|[SetWefProcessId — metoda](../vsto/setwefprocessid-method.md)|Zawiera identyfikator procesu, który uruchomi zawartości w ramach rozszerzenia sieci Web (WEF).|  
  
  
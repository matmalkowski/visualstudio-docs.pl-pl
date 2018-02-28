---
title: Interfejs IDebugDocumentHost | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthost-interface"></a>Interfejs IDebugDocumentHost
Udostępnia funkcje specyficzne dla hosta, takich jak kolorowania do debugera. `IDebugDocumentHelper::SetDebugDocumentHost` Metoda przyjmuje ten interfejs jako argument.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugDocumentHost` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Zwraca zakres znaków, które zostały dodane przy użyciu `IDebugDocumentHelper::AddDeferredText`, w oryginalnym dokumencie hosta.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Zwraca atrybuty tekstu w bloku tekstu dokumentu.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Powiadamia hosta jest tworzony nowy kontekst dokumentu i umożliwia opcjonalnie zwracać obiekt, który określa nowy kontekst hosta.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Zwraca pełną ścieżkę (łącznie z nazwą pliku) w pliku źródłowego dokumentu.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Zwraca nazwę dokumentu, bez informacji o ścieżce.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Powiadamia hosta zapisania pliku źródłowego dokumentu i jego zawartość powinna być odświeżane.|
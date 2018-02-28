---
title: Interfejs IDebugDocumentHelper | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: baadcc1e2dba0b07e132298167b9b711e40cd912
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelper-interface"></a>Interfejs IDebugDocumentHelper
Podaj implementacji dla wielu interfejsy niezbędne do obsługi inteligentne, taki jak `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, i `IDebugDocumentTextEvents` interfejsów.  
  
 Oprócz dziedziczone z metody `IUnknown`, `IDebugDocumentHelper` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Inicjuje pomocnika dokumentu debugowania z nazwą i atrybuty początkowej.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Dodaje ten dokument w drzewie dokumentu.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Usuwa ten dokument w drzewie dokumentu.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Dołącza ciąg Unicode do końca tego dokumentu.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Dołącza do końca ciągu DBCS tego dokumentu.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Ustawia `IDebugDocumentHost` dla tego dokumentu.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Powiadamia pomocnika, że podany tekst jest dostępny, ale nie zawiera znaków.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Oznacza, że do pomocniczego, który określony zakres znaków jest obsługiwane przez aparat skryptów danego blok skryptu.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Ustawia domyślne atrybuty dla tekstu, który nie znajduje się w bloku skryptu.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Ustawia atrybut na zakres tekstu.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Ustawia długiej nazwy dokumentu.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Ustawia krótką nazwę dokumentu.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Ustawia atrybuty dla tego dokumentu.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Zwraca węzła aplikacji debugowania odpowiadającego do tego dokumentu.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Pobiera zakres znaków i aparat skryptu odpowiadający blok skryptu.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Tworzy nowy kontekst dokumentu debugowania.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Powoduje przeniesienie tego dokumentu do góry w debugerze interfejsu użytkownika.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Wprowadzono kontekście tego dokumentu do góry w interfejsie użytkownika debugera.|
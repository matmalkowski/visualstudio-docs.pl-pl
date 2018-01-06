---
title: MODULE_SYMBOL_SEARCH_INFO | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords: MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c4afe972f4f5218c04c1bd8a9223c7b317dc3ab3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
Zawiera informacje dotyczące ścieżki wyszukiwania symboli, które Przeszukano stanu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwValidFields`  
 Kombinacja flag z [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) wyliczenie opisujące rodzaj wyszukiwania informacje opisane w tej struktury.  
  
 `bstrVerboseSearchInfo`  
 Ścieżka wyszukiwania i wyników połączonych w jednym ciągu.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest zwracana z wywołania [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) metody.  
  
 Jeśli `bstrVerboseSearchInfo` pole nie jest puste, a następnie znajduje się lista ścieżek przeszukiwane i wyniki tego wyszukiwania. Lista jest sformatowany w systemie ścieżkę, a następnie wielokropkiem ("..."), a następnie wynik. Jeśli istnieje więcej niż jedna para wyników ścieżki, następnie każda para jest oddzielona parę "\r\n" (karetki return/wysuw wiersza). Wzorzec wygląda następująco:  
  
 \<Ścieżka >... \<wyniku > \r\n\<ścieżka >... \<wyniku > \r\n\<ścieżka >... \<wyniku >  
  
 Należy pamiętać, że ostatni wpis nie ma sekwencji \r\n.  
  
 W tym miejscu jest potencjalnie `bstrVerboseSearchInfo` ciąg, który został wysłany do wyjście standardowe.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
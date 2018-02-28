---
title: "Hierarchia leksykalna typów symboli | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d6f9fe7b24a1e2bdd68d92f6dd22952df0d2a057
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Hierarchia leksykalna typów symboli
W poniższej tabeli przedstawiono typy symbol w leksykalne hierarchii.  
  
## <a name="symbol-types"></a>Typów symboli  
  
|Typ symbolu|Opis|  
|-----------------|-----------------|  
|[Adnotacja](../../debugger/debug-interface-access/annotation.md)|Określa lokalizację adnotacjami w kodzie programu.|  
|[Blok](../../debugger/debug-interface-access/block.md)|Określa zakresy typów zagnieżdżonych funkcji.|  
|`Compiland`|Określa `compiland` połączone z pliku .exe.|  
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Określa dane compiland, które mogą wymagać ładowania compiland dodatkowych szczegółów i w związku z tym pociągnąć za sobą środowiska wykonawczego obciążenie, można pobrać.|  
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Określa wszelkie dodatkowe zmienne środowiskowe istotne dla kompilacji compiland.|  
|[Niestandardowe (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Określa symbol zdefiniowany przez użytkownika.|  
|[Dane (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Określa takie zmienne jako parametry, zmienne lokalne, zmienne globalne i elementów członkowskich klasy.|  
|[Exe](../../debugger/debug-interface-access/exe.md)|Określa globalny zakres danych. odnosi się do całego pliku .exe lub .dll.|  
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Określa funkcja, która ma zdefiniowanych punktów, w których debugowanie jest aby zakończyć.|  
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Określa funkcja, która ma zdefiniowanych punktów, w których debugowanie jest rozpoczęcie.|  
|[Funkcja (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Określa funkcję.|  
|[Etykieta (Zestaw SDK dostępu do interfejsu debugowania)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Określa lokalizację, w kodzie programu.|  
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Określa zewnętrzny symbol, który jest wyświetlany podczas kompilowania programu wykonywalnego.|  
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Określa `thunk`.|  
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Określa `namespace`identyfikator.|  
  
> [!NOTE]
>  Symbol dodatkowe właściwości mogą być dostępne w zależności od typu symbolu. Te właściwości są wyświetlane w tematach pojedynczy symbol.  
  
## <a name="see-also"></a>Zobacz też  
 [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md)
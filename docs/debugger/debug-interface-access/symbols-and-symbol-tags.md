---
title: Symbole i tagi symboli | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f4cb4b6ed35e880e1cb26980420f4e951ffc16
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="symbols-and-symbol-tags"></a>Symbole i tagi symboli
Informacje o debugowaniu o skompilowany program znajduje się w pliku bazy danych (.pdb) program jako symbole, które są dostępne za pośrednictwem interfejsów API zestawu SDK debugowania interfejsu dostępu (DIA). Wszystkie symbole [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) i [IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) właściwości. `symTag` Właściwość wskazuje typ symbolu, zgodnie z definicją w [symtagenum — wyliczenie](../../debugger/debug-interface-access/symtagenum.md) wyliczenia. `symIndexId` Właściwość jest `DWORD` wartość, która zawiera identyfikator unikatowy dla każdego wystąpienia symbolu.  
  
 Symbole zostały także właściwości, które można określić dodatkowe informacje dotyczące symboli, a także odwołania do symboli innych najczęściej [IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) lub [IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Kwerendy właściwość, która zawiera odwołanie, odwołanie, jest zwracana jako [idiasymbol —](../../debugger/debug-interface-access/idiasymbol.md) obiektu. Takie właściwości są zawsze łączyć się z innej właściwości o tej samej nazwie, ale suffixed z "Id", na przykład [IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) i [IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Tabele w [lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md), [leksykalne hierarchii typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), i [Symbol typu klasy hierarchii](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) konspektu właściwości dla każdego z różnych rodzajów z symbole. Te właściwości mogą mieć istotne informacje dotyczące lub odwołania do innych symboli. Ponieważ `*Id` właściwości są po prostu liczbowe identyfikatory porządkowej ich powiązane właściwości, pominięto dalsze dyskusji. Są one określone tylko wtedy, gdy jest to wymagane dla parametru wyjaśnienie.  
  
 Podczas próby dostępu do właściwości, jeśli nie występują błędy, a właściwość symbol zostanie przypisana wartość, właściwości "get" zwraca `S_OK`. Zwracana wartość `S_FALSE` wskazuje, że właściwość jest nieprawidłowa dla bieżącego symbolu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Lokalizacje symboli](../../debugger/debug-interface-access/symbol-locations.md)  
 W tym artykule opisano różne rodzaje lokalizacje, które mogą mieć symbolu.  
  
 [Hierarchia leksykalna typów symboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Zawiera opis typów symboli, które tworzą leksykalne hierarchii, takie jak pliki, moduły i funkcje.  
  
 [Hierarchia klas typów symboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Opisano typy symbol odpowiadające elementom innego języka, takich jak klasy, tablic i funkcja zwracanych typów.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw SDK dostępu do interfejsu debugowania](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
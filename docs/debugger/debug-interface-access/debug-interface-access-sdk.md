---
title: Debug Interface Access SDK | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cd84741d006304f7dfefe8ee4a1060ba64ffdb8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="debug-interface-access-sdk"></a>Zestaw SDK dostępu do interfejsu debugowania
Microsoft debugowania interfejsu dostępu Software Development Kit (DIA SDK) zapewnia dostęp do debugowania informacje przechowywane w plikach bazy danych (.pdb) program generowane przez postcompiler narzędzi firmy Microsoft. Ponieważ format pliku PDB wygenerowany za pomocą narzędzi postcompiler ulega poprawki stałej, udostępnianie format jest niepraktyczne. Przy użyciu interfejsu API DIA, można tworzyć aplikacje, które wyszukiwać i przeglądać informacje o debugowaniu przechowywane w pliku PDB. Takie aplikacje można na przykład raport informacje zwrotne śledzenia stosu i analizowanie danych dotyczących wydajności.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Zawiera omówienie DIA SDK, funkcje i określa, w którym zainstalowano wymaganego nagłówka i pliki biblioteki DIA SDK.  
  
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Instrukcje dotyczące sposobu używania interfejsu API DIA pliku .pdb kwerendy.  
  
 [Symbole i tagi symboli](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 W tym artykule omówiono, jak symbole i tagi symboli są używane w interfejsie API DIA.  
  
 [Dokumentacja](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Zawiera interfejsy, metody, wyliczenia i struktury DIA interfejsu API.  
  
 [Dia2dump — przykład](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Przedstawiono sposób za pomocą interfejsu API DIA wyszukiwać i przeglądać informacje o debugowaniu.  
  
 [Plik źródłowy Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Używany przez kod źródłowy [dia2dump — przykład](../../debugger/debug-interface-access/dia2dump-sample.md) aby zademonstrować DIA interfejsu API.
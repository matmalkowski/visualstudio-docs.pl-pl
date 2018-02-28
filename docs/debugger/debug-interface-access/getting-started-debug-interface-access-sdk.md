---
title: Wprowadzenie (Debug Interface Access SDK) | Dokumentacja firmy Microsoft
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
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d37843917be3a2668e9a2887f046eaee00600dc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-debug-interface-access-sdk"></a>Wprowadzenie (Zestaw SDK dostępu do interfejsu debugowania)
Debugowanie interfejsu dostępu (DIA) zestawu SDK udostępnia z dokumentacją instruktażowy i przykładowe, która ilustruje sposób korzystania z interfejsu API DIA. Umożliwia interfejsy i metody w DIA SDK niestandardowe aplikacje otwierania plików PDB i .dbg i wyszukiwania ich zawartość symbole, wartości atrybutów, adresy i inne informacje debugowania. Zestaw SDK udostępnia tabele odwołań dla właściwości skojarzone z symbole znajdujące się w aplikacji w języku C++.  
  
 Aby najlepiej użyć DIA SDK, należy zapoznać się z następujących czynności:  
  
-   Język programowania w języku C++  
  
-   Programowanie COM  
  
-   Visual Studio zintegrowane środowisko deweloperskie (IDE) do kompilowania próbki  
  
 DIA SDK zazwyczaj jest zainstalowany program Visual Studio i jego domyślna lokalizacja to *[dysk]*\Program Files\Microsoft 9.0\DIA programu Visual Studio SDK. W ramach instalacji, msdia90.dll, który implementuje DIA SDK, jest automatycznie rejestrowane, wszystkie punkty, które należy wykonać w celu używania go ma zawierać `dia2.h` w programie i łącze do `diaguids.lib`.  
  
 Nagłówek: include\dia2.h  
  
 Biblioteki: lib\diaguids.lib  
  
 Biblioteki DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Przegląda podstawowej architektury pakietu DIA.  
  
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Instrukcje krok po kroku dotyczące sposobu używania interfejsu API DIA pliku .pdb kwerendy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw SDK dostępu do interfejsu debugowania](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
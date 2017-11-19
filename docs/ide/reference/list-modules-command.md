---
title: "Lista modułów — polecenie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 081f57f441da17578735317e2d6f8352cd31d30d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="list-modules-command"></a>Lista modułów — Polecenie
Wyświetla listę modułów dla bieżącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Parametry  
 / Adres:`yes|no`  
 Opcjonalny. Określa, czy wyświetlać adresy pamięci w modułach. Wartość domyślna to `yes`.  
  
 / Name:`yes|no`  
 Opcjonalny. Określa, czy są wyświetlane nazwy modułów. Wartość domyślna to `yes`.  
  
 / Order:`yes|no`  
 Opcjonalny. Określa, czy z kolejnością modułów. Wartość domyślna to `no`.  
  
 / Path:`yes|no`  
 Opcjonalny. Określa, czy ścieżki modułów. Wartość domyślna to `yes`.  
  
 / Proces:`yes|no`  
 Opcjonalny. Określa, czy Pokaż procesy modułów. Wartość domyślna to `no`.  
  
 / SymbolFile:`yes|no`  
 Opcjonalny. Określa, czy wyświetlać pliki symboli modułów. Wartość domyślna to `no`.  
  
 / SymbolStatus:`yes|no`  
 Opcjonalny. Określa, czy mają być wyświetlane stany symboli modułów. Wartość domyślna to `yes`.  
  
 / Sygnatura czasowa:`yes|no`  
 Opcjonalny. Określa, czy pokazywać sygnatury czasowe modułów. Wartość domyślna to `no`.  
  
 / Version:`yes|no`  
 Opcjonalny. Określa, czy Pokaż wersje modułów. Wartość domyślna to `no`.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono nazwy modułu, adresy i sygnatury czasowe dla bieżącego procesu.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Porady: Korzystanie z okna modułów](../../debugger/how-to-use-the-modules-window.md)
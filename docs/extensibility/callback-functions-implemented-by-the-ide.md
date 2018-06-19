---
title: Funkcje wywołania zwrotnego zaimplementowana IDE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdcc7d92770f486f9a345acf14e12e14214a2b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109691"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Funkcje wywołania zwrotnego zaimplementowana IDE
Aby Integracja z zintegrowane środowisko programistyczne (IDE) jako bezproblemowe, jak to możliwe oraz zapewnienie ujednoliconego końcowego wtyczkę kontroli źródła można użyć funkcji wywołania zwrotnego, które są implementowane przez IDE. Wtyczka może wywoływać te funkcje w odpowiednich momentach operacji kontroli źródła do przekazywania informacji do środowiska IDE; IDE można następnie wyświetlić te informacje jako elementy osadzone w jego natywnego interfejsu użytkownika. Użytkownik ma mniej pofragmentowane środowisko, w tym scenariuszu niż Jeśli wtyczka zatrudnionych własnego interfejsu użytkownika.  
  
 Plik nagłówka wymagane jest scc.h. Domyślna lokalizacja to \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Jest również folder VSIP, który zawiera przykładowy wtyczkę kontroli źródła na \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Zawiera opis funkcji wywołania zwrotnego, która jest używana przez [SccOpenProject](../extensibility/sccopenproject-function.md) wyświetlać komunikaty z kontroli źródła wtyczek za pomocą środowiska IDE.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Zawiera opis funkcji wywołania zwrotnego, która jest używana przez [SccPopulateList](../extensibility/sccpopulatelist-function.md) gdy IDE nie ma pełny dostęp do informacji, która jest dostępna tylko dla wtyczka do kontroli źródła, takie jak Pełna lista plików w ramach kontroli wersji.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Zawiera opis funkcji wywołania zwrotnego, która jest używana przez [SccQueryChanges](../extensibility/sccquerychanges-function.md) operacji.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Zawiera opis funkcji wywołania zwrotnego, która jest używana przez [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) operacji.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 W tym artykule opisano funkcję wywołania zwrotnego ustawiony przez wywołanie do [SccSetOption](../extensibility/sccsetoption-function.md) , który umożliwia wtyczka do kontroli źródła do komunikowania się nazwa zmian z powrotem do środowiska IDE.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Zostanie otwarty projekt.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Sprawdza, czy lista plików dla ich bieżącego stanu. Ponadto używa `pfnPopulate` funkcji, aby powiadomić wywołującego, jeśli plik nie pasuje do kryteriów dla `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Sprawdza, czy lista katalogów i plików w projekcie, lub projektów, które są pod kontrolą źródła. Znaleziono nazwy katalogów i plików jest przekazany do funkcji wywołania zwrotnego.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Sprawdza, czy zmiany nazwy, które zostały wprowadzone do listy plików. Każda nazwa pliku jest przekazany do funkcji wywołania zwrotnego razem ze statusem zmiany.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Ustawia szeroką gamę opcji. Każda opcja rozpoczyna się od `SCC_OPT_xxx` i ma własną zdefiniowanego zestawu wartości.  
  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)  
 Opisuje zawartość sekcji odwołanie do zestawu SDK dodatku typu Plug-in kontroli źródła.
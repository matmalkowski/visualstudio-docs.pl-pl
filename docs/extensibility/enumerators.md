---
title: "Moduły wyliczające | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7929ead4ced01561adb8c11dcaa56bc97f57884b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="enumerators"></a>Modułów wyliczających
Ta sekcja zawiera modułu wyliczającego typów danych w interfejsie API dodatku typu Plug-in kontroli źródła znajomość wtyczkę kontroli źródła.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Polecenie kodu](../extensibility/command-code-enumerator.md)  
 Wylicza opcje [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) i [SccPopulateList](../extensibility/sccpopulatelist-function.md) funkcji.  
  
 [Komunikat](../extensibility/message-enumerator.md)  
 Wylicza flagi używane do wydruku wywołania zwrotnego, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Kod stanu pliku](../extensibility/file-status-code-enumerator.md)  
 Zawiera nazwanych wartości stałej, określające stan pliku pod kontrolą źródła.  
  
 [Kod stanu katalogu](../extensibility/directory-status-code-enumerator.md)  
 Zawiera nazwanych wartości stałej, określające stan katalogu pod kontrolą źródła.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie wtyczki kontroli kodu źródłowego](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiuje zestaw SDK dodatku typu Plug-in kontroli źródła i opisano dołączone zasoby.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Monituje użytkownika o zaawansowane opcje dla danego polecenia.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Sprawdza, czy lista plików dla ich bieżącego stanu. Ponadto używa `pfnPopulate` funkcji, aby powiadomić wywołującego, jeśli plik nie pasuje do kryteriów dla `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Zawiera opis funkcji wywołania zwrotnego, która jest używana przez [SccOpenProject](../extensibility/sccopenproject-function.md) wyświetlać komunikaty z kontroli źródła wtyczek za pomocą środowiska IDE.  
  
 [Wtyczki kontroli źródła](../extensibility/source-control-plug-ins.md)  
 Zawiera pełną listę wszystkich elementów w interfejsie API dodatku typu Plug-in kontroli źródła.
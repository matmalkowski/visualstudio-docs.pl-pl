---
title: 'Obszar testu 4: Zaewidencjonuj | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7f3e8a343823016f391735aae59e58dfefe1a5f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133154"
---
# <a name="test-area-4-check-in"></a>Obszar testu 4: Zaewidencjonuj
Ten obszar testu wtyczkę kontroli źródła obejmuje wysyłanie zaktualizowane elementy do magazynu wersji za pomocą **Zaewidencjonuj** polecenia.  
  
## <a name="command-menu-access"></a>Dostęp do poleceń Menu  
 Następujące [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programowanie zintegrowanego środowiska menu ścieżki są używane w przypadku testowego.  
  
##### <a name="check-in"></a>Zamelduj się:  
 **Plik**, **kontroli źródła**, **zaewidencjonować**.  
  
 **Plik**, **zaewidencjonować**.  
  
 Menu skrótów **Zaewidencjonuj**.  
  
## <a name="common-expected-behavior"></a>Typowe oczekiwane zachowanie  
  
-   Projekty i pliki dodane do rozwiązania lub projektu pod kontrolą źródła są wyświetlane w **Zaewidencjonuj** okno dialogowe i **oczekujących zaewidencjonowań** okna.  
  
-   Po zaewidencjonowaniu dodawanych elementów są wyświetlane w kontroli źródła.  
  
-   Po zaewidencjonowaniu zaktualizowane elementy są poprawnie określonej wersji w magazynie.  
  
## <a name="test-cases"></a>Przypadki testowe  
 Poniżej przedstawiono określonych przypadków testowych dla obszaru testów zaewidencjonowania.  
  
### <a name="case-4a-modified-items"></a>Przypadek 4a: zmodyfikowane elementy  
 Zawiera opis funkcji w akcji można zaktualizować pliku pod kontrolą źródła, które zostały zmodyfikowane.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Modyfikowanie pliku tekstowego, który został wyewidencjonowany, sprawdź w pliku tylko (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz nowy projekt z pliku tekstowego.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Wyewidencjonuj i modyfikowania pliku tekstowego.<br />4.  Sprawdź w za pomocą okna dialogowego zaewidencjonowania (**pliku**, **kontroli źródła**, **Zaewidencjonuj**).|Typowe oczekiwane zachowanie.|  
|Modyfikowanie pliku tekstowego, który został wyewidencjonowany, sprawdź w pliku tylko (**oczekujących zaewidencjonowań** okna)|1.  Utwórz nowy projekt z pliku tekstowego.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Wyewidencjonuj i modyfikowania pliku tekstowego.<br />4.  Sprawdź w za pomocą **oczekujących zaewidencjonowań** okna.|Typowe oczekiwane zachowanie.|  
  
### <a name="case-4b-adding-files"></a>Przypadek 4b: Dodawanie plików  
 Podczas dodawania pliku projektu lub elementu do rozwiązania, projektu lub rozwiązania należy również zmienić. W związku z tym pliku nadrzędnego również jest wyewidencjonowany i musi być zaewidencjonowany przeprowadzenie operacji dodawania.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dodaj plik tekstowy i zaewidencjonuj wszystko (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik tekstowy do projektu.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie projektu.<br />5.  Wybierz rozwiązanie w **Eksploratora rozwiązań**.<br />6.  Sprawdź w z **Zaewidencjonuj** okno dialogowe.|Typowe oczekiwane zachowanie.|  
|Dodaj plik tekstowy i zaewidencjonuj wszystko (**oczekujących zaewidencjonowań** okna)|1.  Utwórz nowy projekt.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj plik tekstowy do projektu.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie projektu.<br />5.  Sprawdź w rozwiązaniu z **oczekujących zaewidencjonowań** okna.|Typowe oczekiwane zachowanie|  
  
### <a name="case-4c-adding-projects"></a>Przypadek 4c: dodawanie projektów  
 Po dodaniu projektu do rozwiązania, należy także zmienić rozwiązania. W związku z tym plik rozwiązania również jest wyewidencjonowany i musi być zaewidencjonowany przeprowadzenie operacji dodawania.  
  
|Akcja|Kroki testu|Oczekiwanych rezultatów, aby sprawdzić|  
|------------|----------------|--------------------------------|  
|Dodaj projekt do rozwiązania puste pod kontrolą źródła (**Zaewidencjonuj** okno dialogowe)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie rozwiązania.<br />5.  Sprawdź w z **Zaewidencjonuj** okno dialogowe.|Typowe oczekiwane zachowanie.|  
|Dodaj projekt do rozwiązania puste pod kontrolą źródła (**oczekujących zaewidencjonowań** okna)|1.  Utwórz puste rozwiązanie.<br />2.  Dodaj rozwiązanie do kontroli źródła.<br />3.  Dodaj nowy projekt.<br />4.  Jeśli zostanie wyświetlony monit, należy zaakceptować wyewidencjonowanie rozwiązania.<br />5.  Sprawdź w rozwiązaniu z **oczekujących zaewidencjonowań** okna.|Typowe oczekiwane zachowanie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik testowania wtyczek kontroli kodu źródłowego](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
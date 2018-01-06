---
title: "Ustawienia stron właściwości dla projektów sieci Web | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4e58541c5ab0c7a38773740343349880aa5297e0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="property-pages-settings-for-web-projects"></a>Ustawienia stron właściwości dla projektów sieci Web
Możesz zmienić ustawienia właściwości dla konfiguracji debugowania witryny sieci web w **strony właściwości** okno dialogowe, zgodnie z opisem w [konfiguracji Debug i Release](../debugger/how-to-set-debug-and-release-configurations.md). W poniższych tabelach przedstawiono gdzie można znaleźć ustawień debugera w **strony właściwości** okno dialogowe.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Folder właściwości konfiguracji (opcje uruchamiania kategorii)  
  
|**Ustawienie**|**Opis**|  
|-----------------|---------------------|  
|**Uruchomienie akcji**|Pozycja, że opcje grupy dotyczące uruchamiania aplikacji.|  
|**Użyj bieżącej strony.**|Określa bieżącą stronę jako punktu wyjścia do debugowania.|  
|**Określona strona:**|Określa strony sieci Web, w której chcesz rozpocząć debugowanie.|  
|**Uruchom program zewnętrznych:**|Określa polecenia dla uruchamiania programu, które chcesz debugować.|  
|**Argumenty wiersza polecenia:**|Określa argumenty dla polecenia wymienione powyżej.|  
|**Katalog roboczy:**|Określa katalog roboczy debugowany program. W [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], katalog roboczy jest katalogiem, aplikacja jest uruchamiana z \bin\debug domyślnie.|  
|**Początkowy adres URL**|Określa lokalizację, w aplikacji sieci Web, którą chcesz debugować.|  
|**Nie otwieraj strony. Czekaj na żądanie od aplikacji zewnętrznej**|Wskazuje, że wskazuje oczekiwania na żądanie od aplikacji zewnętrznej. Ta opcja nie zostanie uruchomiony program Internet Explorer lub innej aplikacji. Po prostu przygotowuje do debugowania wywołanego przez aplikację.|  
|**Serwer**|Pozycja, że opcje grupy związany z serwera, który będzie używany.|  
|**Użyj domyślnego serwera sieci Web**|Mówi użyć domyślnego serwera sieci Web.|  
|**Użyj niestandardowego serwera**|Umożliwia wprowadzenie do użycia jako serwer podstawowy adres URL.|  
|**Debugery**|Pozycja opcje grupy dotyczące typu debugowania do wykonania.|  
|**Debugowanie ASP.NET**|Włącza debugowanie napisane dla stron serwera [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] platformy programistycznej. Należy określić adres URL w **początkowy adres URL**.|  
|**Debugowanie kodu natywnego**|Umożliwia debugowanie wywołania do kodu natywnego Win32 (niezarządzany) z zarządzanych aplikacji.|  
|**Debugowanie SQL Server**|Pozwala na debugowanie obiektów bazy danych programu SQL Server.|  
|**Silverlight — debugowanie**|Pozwala na debugowanie Silverlight składników.|  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugowania i przygotowanie](../debugger/debugger-settings-and-preparation.md)
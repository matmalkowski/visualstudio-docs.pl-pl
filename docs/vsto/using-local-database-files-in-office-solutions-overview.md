---
title: Użyj plików lokalnej bazy danych w rozwiązań Office ― omówienie
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 01e9dc3df93e1f721eba9ce3bcf65d4fb8bb1ca1
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767585"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Użyj plików lokalnej bazy danych w rozwiązań Office ― omówienie
  Można dołączyć plik bazy danych, takich jak SQL Server Express (*.mdf*) pliku lub Microsoft Office Access (*.mdb*) pliku rozwiązania do pakietu Office. Pozwala to użytkownikom końcowym obsługę lokalnej bazy danych w sytuacji, gdy obsługa scentralizowanej bazie danych nie jest wymagane, na przykład w przypadku rozwiązania lokalnego magazynu używanego na pojedynczym komputerze.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="import-the-database-file-into-a-project"></a>Zaimportuj plik bazy danych do projektu  
 Aby zaimportować plik bazy danych do projektu, należy użyć **Kreator konfiguracji źródła danych** tworzenia źródła danych na podstawie pliku bazy danych. Kreator dodaje plik bazy danych i typizowanego zestaw danych do projektu.  
  
## <a name="deploy-the-database-file"></a>Wdróż plik bazy danych  
 **Kreator konfiguracji źródła danych** korzysta ze ścieżki względnej do utworzenia połączenia z lokalnego pliku bazy danych. Dzięki temu można kopiować rozwiązania z jednego komputera na inny, jeśli obsługa względne położenie plików.  
  
 Wdrażanie rozwiązania z serwerem, a następnie rozpowszechnić dokument dla każdego użytkownika końcowego, należy również ręcznie plik bazy danych, zainstaluj go w tej samej pozycji względem dokumentu. Oznacza to, użytkownik końcowy nie można przenieść go do nowej lokalizacji, na swoim komputerze, o ile nie jest on również przenosi plik bazy danych.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Lokalne pliki bazy danych i buforowania zestawu danych  
 W rozwiązaniach na poziomie dokumentu dla programu Microsoft Office Excel i Microsoft Office Word, zestawy danych w dokumencie można buforować, oznaczając wystąpienia zestawu danych z atrybutem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Podczas dodawania pliku bazy danych do projektu przy użyciu **Kreator konfiguracji źródła danych**, typizowanego zestaw danych jest automatycznie dodawane do projektu. Rzadko należy zastosować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> do tego zestawu danych, ponieważ dane są już lokalnie na komputerze użytkownika. Aby uzyskać więcej informacji, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do formantów w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Dane w pamięci podręcznej](../vsto/caching-data.md)  
  
  
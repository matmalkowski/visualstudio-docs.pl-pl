---
title: "Korzystanie z plików lokalnej bazy danych w rozwiązań Office ― omówienie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1576af3c3fc8a1c7f514a4941eb849df03774c5f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="using-local-database-files-in-office-solutions-overview"></a>Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office ― Omówienie
  Rozwiązania pakietu Office, mogą obejmować plik bazy danych, takich jak plik programu SQL Server Express (mdf) lub plik programu Microsoft Office Access (.mdb). Pozwala to użytkownikom końcowym obsługę lokalnej bazy danych w sytuacji, gdy obsługa scentralizowanej bazie danych nie jest wymagane, na przykład w przypadku rozwiązania lokalnego magazynu używanego na pojedynczym komputerze.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="importing-the-database-file-into-a-project"></a>Importowanie pliku bazy danych do projektu  
 Aby zaimportować plik bazy danych do projektu, należy użyć **Kreator konfiguracji źródła danych** tworzenia źródła danych na podstawie pliku bazy danych. Kreator dodaje plik bazy danych i typizowanego zestaw danych do projektu.  
  
## <a name="deploying-the-database-file"></a>Wdrażanie pliku bazy danych  
 **Kreator konfiguracji źródła danych** korzysta ze ścieżki względnej do utworzenia połączenia z lokalnego pliku bazy danych. Dzięki temu można kopiować rozwiązania z jednego komputera na inny, jeśli obsługa względne położenie plików.  
  
 Wdrażanie rozwiązania z serwerem, a następnie rozpowszechnić dokument dla każdego użytkownika końcowego, należy również ręcznie plik bazy danych, zainstaluj go w tej samej pozycji względem dokumentu. Oznacza to, użytkownik końcowy nie można przenieść go do nowej lokalizacji, na swoim komputerze, o ile nie jest on również przenosi plik bazy danych.  
  
## <a name="local-database-files-and-caching-the-dataset"></a>Lokalne pliki bazy danych i buforowania zestawu danych  
 W rozwiązaniach na poziomie dokumentu dla programu Microsoft Office Excel i Microsoft Office Word, zestawy danych w dokumencie można buforować, oznaczając wystąpienia zestawu danych z atrybutem <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>. Podczas dodawania pliku bazy danych do projektu przy użyciu **Kreator konfiguracji źródła danych**, typizowanego zestaw danych jest automatycznie dodawane do projektu. Rzadko należy zastosować <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> do tego zestawu danych, ponieważ dane są już lokalnie na komputerze użytkownika. Aby uzyskać więcej informacji, zobacz [buforowanie danych](../vsto/caching-data.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Porady: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Porady: aktualizowanie źródła danych danymi z formanty hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)   
 [Buforowanie danych](../vsto/caching-data.md)  
  
  
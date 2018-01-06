---
title: "Projekt podtypów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 21d7f013989607f7f5416a57829bc9b2b29b61d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="project-subtypes"></a>Podtypów projektu
Projekt podtypów pozwalają dostosować lub wersja zachowanie systemów projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Dostosowania obejmują zapisywania dodatkowe dane w pliku projektu, dodając lub filtrowanie elementów w **Dodaj nowy element** okno dialogowe, kontrolowanie jak debugować zestawy i wdrożone oraz w celu rozszerzenia projektu **właściwości Strony** okno dialogowe. VSPackages implementuje podtypów projektu za pomocą modelu COM agregacji.  
  
> [!NOTE]
>  System projektu Visual C++ nie obsługuje podtypów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sam używa podtypów projektu do implementacji projektów programu SQL Server i urządzenia przenośne.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Projektowanie podtypów projektów](../../extensibility/internals/project-subtypes-design.md)  
 Omówienie pojęć podtypów projektu.  
  
 [Sekwencja inicjowania podtypów projektów](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Zawiera opis sekwencji inicjowania podtypu projektu programowe przez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowiska.  
  
 [Właściwości i metody rozszerzane przez podtypy projektów](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Zawiera szczegółowe opisy funkcji i metod najczęściej rozszerzone przy użyciu podtypów projektu.  
  
 [Utrwalanie danych w pliku projektu programu MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Opisuje sposób do utrwalenia danych w pliku projektu i sposobu użycia <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> do obsługi danych w pliku projektu na poziomach agregacji podtypu projektu.  
  
 [Interfejs użytkownika właściwości projektu](../../extensibility/internals/project-property-user-interface.md)  
 W tym artykule opisano, jak podtypów projektu można modyfikować projektu **strony właściwości** okno dialogowe.  
  
 [Rozszerzanie modelu obiektu projektu podstawowego](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Zawiera informacje dotyczące sposobu podtypów projektu można użyć rozszerzeń automatyzacji Rozszerzanie modelu obiektu automatyzacji.  
  
 [Dodawanie elementów do okna dialogowego Dodawanie nowego elementu](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Opisuje sposób dodawania elementów do **Dodaj nowy element** okno dialogowe.  
  
 [Zapisywanie danych w plikach projektu](../../extensibility/saving-data-in-project-files.md)  
 Wyjaśniono, jak podtypu projektu można zapisywać i pobrać dane specyficzne dla podtypu w pliku projektu za pomocą Framework zarządzane pakietu (MPF).  
  
 [Obsługa wdrożeń specjalistycznych](../../extensibility/internals/handling-specialized-deployment.md)  
 Wyjaśniono, jak podtypów projektu można podać zachowanie wdrażania specjalne zaimplementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> interfejsu.  
  
 [Dodawanie i usuwanie stron właściwości](../../extensibility/adding-and-removing-property-pages.md)  
 W tym artykule opisano Dodawanie i usuwanie stron właściwości w Projektancie projektu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 Zawiera łącza do tematów, w której opisano [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektów.
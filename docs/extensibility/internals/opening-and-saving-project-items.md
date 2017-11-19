---
title: "Otwieranie i zapisywanie elementów projektu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a30589591a7cef60ecfb19945366f8fcf539da02
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="opening-and-saving-project-items"></a>Otwieranie i zapisywanie elementów projektu
Po dodaniu nowego typu projektu można zarządzać otwieranie i zapisywanie plików projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). W poniższych tematach opisano różne podejścia do otwierania i zapisywania plików.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Zawiera wyjaśnienie krok po kroku sposób obsługi IDE **Otwórz plik** polecenia i rolą projektów w odpowiedzi na to polecenie.  
  
 [Wyświetlanie plików przy użyciu Otwórz za pomocą polecenia](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Zawiera szczegółowe, krok wyjaśnienie sposobu obsługi IDE **Otwórz za pomocą** polecenie otwarcia pliku, który zawiera niektóre wybór standardowe edytory monitowania.  
  
 [Porady: Otwórz edytory specyficznego dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Instrukcje krok po kroku do określenia, że pliki określonego typu w projekcie powinien zostać otwarty za pomocą edytora określonego projektu.  
  
 [Porady: otwieranie standardowe edytory](../../extensibility/how-to-open-standard-editors.md)  
 Instrukcje krok po kroku do określenia sposobu włączania IDE otworzyć standardowego edytora plików w sieci typu projektu.  
  
 [Porady: Otwórz edytory dla otwarte dokumenty](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Zawiera instrukcje krok po kroku, aby otworzyć Edytor specyficznego dla projektu, dla której plik otwarty.  
  
 [Zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md)  
 Zawiera szczegółowe wyjaśnienie, jak obsługuje IDE **zapisać**, **Zapisz jako**, i **Zapisz wszystko** poleceń dla dokumentu otwarty w edytorze standardowa.  
  
 [Zapisanie dokumentu niestandardowych](../../extensibility/internals/saving-a-custom-document.md)  
 Zapewnia diagram i szczegółowe wyjaśnienie, jak obsługuje IDE **zapisać**, **Zapisz jako**, i **Zapisz wszystko** polecenia dla dokumentów otwarty w edytorze niestandardowych.  
  
 [Określanie otwieranym edytora plików w projekcie](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 W tym artykule omówiono proces, który wykonuje IDE w celu wybrania odpowiedniego edytora projektanta dla pliku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md)  
 Zawiera cztery typy edytory mogła obsługiwać IDE, a zawiera opisy każdej edytora.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono, jak projekty kontrolować sposób kompilacji i skompilowany kod, jak edytory są otwarte i jak sformatowanych elementów projektu.
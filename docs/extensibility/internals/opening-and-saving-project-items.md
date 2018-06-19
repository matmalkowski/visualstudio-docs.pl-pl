---
title: Otwieranie i zapisywanie elementów projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 895306a70d386b7a895b52b22704ec42a07d17ce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130605"
---
# <a name="opening-and-saving-project-items"></a>Otwieranie i zapisywanie elementów projektu
Po dodaniu nowego typu projektu można zarządzać otwieranie i zapisywanie plików projektów w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE). W poniższych tematach opisano różne podejścia do otwierania i zapisywania plików.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)  
 Zawiera wyjaśnienie krok po kroku sposób obsługi IDE **Otwórz plik** polecenia i rolą projektów w odpowiedzi na to polecenie.  
  
 [Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)  
 Zawiera szczegółowe, krok wyjaśnienie sposobu obsługi IDE **Otwórz za pomocą** polecenie otwarcia pliku, który zawiera niektóre wybór standardowe edytory monitowania.  
  
 [Instrukcje: otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)  
 Instrukcje krok po kroku do określenia, że pliki określonego typu w projekcie powinien zostać otwarty za pomocą edytora określonego projektu.  
  
 [Instrukcje: otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)  
 Instrukcje krok po kroku do określenia sposobu włączania IDE otworzyć standardowego edytora plików w sieci typu projektu.  
  
 [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)  
 Zawiera instrukcje krok po kroku, aby otworzyć Edytor specyficznego dla projektu, dla której plik otwarty.  
  
 [Zapisywanie standardowego dokumentu](../../extensibility/internals/saving-a-standard-document.md)  
 Zawiera szczegółowe wyjaśnienie, jak obsługuje IDE **zapisać**, **Zapisz jako**, i **Zapisz wszystko** poleceń dla dokumentu otwarty w edytorze standardowa.  
  
 [Zapisywanie niestandardowego dokumentu](../../extensibility/internals/saving-a-custom-document.md)  
 Zapewnia diagram i szczegółowe wyjaśnienie, jak obsługuje IDE **zapisać**, **Zapisz jako**, i **Zapisz wszystko** polecenia dla dokumentów otwarty w edytorze niestandardowych.  
  
 [Określanie, który edytor służy do otwierania pliku w projekcie](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)  
 W tym artykule omówiono proces, który wykonuje IDE w celu wybrania odpowiedniego edytora projektanta dla pliku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Tworzenie niestandardowych edytorów i projektantów](../../extensibility/creating-custom-editors-and-designers.md)  
 Zawiera cztery typy edytory mogła obsługiwać IDE, a zawiera opisy każdej edytora.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono, jak projekty kontrolować sposób kompilacji i skompilowany kod, jak edytory są otwarte i jak sformatowanych elementów projektu.
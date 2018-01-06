---
title: "Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b72fc46d64034ddc22e929fb1a1eff26115cce70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows
Za pomocą pakietu Instalatora Windows (MSI) nie można wdrożyć pakietu VSIX. Można jednak Wyodrębnij zawartość pakietu VSIX dla wdrożenia MSI. Ten dokument przedstawia sposób przygotowania projektu, której wyjście domyślny jest pakietem VSIX do dołączenia do projektu Instalatora.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Przygotowywanie wdrożenia Instalatora Windows projekt rozszerzenia  
 Wykonaj następujące kroki na nowe projekty rozszerzenia przed dodaniem go do projektu Instalatora.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Aby przygotować projekt rozszerzenia dla wdrożenia Instalatora Windows  
  
1.  Utwórz pakiet VSPackage, składników MEF, ozdób Edytor lub inny typ projektu rozszerzalności, zawierającą manifestu VSIX.  
  
2.  Otwórz plik manifestu VSIX w edytorze kodu.  
  
3.  Element InstalledByMsi manifestu VSIX, aby ustawić `true`. Aby uzyskać więcej informacji na temat manifestu VSIX, zobacz [odwołania 2.0 schematu rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Zapobiega to próbie instalacji składnika Instalatora VSIX.  
  
4.  Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i kliknij przycisk **właściwości**.  
  
5.  Wybierz **VSIX** kartę.  
  
6.  Sprawdź pola o nazwie **VSIX kopiowania zawartości do następującej lokalizacji** i wpisz ścieżkę, do której projektu Instalator pobierze pliki.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Wyodrębnianie plików z istniejącego pakietu VSIX  
 Wykonaj następujące kroki, aby dodać zawartość istniejącego pakietu VSIX do projektu Instalatora, gdy nie ma plików źródłowych.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Aby wyodrębnić pliki z istniejącego pakietu VSIX  
  
1.  Zmień nazwę. Plik VSIX zawierający rozszerzenie z *filename*.vsix do *filename*zip.  
  
2.  Skopiuj zawartość pliku zip do katalogu.  
  
3.  Usuń plik XML [Content_types] z katalogu.  
  
4.  Edytuj VSIX manifest, jak pokazano w poprzedniej procedurze.  
  
5.  Dodaj pozostałe pliki do projektu Instalatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrożenie Instalatora programu Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Wskazówki: Tworzenie niestandardowej akcji](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)
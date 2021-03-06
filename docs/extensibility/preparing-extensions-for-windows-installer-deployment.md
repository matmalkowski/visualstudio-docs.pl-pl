---
title: Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc742fecbbe03ff3d3aa0fb3f8d61a9c5f09254b
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495274"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows
Za pomocą pakietu Instalatora Windows (MSI) nie można wdrożyć pakiet VSIX. Jednak można wyodrębnić zawartości pakietu VSIX do wdrożenia MSI. W tym dokumencie pokazano, jak przygotować projektu, którego domyślne dane wyjściowe to pakiet VSIX do włączenia do projektu Instalatora.  
  
## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Przygotowanie projektu rozszerzenia dla wdrożenia Instalatora Windows  
 Te kroki można wykonać na nowe projekty rozszerzenie, przed dodaniem do projektu Instalatora.  
  
### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Aby przygotować projekt rozszerzenia dla wdrożenia Instalatora Windows  
  
1.  Tworzenie pakietu VSPackage, składnik MEF, zakończeń edytora lub innych typów projektów rozszerzalności, która zawiera manifestu VSIX.  
  
2.  Otwórz manifestu VSIX w edytorze kodu.  
  
3.  Ustaw `InstalledByMsi` elementu manifestu VSIX do `true`. Aby uzyskać więcej informacji na temat manifestu VSIX, zobacz [— dokumentacja schematu 2.0 rozszerzenia VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Zapobiega to próby instalacji składnika Instalator VSIX.  
  
4.  Kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** i kliknij przycisk **właściwości**.  
  
5.  Wybierz **VSIX** kartę.  
  
6.  Sprawdź pole o nazwie **VSIX kopiowania zawartości do następującej lokalizacji** i wpisz ścieżkę, do której pliki przejmą projektu Instalatora.  
  
## <a name="extract-files-from-an-existing-vsix-package"></a>Wyodrębnij pliki z istniejącego pakietu VSIX  
 Wykonaj następujące kroki, aby dodać zawartość istniejącego pakietu VSIX do projektu Instalatora, gdy nie masz pliki źródłowe.  
  
### <a name="to-extract-files-from-an-existing-vsix-package"></a>Aby wyodrębnić pliki z istniejącego pakietu VSIX  
  
1.  Zmień nazwę *. VSIX* plik zawierający rozszerzenie z *filename.vsix* do *filename.zip*.  
  
2.  Skopiuj zawartość *zip* plik do katalogu.  
  
3.  Usuń *[Content_types] .xml* plików z katalogu.  
  
4.  Edytowanie manifestu VSIX, jak pokazano w poprzedniej procedurze.  
  
5.  Dodaj pozostałych plików do projektu Instalatora.  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrożenie Instalatora programu Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Przewodnik: Tworzenie niestandardowej akcji](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
---
title: "Wysyłanie rozszerzeń programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 543f107081a5cc29ac14f1c2ba2e05924b72e353
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="shipping-visual-studio-extensions"></a>Wysyłanie rozszerzeń programu Visual Studio
Po zakończeniu tworzenia rozszerzenia, można go zainstalować na innych komputerach, udostępnić go znajomych i współpracowników lub opublikować go w programie Visual Studio Marketplace. W tej sekcji opisano możemy wszystkie czynności należy wykonać w celu publikowania i obsługa rozszerzenia: Praca z plikami .vsix, publikowania, lokalizowanie i aktualizowanie.  
  
## <a name="working-with-vsix-extensions"></a>Praca z rozszerzenia VSIX  
 Można utworzyć rozszerzenia VSIX tworzenia pustego projektu VSIX, a następnie dodać do niego szablony innego elementu. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).  
  
 Można użyć formatu pliku VSIX pakietu szablony projektów, szablony, VSPackages, składniki Managed Extensibility Framework (MEF), element **przybornika** formantów, zestawy i niestandardowe typy (dotyczy to również niestandardowych stron Start). Format pliku VSIX używa wdrożenia na podstawie pliku. Aby uzyskać więcej informacji na temat pakietów VSIX, zobacz [anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Format pliku VSIX nie obsługuje instalacji fragmentów kodu. Ponadto nie obsługuje niektórych inne scenariusze, takie jak zapisywanie do globalnej pamięci podręcznej zestawów (GAC) lub w rejestrze systemu. Jeśli trzeba zapisać w pamięci podręcznej GAC i rejestru do instalacji, należy użyć Instalatora Windows. Aby uzyskać więcej informacji, zobacz [przygotowywania rozszerzeń dla wdrażania systemu Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publikowanie rozszerzenia programu Visual Studio Marketplace  
 Rozszerzenia do innych osób można rozpowszechniać za pomocą ich .vsix pliku korespondencji lub umieszczenie w na serwerze. Najlepszy sposób pozyskania kodu w ręce wiele osób jest umieszczenie go w [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Rozszerzenia programu Visual Studio Marketplace są dostępne dla użytkowników programu Visual Studio za pomocą **rozszerzenia i aktualizacje**. Aby uzyskać więcej informacji, zobacz [Znajdowanie i rozszerzenia przy użyciu programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Aby uzyskać pełny przykład pokazuje, jak można przekazać rozszerzenie do Visual Studio Marketplace, zobacz [wskazówki: publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Galerie prywatnych  
 Podczas opracowywania formantów, szablony i narzędzia, można udostępniać w swojej organizacji, umieszczając je do galerii prywatnych w sieci intranet. Aby uzyskać więcej informacji, zobacz [galerie prywatnego](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Lokalizowanie rozszerzenia  
 Jeśli planujesz wersji rozszerzenia w różnych lokalizacjach, należy rozważyć lokalizowania go. Opis na czym polega znaleźć [lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>Aktualizowanie i przechowywanie wersji rozszerzenia  
 Po opublikowaniu rozszerzenie, będzie pochodził czas, kiedy trzeba ją zaktualizować. Aby dowiedzieć się, jak zaktualizować rozszerzenie, które zostały opublikowane w Visual Studio Marketplace, zobacz [porady: aktualizowanie rozszerzenie](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Można ustawić rozszerzenia do obsługi wielu wersji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [obsługi wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Wyjaśniono, jak zainstalować szablon niestandardowy projektu przy użyciu szablonu projektu VSIX.|  
|[Anatomia pakietu VSIX](../extensibility/anatomy-of-a-vsix-package.md)|W tym artykule opisano składniki pakietu VSIX.|  
|[Szablon projektu VSIX](../extensibility/vsix-project-template.md)|Instrukcje krok po kroku dotyczące pakietu i publikowanie rozszerzenia.|  
|[Lokalizowanie pakietów VSIX](../extensibility/localizing-vsix-packages.md)|Wyjaśniono, jak udostępnić zlokalizowanego tekstu w trakcie instalacji przy użyciu plików extension.vsixlangpack.|  
|[Porady: aktualizowanie rozszerzenie](../extensibility/how-to-update-a-visual-studio-extension.md)|Opisuje sposób zaktualizować rozszerzenia w systemie i wdrożenia aktualizacji na istniejące rozszerzenie programu Visual Studio.|  
|[Instrukcje: dodawanie zależności do pakietu VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Opisuje sposób dodawania odwołania do pakietów wdrożeniowych VSIX.|  
|[Przygotowywanie rozszerzeń dla wdrożenia Instalatora Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Wyjaśniono, jak wdrożyć rozszerzenie za pomocą Instalatora Windows.|  
|[Podpisywanie pakietów VSIX](../extensibility/signing-vsix-packages.md)|Wyjaśniono, jak do podpisywania pakietów VSIX.|  
|[Galerie prywatne](../extensibility/private-galleries.md)|Wyjaśnia sposób tworzenia prywatnej galerii rozszerzeń.|  
|[Obsługiwanie wielu wersji programu Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Przedstawia sposób mają rozszerzenia obsłudze wielu wersji programu Visual Studio.|
|[Lokalizowanie z programu Visual Studio](locating-visual-studio.md)|Opisuje sposób znaleźć wystąpień programu Visual Studio do wdrażania niestandardowego rozszerzenia.|

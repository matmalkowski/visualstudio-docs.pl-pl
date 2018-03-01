---
title: "Wprowadzenie do usługi języka oraz rozszerzenia Edytora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5f7b7440ff2f42eba1d138872071d4e51d2402c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Wprowadzenie do usługi języka oraz rozszerzenia Edytora
Rozszerzenia edytora służy do dodawania funkcji usługi języka takich jak tworzenie konspektu, pasujących nawiasów klamrowych, IntelliSense i żarówki języka programowania lub dowolnego typu zawartości. Można również dostosować wygląd i zachowanie edytorze programu Visual Studio, na przykład tekstu kolorowania marginesy, skojarzenia i inne elementy wizualne. Można również definiować własne typu zawartości i określić wygląd i zachowanie widoków tekstu, w których zostanie wyświetlona zawartość.  
  
 Aby rozpocząć pisanie rozszerzenia edytora, użyj edytora szablony projektów, które są instalowane jako część programu Visual Studio SDK. Visual Studio SDK jest dostępny do pobrania zestaw narzędzi, które ułatwiają tworzenie rozszerzeń programu Visual Studio za pomocą VSPackages lub przy użyciu Framework Managed Extensibility (MEF).  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat programu Visual Studio SDK, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 Firma Microsoft zaleca zapoznanie się następujące pojęcia i technologii przed przystąpieniem do napisania własnych rozszerzenia edytora.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) i rozszerzenia Edytora  
 Visual Studio Edytor interfejsu użytkownika (UI) jest zaimplementowana przy użyciu systemu Windows Presentation Foundation (WPF). WPF udostępnia bogate środowisko visual i spójny model programowania, która oddziela visual aspektów kod z logiką biznesową. Podczas tworzenia rozszerzenia edytora można użyć wielu elementów WPF i funkcje. Aby uzyskać więcej informacji, zobacz [Windows Presentation Foundation](/dotnet/framework/wpf/index).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) i rozszerzenia Edytora  
 Edytorze programu Visual Studio wykorzystuje Framework Managed Extensibility (MEF) do zarządzania jego składniki i rozszerzenia. MEF umożliwia także deweloperom więcej łatwe tworzenie rozszerzeń dla aplikacji hosta, takimi jak Visual Studio. Ta struktura służy do definiowania rozszerzenie zgodnie z umową MEF i wyeksportować go jako część MEF. Aplikacja hosta zarządza części ich wyszukiwanie, rejestrowanie ich i upewnić się, że są one stosowane do poprawny kontekst.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat MEF w edytorze, zobacz [Managed Extensibility Framework w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Punkty rozszerzenia edytora programu Visual Studio i rozszerzenia  
 Edytor punktów rozszerzenia są składniki MEF, które można dostosowywać i rozszerzać. W niektórych przypadkach można rozszerzyć punkt rozszerzenia przez Implementowanie interfejsu i eksportowania ich razem z prawidłowych metadanych. W innych przypadkach należy po prostu zadeklarować rozszerzenie i wyeksportować go jako określonego typu.  
  
 Poniżej przedstawiono niektóre podstawowe rodzaje rozszerzenia edytora:  
  
-   Marginesy i paski przewijania  
  
-   Znaczniki  
  
-   Skojarzenia  
  
-   Opcje  
  
-   IntelliSense  
  
 Aby uzyskać więcej informacji na temat punktów rozszerzenia edytora, zobacz [usługi języka oraz punktów rozszerzenia edytora](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Wdrażanie rozszerzeń edytora  
 W programie Visual Studio możesz wdrożyć rozszerzenia edytora Dodawanie plik metadanych o nazwie source.extension.vsixmanifest do rozwiązania, budowania rozwiązania, a następnie dodając kopię plików binarnych i manifest w folderze, który jest znany dla programu Visual Studio. Plik manifestu definiuje podstawowych informacji o rozszerzeniu (na przykład nazwa autora, wersji i typu zawartości). Aby uzyskać więcej informacji o pliku manifestu VSIX i sposobu wdrażania rozszerzeń, zobacz [wysyłania rozszerzenia dla programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Po zainstalowaniu rozszerzenia na komputerze obejmują pliki binarne i manifest w podfolderze folderu, który jest znany dla programu Visual Studio.  
  
> [!WARNING]
>  Nie trzeba martwić się o szczegóły manifestów oraz lokalizacje jej wdrożenia, korzystając z jednego z szablonów rozszerzania edytora, uwzględnionych w programie Visual Studio. Szablony zawierają wszystko, co jest wymagane, aby zarejestrować i wdrożyć rozszerzenie.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Rozszerzeniami w eksperymentalnym wystąpieniu  
 Gdy tworzysz rozszerzenie przez wdrożenie jej w następującym folderze eksperymentalne (w systemach Windows Vista i Windows 7), można zabezpieczyć z działającą wersją programu Visual Studio:  
  
 *LOCALAPPDATA %*\VisualStudio\10.0Exp\Extensions\\*firmy*\\*identyfikator rozszerzenia*  
  
 gdzie *LOCALAPPDATA %* to nazwa zalogowanego użytkownika *firmy* to nazwa firmy, który jest właścicielem rozszerzenia i *identyfikator rozszerzenia* identyfikatora rozszerzenia.  
  
 Podczas wdrażania rozszerzenie eksperymentalne lokalizacji jest uruchamiany w trybie debugowania. Drugie wystąpienie programu Visual Studio została uruchomiona i nosi nazwę **programu Microsoft Visual Studio — eksperymentalne wystąpienie**.  
  
## <a name="managing-extensions"></a>Zarządzanie rozszerzeniami  
 Rozszerzenia dla programu Visual Studio są wyświetlane w **rozszerzenia i aktualizacje** (na **narzędzia** menu). Jeśli testujesz rozszerzenie w eksperymentalnym wystąpieniu, znajduje się w **rozszerzenia i aktualizacje** w eksperymentalnym wystąpieniu, ale nie znajduje się w wystąpieniu programowanie.  
  
 Aby uzyskać więcej informacji, zobacz [Znajdowanie i rozszerzenia przy użyciu programu Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Za pomocą szablonów można utworzyć rozszerzenia Edytora  
 Szablony edytora służy do tworzenia rozszerzenia MEF dostosować klasyfikatory, skojarzenia i marginesów. Brak szablonów dla projektów zarówno C# i Visual Basic. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia z szablonem elementu edytor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 Szablon projektu VSIX służy także do tworzenia rozszerzeń. Ten szablon zawiera tylko elementy, które są wymagane do wdrożenia dowolnego rodzaju rozszerzenia, a obejmują plik Source.Extension.vsixmanifest,a, odwołania do wymaganych zestawów i pliku projektu, który zawiera zadania kompilacji, które umożliwiają wdrażanie rozszerzenie. Aby uzyskać więcej informacji, zobacz [szablonu projektu VSIX](../extensibility/vsix-project-template.md).  
  
 Można również utworzyć edytora składników MEF z rozszerzeniem pakiet programu Visual Studio. Zobacz poniższe wskazówki, aby uzyskać szczegółowe informacje:  
  
-   [Przewodnik: używanie polecenia programu PowerShell z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Przewodnik: używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
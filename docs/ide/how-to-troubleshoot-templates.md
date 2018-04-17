---
title: Rozwiązywanie problemów z szablonu projektu programu Visual Studio i szablon elementu ładowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7e97185c6c494bc031d526915b547a5fd0fcd24d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-troubleshoot-templates"></a>Porady: Rozwiązywanie problemów z szablonami

Jeśli szablon nie może załadować w środowisku programistycznym, istnieje kilka sposobów, aby zlokalizować ten problem.

## <a name="validate-the-vstemplate-file"></a>Sprawdź poprawność pliku .vstemplate

Jeśli plik .vstemplate w szablonie nie pasuje do schematu szablonu Visual Studio, szablon nie może występować w **nowy projekt** okno dialogowe.

### <a name="to-validate-the-vstemplate-file"></a>Aby sprawdzić poprawność pliku .vstemplate

1. Zlokalizuj plik zip, który zawiera szablon.

1. Wyodrębnij plik zip.

1. Na **pliku** menu w programie Visual Studio, wybierz **Otwórz** > **pliku**.

1. Wybierz plik .vstemplate szablonu, a następnie wybierz pozycję **Otwórz**.

1. Upewnij się, że kod XML w pliku .vstemplate zgodnego ze schematu szablonu. Aby uzyskać więcej informacji o schemacie .vstemplate, zobacz [odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Aby uzyskać pomoc techniczną IntelliSense podczas tworzenia pliku .vstemplate, Dodaj `xmlns` atrybutu `VSTemplate` element i przypisz jej wartość http://schemas.microsoft.com/developer/vstemplate/2005.

1. Zapisz i zamknij plik .vstemplate.

1. Wybierz pliki zawarte w szablonie, kliknij prawym przyciskiem myszy i wybierz polecenie **przesyłają** > **skompresowanego folderu (zip)**. Wybrane pliki są kompresowane do pliku zip.

1. Umieść nowy plik zip, w tym samym katalogu co stary plik zip.

1. Usuń pliki szablonów wyodrębnionego i stary plik zip szablonu.

## <a name="enable-diagnostic-logging"></a>Włączanie rejestrowania diagnostyki

Można włączyć rejestrowania diagnostycznego w celu odnajdywania szablonu, wykonując kroki opisane w [odnajdywania szablonu rozwiązywania problemów (rozszerzalność)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Zobacz także

[Rozwiązywanie problemów z odnajdywania szablonu (rozszerzalność)](../extensibility/troubleshooting-template-discovery.md)  
[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)  
[Odwołanie do schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
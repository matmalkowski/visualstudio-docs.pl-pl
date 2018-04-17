---
title: Tworzenie szablonów projektów dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d489d09238aba17352f528e73d8c81c2733c0b47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-project-templates"></a>Porady: Tworzenie szablonów projektów

W tym temacie przedstawiono sposób tworzenia szablonu przy użyciu **Kreatora eksportowania szablonu**, które pakiety szablonu w pliku zip.

## <a name="to-create-a-user-project-template-by-using-the-export-template-wizard"></a>Aby utworzyć szablon projektu użytkownika przy użyciu Kreatora eksportowania szablonu

1. Tworzenie projektu.

    > [!NOTE]
    > Gdy nazwy projektu, który będzie źródło szablonu, należy używać tylko znaków prawidłowego identyfikatora. W przeciwnym razie w projektach, które są tworzone na podstawie tego szablonu mogą wystąpić błędy kompilacji. Aby uzyskać więcej informacji na temat prawidłowego identyfikatora znaków, zobacz [zadeklarowane nazwy elementów (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) lub [identyfikatorów (C++)](/cpp/cpp/identifiers-cpp). Alternatywnie można użyć [parametrów szablonu](../ide/template-parameters.md) używanie "bezpiecznej" nazw klas i przestrzenie nazw.

1. Edytuj projekt, dopóki nie jest gotowy do wyeksportowania jako szablon. Na przykład możesz edytować pliki kodu, wskaż, gdzie parametr zastąpienia powinno mieć miejsce. Zobacz [porady: parametry zastępcze w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

1. Na **projektu** menu, wybierz **Eksportuj szablon...** .

   **Kreatora eksportowania szablonu** otwiera.

1. Na **wybierz typ szablonu** wybierz pozycję **szablonu projektu**. Wybierz projekt, aby wyeksportować do szablonu, a następnie wybierz pozycję **dalej**.

1. Na **wybierz opcje szablonu** strony, wprowadź nazwę i opcjonalny opis, ikony i wyświetlić podgląd obrazu szablonu. Te elementy będą wyświetlane w **nowy projekt** okno dialogowe. Wybierz **Zakończ**.

  Projekt jest wyeksportowany do pliku zip i umieszczane w lokalizacji określonej w danych wyjściowych i zaznaczenie tej opcji, należy zaimportować do programu Visual Studio.

>[!NOTE]
> Aby znaleźć szablonu w **nowy projekt** okna dialogowego rozwiń **zainstalowana** , a następnie rozwiń kategorię, która odpowiada `ProjectType` elementu w pliku .vstemplate. Na przykład plik .vstemplate zawierający `<ProjectType>CSharp</ProjectType>` jest wyświetlany w obszarze **zainstalowana** > **Visual C#**, domyślnie. Szablon można organizować w podkatalogu typu projektu przez utworzenie folderu w tym katalogu i umieszczenie w nim plik zip do szablonu. Aby uzyskać więcej informacji, zobacz [porady: lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="other-ways-to-create-project-templates"></a>Inne sposoby Tworzenie szablonów projektów

Ręczne tworzenie szablonów projektów zbieranie plików, które stanowią projektu do folderu, a następnie utworzenie pliku XML .vstemplate o odpowiednie metadane. Aby uzyskać więcej informacji, zobacz [porady: ręczne tworzenie szablonów sieci web](../ide/how-to-manually-create-web-templates.md).

Jeśli masz program Visual Studio SDK zainstalowany Zakończono szablonu może zawijać w pliku VSIX dla wdrożenia przy użyciu **projektu VSIX** szablonu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Zobacz także

[Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)  
[Instrukcje: Tworzenie szablonów elementu](../ide/how-to-create-item-templates.md)  
[Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

---
title: Tworzenie szablonów projektów dla programu Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8e35833f9f8facf0639a87243d46794408167914
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-project-templates"></a>Porady: Tworzenie szablonów projektów

W tym temacie przedstawiono sposób tworzenia szablonu przy użyciu **Kreatora eksportowania szablonu**, które pakiety szablonu w *.zip* pliku.

## <a name="to-create-a-user-project-template-by-using-the-export-template-wizard"></a>Aby utworzyć szablon projektu użytkownika przy użyciu Kreatora eksportowania szablonu

1. Tworzenie projektu.

    > [!NOTE]
    > Gdy nazwy projektu, który będzie źródło szablonu, należy używać tylko znaków prawidłowego identyfikatora. W przeciwnym razie w projektach, które są tworzone na podstawie tego szablonu mogą wystąpić błędy kompilacji. Aby uzyskać więcej informacji na temat prawidłowego identyfikatora znaków, zobacz [zadeklarowane nazwy elementów (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) lub [identyfikatorów (C++)](/cpp/cpp/identifiers-cpp). Alternatywnie można użyć [parametrów szablonu](../ide/template-parameters.md) używanie "bezpiecznej" nazw klas i przestrzenie nazw.

1. Edytuj projekt, dopóki nie jest gotowy do wyeksportowania jako szablon. Na przykład możesz edytować pliki kodu, wskaż, gdzie parametr zastąpienia powinno mieć miejsce. Zobacz [porady: parametry zastępcze w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

1. Na **projektu** menu, wybierz **Eksportuj szablon**.

   **Kreatora eksportowania szablonu** otwiera.

1. Na **wybierz typ szablonu** wybierz pozycję **szablonu projektu**. Wybierz projekt, aby wyeksportować do szablonu, a następnie wybierz pozycję **dalej**.

1. Na **wybierz opcje szablonu** strony, wprowadź nazwę i opcjonalny opis, ikony i wyświetlić podgląd obrazu szablonu. Te elementy będą wyświetlane w **nowy projekt** okno dialogowe. Wybierz **Zakończ**.

  Projekt został wyeksportowany do *.zip* pliku umieszczane w lokalizacji określonej w danych wyjściowych i, jeśli zaznaczone, należy zaimportować do programu Visual Studio.

>[!NOTE]
> Można znaleźć szablonu w **nowy projekt** okna dialogowego rozwiń **zainstalowana** , a następnie rozwiń kategorię, która odpowiada `ProjectType` element *.vstemplate*pliku. Na przykład *.vstemplate* pliku, który zawiera `<ProjectType>CSharp</ProjectType>` jest wyświetlany w obszarze **zainstalowana** > **Visual C#**, domyślnie. Szablon można organizować w podkatalogu typu projektu przez utworzenie folderu w tym katalogu i wprowadzenie do szablonu *zip* plik w nim. Aby uzyskać więcej informacji, zobacz [porady: lokalizowanie i organizacja szablonów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="other-ways-to-create-project-templates"></a>Inne sposoby Tworzenie szablonów projektów

Tworzenie szablonów projektów ręcznie zbieranie plików, które stanowią projektu do folderu, a następnie utworzenie *.vstemplate* plik XML z odpowiednie metadane. Aby uzyskać więcej informacji, zobacz [porady: ręczne tworzenie szablonów sieci web](../ide/how-to-manually-create-web-templates.md).

Jeśli masz program Visual Studio SDK zainstalowany Zakończono szablonu może zawijać w pliku VSIX dla wdrożenia przy użyciu **projektu VSIX** szablonu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Zobacz także

- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Porady: Tworzenie szablonów elementów](../ide/how-to-create-item-templates.md)
- [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
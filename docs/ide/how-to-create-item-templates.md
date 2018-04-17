---
title: Tworzenie szablonów elementów dla programu Visual Studio | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3c6f95cbd0acdaba9e182cdda28692ea28179071
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-item-templates"></a>Porady: Tworzenie szablonów elementów

W tym temacie przedstawiono sposób tworzenia szablonu elementu przy użyciu **Kreatora eksportowania szablonu**. Jeśli szablon będzie składać się z wielu plików, zobacz [porady: Tworzenie szablonów elementów wielu plików](../ide/how-to-create-multi-file-item-templates.md).

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>Aby dodać szablon elementu użytkownika do okna dialogowego Dodaj nowy element

1. Utwórz lub Otwórz projekt w programie Visual Studio.

1. Dodaj element do projektu i zmodyfikować go, jeśli chcesz.

1. Zmodyfikuj kod wskaż, gdzie parametr zastąpienia powinno mieć miejsce. Aby uzyskać więcej informacji, zobacz [porady: parametry zastępcze w szablonie](../ide/how-to-substitute-parameters-in-a-template.md).

1. Na **projektu** menu, wybierz **Eksportuj szablon...** .

1. Na **wybierz typ szablonu** wybierz pozycję **szablon elementu**, wybierz projekt, który zawiera element, a następnie wybierz pozycję **dalej**.

1. Na **wybierz element do eksportowania** wybierz element, który chcesz utworzyć szablon, a następnie wybierz pozycję **dalej**.

1. Na **wybierz odwołania do elementów** wybierz odwołania do zestawów do uwzględnienia w szablonie, a następnie wybierz pozycję **dalej**.

1. Na **wybierz opcje szablonu** strony, wprowadź nazwę szablonu i opcjonalny opis, ikony i podglądu, a następnie wybierz **Zakończ**.

    Pliki szablonu są dodawane do pliku zip i skopiowany do katalogu, określone w kreatorze. Domyślna lokalizacja to %USERPROFILE%\Documents\Visual Studio \<wersji\>\My wyeksportowane szablony.

1. Jeśli użytkownik nie wybrał opcji **automatycznie zaimportuj szablon do programu Visual Studio** w **Kreatora eksportowania szablonu**Znajdź wyeksportowanego szablonu i skopiuj go do katalogu szablonu elementu użytkowników. Domyślna lokalizacja to %USERPROFILE%\Documents\Visual Studio \<wersji\>\Templates\ItemTemplates.

1. Zamknij program Visual Studio, a następnie otwórz go ponownie.

1. Utwórz nowy projekt, ani otworzyć istniejącego projektu, a następnie wybierz **projektu** > **Dodaj nowy element...**  lub naciśnij klawisz **Ctrl** + **Shift** + **A**.

   Szablon elementu jest wyświetlany w **Dodaj nowy element** okno dialogowe. Jeśli dodano opis **Kreatora eksportowania szablonu**, opis jest wyświetlany po prawej stronie okna dialogowego.

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Aby włączyć szablon elementu, który ma być używany w projekcie uniwersalnej aplikacji systemu Windows

Kreator wykona większość zadań, aby utworzyć szablon podstawowy, ale w wielu przypadkach trzeba ręcznie zmodyfikować plik .vstemplate po wyeksportowaniu szablonu. Na przykład, jeśli element ma się pojawiać **Dodaj nowy element** okna dialogowego dla projektu uniwersalnej aplikacji systemu Windows, należy wykonać kilka dodatkowych czynności.

1. Wykonaj kroki opisane w poprzedniej sekcji, aby wyeksportować szablon elementu.

1. Wyodrębnij plik zip, który został utworzony, a następnie otwórz plik .vstemplate w programie Visual Studio.

1. Dla projektów C# uniwersalnych systemu Windows, Dodaj następujący kod XML wewnątrz `<TemplateData>` elementu:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. W programie Visual Studio Zapisz plik .vstemplate i zamknij go.

1. Skopiuj i wklej plik .vstemplate do pliku zip.

     Jeśli **kopiowania pliku** zostanie wyświetlone okno dialogowe, wybierz **Kopiuj i Zamień** opcji.

Teraz można dodać elementu na podstawie tego szablonu do projektu uniwersalnej systemu Windows z **Dodaj nowy element** okno dialogowe.

## <a name="to-enable-templates-for-specific-project-subtypes"></a>Aby umożliwić szablony dla określonego projektu podtypów

Można określić, czy szablon powinien pojawić się tylko dla tylko niektórych projektu podtypów, takie jak Windows, Office, bazy danych lub sieci Web.

1. Znajdź ProjectType element w pliku .vstemplate szablonu elementu.

1. Dodaj [projectsubtype —](../extensibility/projectsubtype-element-visual-studio-templates.md) element natychmiast po elemencie typ projektu.

1. Ustaw wartość tekstowego elementu do jednego z następujących wartości:

    - Windows
    - Office
    - Baza danych
    - sieć Web

Na przykład: `<ProjectSubType>Database</ProjectSubType>`.

W poniższym przykładzie przedstawiono szablon elementu dla **Office** projektów.

```xml
<VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
   <TemplateData>
      <Name>Class</Name>
      <Description>An empty class file</Description>
      <Icon>Class.ico</Icon>
      <ProjectType>CSharp</ProjectType>
      <ProjectSubType>Office</ProjectSubType>
      <DefaultName>Class.cs</DefaultName>
   </TemplateData>
   <TemplateContent>
      <ProjectItem>Class1.cs</ProjectItem>
   </TemplateContent>
</VSTemplate>
```

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Aby ręcznie utworzyć szablon elementu bez użycia Kreatora eksportowania szablonu

W niektórych przypadkach warto utworzyć szablon elementu ręcznie, od początku.

1. Tworzenie projektu i elementu projektu.

1. Element projektu należy modyfikować, dopóki będzie gotowy do zapisania jako szablon.

1. Modyfikowanie pliku kodu, aby wskazać wymiany parametru powinna mieć miejsce, jeśli kontakt. Aby uzyskać więcej informacji na temat wymiany parametru, zobacz [porady: parametry zastępczych w szablonie.](../ide/how-to-substitute-parameters-in-a-template.md)

1. Tworzenie pliku XML, a następnie zapisz plik z rozszerzeniem pliku .vstemplate w tym samym katalogu co plik elementu projektu.

1. Edytuj plik .vstemplate XML do udostępnienia metadanych szablonu elementu. Aby uzyskać więcej informacji, zobacz [odwołanie do schematu szablonu (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md) i przykładowe w poprzedniej sekcji.

1. Zapisz plik .vstemplate i zamknij go.

1. W Eksploratorze Windows, zaznacz pliki, aby uwzględnić w szablonie, kliknij prawym przyciskiem myszy zaznaczenie, a następnie wybierz pozycję **przesyłają** > **skompresowanego folderu (zip)**. Wybrane pliki są kompresowane do pliku zip.

1. Skopiuj plik zip i wklej go w lokalizacji szablonu elementu użytkownika. W programie Visual Studio 2017 r domyślnym katalogiem jest %USERPROFILE%\Documents\Visual Studio 2017\Templates\ItemTemplates. Aby uzyskać więcej informacji, zobacz [porady: Znajdź i organizowanie szablony projektów i elementów](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Zobacz także

[Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)  
[Instrukcje: Tworzenie szablonów elementu obejmujących wiele plików](../ide/how-to-create-multi-file-item-templates.md)  
[Odwołanie do schematu szablonu Visual Studio (rozszerzalność)](../extensibility/visual-studio-template-schema-reference.md)

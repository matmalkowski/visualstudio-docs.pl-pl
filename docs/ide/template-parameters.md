---
title: "Visual Studio projektu i elementu parametrów do szablonu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e3ce315cd1ddff9445c72f7299a8d6aaf0a3a82
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2018
---
# <a name="template-parameters"></a>Parametry szablonu

Przy użyciu parametrów w szablonach, można zamienić wartości kluczowych części szablonu, na przykład nazwy klas i przestrzenie nazw, przy tworzeniu wystąpienia szablonu. Te parametry są zastępowane przez Kreatora szablonu, który działa w tle, gdy użytkownik wybierze **OK** lub **Dodaj** w **nowy projekt** lub **Dodaj nowy element**  okien dialogowych.

## <a name="declaring-and-enabling-template-parameters"></a>Deklarowanie i włączanie parametrów szablonu

Parametry szablonu są zadeklarowane w formacie $*parametru*$. Na przykład:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Aby włączyć podstawienie parametru w szablonach

1. W pliku .vstemplate szablonu zlokalizuj element `ProjectItem`, który odpowiada elementowi, dla którego chcesz włączyć podmianę parametrów.

1. Ustaw atrybut `ReplaceParameters` elementu `ProjectItem` na `true`.

1. W pliku kodu dla elementu projektu dołącz parametry, tam gdzie jest to potrzebne. Na przykład, następujący parametr określa, że bezpieczna nazwa projektu będzie używana dla przestrzeni nazw w pliku:

    ```csharp
    namespace $safeprojectname$
    ```

## <a name="reserved-template-parameters"></a>Parametry szablonu zastrzeżone

Poniższa tabela zawiera listę zastrzeżonych parametrów szablonu, które mogą być używane przez dowolny szablon.

|Parametr|Opis|
|---------------|-----------------|
|clrversion|Aktualna wersja środowiska uruchomieniowego języka wspólnego (CLR).|
|Identyfikator GUID [1 – 10]|Identyfikator GUID służący do zamienienia identyfikatora GUID w pliku projektu. Można określić maksymalnie 10 unikatowych identyfikatorów GUID (na przykład `guid1`).|
|Nazwa elementu|Nazwa podana przez użytkownika w **Dodaj nowy element** okno dialogowe.|
|MachineName|Bieżąca nazwa komputera (na przykład Computer01).|
|projectname|Nazwa podana przez użytkownika w **nowy projekt** okno dialogowe.|
|registeredorganization|Wartość klucza rejestru z HKLM\Software\Microsoft\Windows NT\CurrentVersion\RegisteredOrganization.|
|rootnamespace|Główna przestrzeń nazw bieżącego projektu. Ten parametr dotyczy tylko szablonów elementów.|
|safeitemname|Nazwa podana przez użytkownika w **Dodaj nowy element** okno dialogowe, ze wszystkimi niebezpieczny znaków i usunięte spacje.|
|safeprojectname|Nazwa podana przez użytkownika w **nowy projekt** okno dialogowe, ze wszystkimi niebezpieczny znaków i usunięte spacje.|
|czas|Bieżący czas w formacie DD/MM/RRRR 00:00:00.|
|SpecificSolutionName|Nazwa rozwiązania. W razie wybrania opcji „Utwórz katalog rozwiązania”, `SpecificSolutionName` ma nazwę rozwiązania. Jeżeli „Utwórz katalog rozwiązania” nie jest zaznaczone, `SpecificSolutionName` jest pusta.|
|USERDOMAIN|Bieżąca domena użytkownika.|
|Nazwa użytkownika|Bieżąca nazwa użytkownika.|
|webnamespace|Nazwa bieżącej witryny sieci Web. Ten parametr jest używany w szablonie formularza sieci Web, aby zagwarantować unikalne nazwy klas. Jeśli witryna sieci Web jest w katalogu głównym serwera sieci Web, ten parametr szablonu jest rozpoznawany jako należący do katalogu głównego serwera sieci Web.|
|Roku|Bieżący rok w formacie RRRR.|

> [!NOTE]
> Parametry szablonu uwzględniają wielkość liter.

## <a name="custom-template-parameters"></a>Parametry szablonu niestandardowego

Możesz określić własne parametry szablonu i wartości, oprócz parametry szablonu domyślnego zastrzeżone, które są używane podczas wymiany parametru. Aby uzyskać więcej informacji, zobacz [customparameters — element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-using-the-project-name-for-a-file-name"></a>Przykład: Przy użyciu nazwy projektu dla nazwy pliku

Można określić nazwy zmiennej plików dla elementów projektu za pomocą parametru w `TargetFileName` atrybutu.

Poniższy przykład określa, że nazwa pliku wykonywalnego używa nazwy projektu, określony przez `$projectname$`.

```xml
<TemplateContent>
    <ProjectItem
        ReplaceParameters="true"
        TargetFileName="$projectname$.exe">
            File1.exe
    </ProjectItem>
      ...
</TemplateContent>
```

## <a name="example-using-the-safe-project-name-for-the-namespace-name"></a>Przykład: Przy użyciu nazwy projektu bezpieczne dla nazwy przestrzeni nazw

Aby użyć nazwy projektu bezpieczne dla przestrzeni nazw w pliku klasy C#, użyj następującej składni:

```csharp
namespace $safeprojectname$
{
    public class Class1
    {
        public Class1()
        { }
    }
}
```

W pliku .vstemplate szablonu projektu, obejmują `ReplaceParameters="true"` atrybutu, gdy odwołanie do pliku:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz także

[Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)  
[Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)
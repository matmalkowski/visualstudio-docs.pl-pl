---
title: Visual Studio projektu i elementu parametrów do szablonu
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio templates, parameters
- template parameters [Visual Studio]
- project templates, parameters
- item templates, parameters
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: abac68ff371040a7f121a885065c8c3eaf9af8ff
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
ms.locfileid: "32066537"
---
# <a name="template-parameters"></a>Parametry szablonu

Można zastąpić wartości w szablonie, podczas tworzenia wystąpienia klasy szablonu. Aby skonfigurować tę funkcję, użyj *parametrów szablonu*. Parametry szablonu może być używany do zastąpienia wartości, takie jak nazwy klas i przestrzenie nazw w szablonie. Kreator szablonu, który działa w tle, gdy użytkownik dodaje nowy element lub projektu zastępuje te parametry.

## <a name="declaring-and-enabling-template-parameters"></a>Deklarowanie i włączanie parametrów szablonu

Parametry szablonu są zadeklarowane w formacie $*parametru*$. Na przykład:

- $safeprojectname$

- $guid1$

- $guid5$

### <a name="to-enable-parameter-substitution-in-templates"></a>Aby włączyć podstawienie parametru w szablonach

1. W *.vstemplate* pliku szablonu, zlokalizuj `ProjectItem` element, który odpowiada elementu, dla którego chcesz włączyć wymiany parametru.

1. Ustaw atrybut `ReplaceParameters` elementu `ProjectItem` na `true`.

1. W pliku kodu dla elementu projektu dołącz parametry, tam gdzie jest to potrzebne. Na przykład następujący parametr określa, czy nazwa projektu bezpieczne jest używana dla przestrzeni nazw w pliku:

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
|webnamespace|Nazwa bieżącej witryny sieci web. Ten parametr jest używany w szablonie formularza sieci web w celu zagwarantowania unikatowe nazwy klas. W przypadku witryny sieci web w katalogu głównym serwera sieci web, ten parametr szablonu jest rozpoznawany jako katalog główny serwera sieci web.|
|Roku|Bieżący rok w formacie RRRR.|

> [!NOTE]
> Parametry szablonu uwzględniają wielkość liter.

## <a name="custom-template-parameters"></a>Parametry szablonu niestandardowego

Możesz określić własne parametry szablonu i wartości, oprócz parametry szablonu domyślnego zastrzeżone, które są używane podczas wymiany parametru. Aby uzyskać więcej informacji, zobacz [customparameters — element (szablony Visual Studio)](../extensibility/customparameters-element-visual-studio-templates.md).

## <a name="example-use-the-project-name-for-a-file-name"></a>Przykład: Użyj nazwy projektu dla nazwy pliku

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

## <a name="example-use-the-safe-project-name-for-the-namespace-name"></a>Przykład: Użyj nazwy projektu bezpieczne dla nazwy przestrzeni nazw

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

W *.vstemplate* pliku szablonu projektu, obejmują `ReplaceParameters="true"` atrybutu, gdy odwołanie do pliku:

```xml
<TemplateContent>
    <ProjectItem ReplaceParameters="true">
        Class1.cs
    </ProjectItem>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie szablonów](../ide/customizing-project-and-item-templates.md)
- [Porady: Tworzenie szablonów projektów](../ide/how-to-create-project-templates.md)

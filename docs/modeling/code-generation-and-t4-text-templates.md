---
title: Generowanie kodu i szablony tekstowe T4
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f4fed2cbf00717e4eaf9c1353370dbd96037491
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="code-generation-and-t4-text-templates"></a>Generowanie kodu i szablony tekstowe T4

W programie Visual Studio *szablonu tekstowego T4* jest mieszaniną bloki tekstu i logiki kontroli, które można wygenerować pliku tekstowego. Logika kontroli są zapisywane jako fragmenty kodu programu w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. W programie Visual Studio 2015 Update 2 lub nowszy można użyć funkcji w wersji 6.0 C# w dyrektywach szablony T4. Wygenerowany plik może być tekst dowolnego rodzaju, takich jak strony sieci Web lub plik zasobu lub kodu źródłowego program w dowolnym języku.

Istnieją dwa rodzaje szablonów tekstowych T4: Uruchom czasu i w czasie projektowania.

## <a name="run-time-t4-text-templates"></a>Uruchom szablonów tekstowych T4 czasu

Znany również jako "wstępnie przetworzonych" Szablony, uruchom szablony czasu są wykonywane w aplikacji do tworzenia ciągów tekstowych, zazwyczaj jako część dane wyjściowe. Na przykład można utworzyć szablonu, aby zdefiniować strony HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Zwróć uwagę, że szablon jest podobny wygenerowanych danych wyjściowych. Podobieństwa szablonu, aby dane wyjściowe pomaga uniknąć pomyłek, jeśli chcesz je zmienić.

Ponadto szablon zawiera fragmenty kodu programu. Powtarzaj fragmentów tekstu, aby sekcje warunkowe i umożliwia wyświetlanie danych z aplikacji, można użyć tych fragmentów.

Do generowania danych wyjściowych, aplikacja wywołuje funkcję, która jest generowana przez szablon. Na przykład:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

Aplikację można uruchomić na komputerze, na którym nie ma zainstalowanego programu Visual Studio.

Aby utworzyć szablon czasu wykonywania, Dodaj **szablonu tekstowego preprocesora** plik do projektu. Alternatywnie możesz dodać plik tekstowy i ustawić jej **narzędzie niestandardowe** właściwości **texttemplatingfilepreprocessor —**.

Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Szablony tekstowe T4 czasu projektowania

Szablony czasu projektowania zdefiniuj częścią kodu źródłowego i innych zasobów aplikacji. Zazwyczaj przy użyciu kilku szablonów, które odczytywanie danych w jednym pliku wejściowego lub bazy danych, a niektóre Generowanie Twojej *.cs*, *.vb*, lub innych plików źródłowych. Każdy szablon generuje jeden plik. Są one wykonywane w programie Visual Studio lub MSBuild.

Na przykład dane wejściowe mogą być pliku XML konfiguracji danych. Edytowanie pliku XML podczas tworzenia szablonów tekstowych ponownie wygenerować części kodu aplikacji. Jeden z szablonów można podobne do następujących:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

W zależności od wartości w pliku XML, wygenerowany *.cs* pliku będzie podobne do następujących:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Inny przykład wejściowy może być diagram przepływu pracy w działalności biznesowej. Gdy użytkownicy zmieniać ich biznesowego przepływu pracy lub po rozpoczęciu pracy z nowych użytkowników, którzy mają różne przepływu pracy, jest proste można ponownie wygenerować kod, aby pomieścić nowy model.

Szablony czasu projektowania stał się szybsze i bardziej niezawodny, aby zmienić konfigurację zmiany wymagań. Zwykle dane wejściowe zdefiniowano pod względem wymagań biznesowych, jak pokazano w przykładzie przepływ pracy. Ułatwia to omówiono w nim zmiany z użytkownikami. Szablony czasu projektowania w związku z tym są przydatne narzędzia w procesie elastyczne programowanie.

Aby utworzyć szablon czasu projektowania, Dodaj **szablonu tekstowego** plik do projektu. Alternatywnie możesz dodać plik tekstowy i ustawić jej **narzędzie niestandardowe** właściwości **texttemplatingfilegenerator —**.

Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Termin *modelu* jest czasami używana do opisu danych odczytywane przez jeden lub więcej szablonów. Model może być w dowolnym formacie, w dowolny plik lub bazy danych. Nie ma być modelu UML lub model języka specyficznego dla domeny. "Modelu" tylko wskazuje, czy dane można zdefiniować w kategoriach koncepcje biznesowe, a nie podobny kod.

Nosi nazwę funkcji transformacji szablonu tekstowego *T4*.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
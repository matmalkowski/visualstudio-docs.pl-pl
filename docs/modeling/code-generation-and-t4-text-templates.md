---
title: Generowanie kodu i szablony tekstowe T4 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-techdebt
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: "82"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 60840f3d47b43ea84bec66ea7957f613d2379901
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="code-generation-and-t4-text-templates"></a>Generowanie kodu i szablony tekstowe T4
W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *szablonu tekstowego T4* jest mieszaniną bloki tekstu i logiki kontroli, które można wygenerować pliku tekstowego. Logika kontroli są zapisywane jako fragmenty kodu programu w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. W programie Visual Studio 2015 Update 2 lub nowszy można użyć funkcji w wersji 6.0 C# w dyrektywach szablony T4. Wygenerowany plik może być tekst dowolnego rodzaju, takich jak strony sieci Web lub plik zasobu lub kodu źródłowego program w dowolnym języku.  
  
 Istnieją dwa rodzaje szablonów tekstowych T4:  
  
 **Uruchom szablonów tekstowych T4 czasu** ("wstępnie przetworzony" Szablony) są wykonywane w aplikacji do tworzenia ciągów tekstowych, zazwyczaj jako część dane wyjściowe.  
 Na przykład można utworzyć szablonu, aby zdefiniować strony HTML:  
  
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
  
 Aplikację można uruchomić na komputerze, na którym nie ma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zainstalowane.  
  
 Aby utworzyć szablon czasu wykonywania, Dodaj **szablonu tekstowego preprocesora** plik do projektu. Alternatywnie możesz dodać plik tekstowy i ustawić jej **narzędzie niestandardowe** właściwości **texttemplatingfilepreprocessor —**.  
  
 Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
 **Szablony tekstowe T4 czasu projektowania** są wykonywane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do definiowania częścią kodu źródłowego i innych zasobów aplikacji.  
 Zwykle będzie przy użyciu kilku szablonów, które odczytywanie danych w jednym pliku wejściowego lub bazy danych, a niektóre Generowanie Twojej `.cs`, `.vb`, lub innych plików źródłowych. Każdy szablon generuje jeden plik. Są one wykonywane w ramach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Na przykład dane wejściowe mogą być pliku XML konfiguracji danych. Edytowanie pliku XML podczas tworzenia szablonów tekstowych będzie ponownie wygenerować części kodu aplikacji. Jeden z szablonów można podobne do następujących:  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 Zależne od wartości w pliku XML, wygenerowany `.cs` pliku będzie podobne do następujących:  
  
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
>  Termin *modelu* jest czasami używana do opisu danych odczytywane przez jeden lub więcej szablonów. Model może być w dowolnym formacie, w dowolny plik lub bazy danych. Nie ma być modelu UML lub model języka specyficznego dla domeny. "Modelu" tylko wskazuje, czy dane można zdefiniować w kategoriach koncepcje biznesowe, a nie podobny kod.  
  
 Nosi nazwę funkcji transformacji szablonu tekstowego *T4*.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 W dowolnej aplikacji, które generuje pliki tekstowe szablony tekstowe prekompilowany jest łatwy i niezawodny metodą Definiowanie tekstu. Jednak ta metoda nie może służyć do szablonów tekstowych, które zmieniają się w czasie wykonywania.  
  
 [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 Generowanie kodu i innych zasobów na podstawie modelu pozwala zaktualizować aplikacji, aktualizując modelu.  
  
 [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md)  
 Jeśli zainstalowano [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wizualizacji i modelowania zestawu SDK, można zapewnić wygenerowanego oprogramowania będzie zawsze aktualny zmian w modelu.  
  
 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)  
 Składnia pliku szablonu tekstowego.  
  
 [Wskazówki: Generowanie kodu przy użyciu szablonów tekstowych](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Pokaz sposób użycia generowania kodu.  
  
 [Debugowanie szablonu tekstowego T4](../modeling/debugging-a-t4-text-template.md)  
 Jak szablony tekstowe debugowania i typowych błędów szablonu tekstu.  
  
 [Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)  
 Narzędzie wiersza polecenia można użyć do uruchomienia transformacji szablonu tekstowego.  
  
 [Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)  
 Jak napisać procesory dyrektywy i hosty tworzenia szablonów niestandardowych dla źródeł danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
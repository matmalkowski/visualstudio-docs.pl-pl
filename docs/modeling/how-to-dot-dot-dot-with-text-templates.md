---
title: Jak... with szablony tekstowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: "11"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 93b4d129cd09fe3d3b67bfc743286577b1e285dd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="how-to--with-text-templates"></a>How to ... with — Szablony tekstowe
Szablony tekstowe w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wygodny sposób generowania tekstu dowolnego rodzaju. Szablony tekstowe służy do generowania tekstu w czasie wykonywania w ramach aplikacji i w czasie projektowania, aby wygenerować fragmenty kodu projektu. Ten temat zawiera podsumowanie najczęściej zadawane "Jak...?" pytania.  
  
 W tym temacie wielu odpowiedzi, które są poprzedzone punktory są alternatywne sugestie.  
  
 Aby uzyskać ogólne wprowadzenie do szablonów tekstowych, przeczytaj [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>Jak...  
  
### <a name="generate-part-of-my-application-code"></a>Generowanie część mojego kodu aplikacji  
 Mam konfiguracji lub *modelu* w pliku lub bazy danych. Co najmniej jeden części mojego kodu są zależne od tego modelu.  
  
-   Generuj niektóre pliki kodu z szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) i [to najlepszy sposób, aby rozpocząć pisanie szablonu?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generuj pliki w czasie wykonywania, przekazywanie danych do szablonu  
 W czasie wykonywania Moja aplikacja generuje pliki tekstowe, takie jak raporty, zawierające kombinację tekstu standardowego i danych. Chcę uniknąć zapisywania setki `write` instrukcje.  
  
-   Dodawanie szablonu tekstowego środowiska uruchomieniowego do projektu. Ten szablon tworzy klasę w kodzie, w którym można utworzyć wystąpienia i służy do generowania tekstu. Dane można przekazać do niego w parametrach konstruktora. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Jeśli chcesz wygenerować na podstawie szablonów, które są dostępne tylko w czasie wykonywania, można użyć szablonów tekst standardowy. Jeśli piszesz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia, można wywołać usługi tworzenia szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [wywoływanie transformacji tekstu w rozszerzeniu VS](../modeling/invoking-text-transformation-in-a-vs-extension.md). W innych kontekstach można użyć aparatu tworzenia szablonów tekstowych. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.  
  
     Użyj \<#@parameter#> dyrektywy do przekazania parametrów do tych szablonów. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca parametru](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Przeczytaj innego pliku projektu z szablonu  
 Aby odczytać plik z tej samej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu jako szablonu:  
  
-   Wstaw `hostSpecific="true"` do `<#@template#>` dyrektywy.  
  
     W kodzie, użyj `this.Host.ResolvePath(filename)` uzyskanie pełnej ścieżki pliku.  
  
### <a name="invoke-methods-from-a-template"></a>Wywołanie metody z szablonu  
 Jeśli metody już istnieje, na przykład w standardzie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] klasy:  
  
-   Użyj \<#@assembly#> dyrektywy ładowania zestawu, a następnie użyć \<#@import#> można ustawić kontekstu przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca importowania](../modeling/t4-import-directive.md).  
  
     Jeśli często ten sam zestaw zestawu i zaimportować dyrektywy, należy wziąć pod uwagę zapisywania procesora dyrektywy. W szablonie mogą być wywoływane procesora dyrektywy, które można załadować zestawów i plików modelu i Ustaw kontekst przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [tworzenie procesory dyrektywy szablonu niestandardowego T4 tekstu](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 Jeśli piszesz metody samodzielnie:  
  
-   Jeśli piszesz szablonu tekstowego środowiska uruchomieniowego zapisać definicji częściowej klasy, która ma taką samą nazwę jak szablon tekstu czasu wykonywania. Dodaj dodatkowe metody do tej klasy.  
  
-   Zapis kontroli bloku funkcji klasy `<#+ ... #>` , w którym można zadeklarować metody, właściwości i prywatne klasy. Szablon tekstu jest kompilowana, jest on przekształcany do klasy. Bloki formantu standardowego `<#...#>` tekst są przekształcane do pojedynczej metody i klasa funkcji bloki są wstawiane jako osobne elementy członkowskie. Aby uzyskać więcej informacji, zobacz [bloki formantów szablonów tekstowych](../modeling/text-template-control-blocks.md).  
  
     Metody zdefiniowany jako funkcje klasy mogą również obejmować bloki osadzonych tekstu.  
  
     Zaleca się umieszczenie funkcje klasy w osobnym pliku, które można `<#@include#>` do co najmniej jednego pliku szablonu.  
  
-   Zapisywanie metod w osobny zestaw (Biblioteka klas) i skontaktuj się z szablonu. Użyj `<#@assembly#>` dyrektywy można załadować zestawu, a `<#@import#>` można ustawić kontekstu przestrzeni nazw. Należy pamiętać, że aby odbudować zestaw podczas debugowania go, może być konieczne zatrzymać i uruchomić ponownie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [dyrektywy szablonu tekstowego T4](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Generowanie wiele plików z jednego modelu schematu  
 Jeśli pliki są często generowane z modelami, które mają ten sam schemat XML lub bazy danych:  
  
-   Należy rozważyć zapisywania procesora dyrektywy. Umożliwia użycie wielu instrukcji zestawu i zaimportować instrukcje w szablonie z jednej dyrektywy niestandardowych. Procesor dyrektywy można załadować i przeanalizować pliku modelu. Aby uzyskać więcej informacji, zobacz [tworzenie procesory dyrektywy szablonu niestandardowego T4 tekstu](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Generowanie plików na podstawie modelu złożonego  
  
-   Należy rozważyć utworzenie języka specyficznego dla domeny (DSL) do reprezentowania modelu. Dzięki temu znacznie ułatwia pisanie szablonów, ponieważ używają typów i właściwości, które odzwierciedlać nazwy elementów w modelu. Nie masz przeanalizować pliku lub przejdź węzłów XML. Na przykład:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Aby uzyskać więcej informacji, zobacz [wprowadzenie języki specyficzne dla domeny](../modeling/getting-started-with-domain-specific-languages.md) i [generowania kodu języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Pobieranie danych z[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Aby korzystać z usług w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], przez zestaw `hostSpecific` atrybutu i obciążenia `EnvDTE` zestawu. Na przykład:  
  
```csharp  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>Wykonanie szablonów tekstowych w procesie kompilacji  
  
-   Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="more-general-questions"></a>Pytania ogólne  
  
###  <a name="starting"></a>Co to jest najlepszy sposób, aby rozpocząć pisanie szablonu tekstowego?  
  
1.  Zapis określonych przykład wygenerowanego pliku.  
  
2.  Zamień go szablonu tekstowego wstawiając `<#@template #>` dyrektywy oraz dyrektywy i kodu, które są wymagane do załadowania pliku wejściowego lub modelu.  
  
3.  Zastąp stopniowo części pliku wyrażenie i bloków kodu.  
  
### <a name="what-is-a-model"></a>Co to jest "modelu"?  
  
-   Dane wejściowe odczytywane przez szablon. Może to być w pliku lub w bazie danych. Może być XML, lub rysunku programu Visio lub języka specyficznego dla domeny (DSL) lub modelu UML lub może być zwykły tekst. Może być rozmieszczone w wielu plikach. Zazwyczaj więcej niż jeden szablon odczytuje jeden model.  
  
     Możliwa "modelu" jest reprezentuje pewien aspekt firmy bezpośrednio więcej niż program wygenerowanego kodu lub innych plików. Na przykład go może reprezentować plan komunikacji sieci, która będzie nadzorować wygenerowanego oprogramowania.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Co to jest użycie szablonów tekstowych?  
 Zazwyczaj generowania kodu wielu lub innych plików z jednego modelu. Model reprezentuje wymagania bezpośrednio niż wygenerowanego kodu. Pomija szczegółów implementacji, a są zapisywane w postaci wymagania zamiast kodu. Zmiany wymogów — tak jak zwykle - łatwiejsze i bardziej niezawodnie różnych części kodu programu można zaktualizować modelu.  
  
 Generowanie kodu w związku z tym jest przydatnym narzędziem z punktu widzenia elastyczne programowanie metody.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>"Najlepszych praktyk" istnieją dla szablonów tekstowych?  
  
-   Aby uzyskać więcej informacji, zobacz [wytyczne dotyczące szablonów tekstowych T4 zapisu](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>Co to jest "T4"?  
  
-   Inną nazwę dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablonu tekstowe opisane w tym miejscu. Poprzedniej wersji, który nie został opublikowany, został skrót od "Transformacji szablonu tekstowego".

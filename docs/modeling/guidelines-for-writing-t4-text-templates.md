---
title: Zalecenia dotyczące pisania szablonów tekstowych T4
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 65f4ddf71c904bbe2aeecd7f86b339ac752c3698
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Zalecenia dotyczące pisania szablonów tekstowych T4
Tych ogólnych wytycznych mogą być przydatne w przypadku generowania kodu programu lub innych zasobów aplikacji w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Zasady nie zostały ustalone.

## <a name="guidelines-for-design-time-t4-templates"></a>Wytyczne dotyczące szablony T4 czasu projektowania
 Szablony T4 czasu projektowania są szablony, które generują kod w Twojej [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu w czasie projektowania. Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Generowanie zmiennej aspektów aplikacji.
Generowanie kodu jest najbardziej przydatny w przypadku tych aspektów aplikacji, która może ulec zmianie podczas projektu lub zmieni się między różnymi wersjami aplikacji. Oddzielić od więcej niezmiennej aspekty aspektami zmiennej, dzięki czemu można łatwiej ustalić, co ma zostać wygenerowany. Na przykład jeśli aplikacja zawiera witryny sieci Web, oddzielnych standardowej strony obsługująca funkcji z logiki, która definiuje ścieżek nawigacji między stronami do innego.

 Kodowanie zmiennej aspekty w co najmniej jednego modelu źródłowego.
Model jest pliku lub bazy danych, która odczytuje każdego szablonu można uzyskać określonych wartości dla zmiennej części kodu, który ma zostać wygenerowane. Modele może być baz danych, pliki XML własny projekt, diagramy lub języki specyficzne dla domeny. Zazwyczaj jeden model służy do generowania wielu plików w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Każdy plik jest generowany w ramach oddzielnego szablonu.

 Można użyć więcej niż jednego modelu w projekcie. Na przykład można zdefiniować modelu nawigacji między stronami sieci Web i oddzielne modelu dla układu strony.

 Model skupić się na potrzeby i słownictwa użytkowników, a nie na implementacji.
Na przykład w aplikacji witryny sieci Web, można oczekiwać modelu do odwoływania się do strony sieci Web i hiperłącza.

 W idealnym przypadku Wybierz formę prezentacji, która odpowiada rodzaju informacje, który reprezentuje modelu. Na przykład modelu ścieżek nawigacji za pośrednictwem witryny sieci Web może być diagram pola i strzałki.

 Przetestuj wygenerowanego kodu.
Użyj testy ręczne lub automatyczne, aby sprawdzić, czy wynikowy kod działa zgodnie z wymagają użytkowników. Unikaj Generowanie testów z tego samego modelu, z którego jest generowany kod.

 W niektórych przypadkach ogólne testów można wykonać na modelu bezpośrednio. Na przykład można zapisać testu, który zapewnia, że każdej strony w witrynie sieci Web może być osiągnięta poprzez nawigację od innych.

 Zezwalaj na niestandardowego kodu: generowanie klas częściowych.
Zezwala na kod napisany ręcznie dodatkowo do wygenerowanego kodu. Jest to rzadko schemat generowania kodu można było konta dla wszystkich możliwych zmian, które mogą wystąpić. W związku z tym spodziewać do dodania lub zastępowania niektórych wygenerowanego kodu. Materiał wygenerowanych w przypadku języka .NET takich jak [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], dwie strategie są szczególnie przydatne:

-   Wygenerowane klasy powinny być częściowe. Dzięki temu można dodać zawartości do wygenerowanego kodu.

-   Klasy powinny być generowane w parach, jeden dziedziczenie z innych. Klasa podstawowa powinna zawierać wszystkie wygenerowane metody i właściwości, a klasa pochodna powinna zawierać tylko konstruktory. Dzięki temu odręcznego do przesłonięcia żadnej z metod wygenerowanego kodu.

 W innych językach wygenerowany przykład XML, użyj `<#@include#>` dyrektywy dokonanie proste kombinacji odręcznego i generowane zawartości. W bardziej złożonych przypadkach może być konieczne przetwarzanie końcowe krok, który łączy wygenerowanego pliku z plikami odręcznego zapisu.

 Przenieść wspólnej materiałów do plików dołączanych lub szablony czasu wykonywania, aby uniknąć powtarzania podobne bloki tekstu i kodu w różnych szablonach, użyj `<#@ include #>` dyrektywy. Aby uzyskać więcej informacji, zobacz [obejmują dyrektywa T4 dotycząca](../modeling/t4-include-directive.md).

 Można również tworzyć szablony tekstu czasu wykonywania w oddzielny projekt, a następnie wywołać je z szablonu czasu projektowania. Aby to zrobić, użyj `<#@ assembly #>` dyrektywy dostęp do osobnych projektu. Aby uzyskać przykłady, zobacz ["Dziedziczenia w szablonów tekstowych" w blogu Nowak Gareth](http://go.microsoft.com/fwlink/?LinkId=208373).

 Rozważ przeniesienie dużych bloków kodu na osobny zestaw.
 Jeśli masz bloki kodu dużych a funkcji klasy może być przydatne przenieść część ten kod do metody, które kompilacji w oddzielny projekt. Można użyć `<#@ assembly #>` dyrektywy dostęp do kodu w szablonie. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md).

 Możesz też zaznaczyć metody w klasie abstrakcyjnej szablonu może dziedziczyć. Klasa ogólna musi dziedziczyć z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca szablonu](../modeling/t4-template-directive.md).

 Generowanie kodu, nie konfiguracji plików jedną metodę zapisywania zmiennej aplikacji do pisania kodu ogólny program, który akceptuje pliku konfiguracji. Aplikacja napisana w ten sposób są bardzo elastyczne i mogą zostać skonfigurowane ponownie po zmianie wymagań biznesowych, bez ponownie skompilować aplikację. Jednak wadą tego podejścia jest będą wykonywane przez aplikację także mniej niż więcej określonej aplikacji. Ponadto jego kod programu będzie trudniejsze do odczytu i obsługa, częściowo ponieważ zawsze należy uwzględniać typy najbardziej ogólne.

 Z drugiej strony aplikacji, w których części zmiennych są generowane przed kompilacji może być silnie typizowane. Dzięki temu znacznie łatwiejsze i bardziej niezawodny, aby napisać kod odręcznego i zintegrować ją z wygenerowany części oprogramowania.

 Uzyskanie pełnych korzyści z generowania kodu, spróbuj do generowania kodu programu zamiast plików konfiguracyjnych.

 Użyj folderu wygenerowany kod umieść szablonów i wygenerowanych plików w folderze projektu o nazwie **wygenerowany kod**, aby była Wyczyść, że te nie są pliki, które powinny być edytowane bezpośrednio. Jeśli tworzysz niestandardowy kod, aby zastąpić, lub Dodaj do wygenerowane klasy, umieść tych klas w folderze o nazwie **kod niestandardowy**. Struktura typowe projektu wygląda następująco:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs

```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Wytyczne dotyczące szablony T4 (wstępnie przetworzonych) środowiska wykonawczego
 Przenieś wspólnej materiałów do dziedziczonej szablonów można użyć dziedziczenia udostępniać metod i bloki tekstu między szablonów tekstowych T4. Aby uzyskać więcej informacji, zobacz [dyrektywa T4 dotycząca szablonu](../modeling/t4-template-directive.md).

 Umożliwia także zawierać pliki, których szablony czasu wykonywania.

 Przenieś dużych jednostek kodu do klasy częściowej.
Każdy szablon środowiska wykonawczego generuje definicji częściowej klasy, która ma taką samą nazwę jako szablonu. Można zapisać pliku kodu zawierającego innej definicji częściowej tej samej klasy. Do klasy w ten sposób można dodać metody, pól i konstruktorów. Elementy te można wywołać z bloków kodu w szablonie.

 Zaletą w ten sposób jest, że kod jest łatwiejsze do zapisu, ponieważ IntelliSense jest dostępna. Ponadto można osiągnąć lepszą rozdzielenie prezentacji i podstawowej logiki.

 Na przykład w **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 W **MyReportText Methods.cs**:

 `private string ComputeTotal() { ... }`

 Zezwalaj niestandardowego kodu: Podaj punkty rozszerzenia rozważ generowania metody wirtualne w \<#+ klasy funkcja blokuje #>. Dzięki temu jednego szablonu używanego w kontekstach wiele bez żadnych modyfikacji. Modyfikowanie szablonu, a nie można utworzyć klasy pochodnej, która dostarcza minimalna dodatkową logikę. Klasa pochodna może być albo regularne kodu lub może być szablonem czasu wykonywania.

 Na przykład w MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 W kodzie aplikacji:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();

```

## <a name="guidelines-for-all-t4-templates"></a>Wytyczne dotyczące wszystkie szablony T4
 Oddzielne zbieranie danych z generowania tekstu spróbuj unikać mieszanie obliczeń i bloki tekstu. W szablonie tekstu Użyj pierwszego \<kodu # zablokować #> Ustaw zmienne i wykonywać złożonych obliczeń. Z pierwszego bloku tekstu w dół do końca szablon lub pierwszy \<#+ klasy funkcja blokowania #> uniknąć długich wyrażeń i uniknąć pętli i warunków, chyba że zawierają bloki tekstu. Takie rozwiązanie sprawia, że szablon jest łatwiej odczytywać i obsługa.

 Nie używaj `.tt` to pliki z rozszerzeniem różnych nazwa takich jak `.ttinclude` dla plików dołączanych. Użyj `.tt` tylko pliki, które mają być przetwarzane w czasie wykonywania albo czasu projektowania szablonów tekstowych. W niektórych przypadkach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznaje `.tt` pliki i automatycznie ustawia ich właściwości dla przetwarzania.

 Rozpoczęcie każdego szablonu jako stały prototypu.
Zapis przykładowy kod lub tekst, który chcesz wygenerować i upewnij się, że jest poprawny. Następnie zmień jego rozszerzenie .TT — i stopniowo Wstaw kod, który modyfikuje zawartość odczytując modelu.

 Należy rozważyć użycie typu modeli.
Mimo że można utworzyć schematu XML ani bazy danych dla modeli, może być przydatne do tworzenia domeny określonego języka (DSL). DSL ma tę zaletę generuje klasę do reprezentowania każdego węzła w schematu i właściwości do reprezentowania atrybutów. Oznacza to, umieszczonych pod względem modelu biznesowego. Na przykład:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Należy rozważyć użycie diagramy dla modeli.
Wiele modeli najbardziej efektywne są prezentowane i zarządzane jako tabeli tekstu, zwłaszcza, jeśli są one bardzo duże.

 Jednak dla niektórych typów wymagań biznesowych, ważne jest, aby wyjaśnić złożonych zestawów relacje i przepływów pracy i diagramy są najlepiej nadaje się na nośniku. Zaletą diagram jest łatwo omówimy z użytkownikami i inni uczestnicy projektu. Przez generowanie kodu na podstawie modelu na poziomie wymagań biznesowych, wprowadzeniu kodu bardziej elastyczne zmiany wymagań.

 Można również projektować własny typ diagramu jako języka specyficznego dla domeny (DSL). Kod można wygenerować z UML i DSLs. Aby uzyskać więcej informacji, zobacz [analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)

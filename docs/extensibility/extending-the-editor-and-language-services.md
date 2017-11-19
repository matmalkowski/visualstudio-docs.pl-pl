---
title: "Rozszerzanie edytora i usług języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8490ddefaca1d170c1dbf379364cdf91b41b7803
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="extending-the-editor-and-language-services"></a>Rozszerzanie edytora i usług języka
Dodawanie funkcji usługi języka (takie jak IntelliSense) do własnego edytora i rozszerzenia większość funkcji edytora kodu programu Visual Studio.  Aby uzyskać pełną listę można rozszerzyć, zobacz [usługi języka oraz punktów rozszerzenia edytora](../extensibility/language-service-and-editor-extension-points.md).  
  
 Większość funkcji edytora można rozszerzyć za pomocą Framework Managed Extensibility (MEF). Na przykład, jeśli funkcja edytora, aby rozszerzyć kolorowania składni, należy napisać MEF *część* definiuje klasyfikacje, dla których mają różne kolorowanie i sposobu ich obsługi. Edytor obsługuje również wiele rozszerzeń w tej samej funkcji.  
  
 Warstwa prezentacji Edytor bazuje Windows Presentation Framework (WPF). WPF udostępnia bibliotekę grafiki dla elastycznych formatowania tekstu, a także wizualizacje, takie jak grafiki i animacji.  
  
 Visual Studio SDK udostępnia kart znany jako *podkładek* do obsługi VSPackages napisanych dla wcześniejszych wersji. Jeśli masz istniejący pakiet VSPackage, firma Microsoft zaleca jednak zaktualizować go do nowej technologii, aby uzyskać większą wydajność i niezawodność.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wprowadzenie do usługi języka oraz rozszerzenia Edytora](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Wyjaśnia sposób tworzenia rozszerzenia edytora.|  
|[W edytorze](../extensibility/inside-the-editor.md)|Opisuje ogólne strukturę edytora i przedstawia niektóre z jego funkcji.|  
|[Managed Extensibility Framework w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md)|Wyjaśniono, jak Framework Managed Extensibility (MEF) za pomocą edytora.|  
|[Usługa języka i punkty rozszerzenia Edytora](../extensibility/language-service-and-editor-extension-points.md)|Wyświetla listę punktów rozszerzenia edytora. Punkty rozszerzeń reprezentują funkcje edycji, które mogą zostać rozszerzone.|  
|[Wskazówki: Tworzenie ozdób widoku, poleceń i ustawień (prowadnice kolumn)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Przedstawiono oraz wyjaśniono, tworzenie ozdób widoku, który pobiera linie gudie kolumn zabezpieczać kodu do szerokości ekranu.  Przedstawiono również odczytywania i zapisywania ustawień, a także deklarowanie i wykonania polecenia, które można wywołać z okna poleceń.|  
|[Importy edytora](../extensibility/editor-imports.md)|Wyświetla listę usług, które można zaimportować rozszerzenie.|  
|[Adaptacja starszego kodu do edytora](../extensibility/adapting-legacy-code-to-the-editor.md)|Opisano różne sposoby dostosowania starszego kodu (wstępnie Visual Studio 2010) do rozszerzania edytora.|  
|[Migrowanie usługi języka starsza wersja](../extensibility/internals/migrating-a-legacy-language-service.md)|Wyjaśniono, jak przeprowadzić migrację usługi języka na podstawie pakiet VSPackage.|  
|[Wskazówki: Łączenie typu zawartości z rozszerzeniem nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Pokazuje, jak połączyć typu zawartości to rozszerzenie nazwy pliku.|  
|[Wskazówki: Tworzenie symbolu margines](../extensibility/walkthrough-creating-a-margin-glyph.md)|Pokazuje, jak dodać ikony do margines.|  
|[Wskazówki: Wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)|Przedstawia sposób użycia *tagi* do wyróżnianie tekstu.|  
|[Wskazówki: Tworzenie konspektu](../extensibility/walkthrough-outlining.md)|Przedstawiono sposób dodawania zwijania dla określonych rodzajów nawiasów klamrowych.|  
|[Wskazówki: Wyświetlanie pasujących nawiasów klamrowych](../extensibility/walkthrough-displaying-matching-braces.md)|Przedstawia sposób wyróżnianie pasujących nawiasów klamrowych.|  
|[Wskazówki: Wyświetlanie skrócone informacje etykietek narzędzi](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Przedstawia sposób wyświetlania wyskakujące okienka skrócone informacje, które opisano elementy kodu, takie jak właściwości, metod i zdarzeń.|  
|[Wskazówki: Wyświetlanie pomocy podpisu](../extensibility/walkthrough-displaying-signature-help.md)|Przedstawia sposób wyświetlania wyskakujące okienka, które zapewniają informacje o liczbę i typy parametrów w podpisie.|  
|[Wskazówki: Wyświetlanie uzupełniania](../extensibility/walkthrough-displaying-statement-completion.md)|Przedstawia sposób wykonania uzupełniania instrukcji.|  
|[Wskazówki: Wdrażanie wstawki kodu](../extensibility/walkthrough-implementing-code-snippets.md)|Przedstawia sposób wykonania rozszerzenia fragment kodu.|  
|[Wskazówki: Wyświetlanie sugestii żarówka](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Przedstawia sposób wyświetlania żarówki masz sugestie kodu.|  
|[Wskazówki: Korzystanie z polecenia powłoki z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Przedstawia sposób kojarzenie polecenia menu w pakiet VSPackage z składników MEF.|  
|[Wskazówki: Używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Pokazuje, jak do skojarzenia z składników MEF skrót menu w pakiet VSPackage.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Zawiera informacje dotyczące Framework zarządzane rozszerzalności (MEF).|  
|[Program Windows Presentation Foundation](/dotnet/framework/wpf/index)|Zawiera informacje o Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Tematy pomocy  
 Edytor programu Visual Studio zawiera następujące przestrzenie nazw.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>
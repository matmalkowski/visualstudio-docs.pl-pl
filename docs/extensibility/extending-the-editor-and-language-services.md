---
title: Rozszerzanie usług edytora i języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7194b245ad3803112f5596c82308c384840d7bdf
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39637552"
---
# <a name="extend-the-editor-and-language-services"></a>Rozszerzanie usług edytora i języka
Dodawanie funkcji do usługi języka (takie jak IntelliSense) do własnego edytora i rozszerzenia większość funkcji edytora kodu Visual Studio.  Aby uzyskać pełną listę można rozszerzyć, zobacz [punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md).  
  
 Większość funkcji edytora można rozszerzyć za pomocą Managed Extensibility Framework (MEF). Na przykład, jeśli funkcja edytora, aby rozszerzyć kolorowanie składni, należy napisać MEF *część* definiujący klasyfikacje, dla których ma inną kolorowanie i sposobu ich obsługi. Edytor obsługuje również wiele rozszerzeń w tej samej funkcji.  
  
 Warstwa prezentacji edytora bazuje Windows Presentation Framework (WPF). WPF zawiera bibliotekę graficzną elastyczne formatowania tekstu, a także wizualizacji, takich jak grafiki i animacje.  
  
 Visual Studio SDK zawiera kart znanych jako *podkładki* do obsługi pakietów VSPackage, napisanych dla wcześniejszych wersji. Niemniej jednak w przypadku istniejącego pakietu VSPackage, zaleca się zaktualizować go do nowej technologii w celu uzyskania lepszej wydajności i niezawodności.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wprowadzenie do usługi i Edytor rozszerzenia językowe](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Wyjaśnia, jak utworzyć rozszerzenie edytora.|  
|[Wewnątrz edytora](../extensibility/inside-the-editor.md)|W tym artykule opisano ogólną strukturę edytora i wyświetla część jej dostępnych funkcji.|  
|[Managed Extensibility Framework, w edytorze](../extensibility/managed-extensibility-framework-in-the-editor.md)|Wyjaśnia, jak Managed Extensibility Framework (MEF) za pomocą edytora.|  
|[Punkty rozszerzenia usługi oraz edytora języka](../extensibility/language-service-and-editor-extension-points.md)|Wyświetla listę punktów rozszerzenia edytora. Punkty rozszerzenia reprezentują funkcje edytora, które mogą zostać rozszerzone.|  
|[Przewodnik: Tworzenie zakończeń widoku, poleceń i ustawień (prowadnice kolumn)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Przeprowadzi i wyjaśniono tworzenie zakończeń widoku, który Rysuje linie prowadnic kolumny zabezpieczać kodu na szerokość ekranu.  Pokazuje również, odczytywania i zapisywania ustawień, a także deklarowania i wykonania polecenia, które można wywoływać z okna poleceń.|  
|[Importy edytora](../extensibility/editor-imports.md)|Wyświetla listę usług, które można importować rozszerzenia.|  
|[Dostosowanie starszego kodu do edytora](../extensibility/adapting-legacy-code-to-the-editor.md)|W tym artykule wyjaśniono różne sposoby dostosowania starszego kodu (wcześniej Visual Studio 2010) do rozszerzenia edytora.|  
|[Migrowanie starszej wersji usługi językowej](../extensibility/internals/migrating-a-legacy-language-service.md)|Wyjaśnia, jak przeprowadzić migrację usługi językowej na podstawie pakietu VSPackage.|  
|[Wskazówki: Łączenie typu zawartości na rozszerzenie nazwy pliku](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Pokazuje, jak połączyć typu zawartości z rozszerzeniem nazwy pliku.|  
|[Przewodnik: Tworzenie marginesie](../extensibility/walkthrough-creating-a-margin-glyph.md)|Pokazuje, jak dodać ikonę margines.|  
|[Przewodnik: Wyróżnianie tekstu](../extensibility/walkthrough-highlighting-text.md)|Ilustruje sposób używania *tagi* aby wyróżnić tekst.|  
|[Wskazówki: Dodawanie obramowania](../extensibility/walkthrough-outlining.md)|Pokazuje, jak dodać konspekt dla konkretnych rodzajów nawiasów klamrowych.|  
|[Przewodnik: Wyświetlanie parowanych nawiasów klamrowych](../extensibility/walkthrough-displaying-matching-braces.md)|Pokazuje, jak wyróżnianie pasujących nawiasów klamrowych.|  
|[Instruktażu: Etykietek narzędzi Szybkieinfo ekran](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Pokazuje sposób wyświetlania okna podręczne skrócone informacje, które opisują elementy kodu, takie jak właściwości, metody i zdarzenia.|  
|[Przewodnik: Wyświetlanie — pomocy dotyczącej sygnatur](../extensibility/walkthrough-displaying-signature-help.md)|Pokazuje sposób wyświetlania okna podręczne, które zapewniają informacje o liczbę i typy parametrów w podpisie.|  
|[Przewodnik: Wyświetlanie uzupełniania](../extensibility/walkthrough-displaying-statement-completion.md)|Pokazuje, jak zaimplementować uzupełniania instrukcji.|  
|[Wskazówki: Implementowanie wstawki programu](../extensibility/walkthrough-implementing-code-snippets.md)|Pokazuje, jak zaimplementować rozszerzenia fragmentu kodu.|  
|[Przewodnik: Wyświetlanie sugestie z żarówką](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Pokazuje sposób wyświetlania żarówki dla kodu sugestie.|  
|[Przewodnik: Używanie polecenia powłoki z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Pokazuje, jak kojarzenie polecenia menu w VSPackage za pomocą składnika MEF.|  
|[Przewodnik: Używanie klawisza skrótu z rozszerzeniem edytora](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Pokazuje, jak skojarzyć skrótu w menu w VSPackage z składnik MEF.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Zawiera informacje na temat Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Zawiera informacje o Windows Presentation Foundation (WPF).|  
  
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
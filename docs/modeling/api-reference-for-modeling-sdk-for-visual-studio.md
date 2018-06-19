---
title: Odwołania API do modelowania SDK dla Visual Studio
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7db208bf19f0a2433d4c85af7710a0f5ac70562e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947862"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Odwołania API do modelowania SDK dla Visual Studio

Visual Studio wizualizacji i modelowania SDK udostępnia platformy, na którym są wbudowane narzędziami języki specyficzne dla domeny (DSL).

Ta sekcja zawiera materiału odwołania do przestrzeni nazw, które mają nazwy zaczynające się od "Microsoft.VisualStudio.Modeling".

|Przestrzeń nazw|Zawartość|
|---------------|-------------|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|Klasy takie jak element modelu, który jest klasą bazową dla wszystkich klas domeny zdefiniowanych w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|Klasy, które stanowią część definicji DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|Podgląd magazynu i wydajności pomiaru narzędzi modelu.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|Klasy takie jak ShapeElement, które jest klasą bazową dla wszystkich kształtów, które można zdefiniować w DSL.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|Gest i wybór metod.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|Interfejs API definicji DSL projektanta.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|Klasy wewnętrzne definicji DSL projektanta.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|Atrybuty, które umożliwiają rozszerzanie Projektant DSL z poleceniami, gestów i sprawdzania poprawności.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|Metody rozszerzenia dla ModelElement, które implementują rozszerzalności DSL.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|Atrybuty rozszerzalności|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|Umożliwia tworzenie modelu tylko do odczytu.|
|<xref:Microsoft.VisualStudio.Modeling.Integration?displayProperty=fullName>|Modelbus interfejsu API, która ułatwia integrowanie różne modele.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker?displayProperty=fullName>|Okno dialogowe, które umożliwia użytkownikom przechodzenie do modeli i elementów do tworzenia odwołań Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting?displayProperty=fullName>|Usługa selektora.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell?displayProperty=fullName>|Struktura karty Modelbus programu Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Integration.Shell.Picker?displayProperty=fullName>|Okno dialogowe selektora, który umożliwia użytkownikom przechodzenie do modeli i elementów do tworzenia odwołań Modelbus.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Interfejs między DSLs i Visual Studio.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|Umożliwia definiowanie polecenia menu skrótów (context).|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|Umożliwia definiowanie ograniczeń walidacji.|

## <a name="see-also"></a>Zobacz też

- [Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)

---
title: Dyrektywa T4 Output
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6044dd970029b3f233f8b20eb2e334b5041ceb33
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="t4-output-directive"></a>Dyrektywa T4 Output

W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablony tekstowe `output` dyrektywa jest używane do definiowania rozszerzenie nazwy pliku i kodowanie pliku po przekształceniu.

 Na przykład jeśli Twoje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt zawiera plik szablonu o nazwie **MyTemplate.tt** zawierającą następujące dyrektywy:

 `<#@output extension=".cs"#>`

 następnie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wygeneruje plik o nazwie **MyTemplate.cs**

 `output` Dyrektywy nie jest wymagane w szablonie (wstępnie przetworzonych) tekstu czasu wykonywania. Zamiast tego aplikacja uzyskuje wygenerowany ciąg przez wywołanie metody `TextTransform()`. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania z szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Użycie dyrektywy danych wyjściowych

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Nie powinna istnieć co najwyżej jeden `output` dyrektywy w szablonie tekstu.

## <a name="extension-attribute"></a>Atrybut rozszerzenia
 Określa rozszerzenie nazwy pliku wyjściowego pliku wygenerowanego tekstu.

 Wartość domyślna to **.cs**

 Przykłady: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Dopuszczalne wartości: Wszystkie prawidłowe rozszerzenie nazwy pliku.

## <a name="encoding-attribute"></a>Atrybut kodowania
 Określa kodowanie do użycia podczas generowania pliku wyjściowego. Na przykład:

 `<#@ output encoding="utf-8"#>`

 Wartość domyślna to kodowanie używane przez plik szablonu tekstu.

 Dopuszczalne wartości: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Domyślny)

 Ogólnie rzecz biorąc, można użyć ciągu nazwasieciweb lub numer strony kodowej dowolnego kodowań zwrócony przez <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
---
title: T4 Output dyrektywy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: "4"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: bf96406356799a0953ee34eb736266267fe74510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
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
  
 Przykłady:  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Dopuszczalne wartości:  
 Wszystkie nieprawidłowe rozszerzenie nazwy pliku.  
  
## <a name="encoding-attribute"></a>Atrybut kodowania  
 Określa kodowanie do użycia podczas generowania pliku wyjściowego. Na przykład:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Wartość domyślna to kodowanie używane przez plik szablonu tekstu.  
  
 Dopuszczalne wartości:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0`(Domyślny)  
  
 Ogólnie rzecz biorąc, można użyć ciągu nazwasieciweb lub numer strony kodowej dowolnego kodowań zwrócony przez <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
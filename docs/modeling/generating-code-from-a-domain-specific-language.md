---
title: Generowanie kodu z języka specyficznego dla domeny | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 37dd84cbe3c2c665ce788218c5b802a4a2c05ff3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generowanie kodu z języka specyficznego dla domeny
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] udostępnia zaawansowane metody do generowania kodu, dokumentów, plików konfiguracji i pozostałych artefaktów z dane reprezentowane w modelach. Przy użyciu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], można utworzyć zestaw klas, które reprezentują dane, można napisać szablony tekstu w klasach których nazwy i właściwości odzwierciedlenia tych danych.  
  
 Na przykład firma Fabrikam ma pliku XML nazwy klientów i adresów e-mail. Deweloperów, tworzenie modelu, w którym klient jest klasę o nazwie właściwości i wiadomości e-mail. Zapisują kilka szablonów tekstowych do przetwarzania danych, w tym ten fragment tworzący spis wszystkich klientów jako część strony HTML:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Podczas przetwarzania bazy danych klienta, plik XML jest do odczytu do magazynu modeli. A *procesora dyrektywy*, utworzony przy użyciu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], udostępnia klasy klienta do kodu w szablonie tekstu. Wiele szablonów tekstowych mogą być uruchamiane na tym samym magazynie.  
  
 Szablony tekstowe są istotne dla [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Są one używane do generowania kodu źródłowego dla elementów modelu domeny, jak również pakiet VSPackage i kontrolek, które są używane do integrowanie narzędzi z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 W tej sekcji omówiono niektóre sposoby tworzenia, modyfikacji i szablony tekstowe używane w debugowania [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Uzyskiwanie dostępu do modeli z poziomu szablonów tekstu](../modeling/accessing-models-from-text-templates.md)  
  
 Zawiera podstawowe informacje o odwołujących się do języka specyficznego dla domeny w szablonach tekstowych.  
  
 [Przewodnik: Debugowanie szablonu tekstowego uzyskującego dostęp do modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Opisuje sposób rozwiązywania problemów i debugowanie szablonu tekstowego, która odwołuje się do języka specyficznego dla domeny.  
  
 [Przewodnik: Łączenie hosta z generowanym procesorem dyrektywy](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Opisano sposób podłączania hosta niestandardowego procesora dyrektywy wygenerowany.  
  
 [Polecenie DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 W tym artykule opisano pliku polecenia, która wykonuje TextTransform plik wykonywalny w wierszu polecenia dla szablonów tekstowych, które odwołują się języki specyficzne dla domeny.  
  
## <a name="reference"></a>Tematy pomocy  
 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)  
  
 Udostępnia składni dyrektywy szablonu tekstu i bloków sterowania.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Opisano proces transformacji szablonu tekstowego.  
  
 [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md)  
  
 Przeczytaj ten temat, jeśli pliki są Generowanie na podstawie DSL na serwerze kompilacji.
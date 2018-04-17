---
title: Zabezpieczenia szablonów tekstowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4acbe40d7229551e32f60d1503864b21840655be
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="security-of-text-templates"></a>Zabezpieczenia szablonów tekstowych
Szablony tekstowe są następujące problemy z zabezpieczeniami:  
  
-   Szablony tekstowe są narażone na dowolny kod wstawienia.  
  
-   Jeśli ten mechanizm, który korzysta z hosta można znaleźć procesora dyrektywy nie jest bezpieczne, może uruchomić złośliwe procesora dyrektywy.  
  
## <a name="arbitrary-code"></a>Dowolny kod  
 Podczas pisania szablonu można umieścić dowolny kod w \<## > tagów. Dzięki temu dowolny kod do wykonania z szablonu jako tekst.  
  
 Upewnij się, że możesz uzyskać szablony z zaufanych źródeł. Upewnij się ostrzec użytkowników końcowych w aplikacji nie można wykonać szablonów, które nie pochodzą z zaufanego źródła.  
  
## <a name="malicious-directive-processor"></a>Złośliwe procesora dyrektywy  
 Aparat szablonów tekstowych współdziała z hostem transformacji i co najmniej jeden procesor dyrektywy do przekształcania tekstu szablon do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [proces transformacji szablonu tekstowego](../modeling/the-text-template-transformation-process.md).  
  
 Jeśli ten mechanizm, który korzysta z hosta można znaleźć procesora dyrektywy nie jest bezpieczne, uruchamia ryzyko uruchomienia złośliwego procesora dyrektywy. Złośliwe procesora dyrektywy można podać kod, który jest uruchamiany w `FullTrust` tryb po uruchomieniu tego szablonu. W przypadku utworzenia niestandardowego hosta szablonu tekstowego przekształcania, należy użyć mechanizm bezpiecznego, takich jak rejestru dla aparatu zlokalizować procesory dyrektywy.
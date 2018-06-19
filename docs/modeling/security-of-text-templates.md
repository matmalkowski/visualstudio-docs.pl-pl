---
title: Zabezpieczenia szablonów tekstowych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71052a0d4120a74269f2aa05412230284271e574
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947524"
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
---
title: Ustawienia wykresu kaskadowego | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9265fd0ada4f966f5d5fba01591e10f5f0a4194f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="settings-waterfall"></a>Ustawienia wykresu kaskadowego

Pojęcie wykresu kaskadowego ustawienia oznacza, że użytkownik może określić ustawienia na **zestawu**, **osprzętu** i **eksploracji** poziomu: 

* Zestaw - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Osprzętu - [PexClass](attribute-glossary.md#pexclass)
* Eksploracja - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Ustawienia określone w **zestawu** poziom wpłynie na wszystkie instalacje i eksploracja w tym zestawie. Ustawienia określone w **osprzętu** poziom wpłynie na wszystkie eksploracji pod tym osprzętu. Win ustawienia podrzędne: Jeśli to ustawienie nie jest zdefiniowany **zestawu** i **osprzętu** poziomy, **osprzętu** ustawienia będą stosowane.

Należy pamiętać, że niektóre ustawienia są specyficzne dla **zestawu** poziom lub **osprzętu** poziom. 

**Przykład**

```
using Microsoft.Pex.Framework;

[assembly: PexAssemblySettings(MaxBranches = 1000)] // we override the default value of maxbranches

namespace MyTests
{
    [PexClass(MaxBranches = 500)] // we override the 1000 value and set maxbranches to 500 
    public partial class MyTests
    {
        [PexMethod(MaxBranches = 100)] // we override again, maxbranches = 100
        public void MyTest(...) { ... }
    }
}
```

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

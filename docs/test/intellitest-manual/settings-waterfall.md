---
title: "Ustawienia wykresu kaskadowego | Narzędzie Test Microsoft IntelliTest dewelopera | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Settings waterfall
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: b782987dd3bf1b96c063d43d80634289e5165af7
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
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

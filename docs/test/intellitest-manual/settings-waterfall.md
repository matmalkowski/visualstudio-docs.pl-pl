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
ms.assetid: 45777037-9E16-4ABF-BD26-5AF4E740D4E6
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: fda01f53c02c0de03e69b65287dd627bf4a786e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
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

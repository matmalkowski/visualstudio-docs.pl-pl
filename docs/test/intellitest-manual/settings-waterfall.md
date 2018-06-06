---
title: Ustawienia wykresu kaskadowego | Narzędzie Test Microsoft IntelliTest Developer
ms.date: 05/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Settings waterfall
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ec6364b3d130ab3ca333838c7e1b6eb2fdcb4a3d
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815054"
---
# <a name="settings-waterfall"></a>Kaskadowy model ustawień

Pojęcie wykresu kaskadowego ustawienia oznacza, że użytkownik może określić ustawienia na **zestawu**, **osprzętu**, i **eksploracji** poziomu:

* Zestaw - [PexAssemblySettings](attribute-glossary.md#pexassemblysettings)
* Osprzętu - [PexClass](attribute-glossary.md#pexclass)
* Eksploracja - [PexExplorationAttributeBase](attribute-glossary.md#pexexplorationattributebase)

Ustawienia określone w **zestawu** poziom wpływają na wszystkie instalacje i eksploracja w tym zestawie. Ustawienia określone w **osprzętu** poziom wpływają na wszystkie eksploracji pod tym osprzętu. Win ustawienia podrzędnych&mdash;Jeśli to ustawienie nie jest zdefiniowany **zestawu** i **osprzętu** poziomy, **osprzętu** ustawienia są używane.

Należy pamiętać, że niektóre ustawienia są specyficzne dla **zestawu** poziom lub **osprzętu** poziom.

**Przykład**

```csharp
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

Publikowania własnych pomysłów i funkcji żądań na [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest).

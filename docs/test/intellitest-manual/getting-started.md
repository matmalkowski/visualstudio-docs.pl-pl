---
title: "Tworzenie testu jednostkowego klas zastępczych metody przy użyciu polecenia Utwórz testy jednostkowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IntelliTest, Get started
ms.assetid: 21FE4D68-9E7F-4BB1-BD69-B0D09A941F09
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.openlocfilehash: e89b6d8860e0964eacb9d58f6d92c64cc661afa0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="get-started-with-microsoft-intellitest"></a>Rozpoczynanie pracy z Microsoft IntelliTest

* Jeśli jest to pierwsza z IntelliTest:
  * Obejrzyj [wideo z witryny Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * Przeczytaj [zapoznać się z MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * Przeczytaj nasze [dokumentacji](https://docs.microsoft.com/en-gb/visualstudio/test/generate-unit-tests-for-your-code-with-intellitest)
* Pytania na [stackoverflow](http://stackoverflow.com/questions/tagged/intellitest)
* Czytać dalszej części tego podręcznika
* Wydrukowanie tej strony, aby zapewnić szybkie odwołanie

<a name="important-attributes"></a>
## <a name="important-attributes"></a>Ważnych atrybutów

* [PexClass](attribute-glossary.md#pexclass) oznacza zawierający typ **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) znaczniki **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) oznacza parametr inną niż null 

```
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest) wiąże projekt testowy do projektu
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute) określa zestaw do dokumentu

```
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

<a name="helper-classes"></a>
## <a name="important-static-helper-classes"></a>Ważne pomocnika statycznych klas

* [PexAssume](static-helper-classes.md#pexassume) ocenia założenia (filtrowanie wejściowych)
* [PexAssert](static-helper-classes.md#pexassert) ocenia potwierdzeń
* [PexChoose](static-helper-classes.md#pexchoose) generuje nowe opcje (dodatkowe dane wejściowe)
* [PexObserve](static-helper-classes.md#pexobserve) zaloguje się na żywo wartości wygenerowane testy

```
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="got-feedback"></a>Masz opinię?

Publikowania własnych pomysłów i funkcji żądań na  **[UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest)**.

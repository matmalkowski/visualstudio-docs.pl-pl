---
title: "Tworzenie testu jednostkowego klas zastępczych metody przy użyciu polecenia Utwórz testy jednostkowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9016006f9774c4a9eff2937f32543b9f8d9f5fb8
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="get-started-with-microsoft-intellitest"></a>Rozpoczynanie pracy z Microsoft IntelliTest

* Jeśli jest to pierwsza z IntelliTest:
  * Obejrzyj [wideo z witryny Channel 9](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Intellitest)
  * Przeczytaj [zapoznać się z MSDN Magazine](https://msdn.microsoft.com/magazine/dn904672.aspx)
  * Przeczytaj nasze [dokumentacji](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
* Pytania na [przepełnienie stosu](http://stackoverflow.com/questions/tagged/intellitest)
* Czytać dalszej części tego podręcznika
* Wydrukowanie tej strony, aby zapewnić szybkie odwołanie

## <a name="important-attributes"></a>Ważnych atrybutów

* [PexClass](attribute-glossary.md#pexclass) oznacza zawierający typ **PUT**
* [PexMethod](attribute-glossary.md#pexmethod) znaczniki **PUT**
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull) oznacza parametr inną niż null

```csharp
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

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="helper-classes"></a>Ważne pomocnika statycznych klas

* [PexAssume](static-helper-classes.md#pexassume) ocenia założenia (filtrowanie wejściowych)
* [PexAssert](static-helper-classes.md#pexassert) ocenia potwierdzeń
* [PexChoose](static-helper-classes.md#pexchoose) generuje nowe opcje (dodatkowe dane wejściowe)
* [PexObserve](static-helper-classes.md#pexobserve) zaloguje się na żywo wartości wygenerowane testy

```csharp
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

Publikowania własnych pomysłów i funkcji żądań na [UserVoice](https://visualstudio.uservoice.com/forums/121579-visual-studio-2015/category/157869-test-tools?query=IntelliTest).

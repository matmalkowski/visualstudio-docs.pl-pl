---
title: "Tworzenie testu jednostkowego klas zastępczych metody przy użyciu polecenia Utwórz testy jednostkowe | Dokumentacja firmy Microsoft"
ms.date: 05/02/2017
ms.technology: vs-ide-test
ms.topic: article
helpviewer_keywords:
- IntelliTest, Get started
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: e68235aef04328c637ca12d9dd77cf6176d27669
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2018
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

## <a name="helper-classes"></a> Ważne pomocnika statycznych klas

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

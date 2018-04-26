---
title: Generowanie plików za pomocą narzędzia TextTransform w programie Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 152f8d656bf83a6ad46770e695cd64c508dcc3bb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generowanie plików za pomocą narzędzia TextTransform

TextTransform.exe jest narzędziem wiersza polecenia, które służy do transformacji szablonu tekstowego. Podczas wywoływania TextTransform.exe, należy określić nazwę pliku tekstowego z szablonu jako argumentem. TextTransform.exe wywołuje aparat przekształcania tekstu i przetwarza szablonu tekstowego. TextTransform.exe jest zazwyczaj wywoływana przez skrypty. Jednak nie jest zwykle wymagane, ponieważ można dokonać transformacji tekstu, w programie Visual Studio lub w procesie kompilacji.

> [!NOTE]
> Jeśli chcesz wykonać transformacji tekstu jako część procesu kompilacji, należy rozważyć użycie zadanie transformacji tekstu programu MSBuild. Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md). Na maszynie, na którym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowana, można również napisać aplikację lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozszerzenia, które można przekształcać szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe znajduje się w następującym katalogu:

 **\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional Edition lub

 **\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 Enterprise Edition.

W poprzednich wersjach programu Visual Studio plik znajduje się w następującej lokalizacji:

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

{gdzie wersja} zależy od poprzedniej wersji zainstalowanego.

## <a name="syntax"></a>Składnia

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|------------------|---------------------|
|`templateName`|Określa nazwę pliku szablonu, którego chcesz transformacji.|

|**Opcja**|**Opis**|
|----------------|---------------------|
|**-out** \<nazwa pliku >|Plik, do którego dane wyjściowe przekształcenia są zapisywane.|
|**-r** \<zestawu >|Zestaw używany do kompilowania i uruchamiania szablonu tekstowego.|
|**-u** \<przestrzeń nazw >|Przestrzeń nazw, która jest używana do kompilowania szablonu.|
|**-** \<Includedirectory >|Katalog, który zawiera szablony tekstowe zawarte w szablonie określony tekst.|
|**-P** \<referencepath >|Katalog, aby wyszukać określony w ramach szablonu tekstowego zestawów lub przy użyciu **- r** opcji.<br /><br /> Na przykład aby uwzględnić zestawy używane dla interfejsu API programu Visual Studio, należy użyć<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Nazwa, pełna nazwa typu i zestawu procesora dyrektywy, który może służyć do przetwarzania dyrektywy niestandardowe w szablonie tekstu.|
|**-** [processorName]! [directiveName]! \<parameterName >! \<parameterValue >|Określ wartość parametru dla procesora dyrektywy. Jeśli określisz tylko nazwa parametru i wartość parametru będzie dostępne dla wszystkich procesorów dyrektywy. Jeśli określisz procesora dyrektywy parametr jest dostępne tylko do określonego procesora. Jeśli określisz nazwy dyrektywy parametr jest dostępna tylko wtedy, gdy określony dyrektywa jest przetwarzana.<br /><br /> Aby uzyskać dostęp do wartości parametrów z procesora dyrektywy lub szablonu tekstowego, należy użyć [ITextTemplatingEngineHost.ResolveParameterValue](https://msdn.microsoft.com/library/microsoft.visualstudio.texttemplating.itexttemplatingenginehost.resolveparametervalue.aspx). W szablonie tekst obejmują `hostspecific` w dyrektywie template i wywoływać wiadomości na `this.Host`. Na przykład:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zawsze wpisz '!' znaków, nawet jeśli pominięto opcjonalne procesora i nazwy dyrektywy. Na przykład:<br /><br /> `-a !!param!value`|
|**-h**|Zawiera Pomoc.|

## <a name="related-topics"></a>Tematy pokrewne

|Zadanie|Temat|
|----------|-----------|
|Generowanie plików w rozwiązaniu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Zapis procesory dyrektywy do przekształcania źródeł danych.|[Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)|
|Pisanie tekstu hosta tworzenia szablonów, który pozwala wywoływać szablony tekstowe z własnej aplikacji.|[Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)|
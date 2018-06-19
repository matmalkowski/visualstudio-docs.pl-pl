---
title: Funkcje wstawek kodu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ead5a3f15f5ba7f586c9dfcec86fb309cbda391f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917969"
---
# <a name="code-snippet-functions"></a>Funkcje wstawek kodu

Istnieją trzy funkcje dostępne w programie wstawki kodu C#. Funkcje są określone w [funkcja](../ide/code-snippets-schema-reference.md#function) element fragmentu kodu. Aby uzyskać informacje na temat tworzenia wstawki kodu, zobacz [wstawki kodu](../ide/code-snippets.md).

## <a name="functions"></a>Funkcje

W poniższej tabeli opisano funkcje dostępne w `Function` element wstawki kodu.

|Funkcja|Opis|Język|
|--------------|-----------------|--------------|
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Generuje instrukcji switch i zestaw instrukcji case w elementach członkowskich wyliczenie określony przez `EnumerationLiteral` parametru. `EnumerationLiteral` Parametr musi być odwołaniem do literału wyliczenia lub typu wyliczeniowego.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|
|`ClassName()`|Zwraca nazwę klasy, która zawiera wstawiony fragment kodu.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|
|`SimpleTypeName(` `TypeName` `)`|Zmniejsza *TypeName* parametr do swojej najprostszej formie, w tym kontekście, w którym wywołano fragment kodu.|[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]|

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie `GenerateSwitchCases` funkcji. Gdy ta Wstawka kodu zostanie wstawiony i wyliczenia jest wprowadzany do `$switch_on$` literału, `$cases$` generuje literał `case` instrukcji dla każdej wartości w wyliczeniu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>switch</Title>
            <Shortcut>switch</Shortcut>
            <Description>Code snippet for switch statement</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>expression</ID>
                    <ToolTip>Expression to switch on</ToolTip>
                    <Default>switch_on</Default>
                </Literal>
                <Literal Editable="false">
                    <ID>cases</ID>
                    <Function>GenerateSwitchCases($expression$)</Function>
                    <Default>default:</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    switch ($expression$)
                    {
                        $cases$
                    }
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie `ClassName` funkcji. Po wstawieniu ta Wstawka kodu `$classname$` literał jest zastępowany nazwę otaczającej klasy w tej lokalizacji w pliku kodu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Common constructor pattern</Title>
            <Shortcut>ctor</Shortcut>
            <Description>Code Snippet for a constructor</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal>
                    <ID>type</ID>
                    <Default>int</Default>
                </Literal>
                <Literal>
                    <ID>name</ID>
                    <Default>field</Default>
                </Literal>
                <Literal default="true" Editable="false">
                    <ID>classname</ID>
                    <ToolTip>Class name</ToolTip>
                    <Function>ClassName()</Function>
                    <Default>ClassNamePlaceholder</Default>
                </Literal>
            </Declarations>
            <Code Language="csharp" Format="CData">
                <![CDATA[
                    public $classname$ ($type$ $name$)
                    {
                        this._$name$ = $name$;
                    }
                    private $type$ _$name$;
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób użycia `SimpleTypeName` funkcji. Gdy ta Wstawka kodu zostaną wstawione do pliku kodu `$SystemConsole$` literał zostanie zastąpiony najprostsza forma <xref:System.Console> typu w tym kontekście, w którym wywołano fragment kodu.

```xml
<CodeSnippets xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">
    <CodeSnippet Format="1.0.0">
        <Header>
            <Title>Console_WriteLine</Title>
            <Shortcut>cw</Shortcut>
            <Description>Code snippet for Console.WriteLine</Description>
            <Author>Microsoft Corporation</Author>
            <SnippetTypes>
                <SnippetType>Expansion</SnippetType>
            </SnippetTypes>
        </Header>
        <Snippet>
            <Declarations>
                <Literal Editable="false">
                    <ID>SystemConsole</ID>
                    <Function>SimpleTypeName(global::System.Console)</Function>
                </Literal>
            </Declarations>
            <Code Language="csharp">
                <![CDATA[
                    $SystemConsole$.WriteLine();
                ]]>
            </Code>
        </Snippet>
    </CodeSnippet>
</CodeSnippets>
```

## <a name="see-also"></a>Zobacz także

- [Element — funkcja](../ide/code-snippets-schema-reference.md#function)
- [Odwołanie do schematu wstawki kodu](../ide/code-snippets-schema-reference.md)

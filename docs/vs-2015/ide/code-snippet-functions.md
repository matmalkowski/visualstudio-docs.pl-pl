---
title: Funkcje wstawek kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets [Visual Studio], functions
- snippets [Visual Studio], functions
- IntelliSense code snippets, functions
ms.assetid: c0a2bf21-8fa5-4457-9281-f599beb53e7d
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8e5009a2fcdcc9c3b94417a296bae5e0f88acf83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678936"
---
# <a name="code-snippet-functions"></a>Funkcje wstawek kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [funkcje wstawek kodu](https://docs.microsoft.com/visualstudio/ide/code-snippet-functions).  
  
Istnieją trzy funkcje dostępne do użycia z [!INCLUDE[csprcs](../includes/csprcs-md.md)] fragmenty kodu. Funkcje są określone w [funkcja](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df) element fragmentu kodu. Aby uzyskać informacje na temat tworzenia fragmenty kodu, zobacz [fragmenty kodu](../ide/code-snippets.md).  
  
## <a name="functions"></a>Funkcje  
 W poniższej tabeli opisano funkcje dostępne w połączeniu z `Function` element fragmentów kodu.  
  
|Funkcja|Opis|Język|  
|--------------|-----------------|--------------|  
|`GenerateSwitchCases(` `EnumerationLiteral` `)`|Generuje instrukcję switch i zestaw instrukcji case dla elementów członkowskich wyliczenia określony przez `EnumerationLiteral` parametru. `EnumerationLiteral` Parametr musi być odwołaniem do wyliczenia literału lub typ wyliczenia.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`ClassName()`|Zwraca nazwę klasy, która zawiera wstawiono fragment kodu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
|`SimpleTypeName(` `TypeName` `)`|Zmniejsza *TypeName* parametr najprostszej postaci w kontekście, w której wywołano fragmentu kodu.|[!INCLUDE[csprcs](../includes/csprcs-md.md)]|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać `GenerateSwitchCases` funkcji. Po wstawieniu ten fragment kodu i wyliczenia jest zawierana `$switch_on$` literału, `$cases$` generuje literał `case` poufności informacji dla każdej wartości w wyliczeniu.  
  
```  
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
 Poniższy przykład pokazuje, jak używać `ClassName` funkcji. Podczas wstawiania tego fragmentu kodu `$classname$` literał jest zastępowana nazwą otaczającej klasy w tej lokalizacji w pliku kodu.  
  
```  
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
            <Code Language="vjsharp" Format="CData">  
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
 W tym przykładzie pokazano, jak używać `SimpleTypeName` funkcji. Gdy ten fragment kodu jest wstawiany do pliku z kodem `$SystemConsole$` literał zostanie zastąpiony najprostsza forma <xref:System.Console> typu w kontekście, w której wywołano fragment kodu.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Function — Element (fragmenty kodu Intellisense)](http://msdn.microsoft.com/en-us/572c5549-5821-4e15-8ecd-0fa86c1c65df)   
 [Fragmenty kodu — informacje o schemacie](../ide/code-snippets-schema-reference.md)




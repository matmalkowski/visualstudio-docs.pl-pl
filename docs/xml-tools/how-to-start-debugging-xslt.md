---
title: 'Porady: Uruchom profilowanie XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: b348cd1dc4327954d67c3a3f77a88da3c43c7935
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-start-debugging-xslt"></a>Porady: Uruchom profilowanie XSLT

Debuger XSLT może być używana do debugowania arkusz stylów XSLT lub aplikacji XSLT. Podczas debugowania, można wykonywać jeden wiersz kodu w czasie, Wkraczanie do, pominięcie lub wykonywanie krok po kroku z kodu. Polecenia, aby korzystać z funkcji krokowe wykonywanie kodu są takie same dla debuger XSLT, podobnie jak w przypadku programu Visual Studio debuger. Po rozpoczęciu debugowania, debuger XSLT otwiera systemu windows do pokazania wyjściowe dokument wejściowy i XSLT.

## <a name="xml-editor"></a>Edytor XML

Można uruchomić debugera w edytorze XML. Dzięki temu można debugować jako projektowania arkusza stylów.

### <a name="to-start-debugging-from-a-style-sheet"></a>Aby rozpocząć debugowanie z arkusza stylów

1. Otwórz arkusz stylów w edytorze XML.

1. Wybierz **debugowania XSL** z **XML** menu.

### <a name="to-start-debugging-from-an-xml-input-document"></a>Aby rozpocząć debugowanie z wejściowy dokument XML

1. Otwórz dokument XML w edytorze XML.

1. Wybierz **debugowania XSL** z **XML** menu.

## <a name="xslt-from-other-languages"></a>XSLT z innych języków

Można także przejść do XSLT podczas debugowania aplikacji. Po naciśnięciu F11 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> wywołanie, debuger może wykonywanie kodu XSLT.

> [!NOTE]
> Wykonywanie krok po kroku do XSLT z <xref:System.Xml.Xsl.XslTransform> klasa nie jest obsługiwana. <xref:System.Xml.Xsl.XslCompiledTransform> Klasy jest tylko procesorze XSLT, który obsługuje wykonywanie krok po kroku do XSLT podczas debugowania.

### <a name="to-start-debugging-an-xslt-application"></a>Aby rozpocząć debugowanie aplikacji XSLT

1. Podczas tworzenia wystąpienia <xref:System.Xml.Xsl.XslCompiledTransform> obiekt, ustaw `enableDebug` parametr `true` w kodzie.

     Ta wartość informuje procesorze XSLT można utworzyć informacji o debugowaniu podczas kompilowania kodu.

1. Naciśnij klawisz F11, aby wkraczać do kod XSLT.

     Arkusz stylów XSLT jest ładowany w nowym oknie dokumentu i debuger XSLT jest uruchomiona.

     Można również dodać punkt przerwania do arkusza stylów i uruchom aplikację.

### <a name="example"></a>Przykład

Oto przykład programu w języku C# XSLT. Widoczny jest sposób włączyć debugowanie XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Debugowanie arkusza stylów XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
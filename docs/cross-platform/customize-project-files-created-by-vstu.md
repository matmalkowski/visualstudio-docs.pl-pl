---
title: "Dostosowywanie plików projektu utworzonych za pomocą rozszerzenia VSTU | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-unity-tools
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d051210849f33794ace3aba9786bab3c0156fa74
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych za pomocą rozszerzenia VSTU
Visual Studio Tools for Unity zawiera wywołanie zwrotne stylu platformy Unity podczas generowania pliku projektu. Zarejestruj `VisualStudioIntegration.ProjectFileGeneration` zdarzeń do zmodyfikowania pliku projektu, gdy zostanie ponownie wygenerowany.

## <a name="demonstrates"></a>Demonstracje
 Jak dostosowywać pliki projektu programu Visual Studio, generowane przez Visual Studio Tools for Unity.

## <a name="example"></a>Przykład

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text;
using System.Xml.Linq;

using UnityEngine;
using UnityEditor;

using SyntaxTree.VisualStudio.Unity.Bridge;

[InitializeOnLoad]
public class ProjectFileHook
{
    // necessary for XLinq to save the xml project file in utf8
    class Utf8StringWriter : StringWriter
    {
        public override Encoding Encoding
        {
            get { return Encoding.UTF8; }
        }
    }

    static ProjectFileHook()
    {
        ProjectFilesGenerator.ProjectFileGeneration += (string name, string content) =>
        {
            // parse the document and make some changes
            var document = XDocument.Parse(content);
            document.Root.Add(new XComment("FIX ME"));

            // save the changes using the Utf8StringWriter
            var str = new Utf8StringWriter();
            document.Save(str);

            return str.ToString();
        };
    }
}
```

## <a name="see-also"></a>Zobacz też
 [Przykład: Wywołanie zwrotne dziennika](../cross-platform/share-the-unity-log-callback-with-vstu.md)

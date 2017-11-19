---
title: "Wskazówki: Łączenie typu zawartości z rozszerzeniem nazwy pliku | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bfe19b8733a6ee5ffe3d038778e664a4a1455dbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Wskazówki: Łączenie typu zawartości z rozszerzeniem nazwy pliku
Można definiować własne typu zawartości i połączyć rozszerzenie nazwy pliku przy użyciu edytora rozszerzeń Managed Extensibility Framework (MEF). W niektórych przypadkach rozszerzenie nazwy pliku został już zdefiniowany przez usługę języka; Niemniej jednak do korzystania z niego MEF nadal musisz dołączyć ją do typu zawartości.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, użytkownik nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest uwzględniona jako opcjonalna funkcja w Instalatorze programu Visual Studio. Można także zainstalować zestawu SDK dla programu późniejsze. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Tworzenie projektu MEF  
  
1.  Tworzenie projektu C# VSIX. (W **nowy projekt** okno dialogowe, wybierz opcję **Visual C# / rozszerzalności**, następnie **projektu VSIX**.) Nazwa rozwiązania `ContentTypeTest`.  
  
2.  W **source.extension.vsixmanifest** pliku, przejdź do **zasoby** , a następnie ustaw **typu** do **Microsoft.VisualStudio.MefComponent**, **źródła** do **projekt w bieżącym rozwiązaniu**i **projektu** pole nazwy projektu.  
  
## <a name="defining-the-content-type"></a>Definiowanie typu zawartości  
  
1.  Dodaj plik klasy i nadaj mu nazwę `FileAndContentTypes`.  
  
2.  Dodaj odwołania do następujących zestawów:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Dodaj następujące `using` dyrektywy.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Deklarowanie klasy statycznej, który zawiera definicje.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  W tej klasie wyeksportować <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> o nazwie "hid" ani deklarować jego podstawowej definicji "text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Łączenie rozszerzenie nazwy pliku do typu zawartości  
  
-   Aby mapować rozszerzenie nazwy pliku tego typu zawartości, należy wyeksportować <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> który ma rozszerzenie "HID" i typ zawartości "hid".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Dodawanie typ zawartości do eksportu edytora  
  
1.  Tworzenie rozszerzenia edytora. Na przykład można użyć rozszerzenia symbolu margines opisanego w [wskazówki: Tworzenie symbolu margines](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Dodaj klasę, który zdefiniowano w tej procedurze.  
  
3.  Podczas eksportowania klasa rozszerzenia, Dodaj <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> typu "hid" do niego.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa języka i punkty rozszerzenia Edytora](../extensibility/language-service-and-editor-extension-points.md)
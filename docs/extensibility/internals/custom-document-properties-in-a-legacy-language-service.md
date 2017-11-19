---
title: "Niestandardowe właściwości dokumentu w usłudze języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c82476b9d6fd632ed67acbeeab147743ea16cb40
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Niestandardowe właściwości dokumentu w starsza wersja usługi języka
Dokument, właściwości mogą być wyświetlane w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **właściwości** okna. Języki programowania nie mają zwykle właściwości skojarzone z plikami źródłowymi indywidualnych. Jednak XML obsługuje właściwości dokumentu, które mają wpływ na kodowania, schematów i arkusza stylów.  
  
## <a name="discussion"></a>Omówienie  
 Jeśli język musi niestandardowe właściwości dokumentu, musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy i wdrożenie niezbędne właściwości w klasie pochodnej.  
  
 Ponadto właściwości dokumentu zwykle są przechowywane w samym pliku źródłowego. Wymaga to usługa języka przeprowadzenia analizy informacji o właściwości z pliku źródłowego do wyświetlenia w **właściwości** okna i zaktualizuj plik źródłowy, po zmianie właściwości dokumentu w  **Właściwości** okna.  
  
## <a name="customizing-the-documentproperties-class"></a>Dostosowywanie klasy DocumentProperties  
 Aby obsługiwać niestandardowe właściwości dokumentu, musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy i dodać dowolną liczbę właściwości zgodnie z potrzebami. Należy również określić atrybuty użytkowników, aby zorganizować je w **właściwości** wyświetlania okna. Jeśli właściwość jest tylko `get` dostępu, jest ona wyświetlana jako tylko do odczytu w **właściwości** okna. Jeśli właściwość ma zarówno atrybut `get` i `set` metod dostępu, właściwość może też być aktualizowana w **właściwości** okna.  
  
### <a name="example"></a>Przykład  
 Oto przykład pochodzi od klasy <xref:Microsoft.VisualStudio.Package.DocumentProperties>, przedstawiający dwie właściwości, nazwę i opis. Po zaktualizowaniu właściwości, metody niestandardowej na <xref:Microsoft.VisualStudio.Package.LanguageService> klasy jest wywoływana w celu zapisania właściwość w pliku źródłowym.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestDocumentProperties : DocumentProperties  
    {  
        private string m_filename;  
        private string m_description;  
  
        public TestDocumentProperties(CodeWindowManager mgr)  
            : base(mgr)  
        {  
        }  
  
        // Helper function to initialize this property without  
        // going through the FileName property (which does a lot  
        // more than we need when the filename is set).  
        public void SetFileName(string filename)  
        {  
            m_filename = filename;  
        }  
  
        // Helper function to initialize this property without  
        // going through the Description property (which does a lot  
        // more than we need when the description is set).  
        public void SetDescription(string description)  
        {  
            m_description = description;  
        }  
  
        ////////////////////////////////////////////////////////////  
        // The document properties  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Name of the file")]  
        [DisplayNameAttribute("Filename")]  
        public string FileName  
        {  
            get { return m_filename; }  
            set  
            {  
               if (value != m_filename)  
               {  
                    m_filename = value;  
                    SetPropertyValue("Filename", m_filename);  
               }  
            }  
        }  
  
        [CategoryAttribute("General")]  
        [DescriptionAttribute("Description of the file")]  
        [DisplayNameAttribute("Description")]  
        public string Description  
        {  
            get { return m_description; }  
            set  
            {  
                if (value != m_description)  
                {  
                    m_description = value;  
                    SetPropertyValue("Description", m_description);  
                }  
            }  
        }  
  
        ///////////////////////////////////////////////////////////  
        // Private methods.  
  
        private void SetPropertyValue(string propertyName, string propertyValue)  
        {  
            Source src = this.GetSource();  
            if (src != null)  
            {  
                TestLanguageService service = src.LanguageService as TestLanguageService;  
                if (service != null)  
                {  
                    // Set the property in to the source file.  
                    service.SetPropertyValue(src, propertyName, propertyValue);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="instantiating-the-custom-documentproperties-class"></a>Utworzenie wystąpienia klasy niestandardowych DocumentProperties  
 Można utworzyć wystąpienia klasy właściwości niestandardowego dokumentu, konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> metody w używanej wersji <xref:Microsoft.VisualStudio.Package.LanguageService> klasy, aby przywrócić pojedyncze wystąpienie z <xref:Microsoft.VisualStudio.Package.DocumentProperties> klasy.  
  
### <a name="example"></a>Przykład  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        private TestDocumentProperties m_documentProperties;  
  
        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)  
        {  
            if (m_documentProperties == null)  
            {  
                m_documentProperties = new TestDocumentProperties(mgr);  
            }  
            return m_documentProperties;  
        }  
    }  
}  
```  
  
## <a name="properties-in-the-source-file"></a>Właściwości w pliku źródłowym  
 Ponieważ właściwości dokumentu są zazwyczaj specyficzne dla pliku źródłowego, wartości są przechowywane w samym pliku źródłowego. To wymaga obsługi z analizatora języka lub skanera do definiowania tych właściwości. Na przykład właściwości dokumentu XML są przechowywane dla węzła głównego. Po zmodyfikowaniu wartości dla węzła głównego **właściwości** okna wartości zostaną zmienione, a węzeł główny zostanie zaktualizowany w edytorze.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przechowuje właściwości "Nazwa_pliku" i "Opis" w pierwsze dwa wiersze w pliku źródłowym osadzony w nagłówku specjalne komentarza jako:  
  
```  
//!Filename = file.testext  
//!Description = A sample file  
```  
  
 W tym przykładzie przedstawiono dwie metody get i set właściwości dokumentu z pliku źródłowego, jak również pierwsze dwa wiersze, jak właściwości są aktualizowane, jeśli użytkownik modyfikuje plik źródłowy bezpośrednio. `SetPropertyValue` w przykładzie przedstawionym w tym miejscu jest taka sama co wywołać metody z `TestDocumentProperties` klasy, jak pokazano w sekcji "Dostosowywanie klasy DocumentProperties".  
  
 W tym przykładzie użyto skanera można określić typu tokenów w pierwsze dwa wiersze. W tym przykładzie jest tylko w celach ilustracyjnych. Podejście bardziej typowego w tej sytuacji jest można przeanalizować pliku źródłowego, w której każdy węzeł drzewa zawiera informacje o określonym token tak zwany drzewo analizy. Węzeł główny zawiera właściwości dokumentu.  
  
```csharp  
using System.ComponentModel;  
using Microsoft.VisualStudio.Package;  
  
namespace TestLanguagePackage  
{  
    // TokenType.Comment is the last item in that enumeration.  
    public enum TestTokenTypes  
    {  
        DocPropertyLine = TokenType.Comment + 1,  
        DocPropertyName,  
        DocPropertyAssign,  
        DocPropertyValue  
    }  
  
    class TestLanguageService : LanguageService  
    {  
        // Search this many lines from the beginning for properties.  
        private static int maxLinesToSearch = 2;  
  
        private TestDocumentProperties m_documentProperties;  
  
        // Called whenever a full parsing operation has completed.  
        public override void OnParseComplete(ParseRequest req)  
        {  
            if (m_documentProperties != null)  
            {  
                Source src = GetSource(req.View);  
                if (src != null)  
                {  
                    string value = GetPropertyValue(src, "Filename");  
                    m_documentProperties.SetFileName(value);  
  
                    value = GetPropertyValue(src, "Description");  
                    m_documentProperties.SetDescription(value);  
  
                    // Update the Properties Window.  
                    m_documentProperties.Refresh();  
                }  
            }  
        }  
  
        // Retrieves the specified property value from the given source.  
        public string GetPropertyValue(Source src, string propertyName)  
        {  
            string propertyValue = "";  
  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    string      line;  
                    TokenInfo[] lineInfo = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line.  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                for ( ;  
                                     tokenIndex < lineInfo.Length;  
                                     tokenIndex++)  
                                {  
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)  
                                    {  
                                        break;  
                                    }  
                                }  
                                if (tokenIndex < lineInfo.Length)  
                                {  
                                    propertyValue = src.GetText(i,  
                                                          lineInfo[tokenIndex].StartIndex,  
                                                          i,  
                                                          lineInfo[tokenIndex].EndIndex + 1);  
                                }  
                                break;  
                            }  
                        }  
                    }  
                }  
            }  
            return propertyValue;  
        }  
  
        // Sets the specified property into the given source file.  
        // Called from the TestDocumentProperties class.  
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)  
        {  
            string newLine;  
  
            if (propertyName == null || propertyName == "")  
            {  
                // No property name, so nothing to do  
                return;  
            }  
            if (propertyValue == null)  
            {  
                propertyValue = "";  
            }  
            // This is the line to be inserted.  
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);  
  
            // First, find the line on which the property belongs.  
            // If line is found, replace it.  
            // Otherwise, insert the line at the beginning of the file.  
            if (src != null)  
            {  
                IVsTextColorState colorState = src.ColorState;  
                if (colorState != null)  
                {  
                    int         lineNumber = -1;  
                    string      line;  
                    TokenInfo[] lineInfo   = null;  
                    int         i;  
  
                    for (i = 0; i < maxLinesToSearch; i++)  
                    {  
                        line     = src.GetLine(i);  
                        lineInfo = src.GetColorizer().GetLineInfo(  
                                                        src.GetTextLines(),  
                                                        i,  
                                                        colorState);  
                        if (lineInfo == null)  
                        {  
                            continue;  
                        }  
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)  
                        {  
                            // Not a property line  
                            continue;  
                        }  
                        TokenInfo valueInfo = new TokenInfo();  
                        int tokenIndex = -1;  
                        for (tokenIndex = 0;  
                             tokenIndex < lineInfo.Length;  
                             tokenIndex++)  
                        {  
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)  
                            {  
                                break;  
                            }  
                        }  
                        if (tokenIndex >= lineInfo.Length)  
                        {  
                            // No property name on the line.  
                            continue;  
                        }  
                        string name = src.GetText(i,  
                                                  lineInfo[tokenIndex].StartIndex,  
                                                  i,  
                                                  lineInfo[tokenIndex].EndIndex + 1);  
                        if (name != null)  
                        {  
                            if (String.Compare(name, propertyName, true) == 0)  
                            {  
                                lineNumber = i;  
                                break;  
                            }  
                        }  
                    }  
  
                    // Set up an undo context that also handles the insert/replace.  
                    EditArray editArray = new EditArray(src,  
                                                        true,  
                                                        "Update Property");  
                    if (editArray != null)  
                    {  
                        TextSpan span = new TextSpan();  
                        if (lineNumber != -1)  
                        {  
                            // Replace line.  
                            int lineLength = 0;  
                            src.GetTextLines().GetLengthOfLine(lineNumber,  
                                                               out lineLength);  
                            span.iStartLine  = lineNumber;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = lineNumber;  
                            span.iEndIndex   = lineLength;  
                        }  
                        else  
                        {  
                            // Insert new line.  
                            span.iStartLine  = 0;  
                            span.iStartIndex = 0;  
                            span.iEndLine    = 0;  
                            span.iEndIndex   = 0;  
                            newLine += "\n";  
                        }  
                        editArray.Add(new EditSpan(span, newLine));  
                        editArray.ApplyEdits();  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)
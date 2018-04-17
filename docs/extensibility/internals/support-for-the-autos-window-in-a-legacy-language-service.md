---
title: Obsługa okno zmiennych automatycznych w usłudze języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a1a2627bd36e6047db00afaada231dc49cde2cc3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Obsługa okno zmiennych automatycznych w starsza wersja usługi języka
**Automatycznych** wyświetlany w oknie wyrażeń zmiennych i parametrów, które znajdują się w zakresie, gdy program debugowany jest wstrzymana (albo z powodu punkt przerwania lub wyjątek). Wyrażenia może zawierać zmiennych lokalnych i globalnych oraz parametry, które zostały zmienione w zakresie lokalnym. **Automatycznych** okna mogą również obejmować wystąpień klasy, struktury lub innego typu. Wszystkie elementy, które można ocenić ewaluatora wyrażeń potencjalnie może być wyświetlany w **automatycznych** okna.  
  
 Framework zarządzanego pakietu (MPF) nie ma bezpośrednią obsługę **automatycznych** okna. Jednak jeśli przesłonięcia <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metody, można powrócić do listy wyrażeń, które będą widoczne w **automatycznych** okna.  
  
## <a name="implementing-support-for-the-autos-window"></a>Implementowanie obsługi okno zmiennych automatycznych  
 Wszystko co należy zrobić, aby obsługiwać **automatycznych** okna jest zaimplementowanie <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Należy określić implementacji podany w pliku źródłowym, które wyrażenia powinny znajdować się w lokalizacji **automatycznych** okna. Metoda zwraca listę ciągów, w których każdy ciąg reprezentuje pojedyncze wyrażenie. Zwracana wartość <xref:Microsoft.VisualStudio.VSConstants.S_OK> wskazuje, że lista zawiera wyrażenia, podczas gdy <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> wskazuje, że nie ma żadnych wyrażeń do wyświetlenia.  
  
 Rzeczywiste wyrażenia, zwracane są nazwy zmiennych i parametrów, które pojawiają się w tej lokalizacji w kodzie. Te nazwy są przekazywane do ewaluatora wyrażenia, aby uzyskać wartości i typy, które są następnie wyświetlane w **automatycznych** okna.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia implementację <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> metodę, która pobiera listę wyrażeń z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę przy użyciu z powodu analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Każde wyrażenie jest jest ujęte jako `TestVsEnumBSTR` implementującej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interfejsu.  
  
 Należy pamiętać, że `GetAutoExpressionsCount` i `GetAutoExpression` metody to metody niestandardowe na `TestAuthoringSink` obiektu i zostały dodane do obsługi w tym przykładzie. Reprezentuje jeden sposób w wyrażeniach, które dodano do `TestAuthoringSink` obiektu przez parser (przez wywołanie metody <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> — metoda) jest możliwy poza analizatora.  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```
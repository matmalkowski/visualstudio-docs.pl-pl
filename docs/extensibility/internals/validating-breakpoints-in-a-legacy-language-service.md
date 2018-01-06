---
title: "Sprawdzanie poprawności punktów przerwania w usłudze języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 85d9add1e66fdde2fcdbfd5c83bf99b6180a4642
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Sprawdzanie poprawności punkty przerwania w starsza wersja usługi języka
Punkt przerwania wskazuje, że wykonywanie programu powinna zostać przerwana w określonym punkcie podczas, gdy jest uruchamiana w debugerze. Użytkownika można umieścić punkt przerwania w żadnych wierszy w pliku źródłowym, ponieważ edytor nie ma informacji o to, co stanowi prawidłowej lokalizacji punktu przerwania. Po uruchomieniu debugera, wszystkie oznaczone punkty przerwania (nazywane oczekujących punktów przerwania) są powiązane z odpowiednią lokalizację w uruchomiony program. W tym samym czasie, które są weryfikowane punktów przerwania, aby upewnić się, że ich oznaczanie prawidłowy kod lokalizacji. Na przykład punkt przerwania w komentarz nie jest prawidłowa, ponieważ nie istnieje żaden kod w tej lokalizacji w kodzie źródłowym. Debuger wyłącza nieprawidłowy punktów przerwania.  
  
 Ponieważ usługa języka zna kod źródłowy będzie wyświetlany, można sprawdzić punkty przerwania, zanim debuger jest uruchomiony. Można zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodę, aby zwrócić zakres, określając prawidłową lokalizacją punktu przerwania. Lokalizacji punktu przerwania nadal jest weryfikowana, gdy debuger jest uruchomiona, ale użytkownik jest powiadamiany nieprawidłowy punktów przerwania bez oczekiwania na debugera do załadowania.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Implementowanie obsługi sprawdzania poprawności punkty przerwania  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Metoda jest podana pozycja punktu przerwania. Implementacji należy zdecydować, czy lokalizacja jest prawidłowa i wskazująca, że to zwracając zakres tekstu, który identyfikuje kod skojarzone z pozycji wiersza punktu przerwania.  
  
-   Zwraca <xref:Microsoft.VisualStudio.VSConstants.S_OK> czy lokalizacja jest prawidłowa, lub <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> Jeśli nie jest prawidłowy.  
  
-   Jeśli punkt przerwania jest prawidłowy zakres tekstu jest wyróżniane wraz z punktu przerwania.  
  
-   Jeśli punkt przerwania jest nieprawidłowa, zostanie wyświetlony komunikat o błędzie na pasku stanu.  
  
### <a name="example"></a>Przykład  
 Ten przykład przedstawia implementację <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> metodę, która wywołuje analizator uzyskanie zakresu kodu (jeśli istnieją) w określonej lokalizacji.  
  
 W tym przykładzie przyjęto założenie, że dodano `GetCodeSpan` metodę <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasę weryfikującą zakres tekstu i zwraca `true` Jeśli jest to lokalizacja nieprawidłowy punkt przerwania.  
  
```csharp  
using Microsoft VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    class TestLanguageService : LanguageService  
    {  
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,  
                                                       int line,  
                                                       int col,  
                                                       TextSpan[] pCodeSpan)  
        {  
            int retval = VSConstants.S_FALSE;  
            if (pCodeSpan != null)  
            {  
                // Initialize span to current line by default.  
                pCodeSpan[0].iStartLine = line;  
                pCodeSpan[0].iStartIndex = col;  
                pCodeSpan[0].iEndLine = line;  
                pCodeSpan[0].iEndIndex = col;  
            }  
  
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
                                                              ParseReason.CodeSpan,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        TextSpan span = new TextSpan();  
                        if (sink.GetCodeSpan(out span))  
                        {  
                            pCodeSpan[0] = span;  
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
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)
---
title: Kod komentowania w starsza wersja usługi języka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b573b464c26c3864cece697191cf03545ada779
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128723"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Kod komentowania w starsza wersja usługi języka
Języki programowania zwykle pozwalają na dodawanie adnotacji lub komentarzy kodu. Fragment tekstu, który udostępnia dodatkowe informacje o kodzie, ale jest ignorowany podczas kompilacji lub interpretacji jest komentarz.  
  
 Klasy framework (MPF) zarządzanego pakietu zapewniają obsługę komentowania i Trwa usuwanie komentarza zaznaczonego tekstu.  
  
## <a name="comment-styles"></a>Style komentarza  
 Istnieją dwa ogólne style komentarza:  
  
1.  Wiersz komentarze, gdzie jest komentarz w jednym wierszu.  
  
2.  Komentarze bloku, w którym komentarz może obejmować wiele wierszy.  
  
 Wiersz komentarze zwykle mają początkowy znak (lub znaki), podczas komentarze bloku mieć początek i koniec znaków. Na przykład w języku C# komentarz wiersz rozpoczyna się od / /, i rozpoczyna się od blok komentarza / * i kończy \*/.  
  
 Gdy użytkownik wybierze polecenie **Zaznaczanie komentarzy** z **Edytuj** -> **zaawansowane** menu polecenie jest kierowany do <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metoda <xref:Microsoft.VisualStudio.Package.Source> klasy. Gdy użytkownik wybierze polecenie **wybór usuń znaczniki komentarza**, polecenie jest kierowany do <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metody.  
  
## <a name="supporting-code-comments"></a>Obsługa komentarze w kodzie  
 Komentarze języka usługi pomocy technicznej kodu za pomocą klasy mogą mieć `EnableCommenting` o nazwie parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . To ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Aby uzyskać więcej informacji na temat ustawiania języka servicce funkcji, zobacz [zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Konieczne jest również przesłonięcie <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodę, aby zwrócić <xref:Microsoft.VisualStudio.Package.CommentInfo> struktury znakami komentarza dla danego języka. C# — styl linii komentarz znaki są domyślnie.  
  
### <a name="example"></a>Przykład  
 W tym miejscu jest przykładem implementacji <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metody.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)
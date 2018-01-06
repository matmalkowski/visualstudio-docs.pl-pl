---
title: "Ponowne formatowanie kodu w usłudze języka starszych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2ff6152d5c9b5108dff00d9b17cb4fb2471ac4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Ponowne formatowanie kodu w starsza wersja usługi języka

W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kodu źródłowego można sformatować przy normalizacji wcięcia i spacji. Mogą to być wstawianie lub usunięcie spacji ani tabulatory na początku każdego wiersza, dodawanie nowych wierszy między liniami lub zastąpieniem spacji karty lub kart za pomocą spacji.  
  
>**Uwaga:** Wstawianie lub usuwanie znaków nowego wiersza może mieć wpływ na znaczniki, takie jak punkty przerwania i zakładki, ale Dodawanie lub usuwanie spacji ani karty nie wpływa na znaczników.  
  
Użytkownicy mogą uruchamiać reformatting operacji wybierając **Wybieranie formatu** lub **dokumentu w formacie** z **zaawansowane** menu **Edytuj**menu. Operacja reformatting można również uruchomić po wstawieniu fragmentu kodu lub określonego znaku. Na przykład po wpisaniu zamykającego nawiasu klamrowego w języku C#, wszystko pomiędzy pasującego otwierający nawias klamrowy i Zamknij nawias klamrowy jest automatycznie wcięta odpowiedniego poziomu.
  
Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wysyła **Wybieranie formatu** lub **dokumentu w formacie** polecenia do usługi języka <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy wywołania <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody w <xref:Microsoft.VisualStudio.Package.Source> klasy. Do obsługi formatowania, konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> — metoda i podaj własnego formatowania kodu.  
  
## <a name="enabling-support-for-reformatting"></a>Włączanie obsługi ponownego formatowania  

Do obsługi formatowania, `EnableFormatSelection` parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> musi mieć ustawioną `true` po dokonaniu rejestracji VSPackage. To ustawienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> właściwości `true`. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Metoda zwraca wartość tej właściwości. Jeśli zmienna zwraca wartość true, <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy wywołania <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Implementowanie formatowania

Do zaimplementowania formatowania, musi pochodzić z klasy <xref:Microsoft.VisualStudio.Package.Source> klasy i zastąpić <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody. <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Obiektu opisuje zakres do formatowania i <xref:Microsoft.VisualStudio.Package.EditArray> obiektu przechowywana edycje na zakres. Należy pamiętać, że ten zakres można cały dokument. Jednak ponieważ może być wiele zmian w zakresie, wszystkie zmiany powinny być odwracalnego w ramach jednej akcji. Aby to zrobić, opakuj wszystkie zmiany w <xref:Microsoft.VisualStudio.Package.CompoundAction> obiektu (zobacz sekcja "Za pomocą klasy CompoundAction" w tym temacie).

### <a name="example"></a>Przykład  

Poniższy przykład gwarantuje, że jest spacją po każdym przecinku w zaznaczeniu, chyba że przecinek kartę nastąpią lub znajduje się na końcu linii. Końcowe spacje, po usunięciu ostatniego przecinkami w wierszu. Zobacz sekcję "Przy użyciu klasy CompoundAction" w tym temacie, aby zobaczyć, jak ta metoda jest wywoływana z <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> metody.  

```csharp 
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Za pomocą klasy CompoundAction  
 
Wszystkie ponownego formatowania przeprowadzić sekcji kodu powinny być odwracalnego w ramach jednej akcji. Można to zrobić przy użyciu <xref:Microsoft.VisualStudio.Package.CompoundAction> klasy. Ta klasa jest zawijana zestaw operacji edycji na bufor tekstowy do operacji edycji jednego.  
  
### <a name="example"></a>Przykład

Poniżej przedstawiono przykład sposobu użycia <xref:Microsoft.VisualStudio.Package.CompoundAction> klasy. Zapoznaj się z przykładem w sekcji "Wdrażanie pomocy technicznej dla formatowania" w tym temacie przedstawiono przykład `DoFormatting` metody.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  

## <a name="see-also"></a>Zobacz też

[Funkcje usługi starszej wersji języka](legacy-language-service-features1.md)
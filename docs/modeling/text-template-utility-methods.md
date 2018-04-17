---
title: Metody korzystania z szablonów tekstowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 37e268313aa6662ca250aed36be193864bbf0ed5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="text-template-utility-methods"></a>Metody korzystania z szablonów tekstowych

Istnieje kilka metod, które są zawsze dostępne podczas pisania kodu w szablonie tekstu Visual Studio. Te metody są zdefiniowane w <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Można również używać innych metod i usług udostępnianych przez środowisko hosta w szablonie zwykły tekst (nieprzetworzony). Na przykład można rozpoznać ścieżki do pliku, rejestrowanie błędów i pobrać usług świadczonych przez Visual Studio i wszystkie pakiety załadowane. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do programu Visual Studio z szablonu tekstowego](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).
  
## <a name="write-methods"></a>Metod zapisu

Można użyć `Write()` i `WriteLine()` metody, aby dołączyć tekst wewnątrz bloków kodu standardowe, zamiast blok kodu wyrażenia. Poniższe bloki kodu dwóch działają tak samo.  
  
### <a name="code-block-with-an-expression-block"></a>Blok kodu z blok wyrażenia  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
### <a name="code-block-using-writeline"></a>Blok kodu przy użyciu WriteLine()  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Może być przydatne do korzystania z jednego z tych metod narzędzie zamiast blok wyrażenia wewnątrz bloku kodu długo z zagnieżdżone struktury sterujące.  
  
 `Write()` i `WriteLine()` metody mają dwa przeciążenia, jedną, która przyjmuje parametr będący pojedynczym ciągiem i jeden, który przyjmuje ciąg formatu złożonego plus tablicę obiekty do uwzględnienia w ciągu (takich jak `Console.WriteLine()` metody). Następujące dwa zastosowania `WriteLine()` działają tak samo:  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## <a name="indentation-methods"></a>Wcięcie metody

 Wcięcie metody umożliwia sformatować dane wyjściowe szablonu tekstu. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Klasa ma `CurrentIndent` ciągu właściwość, która zawiera bieżącego wcięcia w szablonu tekstowego i `indentLengths` oznacza to pole listy wcięcia, które zostały dodane. Można dodać wcięcia z `PushIndent()` — metoda i odejmowania wcięcia z `PopIndent()` metody. Jeśli chcesz usunąć wszystkie wcięcia, użyj `ClearIndent()` metody. Poniższy blok kodu pokazano sposób użycia tych metod:  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 Ten blok kodu tworzy następujące dane wyjściowe:  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## <a name="error-and-warning-methods"></a>Błąd i ostrzeżenie metody  
 Błąd i ostrzeżenie metody narzędziowe służy do dodawania wiadomości na liście błędów programu Visual Studio. Na przykład następujący kod doda komunikat o błędzie na liście błędów.  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## <a name="access-to-host-and-service-provider"></a>Dostęp do hosta i dostawcy usług  
 Właściwość `this.Host` umożliwia dostęp do właściwości udostępniane przez hosta, który jest wykonywany szablonu. Aby użyć `this.Host`, należy ustawić `hostspecific` atrybutu w `<@template#>` dyrektywy:  
  
 `<#@template ... hostspecific="true" #>`  
  
 Typ `this.Host` zależy od typu hosta, w którym szablon jest wykonywany. W szablonie, który jest uruchomiony w programie Visual Studio, można rzutować `this.Host` do `IServiceProvider` do uzyskania dostępu do usług, takich jak IDE. Na przykład:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>Przy użyciu innego zestawu metody narzędziowe  
 W ramach procesu tworzenia tekstu, pliku szablonu jest przekształcana na klasy, nosi nazwę zawsze `GeneratedTextTransformation`i dziedziczy <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Jeśli chcesz użyć innego zestawu metod zamiast tego można napisać własne klasy i określ go w dyrektywie template. Musi dziedziczyć po klasie <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Użyj `assembly` dyrektywy odwołać się do zestawu, gdzie można znaleźć klasy skompilowany.
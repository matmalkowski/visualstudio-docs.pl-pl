---
title: 'Porady: rozprowadzanie wstawek kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, distributing
ms.assetid: 5f717abd-e167-47ae-818c-6b0bae100ceb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 870737d9689fd754cc8ff77e2a9040c080e4dfb4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-distribute-code-snippets"></a>Porady: rozprowadzanie wstawek kodu
Możesz po prostu zapewniają Twojej wstawki kodu dla Twoich znajomych i je zainstalować fragmenty kodu na swoich komputerach za pomocą Menedżera wstawki kodu. Jednak jeśli masz kilka fragmentów do dystrybucji lub chcesz przekazać je szerzej, można objąć pliku fragment rozszerzenie programu Visual Studio, które użytkownicy programu Visual Studio można zainstalować.  

Aby można było utworzyć rozszerzeń programu Visual Studio należy zainstalować Visual Studio SDK. Znajdź wersję VSSDK, odpowiadający instalację programu Visual Studio na [programu Visual Studio pobiera](https://www.visualstudio.com/downloads/).  

## <a name="setting-up-the-extension"></a>Konfigurowanie rozszerzenia  
W tej procedurze użyjemy tego samego fragmentu kodu Hello World utworzone w [wskazówki: tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md). Firma Microsoft będzie dostarczać tekst .snippet, dzięki czemu nie trzeba wrócić i zmienić jedną.  

1.  Tworzenie nowego projektu VSIX o nazwie **TestSnippet**. (**Pliku**, **nowe**, **projektu**, **Visual C# (lub Visual Basic)**, **rozszerzalności**.)  

2.  W **TestSnippet** projekt, Dodaj nowy plik XML i nadaj mu **VBCodeSnippet.snippet**. Zamień na następującą zawartość:  

    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <CodeSnippets  
        xmlns="http://schemas.microsoft.com/VisualStudio/2005/CodeSnippet">  
      <CodeSnippet Format="1.0.0">  
        <Header>  
          <Title>Hello World VB</Title>  
          <Shortcut>HelloWorld</Shortcut>  
          <Description>Inserts code</Description>  
          <Author>MSIT</Author>  
          <SnippetTypes>  
            <SnippetType>Expansion</SnippetType>  
            <SnippetType>SurroundsWith</SnippetType>  
          </SnippetTypes>  
        </Header>  
        <Snippet>  
          <Code Language="VB">  
            <![CDATA[Console.WriteLine("Hello, World!")]]>  
          </Code>  
        </Snippet>  
      </CodeSnippet>  
    </CodeSnippets>  
    ```  

#### <a name="setting-up-the-directory-structure"></a>Konfigurowanie struktury katalogu  

1.  W Eksploratorze rozwiązań wybierz węzeł projektu i dodać folder o nazwie ma fragment kodu w Menedżerze fragmentów kodu. W takim przypadku należy go **HelloWorldVB**.  

2.  Przenieść plik .snippet **HelloWorldVB** folderu.  

3.  Wybierz plik .snippet w Eksploratorze rozwiązań i w **właściwości** upewnij się, że okno **Akcja kompilacji** ustawiono **zawartości**, **kopiowania danych wyjściowych Katalog** ma ustawioną wartość **skopiuj zawsze**, i **Include w pliku VSIX** ustawiono **true**.  

#### <a name="adding-the-pkgdef-file"></a>Dodawanie pliku .pkgdef  

1.  Dodaj z pliku tekstowego **HelloWorldVB** folder i nadaj mu nazwę **HelloWorldVB.pkgdef**. Ten plik jest używany do dodania określonych kluczy rejestru. W takim przypadku jest dodawany do nowego klucza  

     **HKCU\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic**.  

2.  Dodaj następujące wiersze do pliku.  

    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  

    Jeśli ten klucz należy zbadać, widać jak określać różnych języków.  

3.  Wybierz plik .pkgdef w Eksploratorze rozwiązań i w **właściwości** upewnij się, że okno **Akcja kompilacji** ustawiono **zawartości**, **Kopiuj do katalogu wyjściowego**  ustawiono **skopiuj zawsze**, i **Include w pliku VSIX** ustawiono **true**.  

4.  Dodaj plik .pkgdef jako zasób w manifeście VSIX. W pliku source.extension.vsixmanifest, przejdź do **zasoby** i kliknij polecenie **nowy**.  

5.  W **Dodaj nowy element zawartości** okno dialogowe, zestaw **typu** do **Microsoft.VisualStudio.VsPackage**, **źródła** do **plików na System plików**i **ścieżki** do **HelloWorldVB.pkgdef** (która powinna zostać wyświetlona na liście rozwijanej).  

### <a name="testing-the-snippet"></a>Testowanie wstawki kodu  

1.  Teraz można upewnić się, że fragment kodu działa w eksperymentalne wystąpienie programu Visual Studio. Eksperymentalne wystąpienie jest drugiej kopii programu Visual Studio, która różni się od tego, który używa się do pisania kodu. Umożliwia pracę na rozszerzeniu bez wpływu na środowiska deweloperskiego.  

2.  Skompiluj projekt i Rozpocznij debugowanie. Powinna pojawić się drugie wystąpienie programu Visual Studio.  

3.  W eksperymentalnym wystąpieniu, przejdź do **narzędzi / kod Menedżerze fragmentów** i ustaw **języka** do **podstawowe**. HelloWorldVB powinna być widoczna jako jeden z folderów i powinno być możliwe rozwinąć folder, aby wyświetlić fragment HelloWorldVB.  

4.  Przetestuj fragment kodu. W eksperymentalnym wystąpieniu Otwórz projekt Visual Basic a jeden z plików kodu. Umieść kursor w miejscu gdzieś w kodzie, kliknij prawym przyciskiem myszy, a na stronie wybierz menu kontekstowe **wstawić fragment**.  

5.  HelloWorldVB powinna zostać wyświetlona jako jeden z folderów. Kliknij go dwukrotnie. Powinny pojawić się okno podręczne **wstawianie fragmentu: HelloWorldVB >** z listy rozwijanej **HelloWorldVB**. Kliknij listę rozwijaną HelloWorldVB. Powinien zostać wyświetlony następujący wiersz dodane do pliku:  

    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  

## <a name="see-also"></a>Zobacz też  
[Fragmenty kodu](../ide/code-snippets.md)

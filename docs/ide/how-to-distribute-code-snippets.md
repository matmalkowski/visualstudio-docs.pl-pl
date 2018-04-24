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
ms.openlocfilehash: e51abd2aa96c5313dfeeb31aabc492d8cfbcd82d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-distribute-code-snippets"></a>Porady: rozprowadzanie wstawek kodu
Można podać Twojej wstawki kodu dla Twoich znajomych i je zainstalować fragmenty kodu na swoich komputerach za pomocą Menedżera wstawki kodu. Jednak jeśli masz kilka fragmentów do dystrybucji lub chcesz przekazać je szerzej, można objąć pliku fragment rozszerzenie programu Visual Studio, które użytkownicy programu Visual Studio można zainstalować.  

Aby można było utworzyć rozszerzeń programu Visual Studio należy zainstalować Visual Studio SDK. Znajdź wersję VSSDK, odpowiadający instalację programu Visual Studio na [program Visual Studio pobiera](https://www.visualstudio.com/downloads/).  

## <a name="set-up-the-extension"></a>Skonfigurować rozszerzenia  
W tej procedurze użyjemy tego samego fragmentu kodu Hello World utworzone w [wskazówki: tworzenie wstawek kodu](../ide/walkthrough-creating-a-code-snippet.md). Firma Microsoft będzie dostarczać *.snippet* tekstu, dzięki czemu nie trzeba wrócić i zmienić jedną.  

1.  Tworzenie nowego projektu VSIX o nazwie **TestSnippet**. (**Pliku** > **nowe** > **projektu** > **Visual C# (lub Visual Basic)**  >  **Rozszerzalności**.)  

2.  W **TestSnippet** projekt, Dodaj nowy plik XML i nadaj mu *VBCodeSnippet.snippet*. Zamień na następującą zawartość:  

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

#### <a name="set-up-the-directory-structure"></a>Konfigurowanie struktury katalogów  

1.  W **Eksploratora rozwiązań**, wybierz węzeł projektu i dodać folder o nazwie ma fragment kodu w celu zapewnienia **Menedżerze fragmentów kodu**. W takim przypadku należy go **HelloWorldVB**.  

2.  Przenieś *.snippet* pliku *HelloWorldVB* folderu.  

3.  Wybierz *.snippet* w pliku **Eksploratora rozwiązań**i w **właściwości** upewnij się, że okno **Akcja kompilacji** ma ustawioną wartość **Zawartości**, **Kopiuj do katalogu wyjściowego** ustawiono **skopiuj zawsze**, i **Include w pliku VSIX** ustawiono **true**.  

#### <a name="add-the-pkgdef-file"></a>Dodaj plik .pkgdef  

1.  Dodaj z pliku tekstowego *HelloWorldVB* folder i nadaj mu nazwę *HelloWorldVB.pkgdef*. Ten plik jest używany do dodania określonych kluczy rejestru. W takim przypadku dodaje nowy klucz do:  

     `HKCU\Software\Microsoft\VisualStudio\15.0\Languages\CodeExpansions\Basic`  

2.  Dodaj następujące wiersze do pliku.  

    ```  
    // Visual Basic   
    [$RootKey$\Languages\CodeExpansions\Basic\Paths]   
    "HelloWorldVB"="$PackageFolder$"  
    ```  

    Jeśli ten klucz należy zbadać, widać jak określać różnych języków.  

3.  Wybierz *.pkgdef* w pliku **Eksploratora rozwiązań**i w **właściwości** upewnij się, że okno **Akcja kompilacji** ma ustawioną wartość **Zawartości**, **Kopiuj do katalogu wyjściowego** ustawiono **skopiuj zawsze**, i **Include w pliku VSIX** ustawiono **true**.  

4.  Dodaj *.pkgdef* pliku jako zasób w manifeście VSIX. W *source.extension.vsixmanifest* pliku, przejdź do **zasoby** i kliknij polecenie **nowy**.  

5.  W **Dodaj nowy element zawartości** okno dialogowe, zestaw **typu** do **Microsoft.VisualStudio.VsPackage**, **źródła** do **plików na System plików**i **ścieżki** do **HelloWorldVB.pkgdef** (która powinna zostać wyświetlona na liście rozwijanej).  

### <a name="test-the-snippet"></a>Testowanie wstawki kodu  

1.  Teraz można upewnić się, że fragment kodu działa w eksperymentalne wystąpienie programu Visual Studio. Eksperymentalne wystąpienie jest drugiej kopii programu Visual Studio, która różni się od tego, który używa się do pisania kodu. Umożliwia pracę na rozszerzeniu bez wpływu na środowiska deweloperskiego.  

2.  Skompiluj projekt i Rozpocznij debugowanie. Powinna pojawić się drugie wystąpienie programu Visual Studio.  

3.  W eksperymentalnym wystąpieniu, przejdź do **Narzędzia > Menedżerze fragmentów kodu** i ustaw **języka** do **podstawowe**. Powinny pojawić się *HelloWorldVB* jako jeden z folderów i być może rozwinąć folder, aby wyświetlić *HelloWorldVB* fragment kodu.  

4.  Przetestuj fragment kodu. W eksperymentalnym wystąpieniu Otwórz projekt Visual Basic a jeden z plików kodu. Umieść kursor w miejscu gdzieś w kodzie, kliknij prawym przyciskiem myszy, a na stronie wybierz menu kontekstowe **wstawić fragment**.  

5.  Powinny pojawić się *HelloWorldVB* jako jeden z folderów. Kliknij go dwukrotnie. Powinny pojawić się okno podręczne **wstawianie fragmentu: HelloWorldVB >** z listy rozwijanej **HelloWorldVB**. Kliknij przycisk **HelloWorldVB** listy rozwijanej. Powinien zostać wyświetlony następujący wiersz dodane do pliku:  

    ```vb  
    Console.WriteLine("Hello, World!")  
    ```  

## <a name="see-also"></a>Zobacz także  
[Fragmenty kodu](../ide/code-snippets.md)

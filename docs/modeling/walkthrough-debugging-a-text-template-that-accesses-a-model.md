---
title: 'Wskazówki: debugowanie szablonu tekstowego uzyskującego dostęp do modelu'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 560849eaeefc8efd8337cbc98ad3de91e4d15fd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31968123"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Wskazówki: debugowanie szablonu tekstowego uzyskującego dostęp do modelu
Podczas modyfikowania lub dodać szablonów tekstowych w rozwiązaniu języka specyficznego dla domeny mogą wystąpić błędy, gdy aparat przekształca szablonu do kodu źródłowego lub kompiluje wygenerowanego kodu. Poniższe wskazówki przedstawiono niektóre czynności, które można wykonywać debugowanie szablonu tekstowego.

> [!NOTE]
>  Aby uzyskać więcej informacji na temat tekstu, szablony ogólnie rzecz biorąc, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md). Aby uzyskać więcej informacji o debugowaniu szablonów tekstowych, patrz [wskazówki: debugowanie szablonu tekstowego](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).

## <a name="creating-a-domain-specific-language-solution"></a>Tworzenie rozwiązania języka specyficznego dla domeny
 Ta procedura służy do tworzenia rozwiązania języka specyficznego dla domeny, które ma następującą charakterystykę:

-   Nazwa: DebuggingTestLanguage

-   Szablon rozwiązania: minimalnego języka

-   Rozszerzenie pliku: .ddd

-   Nazwa firmy: Fabrikam

 Aby uzyskać więcej informacji na temat tworzenia rozwiązania języka specyficznego dla domeny, zobacz [porady: tworzenie rozwiązania języka specyficznego dla domeny](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Tworzenie szablonu tekstowego
 Dodawanie szablonu tekstowego do rozwiązania.

#### <a name="to-create-a-text-template"></a>Aby utworzyć szablonu tekstowego

1.  Skompiluj rozwiązanie i uruchamianie jej w debugerze. (Na **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**, a następnie na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.) Nowe wystąpienie programu Visual Studio otworzy debugowania projektu.

2.  Dodaj plik tekstowy o nazwie `DebugTest.tt` do debugowania projektu.

3.  Upewnij się, że **narzędzie niestandardowe** ma ustawioną właściwość DebugTest.tt `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Debugowanie dyrektywy, które uzyskują dostęp do modelu z szablonu tekstowego
 Przed uzyskaniem dostępu modelu z instrukcji i wyrażenia w szablonu tekstowego, najpierw musisz wywołać wygenerowanego procesora dyrektywy. Wywoływanie wygenerowanego procesora dyrektywy udostępnia klasy modelu tekstu kod szablonu jako właściwości. Aby uzyskać więcej informacji, zobacz [podczas uzyskiwania dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md).

 W poniższych procedurach będzie debugowania nieprawidłową nazwę dyrektywy i nazwy nieprawidłowe właściwości.

#### <a name="to-debug-an-incorrect-directive-name"></a>Aby debugować nieprawidłową nazwę dyrektywy

1.  Zastąp kod w DebugTest.tt następującym kodem:

    > [!NOTE]
    >  Ten kod zawiera błąd. Błąd udostępniono Aby debugować go.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.

     **Listy błędów** okno wyświetla ten błąd:

     **Procesor o nazwie "DebuggingTestLanguageDirectiveProcessor" nie obsługuje dyrektywy o nazwie "modelRoot". Transformacja nie zostanie uruchomiona.**

     W takim przypadku wywołania dyrektywy zawiera nieprawidłową nazwę dyrektywy. Określono `modelRoot` jako nazwy dyrektywy, ale podano poprawną nazwę dyrektywy `DebuggingTestLanguage`.

3.  Kliknij dwukrotnie ten błąd w **listy błędów** okna, aby przejść do kodu.

4.  Aby poprawić kod, należy zmienić nazwę dyrektywy do `DebuggingTestLanguage`.

     Zmiana zostanie wyróżniona.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.

     Teraz system transformacji szablonu tekstowego i generuje odpowiedniego pliku wyjściowego. Wszelkie błędy nie będą widoczne **listy błędów** okna.

#### <a name="to-debug-an-incorrect-property-name"></a>Nazwa właściwości niepoprawne debugowania

1.  Zastąp kod w DebugTest.tt następującym kodem:

    > [!NOTE]
    >  Ten kod zawiera błąd. Błąd udostępniono Aby debugować go.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.ExampleModel #>
    <#
    foreach (ExampleElement element in this.ExampleModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.ExampleModel #>
    <#
    For Each element as ExampleElement in Me.ExampleModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

2.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.

     **Listy błędów** okno zostanie wyświetlony i jeden z tych błędów:

     (C#)

     **Kompilowanie przekształcenia: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation "nie zawiera definicji"ExampleModel"**

     (Visual Basic)

     **Kompilowanie przekształcenia: "ExampleModel" nie jest elementem członkowskim "Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation ".**

     W takim przypadku kod szablonu tekst zawiera nazwę nieprawidłowe właściwości. Określono `ExampleModel` jako nazwa właściwości, ale właściwość poprawna nazwa jest `LibraryModel`. Można znaleźć nazwy właściwości poprawne w zawiera parametr, jak pokazano w poniższym kodzie:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3.  Kliknij dwukrotnie ten błąd w oknie Lista błędów, aby przejść do kodu.

4.  Aby poprawić kod, Zmień nazwę właściwości, aby `LibraryModel` w kodzie szablonu tekstu.

     Zmiany zostały wyróżnione.

    ```csharp
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= this.LibraryModel #>
    <#
    foreach (ExampleElement element in this.LibraryModel.Elements)
    {
    #>
        Element: <#= element.Name #>
    <#
    }
    #>
    ```

    ```vb
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>
    <#@ output extension=".txt" #>
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>

    Model: <#= Me.LibraryModel #>
    <#
    For Each element as ExampleElement in Me.LibraryModel.Elements
    #>
        Element: <#= element.Name #>
    <#
    Next
    #>
    ```

5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy DebugTest.tt, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.

     Teraz system transformacji szablonu tekstowego i generuje odpowiedniego pliku wyjściowego. Wszelkie błędy nie będą widoczne **listy błędów** okna.
---
title: 'Wskazówki: Łączenie hosta z generowanym procesorem dyrektywy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 451dcf21e8965de9ea350577c819daefb150a5d1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632932"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Wskazówki: łączenie hosta z generowanym procesorem dyrektywy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [wskazówki: łączenie hosta z procesorem dyrektywy generowane](https://docs.microsoft.com/visualstudio/modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor).  
  
Możesz napisać własnego hosta, który przetwarza szablonów tekstowych. Podstawowe niestandardowego hosta jest przedstawiona w [wskazówki: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md). Można rozszerzyć tego hosta, aby dodać funkcje, takie jak Generowanie wiele plików wyjściowych.  
  
 W tym przewodniku rozwiń niestandardowy host tak, aby go obsługuje szablony tekstowe, które wywołują procesory dyrektyw. Podczas definiowania języka specyficznego dla domeny generuje *procesora dyrektywy* dla modelu domeny. Procesor dyrektywy ułatwia użytkownikom na zapis szablony uzyskujących dostęp do modelu, co eliminuje konieczność pisania zestawu i Importuj dyrektywy w szablonach.  
  
> [!WARNING]
>  W tym przewodniku opiera się na [wskazówki: Tworzenie niestandardowego hosta szablonu tekstu](../modeling/walkthrough-creating-a-custom-text-template-host.md). Najpierw zadań z tego przewodnika.  
  
 Ten instruktaż zawiera następujące zagadnienia:  
  
-   Za pomocą [!INCLUDE[dsl](../includes/dsl-md.md)] do generowania procesor dyrektywy, która jest oparta na modelu domeny.  
  
-   Łączenie niestandardowego hosta szablonu tekstowego generowanym procesorem dyrektywy.  
  
-   Testowanie niestandardowego hosta z generowanym procesorem dyrektywy.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby zdefiniować DSL, musisz mieć zainstalowane następujące składniki:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Visual Studio Visualisation i Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|  
  
 Ponadto konieczne jest posiadanie przekształcenia szablonu tekstu niestandardowego, które są tworzone w [wskazówki: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Przy użyciu narzędzia języka specyficznego dla domeny, aby wygenerować procesora dyrektywy  
 W tym przewodniku umożliwia Kreator projektanta języka specyficznego dla domeny Tworzenie języka specyficznego dla domeny dla rozwiązania DSLMinimalTest.  
  
#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Aby użyć narzędzia języka specyficznego dla domeny w celu wygenerowania procesor dyrektywy, która jest oparta na modelu domeny  
  
1.  Tworzenie rozwiązania języka dotyczącego określonej domeny, które ma następujące cechy:  
  
    -   Nazwa: DSLMinimalTest  
  
    -   Szablon rozwiązania: minimalne języka  
  
    -   Rozszerzenie pliku: min  
  
    -   Nazwa firmy: Fabrikam  
  
     Aby uzyskać więcej informacji na temat tworzenia rozwiązania języka dotyczącego określonej domeny, zobacz [porady: tworzenie rozwiązania języka dotyczącego określonej domeny](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
2.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
    > [!IMPORTANT]
    >  W tym kroku generuje procesora dyrektywy i dodaje klucz dla niego w rejestrze.  
  
3.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
     Drugie wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostanie otwarty.  
  
4.  W eksperymentalnym kompilacji w **Eksploratora rozwiązań**, kliknij dwukrotnie plik **sample.min**.  
  
     Plik zostanie otwarty w projektancie. Należy zauważyć, że model ma dwa elementy, ExampleElement1 i ExampleElement2 oraz połączenia między nimi.  
  
5.  Zamknij drugie wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
6.  Zapisywanie rozwiązania, a następnie zamknij projektanta języka specyficznego dla domeny.  
  
## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Łączenie niestandardowego hosta szablonu tekstu z procesorem dyrektywy  
 Po wygenerowaniu procesor dyrektywy łączenia procesora dyrektywy i hosta szablonu tekstu niestandardowego, który został utworzony w [wskazówki: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md).  
  
#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Aby połączyć niestandardowego hosta szablonu tekstowego generowanym procesorem dyrektywy  
  
1.  Otwórz rozwiązanie CustomHost.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
     **Dodaj odwołanie** zostanie otwarte okno dialogowe z **.NET** karcie wyświetlane.  
  
3.  Dodaj następujące odwołania:  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0  
  
    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0  
  
4.  W górnej części pliku Program.cs lub Module1.vb Dodaj następujący wiersz kodu:  
  
    ```csharp  
    using Microsoft.Win32;  
    ```  
  
    ```vb  
    Imports Microsoft.Win32  
    ```  
  
5.  Odszukaj kod dla właściwości `StandardAssemblyReferences`i zastąp go następującym kodem:  
  
    > [!NOTE]
    >  W tym kroku należy dodać odwołania do zestawów, które są wymagane przez generowanym procesorem dyrektywy, obsługujących hosta.  
  
    ```csharp  
    //the host can provide standard assembly references  
    //the engine will use these references when compiling and  
    //executing the generated transformation class  
    //--------------------------------------------------------------  
    public IList<string> StandardAssemblyReferences  
    {  
        get  
        {  
            return new string[]  
            {  
                //if this host searches standard paths and the GAC  
                //we can specify the assembly name like this:  
                //"System"  
                //since this host only resolves assemblies from the   
                //fully qualified path and name of the assembly  
                //this is a quick way to get the code to give us the  
                //fully qualified path and name of the System assembly  
                //---------------------------------------------------------  
                typeof(System.Uri).Assembly.Location,  
                            typeof(System.Uri).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,  
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,  
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location  
  
            };  
        }  
    }  
    ```  
  
6.  Znajdź Kod funkcji `ResolveDirectiveProcessor`i zastąp go następującym kodem:  
  
    > [!IMPORTANT]
    >  Ten kod zawiera zakodowanych odwołań do nazwy generowanym procesorem dyrektywy, do którego chcesz się połączyć. Można łatwo dokonać to bardziej ogólne, w którym to przypadku wyszukuje wszystkie procesory dyrektywy wymienionych w rejestrze i podejmie próbę odnalezienia dopasowania. W takim przypadku hosta będzie działać z dowolnym generowanym procesorem dyrektywy.  
  
    ```csharp  
    //the engine calls this method based on the directives the user has   
            //specified it in the text template  
            //this method can be called 0, 1, or more times  
            //---------------------------------------------------------------------  
            public Type ResolveDirectiveProcessor(string processorName)  
            {  
                //check the processor name, and if it is the name of the processor the   
                //host wants to support, return the type of the processor  
                //---------------------------------------------------------------------  
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)  
                {  
                    try  
                    {  
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";  
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))  
                        {  
                            if (specificKey != null)  
                            {  
                                List<string> names = new List<String>(specificKey.GetValueNames());  
                                string classValue = specificKey.GetValue("Class") as string;  
                                if (!string.IsNullOrEmpty(classValue))  
                                {  
                                    string loadValue = string.Empty;  
                                    System.Reflection.Assembly processorAssembly = null;  
                                    if (names.Contains("Assembly"))  
                                    {  
                                        loadValue = specificKey.GetValue("Assembly") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //the assembly must be installed in the GAC  
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);  
                                        }  
                                    }  
                                    else if (names.Contains("CodeBase"))  
                                    {  
                                        loadValue = specificKey.GetValue("CodeBase") as string;  
                                        if (!string.IsNullOrEmpty(loadValue))  
                                        {  
                                            //loading local assembly  
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);  
                                        }  
                                    }  
                                    if (processorAssembly == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    Type processorType = processorAssembly.GetType(classValue);  
                                    if (processorType == null)  
                                    {  
                                        throw new Exception("Directive Processor not found");  
                                    }  
                                    return processorType;  
                                }  
                            }  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        //if the directive processor can not be found, throw an error  
                        throw new Exception("Directive Processor not found");  
                    }  
                }  
  
                //if the directive processor is not one this host wants to support  
                throw new Exception("Directive Processor not supported");  
            }  
    ```  
  
7.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko**.  
  
8.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
## <a name="testing-the-custom-host-with-the-directive-processor"></a>Testowanie niestandardowego hosta z procesorem dyrektywy  
 Aby przetestować niestandardowego hosta szablonu tekstu, najpierw należy napisać szablon tekstowy, który wywołuje generowanym procesorem dyrektywy. Następnie uruchom niestandardowego hosta, Przekaż do niego nazwę szablonu tekstu i sprawdź, czy dyrektywa jest przetwarzany niepoprawnie.  
  
#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Aby utworzyć szablon tekstowy w celu przetestowania niestandardowego hosta  
  
1.  Utwórz plik tekstowy i nadaj mu nazwę `TestTemplateWithDP.tt`. Można użyć dowolnego edytora tekstów, takiego jak Notatnik, aby utworzyć plik.  
  
2.  Dodaj następującą zawartość do pliku tekstowego:  
  
    > [!NOTE]
    >  Język programowania szablonu tekstu nie musi odpowiadać językowi niestandardowego hosta.  
  
    ```csharp  
    Text Template Host Test  
  
    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
    <# //this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
    <# //uncomment this line to test that the host allows the engine to set the extension #>  
    <# //@ output extension=".htm" #>  
  
    <# //uncomment this line if you want to see the generated transformation class #>  
    <# //System.Diagnostics.Debugger.Break(); #>  
    <# //this code uses the results of the examplemodel directive #>  
    <#  
        foreach ( ExampleElement box in this.ExampleModel.Elements )   
        {   
            WriteLine("Box: {0}", box.Name);  
  
            foreach (ExampleElement linkedTo in box.Targets)  
            {  
                WriteLine("Linked to: {0}", linkedTo.Name);  
            }  
  
            foreach (ExampleElement linkedFrom in box.Sources)  
            {  
                WriteLine("Linked from: {0}", linkedFrom.Name);  
            }  
  
            WriteLine("");  
        }   
    #>  
    ```  
  
    ```vb  
    Text Template Host Test  
  
    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>  
  
    <# 'this is the call to the examplemodel directive in the generated directive processor #>  
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>  
  
    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>  
    <# '@ output extension=".htm" #>  
  
    <# 'Uncomment this line if you want to see the generated transformation class. #>  
    <# 'System.Diagnostics.Debugger.Break() #>  
  
    <# 'this code uses the results of the examplemodel directive #>  
  
    <#      
       For Each box as ExampleElement In Me.ExampleModel.Elements   
  
           WriteLine("Box: {0}", box.Name)  
  
            For Each LinkedTo as ExampleElement In box.Targets  
                WriteLine("Linked to: {0}", LinkedTo.Name)  
            Next  
  
            For Each LinkedFrom as ExampleElement In box.Sources  
                WriteLine("Linked from: {0}", LinkedFrom.Name)  
            Next  
  
            WriteLine("")  
  
       Next   
    #>  
    ```  
  
3.  W kodzie, Zastąp \<YOUR ŚCIEŻKA > ze ścieżką pliku Sample.min z języka specyficznego dla projektu utworzonego w pierwszej procedurze.  
  
4.  Zapisz i zamknij plik.  
  
#### <a name="to-test-the-custom-host"></a>Aby przetestować niestandardowego hosta  
  
1.  Otwórz okno wiersza polecenia.  
  
2.  Wpisz ścieżkę pliku wykonywalnego dla niestandardowego hosta, ale nie naciskaj jeszcze ENTER.  
  
     Na przykład wpisz:  
  
     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`  
  
    > [!NOTE]
    >  Zamiast wpisywać adres, możesz przejść do pliku CustomHost.exe w **Windows Explorer**, a następnie przeciągnij go do okna wiersza polecenia.  
  
3.  Wpisz spację.  
  
4.  Wpisz ścieżkę do pliku szablonu tekstu, a następnie naciśnij ENTER.  
  
     Na przykład wpisz:  
  
     `<YOUR PATH>TestTemplateWithDP.txt`  
  
    > [!NOTE]
    >  Zamiast wpisywać adres, możesz przejść do pliku TestTemplateWithDP.txt w **Windows Explorer**, a następnie przeciągnij go do okna wiersza polecenia.  
  
     Aplikacja niestandardowego hosta uruchamia i rozpoczyna proces przekształcania szablonu tekstu.  
  
5.  W **Eksplorator Windows**, przejdź do folderu, który zawiera plik TestTemplateWithDP.txt.  
  
     Folder zawiera także plik TestTemplateWithDP1.txt.  
  
6.  Otwórz ten plik, aby zobaczyć wyniki przekształcenia szablonu tekstu.  
  
     Wyniki wygenerowany tekst wyjściowy pojawi się i powinna wyglądać następująco:  
  
    ```  
    Text Template Host Test  
  
    Box: ExampleElement1  
    Linked to: ExampleElement2  
  
    Box: ExampleElement2  
    Linked from: ExampleElement1  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Tworzenie niestandardowego hosta szablonu tekstowego](../modeling/walkthrough-creating-a-custom-text-template-host.md)




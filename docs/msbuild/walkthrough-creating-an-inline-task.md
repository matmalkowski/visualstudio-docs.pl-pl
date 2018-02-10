---
title: "Wskazówki: Tworzenie zadania wbudowanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fb08d3f4774f0d21c44a29414955f30509456757
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="walkthrough-creating-an-inline-task"></a>Wskazówki: tworzenie zadania wbudowanego
Zadania programu MSBuild są zazwyczaj tworzone przez kompilowanie klasy, która implementuje <xref:Microsoft.Build.Framework.ITask> interfejsu. W programie .NET Framework w wersji 4, można utworzyć zadania wbudowane w pliku projektu. Nie masz Utwórz osobny zestaw do obsługi zadań. Aby uzyskać więcej informacji, zobacz [zadania wbudowane](../msbuild/msbuild-inline-tasks.md).  
  
 W tym przewodniku przedstawiono sposób tworzenia i uruchamiania tych zadań wbudowany:  
  
-   Zadanie, które nie ma wejściowych lub wyjściowych parametrów.  
  
-   Zadanie, które ma jeden parametr wejściowy i bez parametrów wyjściowych.  
  
-   Zadanie, które ma dwa parametry wejściowe i jedno wyjście parametr, który zwraca wartość właściwości programu MSBuild.  
  
-   Zadanie, które ma dwa parametry wejściowe i jedno wyjście parametr, który zwraca elementu MSBuild.  
  
 Do tworzenia i uruchamiania zadań, należy użyć programu Visual Studio i **okno wiersza polecenia usługi Visual Studio**w następujący sposób:  
  
-   Utwórz plik projektu programu MSBuild w programie Visual Studio.  
  
-   Zmodyfikuj plik projektu w programie Visual Studio, aby utworzyć zadanie wbudowanego.  
  
-   Użyj **okno wiersza polecenia** Aby skompilować projekt i przejrzeć wyniki.  
  
## <a name="creating-and-modifying-an-msbuild-project"></a>Tworzenie i modyfikowanie projektu programu MSBuild  
 System projektu programu Visual Studio jest oparty na MSBuild. W związku z tym można utworzyć pliku projektu kompilacji w programie Visual Studio. W tej sekcji utworzysz plik projektu programu Visual C#. (Możesz utworzyć plik projektu programu Visual Basic. W kontekście tego samouczka to różnica między pliki projektu dwóch jest niewielki.)  
  
#### <a name="to-create-and-modify-a-project-file"></a>Do tworzenia i modyfikowania pliku projektu  
  
1.  W programie Visual Studio na **pliku** menu, kliknij przycisk **nowy** , a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** wybierz pozycję Visual C# typ projektu, a następnie wybierz **aplikacji Windows Forms** szablonu. W **nazwa** wpisz `InlineTasks`. Wpisz **lokalizacji** dla rozwiązania, na przykład `D:\`. Upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone, **Dodaj do kontroli źródła** jest wyczyszczone i **Nazwa rozwiązania** jest `InlineTasks`.  
  
     Kliknij przycisk **OK** można utworzyć pliku projektu.  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu InlineTasks, a następnie kliknij przycisk **Zwolnij projekt**.  
  
4.  Ponownie kliknij prawym przyciskiem myszy węzeł projektu, a następnie kliknij przycisk **Edytuj InlineTasks.csproj**.  
  
     Plik projektu zostanie wyświetlony w edytorze kodu.  
  
## <a name="adding-a-basic-hello-task"></a>Dodawanie zadań Hello podstawowe  
 Teraz Dodaj do pliku projektu podstawowe zadania, które zostanie wyświetlony komunikat "Hello, world!" Dodaj również cel TestBuild domyślne, aby wywołać zadania.  
  
#### <a name="to-add-a-basic-hello-task"></a>Aby dodać zadanie hello podstawowe  
  
1.  W folderze głównym `Project` węzła, zmień `DefaultTargets` atrybutu `TestBuild`. Powstałe w ten sposób `Project` węzeł powinien wyglądać następująco:  
  
     `<Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">`  
  
2.  Dodaj następujące zadania wbudowanego i docelowych do pliku projektu bezpośrednio przed `</Project>` tagu.  
  
    ```xml  
    <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup />  
      <Task>  
        <Code Type="Fragment" Language="cs">  
          Log.LogMessage("Hello, world!", MessageImportance.High);  
        </Code>  
      </Task>  
    </UsingTask>  
    <Target Name="TestBuild">  
      <Hello />  
    </Target>  
    ```  
  
3.  Zapisz plik projektu.  
  
 Ten kod tworzy zadania wbudowanego nosi nazwę Hello, który nie ma parametrów, odwołania, lub `Using` instrukcje. Zadanie Hello zawiera tylko jeden wiersz kodu, który wyświetla wiadomość hello na domyślnego rejestrowania urządzenia, zwykle w oknie konsoli.  
  
### <a name="running-the-hello-task"></a>Uruchamianie zadania Hello  
 Uruchom program MSBuild przy użyciu **okno wiersza polecenia** do utworzenia zadania Hello i docelowy TestBuild, który wywołuje go przetworzyć.  
  
##### <a name="to-run-the-hello-task"></a>Aby uruchomić zadanie Hello  
  
1.  Kliknij przycisk **Start**, kliknij przycisk **wszystkie programy**, a następnie zlokalizuj **programu Visual Studio Tools** folder i kliknij przycisk **wiersz polecenia programu Visual Studio**.  
  
2.  W **okno wiersza polecenia**, zlokalizuj folder zawierający plik projektu, w tym przypadku D:\InlineTasks\InlineTasks\\.  
  
3.  Typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie ta tworzy plik InlineTasks.csproj i procesów docelowych domyślne TestBuild, który wywołuje zadań Hello.  
  
4.  Sprawdź dane wyjściowe w **okno wiersza polecenia**. Powinien zostać wyświetlony ten wiersz:  
  
     `Hello, world!`  
  
    > [!NOTE]
    >  Jeśli nie ma wiadomości powitania, spróbuj ponownie zapisać plik projektu, a następnie uruchom zadanie Hello.  
  
 Przez przemian edytora kodu i **okno wiersza polecenia**, można zmienić pliku projektu i szybko wyświetlić wyniki.  
  
## <a name="defining-the-echo-task"></a>Definiowanie zadań Echo  
 Tworzenie zadania wbudowanego, który akceptuje parametr typu string i wyświetla ciąg w domyślnym rejestrowania urządzenia.  
  
#### <a name="to-define-the-echo-task"></a>Aby zdefiniować zadania Echo  
  
1.  W edytorze kodu Zastąp Hello zadań i TestBuild docelowych przy użyciu następującego kodu.  
  
    ```xml  
    <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup>  
        <Text Required="true" />  
      </ParameterGroup>  
      <Task>  
        <Code Type="Fragment" Language="cs">  
          Log.LogMessage(Text, MessageImportance.High);  
        </Code>  
      </Task>  
    </UsingTask>  
    <Target Name="TestBuild">  
      <Echo Text="Greetings!" />  
    </Target>  
    ```  
  
2.  W **okno wiersza polecenia**, typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie to procesów docelowych domyślne TestBuild, który wywołuje zadań Echo.  
  
3.  Sprawdź dane wyjściowe w **okno wiersza polecenia**. Powinien zostać wyświetlony ten wiersz:  
  
     `Greetings!`  
  
 Ten kod definiuje zadania wbudowanego nosi nazwę Echo i ma tylko jednego wymaganego parametru wejściowego tekstu. Domyślnie parametry są typu System.String. Wartość parametru tekst jest ustawiona, gdy element docelowy TestBuild wywoła zadań Echo.  
  
## <a name="defining-the-adder-task"></a>Definiowanie zadań składniki  
 Tworzenie zadania wbudowanego dodaje dwa parametry liczba całkowita, która emituje ich sumy jako właściwość MSBuild.  
  
#### <a name="to-define-the-adder-task"></a>Aby zdefiniować zadania składniki  
  
1.  W edytorze kodu Zastąp Echo zadań i TestBuild docelowych przy użyciu następującego kodu.  
  
    ```xml  
    <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup>  
        <A ParameterType="System.Int32" Required="true" />  
        <B ParameterType="System.Int32" Required="true" />  
        <C ParameterType="System.Int32" Output="true" />  
      </ParameterGroup>  
      <Task>  
        <Code Type="Fragment" Language="cs">  
          C = A + B;  
        </Code>  
      </Task>  
    </UsingTask>    
    <Target Name="TestBuild">  
      <Adder A="4" B="5">  
        <Output PropertyName="Sum" TaskParameter="C" />  
      </Adder>  
      <Message Text="The sum is $(Sum)" Importance="High" />  
    </Target>  
    ```  
  
2.  W **okno wiersza polecenia**, typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie to procesów docelowych domyślne TestBuild, który wywołuje zadań Echo.  
  
3.  Sprawdź dane wyjściowe w **okno wiersza polecenia**. Powinien zostać wyświetlony ten wiersz:  
  
     `The sum is 9`  
  
 Ten kod definiuje zadania wbudowanego o nazwie moduł ma dwa wymagane parametry wejściowe całkowitą, A i B, i jeden argument wyjściowy parametru-C. Zadanie moduł dodaje dwa parametry wejściowe i zwraca sumę w parametr wyjściowy. Suma jest emitowany jako właściwość MSBuild `Sum`. Wartości parametrów wejściowych są ustawiane podczas docelowej TestBuild wywołuje moduł zadań.  
  
## <a name="defining-the-regx-task"></a>Definiowanie zadań RegX  
 Tworzenie zadania wbudowanego akceptuje grupy elementów i wyrażenie regularne, która zwraca listę wszystkich elementów, które mają zawartość pliku, który jest zgodny z wyrażeniem.  
  
#### <a name="to-define-the-regx-task"></a>Aby zdefiniować zadania RegX  
  
1.  W edytorze kodu Zastąp metoda dodająca zadań i TestBuild docelowych przy użyciu następującego kodu.  
  
    ```xml  
    <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >  
      <ParameterGroup>  
        <Expression Required="true" />  
        <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />  
        <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />  
      </ParameterGroup>  
      <Task>  
        <Using Namespace="System.Text.RegularExpressions"/>  
        <Code Type="Fragment" Language="cs">  
    <![CDATA[  
          if (Files.Length > 0)  
          {  
            Result = new TaskItem[Files.Length];  
            for (int i = 0; i < Files.Length; i++)  
            {  
              ITaskItem item = Files[i];  
              string path = item.GetMetadata("FullPath");  
              using(StreamReader rdr = File.OpenText(path))  
              {  
                if (Regex.Match(rdr.ReadToEnd(), Expression).Success)  
                {  
                  Result[i] = new TaskItem(item.ItemSpec);  
                }  
              }  
            }  
          }  
    ]]>  
        </Code>  
      </Task>  
    </UsingTask>    
    <Target Name="TestBuild">  
      <RegX Expression="public|protected" Files="@(Compile)">  
        <Output ItemName="MatchedFiles" TaskParameter="Result" />  
      </RegX>  
      <Message Text="Input files: @(Compile)" Importance="High" />  
      <Message Text="Matched files: @(MatchedFiles)" Importance="High" />  
    </Target>  
    ```  
  
2.  W **okno wiersza polecenia**, typ **msbuild** bez przełączników polecenia, a następnie naciśnij klawisz ENTER. Domyślnie to procesów docelowych domyślne TestBuild, który wywołuje zadań RegX.  
  
3.  Sprawdź dane wyjściowe w **okno wiersza polecenia**. Powinny pojawić się następujące wiersze:  
  
     `Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs`  
  
     `Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs`  
  
 Ten kod definiuje zadania wbudowanego nosi nazwę RegX i ma trzy następujące parametry:  
  
-   `Expression`jest wymagany ciąg. parametr wejściowy, który ma wartość wyrażenia regularnego do dopasowania. W tym przykładzie wyrażenie odpowiada wyrazy "public" lub "protected".  
  
-   `Files`jest wymagany element listy wejściowej parametr ma wartość, która znajduje się lista plików, które mają być wyszukiwane dopasowania. W tym przykładzie `Files` ma ustawioną wartość `Compile` elementu, który zawiera pliki źródłowe projektu.  
  
-   `Result`to parametr wyjściowy, który ma wartość, która jest to lista plików, które mają zawartość, która odpowiada wyrażeniu regularnemu.  
  
 Wartości parametrów wejściowych jest ustawiana, jeśli element docelowy TestBuild wywołuje zadań RegX. Zadanie RegX odczytuje każdego pliku i zwraca listę plików, które odpowiada wyrażeniu regularnemu. Ta lista jest zwracana jako `Result` parametru wyjściowego, który jest emitowany elementu MSBuild `MatchedFiles`.  
  
### <a name="handling-reserved-characters"></a>Obsługa zastrzeżone znaki  
 Analizator MSBuild przetwarza zadania wbudowane jako XML. Znaki, które mają zastrzeżone znaczenie w formacie XML, na przykład "\<" i ">" Wykryto i obsługi, tak jakby były to XML, a nie kodu źródłowego .NET,. Aby uwzględnić zarezerwowanych znaków w wyrażeniach kodu takie jak `Files.Length > 0`, zapisać `Code` element, aby jego zawartości znajdują się w wyrażeniu CDATA w następujący sposób:  
  
 `<Code Type="Fragment" Language="cs">`  
  
 `<![CDATA[`  
  
 `// Your code goes here.`  
  
 `]]>`  
  
 `</Code>`  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania wbudowane](../msbuild/msbuild-inline-tasks.md)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)
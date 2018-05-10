---
title: 'Porady: Określanie kompilacji zdarzeń (C#)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 38f8240d0e0157edd1ebe189d0eafac54be60ebb
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-specify-build-events-c"></a>Porady: Określanie kompilacji zdarzeń (C#)

Korzystanie ze zdarzeń kompilacji Aby określić polecenie, które są uruchamiane przed rozpoczęciem kompilacji lub po zakończeniu kompilacji. Zdarzenia kompilacji są wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji.

Po utworzeniu projektu zdarzenia prekompilacyjnego zostaną dodane do pliku o nazwie *PreBuildEvent.bat* i zdarzenia postkompilacyjnego są dodawane do pliku o nazwie *PostBuildEvent.bat*. Jeśli chcesz upewnić się, sprawdzanie błędów, należy dodać własne polecenia Sprawdzanie błędów do kroków kompilacji.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak określać zdarzenia prekompilacyjnego i mające miejsce po kompilacji

### <a name="to-specify-a-build-event"></a>Aby określić zdarzenia kompilacji

1.  W **Eksploratora rozwiązań**, wybierz projekt, dla którego ma zostać określone zdarzenie kompilacji.

2.  Na **projektu** menu, kliknij przycisk **właściwości**.

3.  Wybierz **zdarzeń kompilacji** kartę.

4.  W **wiersz polecenia zdarzenia prekompilacyjnego** Określ składni zdarzenia kompilacji.

    > [!NOTE]
    > Jeśli projekt jest aktualny i kompilacji nie zostanie wywołany, nie należy uruchamiać zdarzenia prekompilacyjnego.

5.  W **wiersz polecenia zdarzenia po kompilacji** Określ składni zdarzenia kompilacji.

    > [!NOTE]
    > Dodaj `call` instrukcję przed wszystkie postkompilacyjnego polecenia, które uruchamiają *bat* plików. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

6.  W **uruchomić zdarzenie mające miejsce po kompilacji** Określ na jakich warunkach, aby uruchomić zdarzenie mające miejsce po kompilacji.

    > [!NOTE]
    > Aby dodać długiej składni lub wybierz dowolne makra z kompilacji [okno dialogowe wiersza polecenia zdarzenia/po kompilacji — zdarzenia prekompilacyjnego](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), kliknij przycisk oznaczony wielokropkiem (**...** ) do wyświetlenia w polu edycji.

     Składnia zdarzeń kompilacji może zawierać dowolne polecenie, które jest prawidłowa, w wierszu polecenia lub w *bat* pliku. Nazwa pliku wsadowego powinien być poprzedzony `call` aby upewnić się, że wszystkie kolejne polecenia są wykonywane.

    > [!NOTE]
    > Jeśli Twoje zdarzenia prekompilacyjnego lub mające miejsce po kompilacji nie zakończy się pomyślnie, można zakończyć kompilacji przez akcję zdarzeń zamknąć przy użyciu kodu innego niż zero (0), wskazujący pomyślne akcji.

## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Przykład: Jak zmiana informacji manifestu za pomocą zdarzenie mające miejsce po kompilacji

Poniższa procedura pokazuje, jak ustawić minimalnej wersji systemu operacyjnego w manifeście aplikacji przy użyciu *.exe* polecenia, która jest wywoływana z zdarzenia postkompilacyjnego ( *. exe.manifest* w pliku katalog projektu). Minimalna wersja systemu operacyjnego jest liczbą czteroczęściową, takich jak 4.10.0.0. Aby to zrobić, zmieni polecenie `<dependentOS>` sekcji manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Aby utworzyć polecenie .exe, aby zmienić manifest aplikacji

1.  Utwórz aplikację konsoli dla polecenia. Z **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.

2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#**, kliknij przycisk **Windows**, a następnie kliknij przycisk **aplikacji konsoli** szablonu. Nazwij projekt `ChangeOSVersionCS`.

3.  W *Program.cs*, Dodaj następujący wiersz do drugiego `using` instrukcje w górnej części pliku:

    ```csharp
    using System.Xml;
    ```

4.  W `ChangeOSVersionCS` przestrzeni nazw, Zastąp `Program` Implementacja klasy następującym kodem:

    ```csharp
    class Program
    {
       /// <summary>
       /// This function will set the minimum operating system version for a ClickOnce application.
       /// </summary>
       /// <param name="args">
       /// Command Line Arguments:
       /// 0 - Path to application manifest (.exe.manifest).
       /// 1 - Version of OS
       ///</param>
       static void Main(string[] args)
       {
          string applicationManifestPath = args[0];
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

          // Get version name.
          Version osVersion = null;
          if (args.Length >=2 ){
             osVersion = new Version(args[1]);
          }else{
             throw new ArgumentException("OS Version not specified.");
          }
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());

          XmlDocument document;
          XmlNamespaceManager namespaceManager;
          namespaceManager = new XmlNamespaceManager(new NameTable());
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

          document = new XmlDocument();
          document.Load(applicationManifestPath);

          string baseXPath;
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

          // Change minimum required operating system version.
          XmlNode node;
          node = document.SelectSingleNode(baseXPath, namespaceManager);
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

          document.Save(applicationManifestPath);
       }
    }
    ```

     Polecenie przyjmuje dwa argumenty: ścieżka manifest aplikacji (oznacza to, że folder, w którym proces kompilacji tworzy manifestu, zwykle *Projectname.publish*), a nowa wersja systemu operacyjnego.

5.  Skompiluj projekt. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

6.  Kopiuj *.exe* pliku do katalogu, takie jak *C:\TEMP\ChangeOSVersionVB.exe*.

 Następnie wywołaj tego polecenia zdarzenia po kompilacji, aby zmodyfikować manifest aplikacji.

### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Aby wywołać zdarzenia postkompilacyjnego, aby zmodyfikować manifest aplikacji

1.  Tworzenie aplikacji systemu Windows dla projektu do opublikowania. Z **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.

2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#**, kliknij przycisk **klasycznego pulpitu systemu Windows**, a następnie kliknij przycisk **aplikacji formularzy systemu Windows** szablon. Nazwij projekt `CSWinApp`.

3.  W projekcie wybrana w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

4.  W **projektanta projektu**, zlokalizuj **publikowania** strony i ustaw **publikowania lokalizacji** do *C:\TEMP*.

5.  Publikowanie projektu, klikając **opublikować teraz**.

     Plik manifestu zostanie utworzony i umieścić w *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Aby wyświetlić plik manifestu, kliknij prawym przyciskiem myszy plik, kliknij przycisk **Otwórz za pomocą**, wybierz pozycję **wybierz program z listy**, a następnie kliknij przycisk **Notatnik**.

     Wyszukaj w pliku `<osVersionInfo>` elementu. Na przykład może być wersji:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6.  W **projektanta projektu**, kliknij przycisk **zdarzeń kompilacji** i kliknij polecenie **Edytuj postkompilacyjnego** przycisku.

7.  W **wiersz polecenia zdarzenia po kompilacji** wpisz następujące polecenie:

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     Podczas tworzenia projektu, to polecenie spowoduje zmianę minimalnej wersji systemu operacyjnego w manifeście aplikacji na 5.1.2600.0.

     Ponieważ `$(TargetPath)` makro wyraża pełnej ścieżki pliku wykonywalnego tworzone `$(TargetPath)` *manifest* będzie określać utworzone w manifeście aplikacji *bin* katalogu. Publikowanie skopiuje tego manifestu ustawionych wcześniej lokalizację publikowania.

8.  Ponownie opublikować projekt. Przejdź do **publikowania** i kliknij przycisk **opublikować teraz**.

     Ponownie wyświetlić manifestu. Aby wyświetlić plik manifestu, otwórz katalog publikacji, kliknij prawym przyciskiem myszy plik, kliknij przycisk **Otwórz z**, wybierz pozycję **wybierz program z listy**, a następnie kliknij przycisk **Notatnik**.

     Teraz należy odczytać wersji:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Zobacz także

- [Strona zdarzenia kompilacji, Projektant projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Okno dialogowe wiersza polecenia zdarzenia/po kompilacji — zdarzenia prekompilacyjnego](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Porady: Określanie kompilacji zdarzenia (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilowanie i kompilacji](../ide/compiling-and-building-in-visual-studio.md)
---
title: "Dodawanie rozszerzenia protokołu serwera języka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ea93ddee9c47f80322db2403aeecc0fb7dddb209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="adding-a-language-server-protocol-extension"></a>Dodawanie rozszerzenia języka protokół serwera

Protokół serwera języka (LSP) jest wspólny protokół w formie v2.0 wywołania RPC JSON, używane do zapewnienia języka funkcji usługi różne edytory kodu. Przy użyciu protokołu, programiści mogą pisać serwer jednego języka aby podać języka funkcji usługi, takie jak IntelliSense, diagnostyki błędów, Znajdź wszystkie odwołania, itp., aby różne edytory kodu, które obsługują LSP. Tradycyjnie, można dodać usługi językowe w programie Visual Studio, albo przy użyciu plików gramatyki TextMate, aby zapewnić podstawowe funkcje, takie jak wyróżnianie składni lub za pomocą usług języków niestandardowych przy użyciu pełnego zestawu interfejsów API rozszerzania programu Visual Studio do Podaj dokładniejsze dane. Teraz obsługa LSP oferuje trzecia opcja.

![Usługa protokołu języka serwera w programie Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protokół serwera języka

Aby uzyskać więcej informacji dotyczących samego protokołu, zobacz dokumentację [tutaj](https://github.com/Microsoft/language-server-protocol). Implementacja programu Visual Studio języka serwera protokołu jest w wersji zapoznawczej i pomocy technicznej należy traktować jako eksperymentalne. Wersja zapoznawcza ma postać rozszerzenia ([języka serwera protokołu klient w wersji zapoznawczej](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)), **, ale tego rozszerzenia można zainstalować tylko na podglądu kanału programu Visual Studio**. Nowsza wersja programu Visual Studio będzie zawierać wbudowaną obsługę języka serwera protokołu, po tym czasie zostaną usunięte flagi wersji zapoznawczej. **Wersja zapoznawcza nie należy używać do celów produkcyjnych.**

Aby uzyskać więcej informacji na temat tworzenia przykładowym serwerem języka lub jak zintegrować z istniejącego serwera języka Visual Studio Code, zobacz dokumentację [tutaj](https://code.visualstudio.com/docs/extensions/example-language-server).

![Implementacja protokołu serwera języka](media/lsp-implementation.png)

W tym artykule opisano sposób tworzenia rozszerzenia programu Visual Studio, które korzysta z serwera na podstawie LSP języka. Przyjęto założenie, że został już utworzony na podstawie LSP języka serwera i po prostu chcesz zintegrować ją z programu Visual Studio.

Aby uzyskać pomoc w programie Visual Studio serwery języka może komunikować się z klienta (Visual Studio) przy użyciu następujących mechanizmów:

* Standardowe we/wy strumieni
* Nazwane potoki
* Gniazda

Celem LSP i pomocy technicznej dla niego w programie Visual Studio jest dołączyć języka usług, które nie są częścią produktu Visual Studio. Nie jest on przeznaczony do rozszerzania istniejących usług języka (na przykład C#) w programie Visual Studio. Aby rozszerzyć istniejącą języków, można znaleźć w podręczniku rozszerzalności usługi języka (na przykład [platformy kompilatora .NET "Roslyn"](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

## <a name="language-server-protocol-features-supported"></a>Obsługiwane funkcje protokołu serwera języka

Następujące funkcje LSP są obsługiwane w programie Visual Studio do tej pory:

Komunikat | Obsługuje w programie Visual Studio
--- | ---
Inicjowanie | Tak
zainicjowana | Tak
shutdown | Tak
Zakończ | Tak
$/ cancelRequest | Tak
Okno/showMessage | Tak
Okno/showMessageRequest | Tak
Okno/logMessage | Tak
dane telemetryczne lub zdarzenia |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | Tak
workspace/didChangeWatchedFiles | Tak
obszar roboczy/symbol | Tak
workspace/executeCommand | Tak
obszar roboczy/applyEdit | Tak
textDocument/publishDiagnostics | Tak
textDocument/didOpen | Tak
textDocument/didChange | Tak
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | Tak
textDocument/didClose | Tak
textDocument/zakończenia | Tak
uzupełnianie/Rozwiąż | Tak
textDocument/aktywowany | Tak
textDocument/signatureHelp | Tak
textDocument/odwołań | Tak
textDocument/documentHighlight |
textDocument/documentSymbol | Tak
textDocument/formatowania | Tak
textDocument/rangeFormatting | Tak
textDocument/onTypeFormatting |
textDocument/definicji | Tak
textDocument/codeAction | Tak
textDocument/codeLens |
Rozwiąż/codeLens |
textDocument/documentLink |
documentLink/resolve |
textDocument/Zmień nazwę | Tak

## <a name="getting-started"></a>Wprowadzenie

### <a name="create-a-vsix-project"></a>Tworzenie projektu VSIX

Aby utworzyć rozszerzenia usługi języka, używany jest serwer oparty na LSP język, najpierw upewnij się, masz **tworzenia rozszerzenia programu Visual Studio** obciążenia zainstalowane dla wystąpienia programu VS.

Następnie utworzyć nowe VSIXProject puste, przechodząc do **pliku** > **nowy projekt** > **Visual C#**  >   **Rozszerzalność** > **projektu VSIX**:

![Tworzenie projektu vsix](media/lsp-vsix-project.png)

W wersji zapoznawczej będzie VS obsługę LSP w formie VSIX ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). W tym pliku VSIX rozszerzenia deweloperów, którzy do utworzenia rozszerzenia przy użyciu serwerów języka LSP należy przełączyć zależności. W związku z tym klienci chcą zainstalować rozszerzenie serwera języka **, należy najpierw zainstalować język serwera protokołu klient w wersji zapoznawczej VSIX.**

Aby zdefiniować zależności VSIX, otwórz projektanta manifestu VSIX dla Twojego VSIX (przez dwukrotne kliknięcie pliku source.extension.vsixmanifest w projekcie) i przejdź do **zależności**:

![Dodaj odwołanie do klienta protokołu serwera języka](media/lsp-reference-lsp-dependency.png)

Utwórz nową zależność podobne do poniższych:

![Definiowanie zależności klienta protokołu serwera języka](media/lsp-define-lsp-dependency.png)

* **Źródło**: definiowane ręcznie
* **Nazwa**: język serwera protokołu klient w wersji zapoznawczej
* **Identifier**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Zakres wersji**: [1.0,2.0)
* **W jaki sposób zależności**: instalowane przez użytkownika
* **Adres URL pobierania**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> **Pobierz adres URL** musi zostać wypełnione, dlatego użytkownicy instalujący rozszerzenie wiedzieć, jak zainstalować wymaganej zależności.

### <a name="language-server-and-runtime-installation"></a>Instalacja serwera i środowiska uruchomieniowego języka

Domyślnie rozszerzenia utworzone w celu obsługi języka LSP serwerów w programie Visual Studio nie będzie zawierać samych serwerach języka lub środowisk uruchomieniowych, konieczne jest wykonanie ich. Deweloperzy rozszerzenia są odpowiedzialne za dystrybucję serwerów języka i środowiska wykonawczego, potrzebne. Istnieje kilka sposobów, aby to zrobić:

* Język serwery mogą być osadzone w pliku VSIX jako pliki zawartości.
* Utwórz Instalatora MSI w celu zainstalowania języka serwera i/lub potrzeby środowisk uruchomieniowych.
* Zawierają instrukcje w witrynie Marketplace informowania użytkowników uzyskiwania serwerów środowisk uruchomieniowych i języka.

### <a name="textmate-grammar-files"></a>Pliki gramatyki TextMate

LSP nie zawiera specyfikację dostarczania tekstu kolorowania języków. Aby podać niestandardowy kolorowania języków w programie Visual Studio, rozszerzenia deweloperzy mogą używać TextMate pliku gramatyki. Aby dodać niestandardowe pliki TextMate motywu lub gramatyki, wykonaj następujące kroki:

1. Utwórz folder o nazwie "Gramatykach" wewnątrz rozszerzenia (lub może być niezależnie od nazwy).

2. W folderze "Gramatykach" obejmują *.tmlanguage, *.plist, *.tmtheme lub pliki *.json, którą chcesz udostępniających kolorowania niestandardowych.

3. Kliknij prawym przyciskiem myszy na pliki i wybierz **właściwości**. Zmiany akcji kompilacji na **zawartości** i **Include w pliku VSIX** właściwości na wartość true.

4. Utwórz plik .pkgdef i Dodaj wiersz podobny do poniższego:

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Kliknij prawym przyciskiem myszy na pliki i wybierz **właściwości**. Zmiany akcji kompilacji na **zawartości** i **Include w pliku VSIX** właściwości na wartość true.

Po wykonaniu poprzednich kroków, zostanie dodany folder "Gramatykach" do pakietu instalacji katalogu jako źródło repozytorium o nazwie "MyLang" ("MyLang" jest tylko nazwa na Uściślanie i może być dowolnym ciągiem unikatowy). Wszystkie gramatyki (pliki .tmlanguage) i motyw plików (.tmtheme) w tym katalogu są pobrana jako możliwości i zastępują wbudowane gramatyki, wyposażone w TextMate. Jeśli pliku gramatyki zadeklarowane rozszerzenia są zgodne z rozszerzeniem otwierany plik, TextMate będzie kroku.

## <a name="creating-a-simple-language-client"></a>Tworzenie prostego języka klienta

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Interfejs main - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Po utworzeniu projektu VSIX, należy dodać następujące pakiety NuGet do projektu:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Po wykonaniu zależność od pakietu NuGet po wykonaniu poprzednich kroków, pakiety Newtonsoft.Json i StreamJsonRpc są dodawane do projektu również. **Nie Aktualizuj te pakiety, chyba że masz pewność, że te nowe wersje zostanie zainstalowany w wersji programu Visual Studio który celów rozszerzenia**. Zestawy nie zostanie uwzględniony w Twojej VSIX — zamiast tego one będą zostać pobrana z katalogu instalacyjnego programu Visual Studio. Jeśli utworzono odwołanie do nowszej wersji zestawów niż zainstalowana na komputerze użytkownika, Twoje rozszerzenie *nie będzie działać*.

Następnie możesz utworzyć nową klasę, która implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) interfejsu, głównego interfejsu potrzebne dla języka klientów nawiązujących połączenie z serwerem LSP oparty na język.

Oto przykład:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Metody main, które muszą zostać zaimplementowane są [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) i [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) jest wywoływane, gdy program Visual Studio został załadowany rozszerzenia i serwer języka jest gotowy do uruchomienia. W przypadku tej metody można wywoływać [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegata natychmiast, która sygnalizuje, że serwera języka, należy uruchomić, lub wykonaj dodatkową logikę i wywołania [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) później. **Aby uaktywnić serwer języka, należy wywołać StartAsync w pewnym momencie.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) jest ostatecznie wywoływane przez wywołanie metody [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegata; zawiera logikę do uruchomienia serwera języka i nawiązywania połączenia z nią. Musi zostać zwrócony obiekt połączenia, który zawiera strumieni zapisywania na serwerze i odczytywania danych z serwera. Wszelkie wyjątki zgłaszane w tym miejscu są przechwycony i widoczny dla użytkownika za pośrednictwem komunikat informacyjny w programie Visual Studio.

### <a name="activation"></a>Aktywacja

Po zaimplementowaniu klasy klienta języka należy zdefiniować dwa atrybuty na jej definiują sposób będą ładowane do programu Visual Studio i aktywować:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio będzie korzystać [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) do zarządzania jego punkty rozszerzeń. [Wyeksportować](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) atrybut wskazuje dla programu Visual Studio, czy ta klasa powinny być pobrana jako punkt rozszerzenia i załadowany w odpowiednim czasie.

Aby użyć MEF, również muszą definiować MEF jako zasób w manifeście VSIX.

Otwarcie z projektanta manifestu VSIX i przejdź do **zasoby** karty:

![Dodawanie zasobów MEF](media/lsp-add-asset.png)

Kliknij nowy, aby utworzyć nowego elementu zawartości:

![Zdefiniuj MEF zasobów](media/lsp-define-asset.png)

* **Type**: Microsoft.VisualStudio.MefComponent
* **Źródło**: Projekt w bieżącym rozwiązaniu
* **Projekt**: [project]

### <a name="content-type-definition"></a>Definicja typu zawartości

Obecnie jedynym sposobem, aby załadować rozszerzenia serwera na podstawie LSP języka jest typ zawartości pliku. Oznacza to, że podczas definiowania klasy klienta języka (z zaimplementowanym [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), należy zdefiniować typy plików, gdy otwarty, spowoduje, że można załadować rozszerzenia. Jeśli nie pliki, które spełniają Twoje zdefiniowanego typu zawartości są otwierane, rozszerzenia nie można załadować.

Można to zrobić za pośrednictwem zdefiniowania co najmniej jednej klasy ContentTypeDefinition:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

W poprzednim przykładzie, definicja typu zawartości jest tworzona dla plików, które kończą się `.bar` rozszerzenia pliku. Definicja typu zawartości znajduje się nazwa "pasek" i **musi** pochodzi od [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Po dodaniu definicja typu zawartości, można następnie określić, kiedy można załadować rozszerzenia klienta języka w języku klasy klienta:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Dodawanie obsługi dla serwerów języka LSP nie wymaga wdrożenia systemu projektu programu Visual Studio. Klientów można otworzyć pojedynczy plik lub folder, w programie Visual Studio, aby rozpocząć korzystanie z usługi języka. W rzeczywistości Obsługa serwerów języka LSP jest przeznaczona do pracy tylko w scenariuszach, otwórz folderów i plików. Jeśli system projektu niestandardowy jest zaimplementowana, niektóre funkcje (takie jak ustawienia) nie będzie działać.

## <a name="advanced-features"></a>Funkcje zaawansowane

### <a name="settings"></a>Ustawienia

Obsługa niestandardowe ustawienia językowe serwera jest dostępna dla wersji zapoznawczej LSP obsługi w programie Visual Studio, ale jest nadal w trakcie ulepszana. Ustawienia są specyficzne dla co serwer języka obsługuje i zwykle kontroli, jak serwer języka emituje danych. Na przykład serwer język może być ustawienie maksymalnej liczby błędów. Autorzy rozszerzenia zdefiniowane wartości domyślne, która może zostać zmieniona przez użytkowników do określonych projektów.

Wykonaj te kroki, aby dodać obsługę ustawień do rozszerzenia usługi języka LSP:

1. Dodaj plik JSON (na przykład "MockLanguageExtensionSettings.json") w projekcie, który zawiera ustawienia i wartości domyślnych. Na przykład:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Kliknij prawym przyciskiem myszy plik JSON, a następnie wybierz **właściwości**. Zmień **kompilacji** akcji "Zawartość" i "Include w pliku VSIX" właściwości na wartość true.

3. Implementowanie elementów ConfigurationSections i zwraca listę prefiksów dla ustawień zdefiniowanych w pliku JSON (w programie Visual Studio Code, to czy mapowania na nazwę sekcji konfiguracji w pliku package.json):

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Dodaj plik .pkgdef do projektu (Dodaj nowy plik tekstowy i zmień rozszerzenie pliku .pkgdef). Plik pkgdef powinien zawierać te informacje:

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Kliknij prawym przyciskiem myszy plik .pkgdef i wybierz **właściwości**. Zmień **kompilacji** akcji "Zawartość" i właściwości "Obejmują w pliku VSIX" na wartość true.

6. Otwórz `source.extension.vsixmanifest` i Dodaj zasób w **zasobów** karty:

  ![Edytuj pakiet vspackage zasobów](media/lsp-add-vspackage-asset.png)

  * **Type**: Microsoft.VisualStudio.VsPackage
  * **Źródło**: pliku w systemie plików
  * **Ścieżka**: [ścieżka do pliku pkgdef]

### <a name="user-editing-of-settings-for-a-workspace"></a>Edytowanie użytkownika ustawień obszaru roboczego

1. Użytkownik otwiera zawierający pliki, których właścicielem jest serwer obszaru roboczego.
2. Użytkownik dodaje plik w folderze ".vs" o nazwie "VSWorkspaceSettings.json".
3. Użytkownik dodaje wiersza do pliku VSWorkspaceSettings.json ustawienia, które są udostępniane przez serwer. Na przykład:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>Włączanie śledzenia diagnostyki
Śledzenie diagnostyczne można włączyć do wyjściowego wszystkie wiadomości między klientem a serwerem, które mogą być przydatne podczas debugowania problemów.  Aby włączyć śledzenie diagnostyczne, wykonaj następujące czynności:

1. Otwarcia lub utworzenia pliku ustawień obszaru roboczego "VSWorkspaceSettings.json" (zobacz "Użytkownika edycji ustawień obszaru roboczego").
2. Dodaj następujący wiersz w pliku json ustawień:

```json
{
    "foo.server.trace": "Off"
}
```

Istnieją trzy możliwe wartości szczegółowości śledzenia:
* "Wyłączone": całkowicie wyłączyć śledzenie
* "Wiadomości": śledzenie włączona, ale identyfikator jedyną metodą nazwy i odpowiedzi są śledzone.
* "Pełny": śledzenie włączony; komunikat rpc całego są śledzone.

Po włączeniu na zawartość śledzenia są zapisywane do pliku w katalogu "% temp%\VisualStudio\LSP".  Dziennik zgodne z formatem nazewnictwa `[LanguageClientName]-[Datetime Stamp].log`.  Obecnie śledzenie można włączyć tylko w scenariuszach, otwórz folder.  Otwieranie jeden plik, aby uaktywnić serwer języka nie ma diagnostyki śledzenia pomocy technicznej.

### <a name="custom-messages"></a>Niestandardowe komunikaty

Brak interfejsów API w miejscu, w celu ułatwienia przekazywanie komunikatów i odbieranie wiadomości z serwera języka, które nie są częścią protokołu server standard języka. Do obsługi komunikatów niestandardowych, należy zaimplementować [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfejsu w klasie klienta języka. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) biblioteki jest używany do przesyłania niestandardowych komunikatów między języka klienta i serwera języka. Ponieważ rozszerzenia klienta języka LSP podobnie jak inne rozszerzenie programu Visual Studio, można dodać dodatkowe funkcje (nie są obsługiwane przez LSP) dla programu Visual Studio (przy użyciu innych Visual Studio interfejsów API) w rozszerzenia za pomocą niestandardowych komunikatów.

#### <a name="receiving-custom-messages"></a>Odbieranie komunikatów niestandardowych

Do odbierania wiadomości niestandardowych z serwera języka, należy zaimplementować [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) właściwość [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) i zwraca obiekt, który potrafi obsłużyć wiadomości niestandardowych . Przykład poniżej:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Wysyłanie wiadomości niestandardowych

Do wysyłania niestandardowych wiadomości do serwera języka, należy zaimplementować [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) metoda [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Ta metoda jest wywoływana, gdy serwer języka jest uruchomiona i gotowa do odbierania wiadomości. A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) obiekt został przekazany jako parametr, który można następnie zachować do wysyłania wiadomości przy użyciu serwera języka [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) interfejsów API. Przykład poniżej:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Warstwa środkowa

Czasami programisty rozszerzenia można przechwytywać LSP wiadomości wysyłane do i odbierane z serwera języka. Programisty rozszerzenia może na przykład chcesz zmienić parametr wiadomości wysłane dla danego komunikatu LSP lub zmodyfikuj wyniki zwrócone z serwera języka dla funkcji LSP (na przykład zakończeń). Jeśli jest to niezbędne, rozszerzenia deweloperzy mogą używać interfejsu API MiddleLayer przechwycenia LSP wiadomości.

Każdy komunikat LSP ma własny interfejs warstwy środkowej do przechwycenia. Przechwycenia danej wiadomości, Utwórz klasę, która implementuje interfejs warstwy środkowej dla tej wiadomości. Następnie należy zaimplementować [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) interfejsu w klasie klienta języka i zwrócić wystąpienia obiektu w [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) właściwości. Przykład poniżej:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Funkcja warstwy środkowej jest nadal w fazie tworzenia i nie jest jeszcze kompleksowe.

## <a name="sample-lsp-language-server-extension"></a>Rozszerzenie serwera języka LSP próbki

Aby wyświetlić kod źródłowy Przykładowe rozszerzenie za pomocą klienta LSP interfejsu API w programie Visual Studio, zobacz przykłady w przypadku rozszerzania VSSDK [próbki LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Najczęściej zadawane pytania

**Chcę Tworzenie niestandardowych projektu systemu uzupełnienie serwer LSP języka aby zapewnić bardziej zaawansowane funkcje obsługi różnych funkcji w programie Visual Studio, jak przejść o operacją?**

Obsługa języka LSP serwerów w programie Visual Studio polega na [funkcja otwierania folderu](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) i specjalnie z myślą o nie wymagają systemu niestandardowe projektu. Można tworzyć własne niestandardowe projektu systemu instrukcjami [tutaj](https://github.com/Microsoft/VSProjectSystem), ale niektóre funkcje, takie jak ustawienia, może nie działać. Domyślna logika inicjowania dla serwerów języka LSP jest do przekazania w lokalizacji folderu głównego folderu, w obecnie otwierany, dlatego jeśli używasz systemu niestandardowy projekt może być konieczne podanie niestandardowej logiki podczas inicjowania, aby upewnić się, możesz serwera języka prawidłowo uruchomić.

**Jak dodać obsługę debugera?**

Firma Microsoft będzie dostarczać obsługę [wspólnej debugowania protokołu](https://code.visualstudio.com/docs/extensionAPI/api-debugging) w przyszłej wersji.

**Jeśli istnieje już VS obsługiwanego języka zainstalowanej usługi (na przykład JavaScript), można nadal zainstalować rozszerzenie serwera LSP języka, który udostępnia dodatkowe funkcje (na przykład linting)?**

Tak, ale nie wszystkie funkcje będą działać prawidłowo. Dla rozszerzeń serwera języka LSP ostatecznym celem jest umożliwienie usługi języka nieobsługiwane natywnie przez program Visual Studio. Można utworzyć rozszerzenia, które oferują dodatkowe wsparcie przy użyciu LSP języka serwerów, ale niektóre funkcje (takie jak IntelliSense) nie będzie smooth środowisko. Ogólnie rzecz biorąc zaleca się stosowanie rozszerzeń serwera języka LSP udostępnia nowe funkcje języka, nie rozszerzanie istniejących.

**Gdzie publikować ukończone serwer języka LSP VSIX?**

Zapoznaj się z instrukcjami Marketplace [tutaj](walkthrough-publishing-a-visual-studio-extension.md).

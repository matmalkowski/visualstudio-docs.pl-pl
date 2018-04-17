---
title: 'Porady: Podaj usługa asynchronicznego programu Visual Studio | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b4754ccf4a7a66151ad8fb351996c1520dc9483c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Porady: Podaj usługa asynchronicznego programu Visual Studio
Jeśli chcesz uzyskać usługi bez blokowania wątku interfejsu użytkownika, należy utworzyć asynchroniczne usługi i załadować pakiet wątku w tle. W tym celu można użyć <xref:Microsoft.VisualStudio.Shell.AsyncPackage> zamiast <xref:Microsoft.VisualStudio.Shell.Package>i Dodaj usługę z pakietu asynchroniczne specjalnych metod asynchronicznych.
  
 Aby dowiedzieć się, jak udostępnia synchroniczne usługi Visual Studio, zobacz [porady: świadczenia usługi](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Wdrażanie usługi asynchroniczne  
  
1.  Tworzenie projektu VSIX (**Plik > Nowy > Projekt > Visual C# > Extensiblity > projektu VSIX**). Nazwij projekt **TestAsync**.  
  
2.  Dodaj pakiet VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj > Nowy element > Visual C# elementów > rozszerzalności > pakiet programu Visual Studio**. Nazwij ten plik **TestAsyncPackage.cs**.  
  
3.  W TestAsyncPackage.cs Zmień pakietu, który ma dziedziczyć AsyncPackage zamiast pakietu:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Aby wdrożyć usługę, należy utworzyć trzy typy:  
  
    -   Interfejs, który identyfikuje usługę. Wiele z tych interfejsów jest pusty, oznacza to, ponieważ mają one żadnych metod jako są używane tylko podczas wykonywania zapytań usługi.
  
    -   Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody służące do zaimplementowania.  
  
    -   Klasa, która implementuje zarówno usługi, jak i interfejs usługi.  
  
5.  Poniższy przykład przedstawia bardzo proste wykonania trzech typów. Konstruktor klasy usługi, należy ustawić dostawcy usług. W tym przykładzie tylko dodamy usługi do pliku pakietu kodu.  
  
6.  Dodaj następujące instrukcje using do pliku pakietu:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  Oto implementacji usługi asynchronicznego. Należy zwrócić uwagę, należy ustawić dostawcę usługi asynchroniczne, a nie dostawcy usług synchroniczne w Konstruktorze:  
  
    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private IAsyncServiceProvider asyncServiceProvider;  
        
        public TextWriterService(IAsyncServiceProvider provider)  
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;  
        }
        
        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            // We have to use JoinableTaskFactory as code will switch to main thread in some parts
            await ThreadHelper.JoinableTaskFactory.RunAsync(async () =>
            {
                await TaskScheduler.Default;
                // do background operations that involve IO or other async methods
                
                await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);               
                // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
                // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.
                
                IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
                // use Visual Studio services to continue initialization
            });
        }
        
        public async Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
    }  

    public interface STextWriterService  
    {  
    }  
    
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
    }  
    ```  
  
## <a name="registering-a-service"></a>Zarejestrowanie usługi  
 Aby zarejestrować usługi, dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu, która dostarcza usługę. Zarejestrowanie synchroniczne usługi jest inny, konieczne będzie upewnij się, że zarówno pakiet, jak i usługa obsługuje asynchroniczne ładowanie:
  
-   Należy dodać **AllowsBackgroundLoading = true** do <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> w celu zapewnienia pakietu mogą być inicjowane asynchronicznie, aby uzyskać więcej informacji na temat PackageRegistrationAttribute, zobacz [rejestrowanie i Wyrejestrowywanie VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
-   Należy dodać **IsAsyncQueryable = true** do <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> aby upewnić się, wystąpienie usługi, które mogą być inicjowane asynchronicznie.

 Oto przykład AsyncPackage asynchroniczne usługi rejestracji:
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Dodawanie usługi  
  
1.  W TestAsyncPackage.cs, Usuń `Initialize()` — metoda i zastąpienie `InitializeAsync()` metody. Dodaj usługę, a następnie dodaj metodę wywołania zwrotnego do tworzenia usług. Oto przykład asynchroniczne inicjatora Dodawanie usługi:  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implementuje metody wywołania zwrotnego jako metodę asynchroniczną, które tworzy i zwraca usługę.  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="using-a-service"></a>Przy użyciu usługi  
 Teraz można pobrać usługi i używać jej metody.  
  
1.  Poniżej opisano to w inicjatora, ale można pobrać usługi dowolnym chcesz korzystać z usługi.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
  
    }  
  
    ```  
  
     Nie zapomnij zmienić  *\<userpath >* nazwę pliku i ścieżkę, która ma sens na tym komputerze!  
  
2.  Skompiluj i uruchom kod. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, otwórz rozwiązanie. Powoduje to AsyncPackage na automatyczne ładowanie. Po uruchomieniu inicjatora plik powinien znajdować się w określonej lokalizacji.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Przy użyciu usługi asynchronicznego programu obsługi poleceń  
 Poniżej przedstawiono przykład sposobu używania asynchroniczne usługi polecenia menu. Można użyć procedury pokazane do korzystania z usługi w innych metod innych niż asynchronicznych.  
  
1.  Polecenia menu Dodaj do projektu. (W **Eksploratora rozwiązań**, wybierz węzeł projektu, kliknij prawym przyciskiem myszy i wybierz **Add / nowy element / rozszerzalności / polecenia niestandardowych**.) Nazwa pliku polecenia **TestAsyncCommand.cs.**  
  
2.  Szablon polecenia niestandardowych ponownie dodaje `Initialize()` metody do pliku TestAsyncPackage.cs w celu zainicjowania polecenia. Skopiuj wiersza, który inicjuje polecenie metodę Initialize(). Go powinien wyglądać następująco:  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Ten wiersz, aby przenieść `InitializeAsync()` metody w pliku AsyncPackageForService.cs. Ponieważ jest to inicjowania asynchronicznego, musisz przełączyć się do wątku głównego przed zainicjowaniem, za pomocą polecenia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Go powinna wyglądać następująco:  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  

        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync((<userpath>, "this is a test");  
  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);
    }  
  
    ```  
  
3.  Usuń `Initialize()` metody.  
  
4.  W pliku TestAsyncCommand.cs znaleźć `MenuItemCallback()` metody. Usuń treść metody.  
  
5.  Dodaj using instrukcji:  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Dodaj metodę asynchroniczną o nazwie `UseTextWriterAsync()`, który pobiera usługi i używa jej metod:  
  
    ```csharp  
    private async System.Threading.Tasks.Task UseTextWriterAsync()  
    {  
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =   
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))  
              as ITextWriterService;  

        // don't forget to change <userpath> to a local path  
        await textService.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Wywołanie tej metody z `MenuItemCallback()` metody:  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  Skompiluj rozwiązanie i Rozpocznij debugowanie. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, przejdź do **narzędzia** menu i wyszukać **wywołania TestAsyncCommand** elementu menu. Gdy zostanie kliknięty, TextWriterService zapisuje do podanego pliku. (Nie trzeba otworzyć rozwiązanie, ponieważ wywoływanie polecenia powoduje także, że pakiet do załadowania.)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z usług i dostarczanie ich](../extensibility/using-and-providing-services.md)

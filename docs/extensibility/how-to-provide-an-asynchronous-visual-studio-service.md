---
title: "Porady: Podaj usługa asynchronicznego programu Visual Studio | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1bcf34f730411589624075bde4ace0b5457e07a7
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Porady: Podaj usługa asynchronicznego programu Visual Studio
Jeśli chcesz uzyskać usługi bez blokowania wątku interfejsu użytkownika, należy utworzyć asynchroniczne usługi i załadować pakiet wątku w tle. W tym celu można użyć <xref:Microsoft.VisualStudio.Shell.AsyncPackage> zamiast <xref:Microsoft.VisualStudio.Shell.Package>i Dodaj usługę z pakietu asynchroniczne specjalnych metod asynchronicznych  
  
 Aby dowiedzieć się, jak udostępnia synchroniczne usługi Visual Studio, zobacz [porady: świadczenia usługi](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Wdrażanie usługi asynchroniczne  
  
1.  Tworzenie projektu VSIX (**Plik > Nowy > Projekt > Visual C# > Extensiblity > projektu VSIX**). Nazwij projekt **TestAsync**.  
  
2.  Dodaj pakiet VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj > Nowy element > Visual C# elementów > rozszerzalności > pakiet programu Visual Studio**. Nazwij ten plik **TestAsyncPackage.cs**.  
  
3.  W TestAsyncPackage.cs Zmień pakietu, który ma dziedziczyć AsyncPackage zamiast pakietu:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Aby wdrożyć usługę, należy utworzyć trzy typy:  
  
    -   Interfejs, który zawiera opis usługi. Wiele z tych interfejsów jest pusty, oznacza to, ponieważ mają one żadnych metod.  
  
    -   Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody służące do zaimplementowania.  
  
    -   Klasa, która implementuje zarówno usługi, jak i interfejs usługi.  
  
5.  Poniższy przykład przedstawia bardzo proste wykonania trzech typów. Konstruktor klasy usługi, należy ustawić dostawcy usług. W tym przykładzie tylko dodamy usługi do pliku pakietu kodu.  
  
6.  Dodaj następujące instrukcje using do pliku pakietu:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Oto implementacji usługi asynchronicznego. Należy zwrócić uwagę, należy ustawić dostawcę usługi asynchroniczne, a nie dostawcy usług synchroniczne w Konstruktorze:  
  
    ```  
    public class TextWriterService : STextWriterService, ITextWriterService  
    {  
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;  
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)  
        {  
            serviceProvider = provider;  
        }  
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)  
        {  
            StreamWriter writer = new StreamWriter(path);  
            await writer.WriteLineAsync(line);  
            writer.Close();  
        }  
        public TaskAwaiter GetAwaiter()  
        {  
            return new TaskAwaiter();  
        }  
    }  
    public interface STextWriterService  
    {  
    }  
    public interface ITextWriterService   
    {  
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);  
        TaskAwaiter GetAwaiter();  
    }  
    ```  
  
## <a name="registering-a-service"></a>Zarejestrowanie usługi  
 Aby zarejestrować usługi, dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakietu, która dostarcza usługę. Istnieją dwie różnice rejestrowaniu synchroniczne usługi:  
  
-   Jeśli jesteś autoloading pakietu, należy dodać <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad wartość atrybutu. Aby uzyskać więcej informacji na temat autoloading VSPackages, zobacz [ładowania VSPackages](../extensibility/loading-vspackages.md).  
  
-   Należy dodać **AllowsBackgroundLoading = true** do <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Aby uzyskać więcej informacji o PackageRegistrationAttribute, zobacz [rejestrowanie i wyrejestrowywanie VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Oto przykład AsyncPackage z rejestracji usługi asynchroniczne::  
  
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
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Dodaj odwołanie do Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implementuje metody wywołania zwrotnego jako metodę asynchroniczną, które tworzy i zwraca usługę.  
  
    ```csharp  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## <a name="using-a-service"></a>Przy użyciu usługi  
 Teraz można pobrać usługi i używać jej metody.  
  
1.  Poniżej opisano to w inicjatora, ale można pobrać usługi dowolnym chcesz korzystać z usługi.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Nie zapomnij zmienić  *\<userpath >* nazwę pliku i ścieżkę, która ma sens na tym komputerze!  
  
2.  Skompiluj i uruchom kod. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, otwórz rozwiązanie. Powoduje to AsyncPackage na automatyczne ładowanie. Po uruchomieniu inicjatora plik powinien znajdować się w określonej lokalizacji.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Przy użyciu usługi asynchronicznego programu obsługi poleceń  
 Poniżej przedstawiono przykład sposobu używania asynchroniczne usługi polecenia menu. Można użyć procedury pokazane do korzystania z usługi w innych metod innych niż asynchronicznych.  
  
1.  Polecenia menu Dodaj do projektu. (W **Eksploratora rozwiązań**, wybierz węzeł projektu, kliknij prawym przyciskiem myszy i wybierz **Add / nowy element / rozszerzalności / polecenia niestandardowych**.) Nazwa pliku polecenia **TestAsyncCommand.cs.**  
  
2.  Szablon polecenia niestandardowych ponownie dodaje `Initialize()` metody do pliku TestAsyncPackage.cs w celu zainicjowania polecenia. Skopiuj wiersza, który inicjuje polecenie metodę Initialize(). Go powinien wyglądać następująco:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Ten wiersz, aby przenieść `InitializeAsync()` metody w pliku AsyncPackageForService.cs. Ponieważ jest to inicjowania asynchronicznego, musisz przełączyć się do wątku głównego przed zainicjowaniem, za pomocą polecenia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Go powinna wyglądać następująco:  
  
    ```csharp  
  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        TestAsyncCommand.Initialize(this);    
  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService =   
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync((<userpath>, "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
3.  Usuń `Initialize()` metody.  
  
4.  W pliku TestAsyncCommand.cs znaleźć `MenuItemCallback()` metody. Usuń treść metody.  
  
5.  Dodaj using instrukcji:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Dodaj metodę asynchroniczną o nazwie `GetAsyncService()`, który pobiera usługi i używa jej metod:  
  
    ```csharp  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don't forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Wywołanie tej metody z `MenuItemCallback()` metody:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Skompiluj rozwiązanie i Rozpocznij debugowanie. Gdy pojawi się eksperymentalne wystąpienie programu Visual Studio, przejdź do **narzędzia** menu i wyszukać **wywołania TestAsyncCommand** elementu menu. Gdy zostanie kliknięty, TextWriterService zapisuje do podanego pliku. (Nie trzeba otworzyć rozwiązanie, ponieważ wywoływanie polecenia powoduje także, że pakiet do załadowania.)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z usług i dostarczanie ich](../extensibility/using-and-providing-services.md)
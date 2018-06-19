---
title: 'Porady: Użyj AsyncPackage załadować VSPackages w tle | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.technology: vs-ide-sdk
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: bc014b2072c5e6472d17095f0c0789c35116a3c6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135384"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Porady: Użyj AsyncPackage załadować VSPackages w tle
Ładowanie i Inicjowanie pakiet programu VS może spowodować We/Wy dysku. W przypadku takich operacji We/Wy na wątek interfejsu użytkownika, może to prowadzić do problemów czas odpowiedzi. Aby rozwiązać ten problem, wprowadzono programu Visual Studio 2015 <xref:Microsoft.VisualStudio.Shell.AsyncPackage> klasy, która umożliwia ładowanie zestawu wątku w tle.  
  
## <a name="creating-an-asyncpackage"></a>Tworzenie AsyncPackage  
 Można uruchomić tworzenia projektu VSIX (**Plik > Nowy > Projekt > Visual C# > rozszerzalności > projektu VSIX**) i dodać pakiet VSPackage do projektu (kliknij prawym przyciskiem myszy projekt i **Add/nowy element / elementu C# / Pakiet Studio Extensibility/Visual**). Można utworzyć usługi i dodać tych usług do pakietu.  
  
1.  Pakiet pochodzi <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Jeśli udostępniasz usług, których wykonywanie zapytania może spowodować pakietu do ładowania:  
  
     Do wskazywania dla programu Visual Studio do pakietu bezpieczne dla ładowania w tle i zgłosić do tego zachowania do Twojej <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> należy ustawić **AllowsBackgroundLoading** właściwości na wartość true w Konstruktorze atrybutu.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Aby określić dla programu Visual Studio bezpiecznego tworzenia wystąpienia usługi wątku w tle, należy ustawić <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> właściwości na wartość true w <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> konstruktora.  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Jeśli ładowania za pośrednictwem kontekstów interfejsu użytkownika, a następnie należy określić **PackageAutoLoadFlags.BackgroundLoad** dla <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> lub zapisać wartości (0x2) do flag jako wartość wpisu automatyczne ładowanie do pakietu.  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Jeśli masz pracy inicjowania asynchronicznego powinny zastępować <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Usuń **Initialize()** metody dostarczone przez szablon pliku VSIX. ( **Initialize()** metody w **AsyncPackage** jest zapieczętowany). Można użyć dowolnego z <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> metody dodawania asynchronicznych usług do pakietu.  
  
     Uwaga: Aby wywołać **podstawowej. InitializeAsync()**, można zmienić swój kod źródłowy:  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Użytkownik musi zwrócić uwagę, aby nie wprowadzać RPC (zdalne wywoływanie procedury) w kodzie inicjowania asynchronicznego (w **InitializeAsync**). Te mogą wystąpić podczas wywoływania <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> bezpośrednio lub pośrednio.  Podczas synchronizacji obciążenia są wymagane, wątku interfejsu użytkownika zostanie zablokowane, używając <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Domyślny model blokowania wyłącza RPC. Oznacza to, że próba użycia RPC z zadań asynchronicznych będzie zakleszczenie wtedy wątku interfejsu użytkownika jest oczekiwanie załadować pakietu. Ogólne alternatywą jest do organizowania kodu w wątku interfejsu użytkownika, jeśli to konieczne, za pomocą wyglądać mniej więcej tak **podlegającego sprzęganiu fabryki zadań**w <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> lub inny mechanizm, który nie korzysta z usługi RPC.  Nie używaj **ThreadHelper.Generic.Invoke** lub ogólnie blokowania wątek wywołujący oczekiwanie na uzyskanie dostępu do wątku interfejsu użytkownika.  
  
     Uwaga: Należy unikać używania **GetService** lub **QueryService** w Twojej **InitializeAsync** metody. Jeśli masz do niego zastosować, należy najpierw przełącz do wątku interfejsu użytkownika. Alternatywą jest użycie <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> z Twojej **AsyncPackage** (przez rzutowanie na <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
 C#: Utwórz AsyncPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konwertuj istniejący pakiet VSPackage AsyncPackage  
 Większość pracy jest taka sama, jak podczas tworzenia nowego **AsyncPackage**. Należy wykonać kroki od 1 do 5 powyżej. Należy również wykonać wyjątkową ostrożność następujące tematy:  
  
1.  Pamiętaj, aby usunąć **zainicjować** zastąpienie miał do pakietu.  
  
2.  Unikaj zakleszczenie: może być ukryta RPC w kodzie, który teraz się tak zdarzyć w wątku tła. Należy zapewnić, że w przypadku wprowadzania RPC (np. **GetService**), należy albo (1) Przełącz do wątku głównego lub (2) Użyj asynchroniczną wersję interfejsu API, jeśli istnieje (np. **element GetServiceAsync**).  
  
3.  Przełącza między wątkami zbyt często. Spróbuj do zlokalizowania pracy, który może się zdarzyć w wątku w tle. Powoduje to skrócenie czasu ładowania.  
  
## <a name="querying-services-from-asyncpackage"></a>Kwerenda usług z AsyncPackage  
 **AsyncPackage** może lub nie może załadować asynchronicznie w zależności od obiektu wywołującego. Na przykład  
  
-   Jeśli obiekt wywołujący wywołuje **GetService** lub **QueryService** (zarówno synchroniczne interfejsów API) lub  
  
-   Jeśli obiekt wywołujący wywołuje **IVsShell::LoadPackage** (lub **IVsShell5::LoadPackageWithContext**) lub  
  
-   Obciążenie zostanie wywołany w kontekście interfejsu użytkownika, ale nie określono, że mechanizm kontekstu interfejsu użytkownika można załadowania asynchronicznie  
  
 następnie pakietu załaduje synchronicznie.  
  
 Pamiętaj, że pakietu nadal ma możliwość (w fazie inicjowania asynchronicznego) do pracy poza wątku interfejsu użytkownika, chociaż wątku interfejsu użytkownika zostanie zablokowane do zakończenia tej pracy. Jeśli element wywołujący używa **IAsyncServiceProvider** asynchronicznie zapytanie dla usługi, następnie inicjowania i obciążenia, na których zostanie wykonane asynchronicznie przy założeniu, nie są natychmiast zablokować w powstałym obiekcie zadania.  
  
 C#: Jak wykonać zapytanie usługi asynchronicznie:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
  

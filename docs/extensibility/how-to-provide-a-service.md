---
title: 'Porady: udostępnianie usługi | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70d16085bc6cbc7f01a991a1eca731b8abed2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129459"
---
# <a name="how-to-provide-a-service"></a>Porady: udostępnianie usługi
Pakiet VSPackage może zapewnić usługi, które mogą używać inne pakiety VSPackage. Do świadczenia usług, pakiet VSPackage musi zarejestrować usługi z programem Visual Studio, a następnie Dodaj usługę.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Klasa implementuje zarówno <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> i <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> zawiera metody wywołania zwrotnego, które udostępniają usługi na żądanie.  
  
 Aby uzyskać więcej informacji na temat usług, zobacz [Essentials usługi](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Gdy pakiet VSPackage ma zostać zwolniony, Visual Studio czeka, aż wszystkie żądania dotyczące usług, które zawiera pakiet VSPackage zostały dostarczone. Nie zezwala nowych żądań dla tych usług. Nie należy bezpośrednio wywoływać <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodę, aby odwołać usługi podczas wyładowywania.  
  
#### <a name="implementing-a-service"></a>Wdrażanie usługi  
  
1.  Tworzenie projektu VSIX (**Plik > Nowy > Projekt > Visual C# > rozszerzalności > projektu VSIX**).  
  
2.  Dodaj pakiet VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj > Nowy element > Visual C# elementów > rozszerzalności > pakiet programu Visual Studio**.  
  
3.  Aby wdrożyć usługę, należy utworzyć trzy typy:  
  
    -   Interfejs, który zawiera opis usługi. Wiele z tych interfejsów jest pusty, oznacza to, ponieważ mają one żadnych metod.  
  
    -   Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody służące do zaimplementowania.  
  
    -   Klasa, która implementuje zarówno usługi, jak i interfejs usługi.  
  
     W poniższym przykładzie przedstawiono podstawową implementację trzech typów. Konstruktor klasy usługi, należy ustawić dostawcy usług.  
  
    ```csharp  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### <a name="registering-a-service"></a>Zarejestrowanie usługi  
  
1.  Aby zarejestrować usługi, dodać <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do pakiet VSPackage, która dostarcza usługę. Oto przykład:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Ten atrybut rejestruje `SMyService` z programem Visual Studio.  
  
    > [!NOTE]
    >  Aby zarejestrować to usługa, która zastępuje inną usługę o takiej samej nazwie, użyj <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Uwaga tego tylko jedno przesłonięcie usługi jest dozwolone.  
  
### <a name="adding-a-service"></a>Dodawanie usługi  
  
1.  W inicjatorze pakiet VSPackage Dodaj usługę, a następnie dodaj metodę wywołania zwrotnego do tworzenia usług. W tym miejscu została zmieniona, aby wprowadzić <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementuje metody wywołania zwrotnego, który należy utworzyć i zwracać usługi lub wartość null, jeśli nie można utworzyć.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio może odrzucać żądania do świadczenia usług. Robi to jeśli inny pakiet VSPackage już zawiera usługę.  
  
3.  Teraz można pobrać usługi i używać jej metody. W poniższym przykładzie pokazano, przy użyciu usługi inicjatora, ale można pobrać usługi dowolnym chcesz korzystać z usługi.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.Goodbye();  
  
        base.Initialize();  
    }  
    ```  
  
     Wartość `helloString` powinna być "tekst Hello".  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)   
 [Przy użyciu i świadczenia usług](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)

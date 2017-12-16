---
title: "Porady: udostępnianie usługi | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c37f4dc215027752da9c16fbdfba44b4e10c41c
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-provide-a-service"></a>Porady: udostępnianie usługi
Pakiet VSPackage może zapewnić usługi, które mogą używać inne pakiety VSPackage. Do świadczenia usług, pakiet VSPackage musi zarejestrować usługi z programem Visual Studio, a następnie Dodaj usługę.  
  
 <xref:Microsoft.VisualStudio.Shell.Package> Klasa implementuje zarówno <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> i <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer>zawiera metody wywołania zwrotnego, które udostępniają usługi na żądanie.  
  
 Aby uzyskać więcej informacji na temat usług, zobacz [Essentials usługi](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Gdy pakiet VSPackage ma zostać zwolniony, Visual Studio czeka, aż wszystkie żądania dotyczące usług, które zawiera pakiet VSPackage zostały dostarczone. Nie zezwala nowych żądań dla tych usług. Nie należy bezpośrednio wywoływać <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> metodę, aby odwołać usługi podczas wyładowywania.  
  
#### <a name="implementing-a-service"></a>Wdrażanie usługi  
  
1.  Tworzenie projektu VSIX (**Plik > Nowy > Projekt > Visual C# > Extensiblity > projektu VSIX**).  
  
2.  Dodaj pakiet VSPackage do projektu. Wybierz węzeł projektu w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj > Nowy element > Visual C# elementów > rozszerzalności > pakiet programu Visual Studio**.  
  
3.  Aby wdrożyć usługę, należy utworzyć trzy typy:  
  
    -   Interfejs, który zawiera opis usługi. Wiele z tych interfejsów jest pusty, oznacza to, ponieważ mają one żadnych metod.  
  
    -   Interfejs, który opisuje interfejs usługi. Ten interfejs zawiera metody służące do zaimplementowania.  
  
    -   Klasa, która implementuje zarówno usługi, jak i interfejs usługi.  
  
     Poniższy przykład przedstawia bardzo proste wykonania trzech typów. Konstruktor klasy usługi, należy ustawić dostawcy usług.  
  
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
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio może odrzucać żądania do świadczenia usług. Robi to jeśli inny pakiet VSPackage już zawiera usługę.  
  
3.  Teraz można pobrać usługi i używać jej metody. Poniżej opisano to w inicjatora, ale można pobrać usługi dowolnym chcesz korzystać z usługi.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Wartość `helloString` powinna być "tekst Hello".  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: uzyskiwanie usługi](../extensibility/how-to-get-a-service.md)   
 [Przy użyciu i świadczenia usług](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)

---
title: Usługa Essentials | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5a9858109c9fe0d8af0d00621b717417a0c0e53
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="service-essentials"></a>Usługa Essentials
Usługa jest Umowa między dwoma VSPackages. Jeden pakiet VSPackage zawiera określony zbiór interfejsów dla innego pakiet VSPackage korzystać. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest to zbiór VSPackages udostępniająca usługi inne pakiety VSPackage.  
  
 Na przykład można użyć usługi SVsActivityLog można uzyskać interfejsu IVsActivityLog, w którym można zapisać do dziennika aktywności. Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z dziennika aktywności](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dostępne są także niektóre wbudowane usługi, które nie zostały zarejestrowane. VSPackages można zastąpić wbudowanych lub innych usług, udostępniając zastąpienie usług. Zastąpienie tylko jedna usługa jest dozwolony dla usługi.  
  
 Usługi mają nie odnajdywania. W związku z tym musisz znać identyfikator usługi (SID), usługi, którą chcesz używać, i musi znać interfejsów, które zapewnia. Informacje te dokumentacji dla usługi.  
  
-   VSPackages, które udostępniają usługi są nazywane usługodawców.  
  
-   Usługi, które znajdują się na inne pakiety VSPackage są nazywane usług globalnych.  
  
-   Usługi, które są dostępne tylko dla pakiet VSPackage, który implementuje je lub do obiektu, który tworzy, są nazywane usługami lokalnymi.  
  
-   Usługi, które zastępuje wbudowane usługi lub usług świadczonych przez inne pakiety są nazywane zastąpienia usługi.  
  
-   Usługi lub zastąpienia usługi są ładowane na żądanie, oznacza to, że dostawca usług jest ładowany podczas świadczonej usługi jest wymagany przez inny pakiet VSPackage.  
  
-   Aby zapewnić obsługę ładowania na żądanie, dostawcy usług rejestruje jego usług globalnych z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [porady: udostępnianie usługi](../../extensibility/how-to-provide-a-service.md).  
  
-   Po uzyskaniu usługi, użyj [QueryInterface](/cpp/atl/queryinterface) (niezarządzany kod) lub Rzutowanie (zarządzany kod), aby pobrać żądaną interfejsu, na przykład:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
    ```  
  
-   Zarządzany kod odwołuje się do usługi przez jej typ niezarządzany kod odnosi się do usługi za pomocą identyfikatora GUID.  
  
-   Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obciążenia, a pakiet VSPackage, przekazaniem dostawcę usług do pakiet VSPackage w celu udzielenia dostępu pakiet VSPackage usług globalnych. Jest to określane jako "Lokalizacja" pakiet VSPackage.  
  
-   VSPackages może być dostawcy usług dla tworzonych obiektów. Na przykład formularz może wysyłać żądania usługi kolorów do ramki, który może przekazać żądanie do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Głęboko zagnieżdżone, lub nie ulokowany na wszystkich obiektów zarządzanych może wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> uzyskać bezpośredni dostęp do usług globalnych.   
  
<a name="how-to-use-getglobalservice"></a>  
  
## <a name="use-getglobalservice"></a>Użyj GetGlobalService  
  
Czasami może być konieczne uzyskanie usługi okna narzędzia lub kontrolować kontener, który nie został ulokowany, w przeciwnym razie zostały zlokalizowane z dostawcą usługi, która nie może określić dotyczących usługi, który ma. Na przykład można zapisywać w Dzienniku działania z wewnątrz formantu. Aby uzyskać więcej informacji na temat tych i innych scenariuszy, zobacz [porady: Rozwiązywanie problemów z usługami](../../extensibility/how-to-troubleshoot-services.md).  
  
Większość usług programu Visual Studio można uzyskać przez wywołanie metody statycznych <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> opiera się na usługi z pamięci podręcznej jest ulokowany dostawcy, który został zainicjowany po raz pierwszy żadnych pakiet VSPackage pochodzących z pakietu. Należy zagwarantować, że ten warunek jest spełniony, w przeciwnym razie należy przygotować usługę wartości null.  
  
Na szczęście <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> działa prawidłowo w większości przypadków.  
  
-   Jeśli pakiet VSPackage udostępnia usługę zna nikt inny pakiet VSPackage, pakiet VSPackage, żądanie usługi jest ulokowany przed VSPackage warunkiem, że usługa jest załadowany.  
  
-   Jeśli okno narzędzia jest tworzony przez pakiet VSPackage, pakiet VSPackage jest ulokowany przed utworzeniem okna narzędzia.  
  
-   Jeśli kontener formantu jest hostowana przez okna narzędzia utworzonego przez pakiet VSPackage, pakiet VSPackage jest ulokowany przed utworzeniem formantu kontenera.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Aby uzyskać usługi z znajdujące się w kontenerze okna lub formant narzędzia  
  
-   Wstaw ten kod w konstruktorze, okna narzędzia lub formantu kontenera:  
  
    ```csharp  
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```  
    ```vb  
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```  
    
    Ten kod uzyskuje usługi SVsActivityLog i rzutuje interfejs IVsActivityLog, która może służyć do zapisu do dziennika aktywności. Na przykład zobacz [porady: Korzystanie z dziennika aktywności](../../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Lista dostępnych usług](../../extensibility/internals/list-of-available-services.md)   
 [Przy użyciu i świadczenia usług](../../extensibility/using-and-providing-services.md)   
 [Rzutowanie i konwersje typów](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)   
 [Rzutowanie](/cpp/cpp/casting)
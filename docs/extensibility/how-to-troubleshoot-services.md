---
title: 'Porady: Rozwiązywanie problemów z usługami | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d9efe3c1c7032f1db41272a03cf689e015a79522
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128678"
---
# <a name="how-to-troubleshoot-services"></a>Porady: Rozwiązywanie problemów z usługami
Istnieje kilka typowych problemów, które mogą wystąpić podczas próby pobrania usługi:  
  
-   Usługa nie jest zarejestrowana na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Usługa jest wymagany przez typ interfejsu i nie przez typ usługi.  
  
-   Nie ma zostały ulokowany VSPackage żądanie usługi.  
  
-   Dostawca usługi niewłaściwy jest używany.  
  
 Jeśli żądanej usługi nie można uzyskać, wywołanie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zwraca wartość null. Należy zawsze przetestować dla wartości null po zażądaniu usługi:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Rozwiązywania problemów z usługą  
  
1.  Sprawdź, czy rejestr systemu, aby zobaczyć, czy usługa została prawidłowo zarejestrowana. Aby uzyskać więcej informacji, zobacz [porady: udostępnianie usługi](../extensibility/how-to-provide-a-service.md).  
  
     Poniższy fragment pliku reg pokazuje, jak usługa SVsTextManager może być zarejestrowana:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     W powyższym przykładzie numer wersji jest wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], takie jak 12.0 lub 14.0, klucz {F5E7E71D-1401-11d1-883B-0000F87579D2} jest identyfikatorem usługi (SID), usługi, SVsTextManager i {wartość domyślną F5E7E720-1401-11d1-883B-0000F87579D2} jest identyfikator GUID menedżera tekstu pakiet VSPackage, która zapewnia usługi pakietu.  
  
2.  Podczas wywoływania funkcji GetService, użyj typu usługi, a nie typu interfejsu. Podczas żądania usługi z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> wyodrębnianie identyfikatora GUID z typu. Usługa nie zostanie znaleziona, jeśli następujące warunki:  
  
    1.  Typ interfejsu są przekazywane do elementu GetService zamiast typu usługi.  
  
    2.  Żaden identyfikator GUID nie zostały wyraźnie przypisane do interfejsu. W związku z tym system tworzy domyślny identyfikator GUID dla obiekt zgodnie z potrzebami.  
  
3.  Upewnij się, że pakiet VSPackage, żądanie usługi zostały zlokalizowane. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Lokacje pakiet VSPackage, po jego konstruowanie i przed wywołaniem <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Jeśli w Konstruktorze pakiet VSPackage, który wymaga usługi kodu, przenieś go do metody Initialize.  
  
4.  Pamiętaj, używasz poprawne usługodawcy.  
  
     Nie wszyscy dostawcy usług są podobne. Dostawca usług który [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przekazuje do okna narzędzia różni się od tego, przekazaniem do pakiet VSPackage. Zna dostawcy usług okna narzędzia <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ale nie może określić dotyczących <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Możesz wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> można pobrać pakiet VSPackage usługodawcy z poziomu okna narzędzia.  
  
     Jeśli okno narzędzia obsługuje kontrolkę użytkownika lub inne kontenera formantu, kontener będzie znajdować się przez model składników systemu Windows i nie ma dostępu do dowolnego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usług. Możesz wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> można pobrać pakiet VSPackage usługodawcy z kontenera formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista dostępnych usług](../extensibility/internals/list-of-available-services.md)   
 [Przy użyciu i świadczenia usług](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)
---
title: 'Porady: Użyj GetGlobalService | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: douge
ms.openlocfilehash: bd0a82281d2271f9badfbda9a7b32d20edf0c12c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42690097"
---
# <a name="how-to-use-getglobalservice"></a>Porady: Użyj GetGlobalService
Czasami może być konieczne uzyskiwanie usługi okno narzędzia lub kontroli kontenera, które nie zostały zlokalizowane; w przeciwnym razie ma zostały umieszczone u dostawcy usług, które nie wie o usługę, którą chcesz. Na przykład można zapisywać w dzienniku aktywności ze znajdujących się pod kontrolą. Aby uzyskać więcej informacji na temat tych i innych scenariuszy, zobacz [porady: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md).  
  
 Możesz uzyskać większość [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usług przez wywołanie metody statyczne <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> opiera się na pamięci podręcznej usługodawcy, który jest zainicjowany po raz pierwszy pochodną dowolnego pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> jest ulokowany. Musisz gwarantować, że ten warunek jest spełniony; w przeciwnym razie należy przygotować usługę o wartości null.  
  
 Na szczęście <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> działa prawidłowo w większości przypadków.  
  
-   Jeśli pakietu VSPackage udostępnia usługę znanego tylko innego pakietu VSPackage, pakietu VSPackage żądania usługi jest ulokowany przed pakietu VSPackage warunkiem, że usługa jest ładowany.  
  
-   Jeśli okno narzędzia jest tworzony przez pakietu VSPackage, pakietu VSPackage jest ulokowany przed utworzeniem okna narzędzia.  
  
-   Jeśli formant kontenera jest hostowana przez okna narzędzia utworzonego przez pakietu VSPackage, pakietu VSPackage jest ulokowany przed utworzeniem kontenera kontrolki.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Aby uzyskać to usługa firmy znajdujące się w kontenerze okna lub kontroli narzędzi  
  
-   Wstaw ten kod w konstruktorze, okno narzędzia lub kontroli kontenera:  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     Ten kod uzyskuje usługi SVsActivityLog i rzutuje je na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> interfejs, który może służyć do zapisu w dzienniku aktywności. Aby uzyskać przykład, zobacz [porady: Korzystanie z dziennika aktywności](../extensibility/how-to-use-the-activity-log.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Rozwiązywanie problemów z usługami](../extensibility/how-to-troubleshoot-services.md)   
 [Korzystanie z usług i dostarczanie](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)
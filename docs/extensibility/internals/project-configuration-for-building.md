---
title: Konfiguracja dla tworzenia projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d78ac1cabc356db162639d3eb19d0bff71e295e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133314"
---
# <a name="project-configuration-for-building"></a>Konfiguracja projektu dla tworzenia
Lista konfiguracje rozwiązania dla danego rozwiązania jest zarządzana przez okno dialogowe konfiguracji rozwiązania.  
  
 Użytkownik może utworzyć rozwiązanie dodatkowe konfiguracje, każdy z własną unikatową nazwę. Gdy użytkownik tworzy nową konfigurację rozwiązania, IDE domyślnie nazwę konfiguracji w projektach lub debugowania, jeśli nie ma żadnej odpowiedniej nazwy. Użytkownik może zmienić wybór, aby spełniały określone wymagania, jeśli to konieczne. Jedynym wyjątkiem to zachowanie jest, gdy projekt obsługuje konfigurację, która jest zgodna z nazwą nowej konfiguracji rozwiązania. Załóżmy na przykład, że rozwiązanie zawiera Project1 i projekcie 2. Project1 ma konfiguracje projektu debugowania, detaliczna i MyConfig1. Projekcie 2 ma konfiguracje projektu debugowania, detaliczna i MyConfig2.  
  
 Jeśli użytkownik tworzy nową konfigurację rozwiązania o nazwie MyConfig2, Project1 wiąże konfigurację debugowania konfiguracji rozwiązania domyślnie. Projekcie 2 wiąże również konfigurację MyConfig2 konfiguracji rozwiązania domyślnie.  
  
> [!NOTE]
>  Powiązanie jest rozróżniana wielkość liter.  
  
 Gdy użytkownik wybierze **wybór wielokrotny** elementu na liście rozwijanej konfiguracji środowiska Wyświetla okno dialogowe, który zawiera listę dostępnych konfiguracji.  
  
 ![Wiele konfiguracji](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Wiele konfiguracji  
  
 W oknie dialogowym użytkownik może wybrać jeden lub wiele konfiguracji. Po wybraniu wartości właściwości wyświetlane w oknie dialogowym stron właściwości odzwierciedlają część wspólną wartości dla wybranej konfiguracji.  
  
 Zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md) informacji dotyczących dodawania i zmiana nazwy konfiguracji dla rozwiązań i projektów.  
  
 Zależności projektu i kolejność kompilacji są niezależne konfiguracji rozwiązania: oznacza to, możesz skonfigurować tylko jedną zależność drzewa dla wszystkich projektów w rozwiązaniu. Prawym przyciskiem myszy rozwiązanie lub projekt i wybierając jedną **zależności projektu** lub **kolejność kompilacji projektu** opcji otwiera **zależności projektu** okno dialogowe. Można go również otworzyć z **projektu** menu.  
  
 ![Zależności projektu](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Zależności projektu  
  
 Zależności projektu określić kolejność, w którym kompilacji projektów. Karta kolejność kompilacji w oknie dialogowym zawiera dokładnie kolejność, w którym projektów w rozwiązaniu będzie kompilacji i użyj karty zależności, aby zmodyfikować kolejność kompilacji.  
  
> [!NOTE]
>  Projekty na liście swoich pól wyboru zaznaczone, które jest wyszarzone zostały dodane przez środowisko z powodu jawne zależności określony przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsy i nie można zmienić. Na przykład dodać odwołanie do projektu z [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu do innego projektu automatycznie dodaje zależność kompilacji, która może być usunięta tylko przez usunięcie odwołania. Nie można wybrać projekty, których pola wyboru wyraźnie i wyszarzone, ponieważ w ten sposób spowoduje utworzenie pętli zależności (na przykład Project1 są zależne od projekcie 2 i są zależne od Project1 projekcie 2), który będzie zatrzymania kompilacji.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] procesów tworzenia obejmują typowe kompilacji i operacji łączy, które są wywoływane za pomocą jednego polecenia kompilacji. Mogą być również obsługiwane dwa procesy kompilacji: operacji czyszczenia, aby usunąć wszystkie elementy danych wyjściowych z ostatniej kompilacji i aktualne sprawdzanie, czy element danych wyjściowych w konfiguracji został zmieniony.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Zwraca obiekty odpowiadające mu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (zwrócony z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) do zarządzania procesu kompilacji. Aby zgłosić stan operacji kompilacji, sprawdzeniem, konfiguracje wykonywania wywołań do <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>, interfejs implementowany przez środowisko i innych obiektów zainteresowani zdarzeń stanu kompilacji.  
  
 Raz utworzone ustawienia konfiguracji można określić, czy można je uruchamiać pod kontrolą debugera. Konfiguracje wdrożenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> do obsługi debugowania.  
  
 Po wdrożeniu zależności projektu, można programowo manipulować zależności za pomocą modelu automatyzacji. Należy wywołać <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> w modelu automatyzacji. Nie ma żadnych dostępnych interfejsów poziom interfejsu API VSIP zezwalających na bezpośrednią manipulację konfiguracje Menedżera kompilacji rozwiązania i ich właściwości.  
  
 Ponadto musisz podać siatki w oknie zależności projektu. Aby uzyskać więcej informacji, zobacz [właściwości wyświetlania siatki](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje konfiguracji zarządzania](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguracja projektu do zarządzania wdrożenia](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
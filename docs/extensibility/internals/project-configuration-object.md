---
title: Obiekt konfiguracji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, object
- objects, project configuration
ms.assetid: 877756c9-4261-43d9-9f32-51bf06b4219f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7385a5f7768a57fd1a3d9688df152fd60a1ea130
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="project-configuration-object"></a>Obiekt konfiguracji projektu
Obiekt konfiguracji projektu zarządza wyświetlania informacji o konfiguracji do interfejsu użytkownika.  
  
 ![Konfiguracja projektu w usłudze Visual Studio](../../extensibility/internals/media/vsprojectcfg.gif "vsProjectCfg")  
Strony właściwości konfiguracji projektu  
  
 Dostawca konfiguracji projektu zarządza konfiguracje projektu. Środowisko i inne pakiety w celu uzyskania dostępu do i pobierania informacji o konfiguracji projektu, należy wywołać interfejsy dołączony do obiektu dostawcy konfiguracji projektu.  
  
> [!NOTE]
>  Nie można utworzyć lub edytować pliki konfiguracji rozwiązania programowo. Należy użyć `DTE.SolutionBuilder`. Zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md) Aby uzyskać więcej informacji.  
  
 Aby opublikować nazwę wyświetlaną mają być używane w konfiguracji interfejsu użytkownika, należy zaimplementować projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_DisplayName%2A>. Wywołania środowiska <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, które zwraca listę `IVsCfg` wskaźników, które służy do pobierania nazw wyświetlanych informacji Configuration i Platform był wyświetlany w interfejsie użytkownika w środowisku. Aktywna konfiguracja i platforma są określane przez konfigurację projektu w aktywnej konfiguracji rozwiązania. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager.FindActiveProjectCfg%2A> Metody można użyć do pobrania Konfiguracja aktywnego projektu.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> Obiektu Opcjonalnie można zaimplementować w <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obiekt z <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProviderEventsHelper> obiektu pozwala pobrać `IVsProjectCfg2` obiekt na podstawie projektu canonical konfiguracji nazwy.  
  
 Innym sposobem udostępnienia środowiska i innych projektów konfiguracje projektu jest dla projektów zapewniać implementację elementu `IVsCfgProvider2::GetCfgs` metodę, aby zwrócić co najmniej jeden obiekt konfiguracji. Projekty może również zastosować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>, który dziedziczy z `IVsProjectCfg` i tym samym z `IVsCfg`, aby podać informacje specyficzne dla konfiguracji. <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> obsługuje platformy i funkcje, dodawanie, usuwanie i zmiana nazwy konfiguracji projektu.  
  
> [!NOTE]
>  Ponieważ Visual Studio nie jest już ograniczona do dwa typy konfiguracji ani kodu, który przetwarza konfiguracje nie powinien być zapisywany z założenia o liczbie konfiguracje nie powinna być ona zapisana przy założeniu, że projekt, który ma tylko jeden Konfiguracja jest zawsze debugowania lub wersji detalicznej. Dzięki temu używanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsReleaseOnly%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg.get_IsDebugOnly%2A> przestarzałe.  
  
 Wywoływanie `QueryInterface` zwrócony z obiektu`IVsGetCfgProvider::GetCfgProvider` pobiera `IVsCfgProvider2`. Jeśli `IVsGetCfgProvider` nie znaleziono wywołując `QueryInterface` na `IVsProject3` obiekt projektu, można uzyskać dostęp do obiektu dostawcy konfiguracji przez wywołanie metody `QueryInterface` obiektu przeglądarki główny hierarchii zwrócony dla obiektu `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_BrowseObject)`, lub za pomocą wskaźnik do dostawcę konfiguracji dla zwracany `IVsHierarchy::GetProperty(VSITEM_ROOT, VSHPROPID_ConfigurationProvider)`.  
  
 `IVsProjectCfg2` przede wszystkim zapewnia dostęp do tworzenia, debugowania i wdrażania zarządzania obiektów i umożliwia swobodne wyjść grupy projektów. Metody `IVsProjectCfg` i `IVsProjectCfg2` może służyć do zaimplementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> do zarządzania procesem kompilacji i <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> wskaźniki grupy danych wyjściowych konfiguracji.  
  
 Projekt musi zwracać taką samą liczbę grup dla każdej konfiguracji obsługującego nawet, jeśli liczba wyjść zawarty w grupie może się różnić od konfiguracji konfiguracji. Grupy musi mieć te same informacje identyfikator (nazwa kanoniczna, nazwa wyświetlana i informacje o grupie) z Konfiguracja w projekcie. Aby uzyskać więcej informacji, zobacz [konfiguracji projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md).  
  
 Aby włączyć debugowanie, powinien implementować konfiguracje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>. `IVsDebuggableProjectCfg` jest opcjonalny interfejs implementowany przez projektów, aby umożliwić debugera uruchomić konfigurację i zostało zaimplementowane dla obiekt konfiguracji z `IVsCfg` i `IVsProjectCfg`. Środowisko wywołuje go, gdy użytkownik wybiera uruchomienia debugera, naciskając klawisz F5.  
  
 `ISpecifyPropertyPages` i `IDispatch` są używane w połączeniu z strony właściwości można pobrać i wyświetlać informacje zależne od konfiguracji dla użytkownika. Aby uzyskać więcej informacji, zobacz [strony właściwości](../../extensibility/internals/property-pages.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje konfiguracji zarządzania](../../extensibility/internals/managing-configuration-options.md)   
 [Konfiguracja projektu dla tworzenia](../../extensibility/internals/project-configuration-for-building.md)   
 [Konfiguracja projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)   
 [Strony właściwości](../../extensibility/internals/property-pages.md)   
 [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md)
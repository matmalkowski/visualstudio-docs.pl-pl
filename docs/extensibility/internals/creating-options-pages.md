---
title: Tworzenie Opcje strony | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51e05c5f2660adfe8d7a35c816e5f94706631c8f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-options-pages"></a>Tworzenie stron opcje
W [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework zarządzanego pakietu pochodną klasy <xref:Microsoft.VisualStudio.Shell.DialogPage> rozszerzyć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, dodając **opcje** stron w obszarze **narzędzia** menu.  
  
 Implementacja obiektu danego **opcji narzędzia** strona jest skojarzona z określonym VSPackages przez <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> obiektu.  
  
 Ponieważ środowisko tworzy obiekt zawierający implementację określonego **opcje narzędzia** strony po wyświetleniu IDE danej strony:  
  
-   A **opcji narzędzia** strony powinny być implementowane we własnym obiekcie, a nie dla obiekt implementujący pakiet VSPackage.  
  
-   Obiekt nie implementuje wiele **opcje narzędzia** stron.  
  
## <a name="registering-as-a-tools-options-page-provider"></a>Rejestrowanie dostawcy strony opcji narzędzi  
 Pakiet VSPackage obsługi konfiguracji użytkownika za pośrednictwem **opcje narzędzia** stron wskazuje obiekty, podając te **opcje narzędzia** stron, stosując wystąpienia <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> stosowane do <xref:Microsoft.VisualStudio.Shell.Package>implementacji.  
  
 Musi być jedno wystąpienie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> dla każdego <xref:Microsoft.VisualStudio.Shell.DialogPage>-pochodzi z typu, który implementuje **opcje narzędzia** strony.  
  
 Każde wystąpienie <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> używa typu, który implementuje **opcje narzędzia** strony ciągi zawierające kategorii i podkategorii używany do identyfikowania **opcje narzędzia** strony i zasobów informacje, aby zarejestrować typ jako zapewniające **opcje narzędzia** strony.  
  
## <a name="persisting-tools-options-page-state"></a>Utrwalanie stanu strony opcji narzędzi  
 Jeśli **opcje narzędzia** implementacja strony jest zarejestrowany z włączoną obsługą automatyzacji, IDE utrwala stan strony wraz ze wszystkich innych **opcje narzędzia** stron.  
  
 Pakiet VSPackage można zarządzać własną trwałości za pomocą <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Można użyć tylko jednego lub innej metody trwałości.  
  
## <a name="implementing-dialogpage-class"></a>Implementacja elementu DialogPage — klasa  
 Obiekt dostarczający implementacja pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.DialogPage>— Typ pochodny można korzystać z następujących funkcji dziedziczonych:  
  
-   Domyślne okno interfejsu użytkownika.  
  
-   A domyślna mechanizmu stanu trwałego dostępne albo jeśli <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> jest stosowany do klasy, lub jeśli <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> właściwość jest ustawiona na `true` dla <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> do klasy zastosowano.  
  
-   Obsługa automatyzacji.  
  
 Minimalne wymagania dla obiekt implementacja **opcje narzędzia** strony <xref:Microsoft.VisualStudio.Shell.DialogPage> jest dodanie właściwości publiczne.  
  
 Jeśli klasa jest poprawnie zarejestrowany jako **opcje narzędzia** strony dostawcy, a następnie jego właściwości publiczne są dostępne na **opcje** sekcji **narzędzia** menu w formie siatki właściwości.  
  
 Wszystkie te funkcje domyślne można przesłonić. Na przykład tworzenie bardziej zaawansowanych użytkownika interfejsu wymaga tylko zastępowanie domyślną implementację elementu <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Przykład  
 Poniżej jest proste implementacją "hello world" Opcje strony. Dodawanie następujący kod do projektu domyślnego utworzone przez szablon pakietu Visual Studio, z **polecenie** wybrana opcja zostanie odpowiednio pokazu funkcjonalności strony opcji.  
  
### <a name="description"></a>Opis  
 Następujące klasy definiuje minimalna strona Opcje "hello world". Po otwarciu, użytkownik może ustawić publicznego `HelloWorld` właściwość w siatce właściwości.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Opis  
 Stosowanie następującego atrybutu do klasy pakietu udostępnia opcje strony podczas ładowania pakietu. Liczby są dowolne identyfikatorów zasobów dla kategorii i strony, a wartość logiczną na końcu Określa, czy strona obsługuje automatyzacji.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Opis  
 Następujące procedury obsługi zdarzeń wyświetla wynik w zależności od wartości właściwości wartości na stronie opcji. Używa <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metody z wynikiem jawne Rzutowanie na typ strony opcja niestandardowa uzyskać dostęp do właściwości udostępnianych przez strony.  
  
 W przypadku projektu generowane przez szablon pakietu, wywołanie tej funkcji z `MenuItemCallback` funkcji, aby dołączyć do polecenia domyślne dodane do **narzędzia** menu.  
  
### <a name="code"></a>Kod  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje i rozszerzanie ustawień użytkownika](../../extensibility/extending-user-settings-and-options.md)   
 [Obsługa automatyzacji dla stron opcji](../../extensibility/internals/automation-support-for-options-pages.md)
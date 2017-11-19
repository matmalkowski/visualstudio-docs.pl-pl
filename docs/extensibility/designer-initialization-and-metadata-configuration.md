---
title: Inicjowanie projektanta i konfiguracji metadanych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 12ed4c42335590b7e48d0f6f0fed716a7f149bd0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicjowanie projektanta i konfiguracji metadanych
Manipulowanie metadanych i filtr atrybuty skojarzone z projektantem lub składnika projektanta udostępnia mechanizm dla aplikacji, aby określić, jakie narzędzia są używane przez konkretnego projektanta do obsługi różnych <xref:System.Type> obiektów (takich jak struktury danych klasy lub graficznego jednostek), gdy projektant jest dostępna, i jak środowiska IDE programu Visual Studio jest skonfigurowany do obsługi projektanta (dla wystąpienia, które **przybornika** kategorii lub karta jest dostępna).  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Udostępnia kilka mechanizmów ułatwiających kontroli inicjowania projektanta lub składnika projektanta i manipulowania nimi metadanych przez pakiet VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicjowanie metadane i informacje o konfiguracji  
 Ponieważ są załadowane na żądanie, VSPackages nie mógł zostać załadowany przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska przed wystąpienia projektanta. W związku z tym VSPackages nie można użyć standardowego mechanizmu konfigurowania designer lub składnika projektanta na tworzenie, który ma obsługiwać <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> zdarzeń. Zamiast tego pakiet VSPackage implementuje wystąpienia <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfejsu i rejestruje się w celu zapewnienia dostosowania, określany jako rozszerzenia powierzchni projektu.  
  
### <a name="customizing-initialization"></a>Dostosowywanie inicjowania  
 Dostosowywanie projektanta, składnika lub powierzchnię projektanta obejmuje:  
  
1.  Modyfikowanie projektanta metadanych i efektywnie zmiana sposobu określony <xref:System.Type> jest lub uzyskać dostępu do konwersji.  
  
     Jest to zazwyczaj wykonywane za pośrednictwem <xref:System.Drawing.Design.UITypeEditor> lub <xref:System.ComponentModel.TypeConverter> mechanizmów.  
  
     Na przykład, jeśli <xref:System.Windows.Forms>— Designer na podstawie są inicjowane, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modyfikuje środowiska <xref:System.Drawing.Design.UITypeEditor> dla <xref:System.Web.UI.WebControls.Image> obiekty używane przy użyciu projektanta do uzyskania mapy bitowe, a nie z systemu plików za pomocą Menedżera zasobów.  
  
2.  Integracja ze środowiskiem, na przykład przez subskrybowanie zdarzeń i uzyskiwanie informacji o konfiguracji projektu. Można uzyskać informacji o konfiguracji projektu i subskrybowanie zdarzeń, uzyskując <xref:System.ComponentModel.Design.ITypeResolutionService> interfejsu.  
  
3.  Modyfikacja środowiska użytkownika, aktywować odpowiednie **przybornika** kategorii lub przez ograniczenie możliwości zastosowania projektanta, stosując wystąpienia <xref:System.ComponentModel.ToolboxItemFilterAttribute> klasy do projektanta.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicjowanie projektanta przez pakiet VSPackage  
 Pakiet VSPackage powinna obsługiwać projektanta inicjowania przez:  
  
1.  Tworzenie, wdrażanie obiektu <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> klasy.  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasy nigdy nie powinny być wdrożone na tym samym obiekcie jako <xref:Microsoft.VisualStudio.Shell.Package> klasy.  
  
2.  Zarejestruj Implementacja klasy <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> jako zapewnienia obsługi rozszerzenia projektanta pakiet VSPackage, stosując wystąpienia <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do klasy, zapewniając implementacja pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
 Zawsze, gdy projektant ani składnika projektanta został utworzony, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska:  
  
1.  Uzyskuje dostęp do każdego dostawcy rozszerzenia powierzchni projektu w zarejestrowany.  
  
2.  Tworzy i inicjuje wystąpienie każdego dostawcy rozszerzenia powierzchni projektu <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu  
  
3.  Wywołuje każdego dostawcy rozszerzenia powierzchni projektu <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> — metoda (zależnie od potrzeb).  
  
 Podczas implementowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiekt jako członek pakiet VSPackage, należy pamiętać, że:  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Środowisku nie ma żadnego formantu, przez jaki metadanych lub innych ustawień konfiguracyjnych, w szczególności `DesignSurfaceExtension` modyfikuje dostawcy. Istnieje możliwość co najmniej dwa `DesignSurfaceExtension` dostawców modyfikowanie tej samej funkcji projektanta powodujące konflikt sposoby, za pomocą końcowych modyfikacji jest ostatecznym. Jest nieokreślony modyfikacji, które jest ostatnio zastosowane.  
  
2.  Można ograniczyć jawnie implementacja <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiekt do określonego projektantów, stosując wystąpienia <xref:System.ComponentModel.ToolboxItemFilterAttribute> tej implementacji. Aby uzyskać więcej informacji na temat **przybornika** elementu filtrowania, zobacz <xref:System.ComponentModel.ToolboxItemFilterAttribute> i <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Dodatkowe metadane inicjowania obsługi administracyjnej.  
 Pakiet VSPackage można zmienić konfiguracji designer lub składnika projektanta innych niż w czasie projektowania.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasy można programowo, lub można zastosować do pakiet VSPackage dostarczanie projektanta.  
  
 Wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> klasa jest używana do zmodyfikowania metadanych składników utworzony na powierzchnię projektu. Na przykład, jeden zastąpić domyślną przeglądarkę właściwości używanych przez <xref:System.Windows.Forms.CommonDialog> obiektów przy użyciu przeglądarki właściwości niestandardowej.  
  
 Modyfikacje udostępniane przez wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> stosowane do wykonania pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.Package> może mieć jeden z dwóch zakresów:  
  
-   Global — dla wszystkich nowych wystąpień danego składnika  
  
-   Lokalne — dotyczących tylko wystąpienia składnika utworzone na powierzchni projektowej, dostarczone przez bieżący pakiet VSPackage.  
  
 `IsGlobal` Właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wystąpienia stosowane do wykonania pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.Package> określa ten zakres.  
  
 Stosowanie atrybutu do wykonania <xref:Microsoft.VisualStudio.Shell.Package> z <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> ustawioną obiektu `true`, jak poniżej zmienia przeglądarki dla całego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowiska:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
 Jeśli ustawiono flagi globalne `false`, a następnie zmiany metadanych jest lokalny dla biezacym projektantem obsługiwane przez bieżący pakiet VSPackage:  
  
 `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
 `internal class MyPackage : Package {}`  
  
> [!NOTE]
>  W chwili obecnej powierzchni projektowej obsługuje tylko tworzenie składników, a więc metadanymi lokalnymi tylko składniki. W powyższym przykładzie mamy próba zmodyfikowania właściwości, takie jak `Color` właściwości obiektu. Jeśli `false` została przekazana dla flagi globalne `CustomBrowser` nigdy nie będzie wyglądać, ponieważ projektanta nigdy tworzy wystąpienie `Color`. Ustawienie flagi globalne `false` jest przydatne w przypadku składniki, takie jak kontrolki, czasomierze i oknach dialogowych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
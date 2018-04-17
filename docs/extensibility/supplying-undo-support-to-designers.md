---
title: Dostarczanie cofnąć techniczną, aby projektanci | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5fc289426c2560e978819efcd8eaf17e56b224a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="supplying-undo-support-to-designers"></a>Dostarczanie Obsługa polecenia Cofnij konstruktorom
Projektanci, takie jak edytory, zazwyczaj konieczne obsługuje operacji cofania, dzięki czemu użytkownicy można cofnąć ich ostatnich zmian, modyfikując element kodu.  
  
 Większość projektantów zaimplementowany w programie Visual Studio ma automatycznie udostępniane przez środowisko Obsługa polecenia Cofnij.  
  
 Implementacje projektanta wymagające zapewnia obsługę funkcji cofania:  
  
-   Podaj zarządzania cofania zaimplementowanie abstrakcyjna klasa podstawowa <xref:System.ComponentModel.Design.UndoEngine>  
  
-   Trwałość dostawy i CodeDOM obsługuje zaimplementowanie <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> klasy.  
  
 Aby uzyskać więcej informacji na temat pisania projektantów przy użyciu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], zobacz [rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2).  
  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Zapewnia infrastrukturę cofania domyślne przez:  
  
-   Zapewnianie cofnąć implementacji management za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> i <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> klasy.  
  
-   Dostarczanie trwałości i pomocy technicznej CodeDOM za pomocą domyślnego <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> implementacji.  
  
## <a name="obtaining-undo-support-automatically"></a>Automatyczne uzyskiwanie Obsługa polecenia Cofnij  
 Projektanta utworzone w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] obsługuje automatyczne i pełne cofania projektanta, jeżeli:  
  
-   Sprawia, że użycie <xref:System.Windows.Forms.Control> na podstawie klasy interfejs użytkownika.  
  
-   Wykorzystuje przetwarzania systemu i generowanie kodu na podstawie CodeDOM standardowe dla generowania kodu i trwałości.  
  
     Aby uzyskać więcej informacji na temat pracy z programu Visual Studio CodeDOM pomocy technicznej, zobacz [dynamiczne generowanie kodu źródłowego i kompilacji](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)  
  
## <a name="when-to-use-explicit-designer-undo-support"></a>Kiedy należy używać Obsługa polecenia Cofnij projektanta jawne  
 Projektanci podać własne zarządzania cofania użycie graficznego interfejsu użytkownika, określone jako karty widoku, innego niż ten, dostarczonych przez <xref:System.Windows.Forms.Control>.  
  
 Na przykład może być tworzenie produktu z interfejsem sieci web projektu graficznego zamiast [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] na podstawie interfejsu graficznego.  
  
 W takich przypadkach jeden musi zarejestrować tej karty widoku z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy użyciu <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>i podaj zarządzania jawne cofania.  
  
 Projektanci wymaga podania CodeDOM i trwałości obsługuje, jeśli nie należy używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] model generowanie kodu w <xref:System.CodeDom> przestrzeń nazw.  
  
## <a name="undo-support-features-of-the-designer"></a>Cofnij funkcji obsługi projektanta  
 Zestaw SDK środowiska zawiera domyślne implementacje interfejsów potrzebnych do udostępniania cofnąć pomocy technicznej, które mogą być używane przez projektantów nie używa <xref:System.Windows.Forms.Control> na podstawie klasy dla ich interfejsy użytkownika lub standardowy modelu CodeDOM i trwałości.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Pochodną klasy [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> przy użyciu implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> klasy do zarządzania cofnąć operacji.  
  
 Program Visual Studio udostępnia następującą funkcję do projektanta cofania:  
  
-   Funkcja połączonego cofania w wielu projektantów.  
  
-   Podrzędne jednostki w Projektancie mogą prowadzić interakcję z ich elementów nadrzędnych, implementując <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> na <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.  
  
 Zestaw SDK środowiska umożliwia obsługę CodeDOM i trwałości podając:  
  
-   <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementacji <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
 A <xref:System.ComponentModel.Design.IComponentChangeService> podał [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]'' hosta projektu.  
  
## <a name="using-the-environment-sdk-features-to-supply-undo-support"></a>Przy użyciu funkcji zestawu SDK środowiska do dostarczania Obsługa polecenia Cofnij  
 Aby uzyskać pomoc techniczną cofania, obiekt implementujący projektanta musi:  
  
-   Utwórz wystąpienie i zainicjować wystąpienia <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> klasy z prawidłowym <xref:System.IServiceProvider> implementacji.  
  
-   To <xref:System.IServiceProvider> klasy należy podać następujące usługi:  
  
    -   <xref:System.ComponentModel.Design.IDesignerHost>.  
  
    -   <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  
  
         Projektanci przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serializacji CodeDOM może wybrać <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> wyposażone [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] jako jej implementacja <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.  
  
         W takim przypadku <xref:System.IServiceProvider> klasy do <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Konstruktor powinien zwrócić tego obiektu jako implementacja <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> klasy.  
  
    -   <xref:System.ComponentModel.Design.IComponentChangeService>  
  
         Projektanci przy użyciu domyślnego <xref:System.ComponentModel.Design.DesignSurface> dostarczonych przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hostem projektowania dotrą do mają domyślną implementację <xref:System.ComponentModel.Design.IComponentChangeService> klasy.  
  
 Projektanci implementacja <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> cofania na podstawie mechanizmu automatycznie śledzi zmiany, jeśli:  
  
-   Zmiany właściwości są wprowadzane za pośrednictwem <xref:System.ComponentModel.TypeDescriptor> obiektu.  
  
-   <xref:System.ComponentModel.Design.IComponentChangeService> zdarzenia są generowane ręcznie, gdy można cofnąć zmiana zostaje zatwierdzona.  
  
-   Modyfikowanie w Projektancie został utworzony w kontekście <xref:System.ComponentModel.Design.DesignerTransaction>.  
  
-   Projektant zdecydował się jawnie tworzyć jednostki cofania przy użyciu modułu cofnięcia standardowe, dostarczonej przez implementację elementu <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> lub implementacji programu Visual Studio specyficzne dla <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, pochodzący od <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> i udostępnia również Implementacja obu <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.Design.UndoEngine>   
 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>   
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
---
title: Dodawanie właściwości niestandardowych do diagramów zależności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f05c5f5a16b0d44794bf6fdcc6990a206dec30f5
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Dodawanie właściwości niestandardowych do diagramów zależności
Podczas pisania kodu rozszerzenie dla diagramów zależności wartości z żadnym elementem można przechowywać na diagramie zależności. Wartości będzie umieszczony po zapisaniu i ponownym otwarciu diagramu. Może także zawierać te właściwości są wyświetlane w **właściwości** okna tak, aby użytkownicy mogli widzieć i je edytować. Na przykład można zezwolić użytkownikom Określ wyrażenie regularne dla każdej warstwy, a napisać kod sprawdzania poprawności, aby sprawdzić, czy nazwy klasy w każdej warstwie jest zgodna z wzorcem określone przez użytkownika.  
  
## <a name="properties-not-visible-to-the-user"></a>Właściwości nie są widoczne dla użytkownika  
 Jeśli chcesz swój kod, aby dołączyć do dowolnego elementu na diagramie zależności wartości, nie trzeba definiować składników MEF. Jest słownikiem o nazwie `Properties` w <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Po prostu Dodaj zorganizowania wartości do słownika elementu wszystkie warstwy. Zostaną one zapisane jako część diagramu zależności. Aby uzyskać więcej informacji, zobacz [nawigowanie i aktualizowanie modeli w kodzie programu warstwy](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
## <a name="properties-that-the-user-can-edit"></a>Właściwości, które użytkownik może edytować  
 **Wstępnego przygotowania**  
  
> [!IMPORTANT]
>  Aby właściwości są wyświetlane, należy następującej zmiany na każdym komputerze, na którym ma właściwości warstwy, która będzie widoczna.  
>   
>  1.  Uruchom program Notatnik, używając **Uruchom jako Administrator**. Otwórz `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`  
> 2.  Wewnątrz `Content` elementu, dodać:  
>   
>     ```xml  
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>  
>     ```  
> 3.  W obszarze **programu Visual Studio Tools** część programu Visual Studio aplikacji menu start, otwórz **wiersza polecenia dewelopera**.  
>   
>      Wprowadź:  
>   
>      `devenv /rootSuffix /updateConfiguration`  
>   
>      `devenv /rootSuffix Exp /updateConfiguration`  
> 4.  Uruchom ponownie program Visual Studio.  
  
 **Upewnij się, że kod jest w projekcie VSIX**  
  
 Twoje właściwość jest częścią polecenia, gestu lub sprawdzania poprawności projektu, nie trzeba dodawać żadnych czynności. W projekcie programu Visual Studio Extensibility zdefiniowany jako składników MEF powinien być zdefiniowany kod dla właściwości niestandardowej. Aby uzyskać więcej informacji, zobacz [Dodawanie poleceń i gestów do diagramów zależności](../modeling/add-commands-and-gestures-to-layer-diagrams.md) lub [Dodawanie niestandardowej weryfikacji architektury do diagramów zależności](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 **Definiowanie właściwości niestandardowej**  
  
 Aby utworzyć właściwość niestandardową, należy zdefiniować klasę następująco:  
  
```  
[Export(typeof(IPropertyExtension))]  
public class MyProperty   
      : PropertyExtension<ILayerElement>  
{  
  // Implement the interface.  
}  
```  
  
 Można zdefiniować właściwości <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> ani dla żadnej z jej klas pochodnych, które obejmują:  
  
-   `ILayerModel` -modelu  
  
-   `ILayer` -poszczególnych warstw  
  
-   `ILayerDependencyLink` -łącza między warstwami  
  
-   `ILayerComment`  
  
-   `ILayerCommentLink`  
  
## <a name="example"></a>Przykład  
 Następujący kod jest deskryptora typowe właściwości niestandardowej. Definiuje właściwości typu Boolean na modelu warstwy (`ILayerModel`) umożliwiający użytkownika Podaj wartości dla metody niestandardowego sprawdzania poprawności.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
  
namespace MyNamespace  
{  
  /// <summary>  
  /// Custom properties are added to the Layer Designer via a custom  
  /// Property Descriptor. We have to export this Property Descriptor  
  /// using MEF to make it available in the Layer Designer.  
  /// </summary>  
  [Export(typeof(IPropertyExtension))]  
  public class AllTypesMustBeReferencedProperty   
      : PropertyExtension<ILayerModel>  
  {  
    /// <summary>  
    /// Each custom property must have a unique name.   
    /// Usually we use the full name of this class.  
    /// </summary>  
    public static readonly string FullName =  
      typeof(AllTypesMustBeReferencedProperty).FullName;  
  
    /// <summary>  
    /// Construct the property. Notice the use of FullName.  
    /// </summary>  
    public AllTypesMustBeReferencedProperty()  
            : base(FullName)  
    {  }  
  
    /// <summary>  
    /// The display name is shown in the Properties window.  
    /// We therefore use a localizable resource.  
    /// </summary>  
    public override string DisplayName  
    {  
      get { return Strings.AllTypesMustBeReferencedDisplayName; }  
    }  
  
    /// <summary>  
    /// Description shown at the bottom of the Properties window.  
    /// We use a resource string for easier localization.  
    /// </summary>  
    public override string Description  
    {  
      get { return Strings.AllTypesMustBeReferencedDescription; }  
    }  
  
    /// <summary>  
    /// This is called to set a new value for this property. We must  
    /// throw an exception if the value is invalid.  
    /// </summary>  
    /// <param name="component">The target ILayerElement</param>  
    /// <param name="value">The new value</param>  
    public override void SetValue(object component, object value)  
    {  
      ValidateValue(value);  
      base.SetValue(component, value);  
    }  
    /// <summary>  
    /// Helper to validate the value.  
    /// </summary>  
    /// <param name="value">The value to validate</param>  
    private static void ValidateValue(object value)  
    {  }  
  
    public override Type PropertyType  
    { get { return typeof(bool); } }  
  
    /// <summary>  
    /// The segment label of the properties window.  
    /// </summary>  
    public override string Category  
    {   
      get  
      {  
        return Strings.AllTypesMustBeReferencedCategory;  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie diagramów zależności](../modeling/extend-layer-diagrams.md)

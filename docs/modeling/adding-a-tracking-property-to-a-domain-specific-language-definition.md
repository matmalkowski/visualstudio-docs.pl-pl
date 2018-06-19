---
title: Dodawanie właściwości śledzenia do definicji języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: aec41a7ad2c93d9ad5762f8e4c7e67ea93704f1f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953864"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Dodaj właściwość śledzenia do definicji języka specyficznego dla domeny

W tym przewodniku przedstawiono sposób dodawania właściwości śledzenia do modelu domeny.

A *śledzenia domeny* właściwość jest właściwością, która może być aktualizowany przez użytkownika, ale który ma wartość domyślną, która jest obliczana przy użyciu wartości innych właściwości domeny lub elementów.

W narzędzia języka specyficznego dla domeny (narzędzia DSL), wyświetlana nazwa właściwości klasy domeny ma wartość domyślną, która jest obliczana przy użyciu nazwy klasy domeny, ale użytkownik może na przykład zmień wartość w czasie projektowania lub zresetować go do obliczonej wartości.

W tym przewodniku możesz utworzyć języka specyficznego dla domeny (DSL), którego Namespace, śledzenie właściwość, która ma wartość domyślną, na podstawie właściwości Namespace domyślny modelu. Aby uzyskać więcej informacji na temat śledzenia właściwości, zobacz [Definiowanie właściwości śledzenia](http://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

-   Obsługa narzędzia DSL, śledzenie deskryptorów właściwości. Jednak DSL projektanta nie można dodać właściwość śledzenia na język. W związku z tym należy dodać kodu niestandardowego do definiowania i implementować właściwość śledzenia.

 Właściwość śledzenia ma dwa stany: śledzenie i zaktualizowane przez użytkownika. Śledzenie właściwości mają następujące funkcje:

-   W przypadku stanu śledzenia jest obliczana wartość właściwości śledzenia, a wartość jest aktualizowana jako innych właściwości w przypadku zmiany modelu.

-   Kiedy w zaktualizowanego według stanu użytkownika, wartość właściwości śledzenia zachowuje wartość, do którego użytkownik ostatnim ustawieniu właściwości.

-   W **właściwości** okna, **zresetować** polecenia dla właściwości śledzenia jest włączona tylko, gdy właściwość jest zaktualizowane według stanu użytkownika. **Zresetować** polecenie ustawia właściwość śledzenia stanu do śledzenia.

-   W **właściwości** okna, gdy właściwość śledzenia jest w stanie śledzenia, jego wartość jest wyświetlana w regularnych czcionki.

-   W **właściwości** okna, gdy właściwość śledzenia jest zaktualizowane przez użytkownika stanu, jego wartość jest wyświetlana pogrubioną czcionką.

## <a name="prerequisites"></a>Wymagania wstępne

Przed skorzystaniem z tego przewodnika, należy najpierw zainstalować te składniki:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|

## <a name="create-the-project"></a>Utwórz projekt

1.  Tworzenie projektu Projektanta języka specyficznego dla domeny. Nadaj mu nazwę `TrackingPropertyDSL`.

2.  W **kreatora Designer języka specyficznego dla domeny**, ustaw następujące opcje:

    1.  Wybierz **MinimalLanguage** szablonu.

    2.  Użyj nazwy domyślnej dla języka specyficznego dla domeny `TrackingPropertyDSL`.

    3.  Ustawienia rozszerzenia plików modelu do `trackingPropertyDsl`.

    4.  Użyj ikony szablonu domyślnego dla plików modelu.

    5.  Ustaw nazwę produktu `Product Name`.

    6.  Ustaw nazwę firmy, aby `Company Name`.

    7.  Użyj wartości domyślnej dla głównej przestrzeni nazw dla projektów w rozwiązaniu, `CompanyName.ProductName.TrackingPropertyDSL`.

    8.  Zezwalaj na kreatora, aby utworzyć plik klucza o silnej nazwie z zestawów.

    9. Przejrzyj szczegóły rozwiązania, a następnie kliknij przycisk **Zakończ** do tworzenia projektu definicji DSL.

## <a name="customize-the-default-dsl-definition"></a>Dostosowywanie definicji domyślnej DSL
 W tej sekcji można dostosować definicję DSL zawiera następujące elementy:

-   Namespace, śledzenie właściwości dla każdego elementu modelu.

-   Właściwość logiczna IsNamespaceTracking dla każdego elementu modelu. Ta właściwość będzie wskazywać, czy właściwość śledzenia jest w stanie śledzenia lub zaktualizowane według stanu użytkownika.

-   Właściwość Namespace domyślne dla modelu. Ta właściwość będzie używana do obliczania wartości domyślne Namespace śledzenia właściwości.

-   Właściwość CustomElements obliczona dla modelu. Ta właściwość wskazuje część elementów, które mają niestandardowej przestrzeni nazw.

### <a name="to-add-the-domain-properties"></a>Aby dodać właściwości domeny

1.  W Projektancie DSL, kliknij prawym przyciskiem myszy **ExampleModel** klasy domeny, wskaż **Dodaj**, a następnie kliknij przycisk **DomainProperty**.

    1.  Nazwa nowej właściwości `DefaultNamespace`.

    2.  W **właściwości** ustawiony w oknie nową właściwość **wartość domyślną** do `DefaultNamespace`i ustaw **typu** do **ciąg**.

2.  Aby **ExampleModel** domeny Dodaj właściwość domeny o nazwie `CustomElements`.

     W **właściwości** ustawiony w oknie nową właściwość **rodzaj** do **obliczona**.

3.  Aby **ExampleElement** domeny Dodaj właściwość domeny o nazwie `Namespace`.

     W **właściwości** ustawiony w oknie nową właściwość **jest można przeglądać** do **False**i ustaw **rodzaj** do **wartości CustomStorage** .

4.  Aby **ExampleElement** domeny Dodaj właściwość domeny o nazwie `IsNamespaceTracking`.

     W **właściwości** ustawiony w oknie nową właściwość **jest można przeglądać** do **False**ustaw **wartość domyślną** do `true`i ustaw **Typu** do **logiczna**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Aby zaktualizować diagram elementów i szczegóły DSL

1.  W Projektancie DSL, kliknij prawym przyciskiem myszy **ExampleShape** geometrii kształtu, wskaż **Dodaj**, a następnie kliknij przycisk **Dekoratora tekstu**.

    1.  Nazwa nowej dekoratora tekstu `NamespaceDecorator`.

    2.  W **właściwości** dekoratora tekst w oknie Ustaw **pozycji** do **InnerBottomLeft**.

2.  W Projektancie DSL wybierz linii łączącej **ExampleElement** klasy do **ExampleShape** kształtu.

    1.  W **szczegóły DSL** wybierz **mapy Dekoratora** kartę.

    2.  W **Dekoratory** listy, wybierz **NamespaceDecorator**, zaznacz jej pole wyboru, a następnie na **Właściwość wyświetlania** listy, wybierz **Namespace**.

3.  W **DSL Explorer**, rozwiń węzeł **klasy domeny** folderu, kliknij prawym przyciskiem myszy **ExampleElement** węzeł, a następnie kliknij przycisk **Dodawanie nowej domeny deskryptor typu**.

    1.  Rozwiń węzeł **ExampleElement** , a następnie wybierz węzeł **deskryptora typu niestandardowego (deskryptor typu domeny)** węzła.

    2.  W **właściwości** ustawiony w oknie deskryptor typu domeny **kodowanego niestandardowe** do **True**.

4.  W **DSL Explorer**, wybierz pozycję **zachowanie serializacji Xml** węzła.

    1.  W **właściwości** ustaw **obciążenia Post niestandardowe** do **True**.

## <a name="transform-templates"></a>Przekształć szablony

Teraz, gdy zdefiniowano klasy i właściwości dla użytkownika DSL, możesz sprawdzić, czy definicja DSL można je przekształcać poprawnie można ponownie wygenerować kodu dla projektu.

1.  Na **Eksploratora rozwiązań** narzędzi, kliknij przycisk **Przekształć wszystkie szablony**.

2.  System generuje kod dla rozwiązania i zapisuje DslDefinition.dsl. Aby uzyskać informacje na temat formatu XML plików definicji, zobacz [plik DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Tworzenie plików niestandardowego kodu

Gdy Przekształć wszystkie szablony, system generuje kod źródłowy, który definiuje język specyficznego dla domeny w projektach Dsl i DslPackage. Tak, aby uniknąć konfliktu z wygenerowanego tekstu, należy zapisać niestandardowy kod w plikach, które różnią się od plików wygenerowanego kodu.

Musisz podać kod do przechowywania wartości i stanu Twojej właściwości śledzenia. Aby ułatwić rozróżnienie niestandardowy kod w wygenerowanym kodzie i uniknąć konfliktów nazw plików, należy umieścić pliki kodu niestandardowego w oddzielnym podfolderze.

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **DSL** projektu, wskaż pozycję **Dodaj**, a następnie kliknij przycisk **nowy Folder**. Nazwa nowego folderu `CustomCode`.

2.  Kliknij prawym przyciskiem myszy nowy **CustomCode** folderu, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.

3.  Wybierz **pliku kodu** szablonu, ustaw **nazwa** do `NamespaceTrackingProperty.cs`, a następnie kliknij przycisk **OK**.

     Plik NamespaceTrackingProperty.cs jest utworzony i otwarty do edycji.

4.  W folderze, należy utworzyć następujące pliki kodu: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, i `TypeDescriptor.cs`.

5.  W **DslPackage** projektu, należy także utworzyć `CustomCode` folderu i Dodaj do niej `Package.cs` pliku kodu.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Dodawanie klasy pomocy w celu obsługi śledzenia właściwości

Do pliku HelperClasses.cs dodać `TrackingHelper` i `CriticalException` klas w następujący sposób. Będzie odwoływać się te klasy w dalszej części tego przewodnika.

1.  Dodaj następujący kod do pliku HelperClasses.cs.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Dodaj niestandardowy kod dla deskryptora typu niestandardowego

Implementowanie `GetCustomProperties` deskryptor typu dla metody `ExampleModel` klasy domeny.

> [!NOTE]
> Kod generowany dla deskryptora typu niestandardowego narzędzia DSL `ExampleModel` wywołania `GetCustomProperties`; jednak narzędzia DSL nie generują kod, który implementuje metody.

Definiowanie ta metoda tworzy śledzenia deskryptora właściwości Namespace śledzenia właściwości. Ponadto umożliwia zapewnienie atrybuty dla właściwości śledzenia **właściwości** okno, aby prawidłowo wyświetlić właściwości.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Aby zmodyfikować deskryptora typu dla klasy domeny ExampleModel

1.  Dodaj następujący kod do pliku TypeDescriptor.cs.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Dodawanie niestandardowego kodu pakietu

Wygenerowany kod definiuje dostawcy opisu typu dla klasy domeny ExampleElement; jednak należy dodać kodu nakazać DSL do używania dostawcy opisu tego typu.

1.  Dodaj następujący kod do pliku Package.cs.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="add-custom-code-for-the-model"></a>Dodaj niestandardowy kod dla modelu

Implementowanie `GetCustomElementsValue` metodę `ExampleModel` klasy domeny.

> [!NOTE]
> Kod generowany dla narzędzia DSL `ExampleModel` wywołania `GetCustomElementsValue`; jednak narzędzia DSL nie generują kod, który implementuje metody.

Definiowanie `GetCustomElementsValue` metoda zapewnia logikę właściwości CustomElements obliczana `ExampleModel`. Ta metoda zlicza `ExampleElement` klasy domeny, które mają Namespace, śledzenie właściwość, która ma wartość użytkownik zaktualizował i zwraca wartość typu ciąg, który reprezentuje ta liczba jako część całkowita liczba elementów w modelu.

Ponadto Dodaj `OnDefaultNamespaceChanged` metodę `ExampleModel`i Zastąp `OnValueChanged` metody `DefaultNamespacePropertyHandler` zagnieżdżona klasa `ExampleModel` do wywołania `OnDefaultNamespaceChanged`.

Ponieważ właściwości DefaultNamespace służy do obliczania Namespace śledzenia właściwość `ExampleModel` należy powiadomić wszystkich `ExampleElement` klasy domeny, które wartość właściwości DefaultNamespace została zmieniona.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Aby zmodyfikować właściwości obsługę śledzonych właściwości

1.  Dodaj następujący kod do pliku ExampleModel.cs.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-for-the-tracking-property"></a>Dodaj niestandardowy kod dla właściwości śledzenia

Dodaj `CalculateNamespace` metody `ExampleElement` klasy domeny.

Definiowanie tej metody zawiera logikę właściwości CustomElements obliczana `ExampleModel`. Ta metoda zlicza `ExampleElement` klasy domeny, które mają Namespace, śledzenie właściwość, która jest zaktualizowane według stanu użytkownika i zwraca wartość typu ciąg, który reprezentuje ta liczba jako część całkowita liczba elementów w modelu.

Ponadto Dodaj magazyn dla i metody get i set-Namespace właściwości magazynu niestandardowego `ExampleElement` klasy domeny.

> [!NOTE]
> Kod generowany dla narzędzia DSL `ExampleModel` wywołuje get i metod; Ustaw jednak narzędzia DSL nie generują kod, który implementuje metody.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Aby dodać metodę dla deskryptora typu niestandardowego

1.  Dodaj następujący kod do pliku NamespaceTrackingProperty.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="add-custom-code-to-support-serialization"></a>Dodaj niestandardowy kod do obsługi serializacji

Dodaj kod, aby obsługiwać niestandardowe zachowanie po załadowaniu do serializacji XML.

> [!NOTE]
> Kod, że narzędzia DSL generować wywołania `OnPostLoadModel` i `OnPostLoadModelAndDiagram` metod; jednak narzędzia DSL nie generują kod, który implementuje tych metod.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Aby dodać kod, aby obsługiwać niestandardowe zachowanie po załadowaniu

1.  Dodaj następujący kod do pliku Serialization.cs.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="test-the-language"></a>Testowanie język

Następnym krokiem jest, aby skompilować i uruchomić projektanta DSL w nowe wystąpienie klasy [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] tak, aby sprawdzić, czy właściwość śledzenia działa poprawnie.

1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj ponownie rozwiązanie**.

2.  Na **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.

     Kompilacja eksperymentalne [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] otwiera **debugowanie** rozwiązania, które zawiera plik testowy puste.

3.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik Test.trackingPropertyDsl, aby otworzyć go w projektancie, a następnie kliknij przycisk powierzchnię projektu.

     Zwróć uwagę, że w **właściwości** w oknie diagram, **domyślne Namespace** właściwość jest **DefaultNamespace**i **elementy niestandardowe** właściwość jest **0/0**.

4.  Przeciągnij **ExampleElement** element z **przybornika** powierzchnię diagramu.

5.  W **właściwości** okna dla elementu, wybierz opcję **Namespace elementu** właściwości i zmień wartość **DefaultNamespace** do  **OtherNamespace**.

     Zwróć uwagę, że wartość **Namespace elementu** jest teraz pogrubione.

6.  W **właściwości** okna, kliknij prawym przyciskiem myszy **Namespace elementu**, a następnie kliknij przycisk **zresetować**.

     Wartość właściwości jest zmieniana na **DefaultNamespace**, i wartość jest wyświetlany w regularnych czcionki.

     Kliknij prawym przyciskiem myszy **Namespace elementu** ponownie. **Zresetować** polecenia jest obecnie wyłączony, ponieważ właściwość jest obecnie w stanie śledzenia.

7.  Przeciągnij kolejny **ExampleElement** z **przybornika** powierzchnię i zmień jego **Namespace elementu** do **OtherNamespace**.

8.  Kliknij przycisk powierzchnię projektu.

     W **właściwości** okna diagramu wartość **elementy niestandardowe** jest teraz **1/2**.

9. Zmień **domyślne Namespace** diagramu z **DefaultNamespace** do **właściwości, NewNamespace**.

     **Namespace** pierwszy ścieżki elementu **domyślne Namespace** właściwości, podczas gdy **Namespace** drugiego elementu zachowuje wartość użytkownik zaktualizował  **OtherNamespace**.

10. Zapisz rozwiązanie, a następnie zamknij eksperymentalne kompilacji.

## <a name="next-steps"></a>Następne kroki

Jeśli planujesz użyć śledzenia więcej niż jedną właściwość lub zaimplementowane właściwości śledzenia w więcej niż jeden DSL, można utworzyć szablonu tekstowego do generowania typowy kod obsługi każdej właściwości śledzenia. Aby uzyskać więcej informacji na temat szablonów tekstowych, patrz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Instrukcje: Definiowanie języka właściwego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)
- [Instrukcje: Tworzenie rozwiązania języka właściwego dla domeny](../modeling/how-to-create-a-domain-specific-language-solution.md)

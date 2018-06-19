---
title: Korzystanie z członków Microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych
ms.date: 03/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ccc41d7cc2e1150c6c4eb9ca1e62719517b194fa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975549"
---
# <a name="use-the-mstest-framework-in-unit-tests"></a>Za pomocą architektury MSTest w testy jednostkowe

[MSTest](<xref:Microsoft.VisualStudio.TestTools.UnitTesting>) framework obsługuje jednostki testowania w programie Visual Studio. Używać klas i członków <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzenią nazw, gdy są kodowania testów jednostkowych. Umożliwia także je podczas są korygowania testu jednostkowego, który został wygenerowany z kodu.

## <a name="framework-members"></a>Elementy członkowskie struktury

Aby zapewnić lepszy przegląd testowania framework jednostek, w tej części są uporządkowane członków <xref:Microsoft.VisualStudio.TestTools.UnitTesting> przestrzeni nazw w grupach funkcje.

> [!NOTE]
> Atrybut elementów, których nazwy kończyć się "Atrybutu", użyciem lub bez "Atrybutu" na końcu. Na przykład następujący przykładowy kod dwóch działać tak samo:
>
> `[TestClass()]`
>
> `[TestClassAttribute()]`

### <a name="members-used-for-data-driven-testing"></a>Elementy członkowskie używany do testów opartych na danych

Następujące elementy umożliwia konfigurowanie testów jednostkowych opartych na danych. Aby uzyskać więcej informacji, zobacz [utworzenia testu jednostkowego Data-driven](../test/how-to-create-a-data-driven-unit-test.md) i [Określ źródło danych przy użyciu pliku konfiguracji](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataAccessMethod>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElement>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceElementCollection>

## <a name="attributes-used-to-establish-a-calling-order"></a>Atrybuty używany do ustanawiania kolejności wywoływania

Element kodu ozdobione jedną z następujących atrybutów jest wywoływana w tej chwili, które określisz. Aby uzyskać więcej informacji, zobacz [anatomia testu jednostkowego](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

### <a name="attributes-for-assemblies"></a>Atrybuty dla zestawów

AssemblyInitialize i AssemblyCleanup są nazywane prawo po załadowaniu używanemu zestawowi oraz prawo przed używanemu zestawowi zostanie zwolniona.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssemblyCleanupAttribute>

### <a name="attributes-for-classes"></a>Atrybuty klasy

ClassInitialize i ClassCleanup są nazywane prawo po załadowaniu klasy i w prawo przed klasy zostanie zwolniona.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ClassCleanupAttribute>

### <a name="attributes-for-test-methods"></a>Atrybuty metody testowe

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>

## <a name="attributes-used-to-identify-test-classes-and-methods"></a>Atrybuty używane do identyfikowania testu klasy i metody

Każda klasa testu musi mieć `TestClass` musi mieć atrybut i każdej metody testowej `TestMethod` atrybutu. Aby uzyskać więcej informacji, zobacz [anatomia testu jednostkowego](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>

## <a name="assert-classes-and-related-exceptions"></a>Assert klasy i powiązanych wyjątków

Testy jednostkowe sprawdzić zachowanie aplikacji określonych przez ich użycie różnych rodzajów potwierdzeń, wyjątków i atrybuty. Aby uzyskać więcej informacji, zobacz [korzystanie z klas potwierdzeń](../test/using-the-assert-classes.md).

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

## <a name="the-testcontext-class"></a>Klasa TestContext

Następujące atrybuty i wartości do nich przypisane są wyświetlane w oknie właściwości usługi Visual Studio dla określonej metody. Te atrybuty nie mają być dostępne za pośrednictwem kod testu jednostkowego. Zamiast tego wpływają one na sposoby testu jednostkowego jest używany lub uruchom przez użytkownika za pomocą środowiska IDE programu Visual Studio lub aparat testów programu Visual Studio. Na przykład niektóre z tych atrybutów są wyświetlane jako kolumny w **Test Manager** okna i **wyników testu** okna, które oznacza, że można używać ich do grupy i sortować testy i wyniki testu. Jeden taki atrybut jest <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>, które umożliwia dodanie dowolnego metadanych do testów jednostkowych. Na przykład użytkownik może służyć do przechowywania nazwy przebiegu testowego, które obejmuje ten test, przez oznaczenie testu jednostkowego z `[TestProperty("TestPass", "Accessibility")]`. Lub może być używany do przechowywania wskaźnika typu testu jest z `[TestProperty("TestKind", "Localization")]`. Właściwości tworzenia za pomocą tego atrybutu, a wartość właściwości, należy przypisać zarówno wyświetlanych w programie Visual Studio **właściwości** okna pod nagłówkiem **konkretnego testu**.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DeploymentItemAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DescriptionAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.IgnoreAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.WorkItemAttribute>

## <a name="test-configuration-classes"></a>Klasy konfiguracji testu

- <xref:Microsoft.TeamFoundation.TestManagement.Client.ObjectTypes>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection>

## <a name="attributes-used-to-generate-reports"></a>Atrybuty używane do generowania raportów

Atrybuty w tej sekcji dotyczą metody testowej, która ich dekoracji dla jednostek w hierarchii projektu z projektu zespołowego Team Foundation Server.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssIterationAttribute>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CssProjectStructureAttribute>

## <a name="classes-used-with-private-accessors"></a>Klasy używane z prywatnych metod dostępu

Możesz wygenerować testu jednostkowego dla metody prywatnej. Tej generacji tworzy klasę prywatnego akcesora, która tworzy wystąpienie obiektu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> klasy. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject> Klasy to klasa otoki używającej odbicia w ramach procesu prywatnej metody dostępu. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType> Klasy jest podobny, ale jest używana do wywoływania prywatnych metod statycznych, zamiast wywoływania metod prywatnych wystąpienia.

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateObject>

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.PrivateType>

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting> dokumentacji

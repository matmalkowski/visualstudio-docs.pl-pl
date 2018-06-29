---
title: Przybornik, karta Dane
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1af6ac0f9a382a91d2c87e5cb84053b8b51bf961
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089675"
---
# <a name="toolbox-data-tab"></a>Przybornik, karta Dane

Wyświetla obiekty danych, które można dodać do formularzy i składniki. **Danych** karcie **przybornika** pojawia się podczas tworzenia projektu, który ma skojarzone projektanta. **Przybornika** pojawia się domyślnie w programie Visual Studio zintegrowane środowisko programistyczne; konieczne jest wyświetlenie **przybornika**, wybierz pozycję **przybornika** z **Widoku** menu.

> [!TIP]
> Uruchomiony Kreator konfiguracji źródła danych, automatycznie tworzy i konfiguruje większość elementów danych. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](../../data-tools/add-new-data-sources.md).

## <a name="ui-element-list"></a>Lista elementów interfejsu użytkownika

Aby przejść bezpośrednio do strony odwołanie .NET Framework dla składnika, naciśnij **F1** na elemencie **przybornika** lub w elemencie składnika w zasobniku projektanta.

|Nazwa|Opis|
|----------|-----------------|
|<xref:System.Data.DataSet>|Dodaje wystąpienie typizowany lub nietypizowany zestaw danych do formularza lub składnika. Ten obiekt przeciągnij projektanta, wyświetla okno dialogowe, który umożliwia wybranie istniejącej klasy typizowanego zestawu danych lub określ, czy chcesz utworzyć nowy, pusty, bez typu zestawu danych. **Uwaga:** nie należy używać <xref:System.Data.DataSet> obiekt na **przybornika** można utworzyć nowego zestawu danych typu schematu i klasy. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../../data-tools/create-and-configure-datasets-in-visual-studio.md).|
|<xref:System.Windows.Forms.DataGridView>|Zapewnia wydajny i elastyczny sposób wyświetlania danych w formacie tabelarycznym.|
|<xref:System.Windows.Forms.BindingSource>|Upraszcza proces powiązania kontroli źródła danych.|
|<xref:System.Windows.Forms.BindingNavigator>|Reprezentuje nawigacji i manipulacji interfejsu użytkownika (UI) dla formantów w formularzu, które są związane z danymi.|

## <a name="see-also"></a>Zobacz też

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../../data-tools/accessing-data-in-visual-studio.md)
- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Narzędzia zestawu danych w programie Visual Studio](../../data-tools/dataset-tools-in-visual-studio.md)
- [Powiązywanie formantów z danymi w Visual Studio](../../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Powiązywanie formantów formularzy systemu Windows z danymi w Visual Studio](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Edytowanie danych w zestawach danych](../../data-tools/edit-data-in-datasets.md)
- [Weryfikowanie danych w zestawach danych](../../data-tools/validate-data-in-datasets.md)
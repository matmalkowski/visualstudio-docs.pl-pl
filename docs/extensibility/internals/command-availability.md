---
title: Polecenie dostępności | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ee0f746b87fcc83e9967ea65be08b8f4b04f2e3f
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="command-availability"></a>Polecenie dostępności

W kontekście programu Visual Studio Określa, które polecenia są dostępne. W zależności od bieżącego projektu, bieżącego edytora VSPackages, które zostały załadowane i innych aspektów zintegrowane środowisko programistyczne (IDE), można zmienić kontekstu.

## <a name="command-contexts"></a>Konteksty polecenia

Konteksty poniższe polecenia są najbardziej rozpowszechnione.

-   **IDE** poleceń IDE są zawsze dostępne.

-   **Pakiet VSPackage** VSPackages można zdefiniować, kiedy są polecenia mają być wyświetlane lub ukryte.

-   **Projekt** polecenia projektu są wyświetlane tylko dla aktualnie wybranego projektu.

-   **Edytor** tylko jeden z nich mogą być aktywne w czasie. Polecenia w edytorze active są dostępne. Edytor ściśle współpracuje z usługą języka. Usługa języka musi przetworzyć polecenia w kontekście skojarzone edytora.

-   **Typ pliku** edytora można załadować więcej niż jeden typ pliku. Dostępne polecenia, można zmienić w zależności od typu pliku.

-   **Aktywne okno** ostatniego okna dokumentów aktywnych ustawia kontekst interfejsu użytkownika dla powiązania klucza. Jednak okna narzędzia, która zawiera tabelę klucza — wiązanie podobny wewnętrznej przeglądarce sieci Web można również ustawić kontekst interfejsu użytkownika. Okna dokumentów z wieloma kartami takich jak edytor HTML co kartę ma kontekst polecenia inny identyfikator GUID. Po zarejestrowaniu okna narzędzia są zawsze dostępne na **widoku** menu.

-   **Kontekst interfejsu użytkownika** kontekstów interfejsu użytkownika są identyfikowane za pomocą wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> klasy, na przykład <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> podczas tworzenia rozwiązania lub <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> gdy debuger jest aktywny. Wielu kontekstów interfejsu użytkownika mogą być aktywne w tym samym czasie.

## <a name="defining-custom-context-guids"></a>Definiowanie kontekstu niestandardowych identyfikatorów GUID

Jeśli kontekst odpowiednie polecenia, którego identyfikator GUID nie jest już zdefiniowany, można zdefiniować w VSPackage i następnie program to być aktywne lub nieaktywne zgodnie z wymaganiami, aby kontrolować widoczności poleceń.

1.  Zarejestruj identyfikatorów GUID kontekstu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody.

2.  Pobierz stan kontekstu GUID przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody.

3.  Włączanie i wyłączanie identyfikatorów GUID kontekstu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.

    > [!CAUTION]
    > Upewnij się, że VSPackage nie wpływa na dowolnym kontekście istniejących identyfikatorów GUID, ponieważ inne pakiety VSPackage może zależeć od nich.

## <a name="see-also"></a>Zobacz także

- [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
---
title: Polecenie Dostępność | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98250763f504bc7d142f15e559334f296a2e026b
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511137"
---
# <a name="command-availability"></a>Dostępność poleceń

Kontekst programu Visual Studio Określa, jakie polecenia są dostępne. Kontekst można zmienić w zależności od bieżącego projektu, bieżącego edytora, pakietów VSPackage, które są ładowane i inne aspekty zintegrowanego środowiska programistycznego (IDE).

## <a name="command-contexts"></a>Konteksty polecenia

Następujących kontekstów się polecenia są najbardziej rozpowszechnione:

- IDE: Poleceń środowiska IDE są zawsze dostępne.

- Pakietu VSPackage: Pakietów VSPackage można zdefiniować podczas poleceń mają być wyświetlane lub ukryte.

- Projekt: Polecenia projektu są widoczne tylko dla obecnie wybranego projektu.

- Edytor: Tylko jeden z nich może być aktywne w danym momencie. Polecenia z aktywnego edytora są dostępne. Edytor ściśle współpracuje z usługą language. Usługa językowa musi przetworzyć polecenia w kontekście skojarzonego edytora.

- Typ pliku: Edytor mogą ładować więcej niż jeden typ plików. Dostępne polecenia można zmienić w zależności od typu pliku.

- Aktywne okno: ostatni aktywne okno dokumentu ustawia kontekst interfejsu użytkownika dla powiązań klawiszy. Jednak okna narzędzi, które ma jedną tabelę powiązanie klucza, który przypomina wewnętrznej przeglądarki sieci web można również ustawić kontekstu interfejsu użytkownika. Dla systemu windows z wieloma kartami dokumentu, takich jak edytor HTML każda karta ma innego polecenia kontekstu identyfikatora GUID. Po zarejestrowaniu okna narzędzia jest zawsze dostępne na **widoku** menu.

- Kontekstu interfejsu użytkownika: kontekstów interfejsu użytkownika są identyfikowane za pomocą wartości <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> klasy, na przykład <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> podczas kompilowania rozwiązania lub <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> gdy aktywny jest debugera. Wiele kontekstów interfejsu użytkownika może być aktywne w tym samym czasie.

## <a name="define-custom-context-guids"></a>Zdefiniuj kontekstowego identyfikatorów GUID

Jeśli kontekst odpowiednie polecenia, identyfikator GUID nie jest już zdefiniowany, możesz zdefiniować w swojej pakietu VSPackage i Zaprogramuj się być aktywne lub nieaktywne zgodnie z potrzebami można kontrolować widoczność poleceń:

1.  Rejestrowanie identyfikatorów GUID w kontekście przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody.

2.  Pobieranie stanu kontekstu identyfikatora GUID, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody.

3.  Włączanie i wyłączanie identyfikatorów GUID w kontekście przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody.
   
> [!CAUTION]
> Upewnij się, że Twoje pakietu VSPackage nie wpływa na wszystkich kontekstach istniejące identyfikatory GUID ponieważ innych pakietów VSPackage może zależeć od ich.

## <a name="see-also"></a>Zobacz także

- [Wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md)
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
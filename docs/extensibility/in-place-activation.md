---
title: Aktywacja w miejscu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - in-place view activation
ms.assetid: 7d316945-06e0-4d8e-ba3a-0ef96fc75399
manager: douge
ms.openlocfilehash: d20c88dbb93712c7ef2e6342cbb3d9cd0d38a086
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131636"
---
# <a name="in-place-activation"></a>Aktywacja w miejscu
Jeśli widok Edytor obsługuje ActiveX lub innych formantów active, musi implementować widoku edytora jako formant ActiveX lub jako aktywny dokument. obiekt danych przy użyciu modelu aktywacji w miejscu.  
  
## <a name="support-for-menus-toolbars-and-commands"></a>Obsługa menu, pasków narzędzi i poleceń  
 Program Visual Studio umożliwia widok edytora, aby używać menu i pasków narzędzi IDE. Te rozszerzenia są określane jako *OLE w miejscu składniki*. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> i <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager>.  
  
 W przypadku zastosowania formantu ActiveX, mogą być hostowane inne obiekty osadzone. Obiekt danych dokumentu w przypadku zastosowania, ramki okna ogranicza możliwość korzystania z kontrolki ActiveX.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> interfejsy umożliwiają do rozdzielania dane i przeglądać. Jednak program Visual Studio nie obsługuje tej funkcji, a te interfejsy są używane tylko do reprezentowania obiektu widoku dokumentu.  
  
 Edytory, które używają <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi zapewniają menu, paska narzędzi i integracja z polecenia przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfejs implementowany przez <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi. Edytory można zaoferować inne funkcje programu Visual Studio, takie jak śledzenie zaznaczenia i Cofnij zarządzania. Aby uzyskać więcej informacji, zobacz [projektanci i tworzenie niestandardowych edytory](../extensibility/creating-custom-editors-and-designers.md).  
  
## <a name="objects-and-interfaces-used"></a>Obiekty i interfejsy używane  
 Obiekty, które są używane do tworzenia Aktywacja w miejscu przedstawiono na poniższej ilustracji.  
  
 ![In&#45;place Activation Editor](../extensibility/media/vsinplaceactivationeditor.gif "vsInPlaceActivationEditor")  
Edytor aktywacji w miejscu  
  
> [!NOTE]
>  Obiekty w tym rysunku, tylko `CYourEditorFactory` obiektu jest wymagane do utworzenia standardowego edytora. W przypadku tworzenia edytora niestandardowego, nie należy do implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> ponieważ edytora prawdopodobnie będzie miał własną mechanizmu stanu trwałego prywatnych. Aby uzyskać więcej informacji, zobacz [projektanci i tworzenie niestandardowych edytory](../extensibility/creating-custom-editors-and-designers.md).  
  
 Wszystkie interfejsy implementowane utworzyć aktywacji w miejscu edytora są wyświetlane na pojedynczą `CYourEditorDocument` obiekt, ale ta konfiguracja obsługuje tylko pojedynczy widok danych dokumentu. Aby uzyskać więcej informacji na temat obsługi wielu widoków danych dokumentu, zobacz [obsługi wielu widoków dokumentu](../extensibility/supporting-multiple-document-views.md).  
  
|Interface|Typ obiektu|Zastosowanie|  
|---------------|--------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>|Widok|Włącza w miejscu pakiet VSPackage obiektów do działania jako składniki pełni zintegrowane środowisko IDE przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> usługi. Ta usługa integruje się z menu, pasków narzędzi i poleceń obiektu IDE i wystawia powiadomienia o zmianie stanu.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>|Widok|Podmiotu zabezpieczeń oznacza, że za pomocą którego osadzonego obiektu zapewnia podstawowe funkcje do jego kontenera i komunikuje się z nim.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>|Widok|Zarządza Aktywacja i dezaktywacja obiektów w miejscu i określa, ile obiektu w miejscu powinny być widoczne.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceObject>|Widok|Udostępnia bezpośredni channel komunikacji między skojarzonej aplikacji zewnętrznych ramkę okna, okno dokumentu w aplikacji, która zawiera osadzonego obiektu i obiektu w miejscu.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>|Widok|Implementuje obiektu ActiveX. Należy pamiętać, że metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocumentView> czy oddzielny dokument dane i przeglądać nie są używane w środowisku IDE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Wyświetlanie i danych|Umożliwia obiektu danych dokumentu obiekt widoku dokumentu i/lub do udziału w obsłudze polecenia.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Widok|Włącza aktualizacje paska stanu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Widok|Umożliwia dodawanie elementów do przybornika.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Dane|Wysyła powiadomienia o zmianach edytowanego pliku. (Ten interfejs jest opcjonalny).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Dane|Umożliwia włączenie funkcji Zapisz jako dla typu pliku.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Dane|Włącza trwałość dla dokumentu. W przypadku plików tylko do odczytu, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SetDocDataReadOnly%2A> zapewnienie ikonę "lock", który wskazuje pliki tylko do odczytu.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Dane|Określa, czy należy ją ignorować zmiany danych dokumentu.|
---
title: Struktura pakietu VSPackage (VSPackage kontroli źródła) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d36e31db9c47325e62fe759cd5030c5f24fb73be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057626"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (pakiet VSPackage kontroli kodu źródłowego)

Zestaw SDK pakietu kontroli źródła zawiera wytyczne dotyczące tworzenia pakiet VSPackage, który zezwala na implementujący kontroli źródła, jego funkcja kontroli źródła jest integrowana z środowiska Visual Studio. Pakiet VSPackage jest składnik COM, który jest zwykle ładowane na żądanie przez Visual Studio zintegrowane środowisko programistyczne (IDE) na podstawie usług, które są rozgłaszane przez pakiet w nim wpisów rejestru. Każdy pakiet VSPackage musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Pakiet VSPackage zwykle zużywa usług oferowanych przez środowiska IDE programu Visual Studio i proffers niektóre usługi własnych.

Pakiet VSPackage deklaruje elementy jego menu i ustanawia domyślny stan elementu za pomocą pliku vsct. Środowiska IDE programu Visual Studio wyświetla elementów menu w tym stanie do momentu załadowania pakiet VSPackage. Następnie pakiet VSPackage implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda jest wywoływana, aby włączyć lub wyłączyć elementów menu.

## <a name="source-control-package-characteristics"></a>Właściwości pakietu kontroli źródła

Pakiet VSPackage kontroli źródła jest ściśle zintegrowana w programie Visual Studio. Semantyka pakiet VSPackage obejmują:

-   Interfejs do zaimplementowania przez trwa pakiet VSPackage ( `IVsPackage` interfejsu)

-   Wykonanie polecenia interfejsu użytkownika (pliku vsct i stosowania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)

-   Rejestracja pakiet VSPackage z programem Visual Studio.

Kontroli źródła pakiet VSPackage muszą komunikować się z innymi jednostkami Visual Studio:

-   Projekty

-   Edytory

-   Rozwiązania

-   Windows

-   Uruchomionej tabeli dokumentów

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Usługi środowiska Visual Studio, które mogą być używane

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Usługa SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP interfejsy zaimplementowane i o nazwie

Pakiet kontroli źródła jest pakiet VSPackage, a więc może współdziałać bezpośrednio z innych VSPackages, które są zarejestrowane w usłudze Visual Studio. Aby zapewnić rozmaitych funkcja kontroli źródła, kontroli źródła pakiet VSPackage można uwzględniać interfejsami projektów lub powłoki.

Każdy projekt w programie Visual Studio musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> zostały rozpoznane jako projekt w programie Visual Studio IDE. Jednak ten interfejs nie jest przeznaczone wystarczająca do kontroli źródła. Wdrożenie kontroli projektów, które powinny być w sekcji źródłowej <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Ten interfejs jest używany przez pakiet VSPackage kontroli źródła do badania projekt do jego zawartości i do tego celu symboli i informacje o powiązaniu (informacje potrzebne do nawiązywania połączenia między lokalizacji serwera i lokalizację dysku projektu, który znajduje się w kontroli źródła).

Implementuje pakiet VSPackage kontroli źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, co z kolei umożliwia projektów, aby zarejestrować się do kontroli źródła i pobrać symboli ich stan.

Aby uzyskać pełną listę interfejsów, które należy wziąć pod uwagę kontroli źródła pakiet VSPackage, zobacz [powiązanych usług i interfejsów](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Zobacz także

- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
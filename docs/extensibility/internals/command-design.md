---
title: Polecenie projektu | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- commands, implementation
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: "34"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fe3db0582c65a2ece2162ab24afb6d179b865a27
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="command-design"></a>Polecenie projektu
Dodając polecenie do pakiet VSPackage, należy określić, którym jest wyświetlany, jeśli jest dostępny i jak ma być obsługiwane.  
  
## <a name="defining-commands"></a>Definiowanie polecenia  
 Aby zdefiniować nowe polecenia, należy dołączyć plik tabeli poleceń w usłudze Visual Studio (vsct) w projekcie pakiet VSPackage. Jeśli utworzono pakiet VSPackage przy użyciu szablonu pakietu Visual Studio, projekt zawiera jeden z tych plików. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio scala wszystkie pliki vsct znalezionych tak, aby go wyświetlić polecenia. Ponieważ te pliki są różne od pakiet VSPackage binarnego, Visual Studio nie ma się załadowanie pakietu można znaleźć polecenia. Aby uzyskać więcej informacji, zobacz [jak VSPackages Dodaj elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio będzie korzystać <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> atrybutów rejestracji, aby zdefiniować zasoby menu i poleceń. Aby uzyskać więcej informacji, zobacz [implementacji](../../extensibility/internals/command-implementation.md).  
  
 Polecenia można zmienić w czasie wykonywania na kilka różnych sposobów. One mogą być wyświetlane lub ukryte, włączone lub wyłączone. Ich wyświetlania ikon lub inny tekst lub zawierają różne wartości. Bardzo duże możliwości dostosowania mogą być wykonywane przed Visual Studio ładuje VSPackage. Aby uzyskać więcej informacji, zobacz [jak VSPackages Dodaj elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## <a name="command-handlers"></a>Programy obsługi poleceń  
 Podczas tworzenia polecenia, musisz podać program obsługi zdarzeń w celu wykonania tego polecenia. Jeśli użytkownik wybierze polecenie, należy odpowiednio kierowane. Routing polecenie oznacza wysłanie ich do poprawne pakiet VSPackage, aby włączyć lub ją wyłączyć, Ukryj lub wyświetl ją i wykonaj go, jeśli użytkownik zdecyduje się w tym celu. Aby uzyskać więcej informacji, zobacz [routingu algorytmu](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="the-visual-studio-command-environment"></a>Polecenie środowiska Visual Studio  
 Visual Studio może zawierać dowolną liczbę VSPackages, a każdy może przyczynić się własny zestaw poleceń. Środowisko zawiera tylko z poleceniami, które są odpowiednie do bieżącego zadania. Aby uzyskać więcej informacji, zobacz [dostępności](../../extensibility/internals/command-availability.md) i [wybór obiektów kontekstu](../../extensibility/internals/selection-context-objects.md).  
  
 Pakiet VSPackage, który definiuje nowego polecenia, menu, pasków narzędzi lub menu skrótów zapewnia informacje o jego polecenia programu Visual Studio w momencie instalacji za pomocą wpisy rejestru, które odwołują się do zasobów w zestawach natywnego lub zarządzanego. Następnie każdy zasób odwołuje się do danych binarnych pliku zasobów (.cto), który jest tworzony podczas kompilowania pliku tabeli poleceń w usłudze Visual Studio (vsct). Dzięki temu Visual Studio, aby zapewnić zestawy poleceń scalone, menu i pasków narzędzi bez konieczności obciążenia co zainstalowany pakiet VSPackage.  
  
### <a name="command-organization"></a>Polecenie organizacji  
 Środowisko umieszcza polecenia przez grupę, priorytet i menu.  
  
-   Grupy są zbiorami logicznymi pokrewne polecenia, na przykład, **Wytnij**, **kopiowania**, i **Wklej** grupy poleceń. Grupy są poleceniami, które są wyświetlane w menu.  
  
-   Priorytet określa kolejność wyświetlania poszczególnych poleceń w grupie w menu.  
  
-   Menu działają jak kontenery grup.  
  
 Środowisko powoduje wstępne definiowanie niektórych poleceń, grup i menu. Aby uzyskać więcej informacji, zobacz [polecenie domyślne, grupy i umieszczania narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Polecenie można przypisać do głównej grupy. Grupy podstawowej Określa położenie polecenia w strukturze menu głównego, a w **Dostosuj** okno dialogowe. Polecenie może występować w wielu grupach; na przykład polecenie może być w menu głównym, w menu skrótów i na pasku narzędzi. Aby uzyskać więcej informacji, zobacz [jak VSPackages Dodaj elementy interfejsu użytkownika](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### <a name="command-routing"></a>Routing poleceń  
 Proces wywoływania i routing poleceń dla VSPackages różni się od proces wywoływania metod dla wystąpienia obiektu.  
  
 Środowisko kieruje polecenia sekwencyjnie z kontekstu najbardziej polecenia (local), które jest oparte na bieżącym zaznaczeniu, peryferyjnych kontekst (globalne). Pierwszy kontekście, który jest w stanie wykonać polecenia jest to, która je obsługuje. Aby uzyskać więcej informacji, zobacz [routingu algorytmu](../../extensibility/internals/command-routing-algorithm.md).  
  
 W większości przypadków środowisko obsługi przy użyciu polecenia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Ponieważ polecenie schemat routingu umożliwia wiele różnych obiektów poleceń, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> może być zaimplementowany przez dowolną liczbę obiektów; te obejmują kontrolek ActiveX firmy Microsoft, okno widoku implementacji, obiekty dokumentów, hierarchii projektu i pakiet VSPackage same obiekty (w przypadku polecenia globalne). W niektórych przypadkach specjalnych, na przykład routingu poleceń w hierarchii, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu muszą zostać zaimplementowane.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Implementacja](../../extensibility/internals/command-implementation.md)|Opisuje sposób wykonania polecenia w pakiecie VSPackage.|  
|[Dostępność](../../extensibility/internals/command-availability.md)|W tym artykule opisano, jak Visual Studio kontekstu Określa, które polecenia są dostępne.|  
|[Algorytm routingu](../../extensibility/internals/command-routing-algorithm.md)|W tym artykule opisano, jak architektura routingu polecenia programu Visual Studio umożliwia poleceń, które mają być obsługiwane przez różnych VSPackages.|  
|[Wskazówki dotyczące umieszczania](../../extensibility/internals/command-placement-guidelines.md)|Sugeruje położenie poleceń w środowisku Visual Studio.|  
|[Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|W tym artykule opisano, jak VSPackages najlepiej może korzystać z architekturą polecenia programu Visual Studio.|  
|[Domyślne położenie poleceń, grup i pasków narzędzi](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|W tym artykule opisano, jak VSPackages najlepiej używać poleceń, które znajdują się w programie Visual Studio.|  
|[Zarządzanie pakietami VSPackage](../../extensibility/managing-vspackages.md)|W tym artykule opisano, jak Visual Studio ładuje VSPackages.|  
|[Tabela poleceń programu Visual Studio (pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Zawiera informacje o plikach vsct opartych na języku XML, które służą do opisywania układu i wyglądu poleceń w VSPackages.|
---
title: Interfejs użytkownika właściwości projektu | Dokumentacja firmy Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9355cd730d58b19dbae0840fa225032ca3ec1589
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="project-property-user-interface"></a>Interfejs użytkownika właściwości projektu
Podtyp projektu można użyć elementów w projekcie **strony właściwości** — okno dialogowe jak są one dostarczane przez podstawową projektu, Ukryj lub był służy tylko do odczytu i całe strony dostarczony lub Dodaj stron specyficzne dla podtypu projektu do **Strony właściwości** okno dialogowe.

## <a name="extending-the-project-property-dialog-box"></a>Rozszerzanie okno dialogowe właściwości projektu
 Podtyp projektu implementuje rozszerzeń automatyzacji i obiektów przeglądania konfiguracji projektu. Wdrożenie tych rozszerzeń <xref:EnvDTE.IFilterProperties> interfejsu aby określonej właściwości ukryte lub tylko do odczytu. **Strony właściwości** okno dialogowe podstawowego projektu, zaimplementowana przez podstawowy projekt będzie honorować filtrowania wykonywane przez rozszerzeń automatyzacji.

 Proces rozszerzania **właściwości projektu** okno dialogowe opisanym poniżej:

-   Podstawowy projekt pobiera rozszerzeń z podtypu projektu zaimplementowanie <xref:EnvDTE80.IInternalExtenderProvider> interfejsu. Przeglądanie, automatyzacja projektu i projektu obiektów przeglądania konfiguracji podstawowej wszystkich projektu implementuje ten interfejs.

-   Implementacja <xref:EnvDTE80.IInternalExtenderProvider> dla obiekt przeglądania projektu i projektu obiektu automatyzacji delegować do <xref:EnvDTE80.IInternalExtenderProvider> implementacji agregatora podtypu projektu (oznacza to, że ich `QueryInterface` dla <xref:EnvDTE80.IInternalExtenderProvider> na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt projektu).

-   Obiekt przeglądania konfiguracji podstawowej projektu implementuje również <xref:EnvDTE80.IInternalExtenderProvider> do okablować bezpośrednio w rozszerzenie automatyzacji z obiektu konfiguracji podtypu projektu. Jej implementacja deleguje do <xref:EnvDTE80.IInternalExtenderProvider> interfejsu zaimplementowanego przez agregator podtypu projektu.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementowane przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu.

-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, również jest implementowana przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiektu.

-   Podtyp projektu można określić odpowiednie CATIDs dla różnych obiektów rozszerzalne podstawowa projektu w czasie wykonywania, pobierając następujące <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wartości:

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>

Aby ustalić CATIDs dla zakresu projektu, podtypu projektu pobiera powyżej właściwości [VSITEMID. Główny](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>) z `VSITEMID typedef`. Podtyp projektu może być również kontrolować, które **strony właściwości** strony — okno dialogowe są wyświetlane w projekcie obu konfiguracji zależne i niezależne. Niektóre podtypów projektu może być konieczne usuwanie stron, wbudowane i Dodaj określonych stron podtypu projektu. Aby włączyć to wywołania projektu zarządzanego klienta <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metody następujących właściwości:

-   `VSHPROPID_PropertyPagesCLSIDList` — Rozdzielana średnikami lista CLSID strony właściwości niezależny od konfiguracji.

-   `VSHPROPID_CfgPropertyPagesCLSIDList —` Rozdzielana średnikami lista CLSID strony właściwości zależne od konfiguracji.

Ponieważ agregacje podtypu projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu, można zmienić definicji te właściwości, można kontrolować, które **strony właściwości** są wyświetlane w oknach dialogowych. Podtyp projektu można pobrać te właściwości z podstawowej wewnętrzny projektu, a następnie dodaj lub usuń CLSID w razie potrzeby.

Nowe strony właściwości dodane przez podtypu projektu przekazuje obiekt przeglądania konfiguracji projektu z wdrożenia podstawowego projektu. Ten obiekt przeglądania konfiguracji projektu obsługuje rozszerzeń automatyzacji. Aby uzyskać więcej informacji o AutomationExtenders, zobacz [wdrażania i przy użyciu rozszerzeń automatyzacji](http://msdn.microsoft.com/Library/0d5c218c-f412-4b28-ab0c-33a611f62356). Strony właściwości implementowane przez wywołanie podtypu projektu <xref:EnvDTE.Project.Extender%2A> można pobrać własnych projektu podtyp konfiguracji przeglądania obiektu prowadzący obiekt przeglądania konfiguracji podstawowej projektu.

## <a name="see-also"></a>Zobacz także

- <xref:EnvDTE.IFilterProperties>
- [Strony właściwości — okno dialogowe](http://msdn.microsoft.com/en-us/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
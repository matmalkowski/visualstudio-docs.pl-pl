---
title: Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97eed0e4cec143e51195347bfb90d430d8e1eadb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573001"
---
# <a name="manage-documents-on-a-server-by-using-the-serverdocument-class"></a>Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument
  Można użyć `ServerDocument` klasy w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do zarządzania kilka aspektów dostosowań na poziome dokumentu, nawet jeśli nie zainstalowano programu Microsoft Office Word i Microsoft Office Excel. Można wykonywać następujące zadania:  
  
-   Dostęp i modyfikowanie danych w pamięci podręcznej danych dokumentu lub skoroszytu. Aby uzyskać więcej informacji, zobacz [pracować z buforowane dane w dokumencie](#CachedData).  
  
-   Zarządzanie zestawu dostosowania, który jest skojarzony z dokumentem. Aby uzyskać więcej informacji, zobacz [Zarządzanie dostosowania dokumentu](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understand-the-serverdocument-class"></a>Zrozumienie klasy ServerDocument  
 `ServerDocument` Klasy jest przeznaczony do użycia na komputerach, które nie mają zainstalowany pakiet Office. W związku z tym używane zwykle do tej klasy w aplikacjach, które obsługują pakiet Office, takich jak projekty konsoli lub projektów formularzy systemu Windows, a nie projektów pakietu Office. Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* zestawu.  
  
 `ServerDocument` Klasa może być używana do działania na poziomie dokumentu, które zostały utworzone przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Aby uzyskać więcej informacji dotyczących programu Visual Studio 2010 Tools for Office Runtime oraz rozszerzenia pakietu Office dla programu .NET Framework, zobacz [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Jeśli masz starszej wersji aplikacji, która używa `ServerDocument` klasy w `Visual Studio Tools for Office` system (w wersji 3.0 Runtime), `Visual Studio Tools for Office` system (wersja 3.0 runtime) musi być zainstalowany na komputerach z systemem aplikacji. `Visual Studio 2010 Tools for Office runtime` Nie można uruchomić te aplikacje.  
  
##  <a name="CachedData"></a> Praca z pamięci podręcznej danych w dokumencie  
 `ServerDocument` Klasa udostępnia służy do pracy z pamięci podręcznej danych w dokumentach dostosowane elementy członkowskie. Aby uzyskać więcej informacji o pamięci podręcznej danych, zobacz [dane z pamięci podręcznej](../vsto/caching-data.md) i [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 W poniższej tabeli przedstawiono składniki, które służy do pracy z pamięci podręcznej danych.  
  
|Zadanie|Elementu członkowskiego do użycia|  
|----------|-------------------|  
|Aby określić, czy dokument ma pamięci podręcznej danych.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> Metody.|  
|Aby uzyskać dostęp do pamięci podręcznej danych dokumentu.<br /><br /> Aby uzyskać więcej informacji, zobacz [dostęp do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Właściwości.|  
  
##  <a name="CustomizationInfo"></a> Zarządzanie dostosowania dokumentu  
 Korzystając z członkami `ServerDocument` klasy do zarządzania zestawu dostosowania, który jest skojarzony z dokumentem. Na przykład można programistycznie usunąć dostosowań z dokumentu, aby dokument nie jest już częścią dostosowanie.  
  
 W poniższej tabeli wymieniono elementy członkowskie, których można użyć do zarządzania zestawu dostosowania.  
  
|Zadanie|Elementu członkowskiego do użycia|  
|----------|-------------------|  
|Aby określić, czy dokument jest częścią dostosowania poziomie dokumentu.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> Metody.|  
|Aby programowo dołączyć dostosowanie do dokumentów w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [jak: dołączanie rozszerzenia kodu do dokumentów zarządzanych](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Jeden z <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody.|  
|Aby programowo usunąć dostosowanie dokumentu w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: usuwanie kodu rozszerzeń zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> Metody.|  
|Aby uzyskać adres URL manifestu rozmieszczenia, który jest skojarzony z dokumentem.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> Właściwości.|  
  
## <a name="see-also"></a>Zobacz także  
 [Porady: dołączanie rozszerzenia kodu do dokumentów zarządzanych](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Porady: Usuwanie rozszerzenia managed extensions kodu z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Dane w pamięci podręcznej](../vsto/caching-data.md)  
  
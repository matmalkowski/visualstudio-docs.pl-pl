---
title: "Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], managing on server
- Office documents [Office development in Visual Studio, managing on server
- ServerDocument class, managing documents on server
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2120e7c70abaddd4f51c0214a2c5ae517cf955cc
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="managing-documents-on-a-server-by-using-the-serverdocument-class"></a>Zarządzanie dokumentami na serwerze za pomocą klasy ServerDocument
  Można użyć klasy ServerDocument w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do zarządzania kilka aspektów dostosowań na poziome dokumentu, nawet jeśli nie zainstalowano programu Microsoft Office Word i Microsoft Office Excel. Można wykonywać następujące zadania:  
  
-   Dostęp i modyfikowanie danych w pamięci podręcznej danych dokumentu lub skoroszytu. Aby uzyskać więcej informacji, zobacz [Praca z pamięci podręcznej danych, w dokumencie](#CachedData).  
  
-   Zarządzanie zestawu dostosowania, który jest skojarzony z dokumentem. Aby uzyskać więcej informacji, zobacz [Zarządzanie dostosowania dokumentu](#CustomizationInfo).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="understanding-the-serverdocument-class"></a>Omówienie klasy ServerDocument  
 Klasy ServerDocument jest przeznaczony do użycia na komputerach, które nie mają zainstalowany pakiet Office. W związku z tym używane zwykle do tej klasy w aplikacjach, które obsługują pakiet Office, takich jak projekty konsoli lub projektów formularzy systemu Windows, a nie projektów pakietu Office. Użyj <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> klasy w zestawie Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
 Klasy ServerDocument może służyć do działania na poziomie dokumentu, które zostały utworzone przy użyciu [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)].  
  
 Aby uzyskać więcej informacji dotyczących programu Visual Studio 2010 Tools for Office Runtime oraz rozszerzenia pakietu Office dla programu .NET Framework, zobacz [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
> [!NOTE]  
>  Jeśli masz starszych aplikacji używającej klasy ServerDocument w Visual Studio Tools dla pakietu Office system (w wersji 3.0 środowiska uruchomieniowego), Visual Studio Tools dla pakietu Office system (w wersji 3.0 Runtime) musi być zainstalowany na komputerach z systemem aplikacji. Visual Studio 2010 Tools for Office Runtime nie można uruchomić te aplikacje.  
  
##  <a name="CachedData"></a>Praca z pamięci podręcznej danych w dokumencie  
 Klasy ServerDocument zawiera członków, których można użyć do pracy z pamięci podręcznej danych w dokumentach dostosowane. Aby uzyskać więcej informacji o pamięci podręcznej danych, zobacz [buforowanie danych](../vsto/caching-data.md) i [uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).  
  
 W poniższej tabeli przedstawiono składniki, które służy do pracy z pamięci podręcznej danych.  
  
|Zadanie|Elementu członkowskiego do użycia|  
|----------|-------------------|  
|Aby określić, czy dokument ma pamięci podręcznej danych.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> Metody.|  
|Aby uzyskać dostęp do pamięci podręcznej danych dokumentu.<br /><br /> Aby uzyskać więcej informacji, zobacz [uzyskiwanie dostępu do danych w dokumentach na serwerze](../vsto/accessing-data-in-documents-on-the-server.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Właściwości.|  
  
##  <a name="CustomizationInfo"></a>Zarządzanie dostosowania dokumentu  
 Elementy członkowskie klasy ServerDocument służy do zarządzania zestawu dostosowania, który jest skojarzony z dokumentem. Na przykład można programistycznie usunąć dostosowań z dokumentu, aby dokument nie jest już częścią dostosowanie.  
  
 W poniższej tabeli wymieniono elementy członkowskie, których można użyć do zarządzania zestawu dostosowania.  
  
|Zadanie|Elementu członkowskiego do użycia|  
|----------|-------------------|  
|Aby określić, czy dokument jest częścią dostosowania poziomie dokumentu.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> Metody.|  
|Aby programowo dołączyć dostosowanie do dokumentu w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: dołączanie kodu rozszerzeń zarządzanych do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)|Jeden z <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> metody.|  
|Aby programowo usunąć dostosowanie dokumentu w czasie wykonywania.<br /><br /> Aby uzyskać więcej informacji, zobacz [porady: usuwanie zarządzane rozszerzenia kodu z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md).|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> Metody.|  
|Aby uzyskać adres URL manifestu rozmieszczenia, który jest skojarzony z dokumentem.|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> Właściwości.|  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: dołączanie rozszerzenia kodu zarządzanego do dokumentów](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [Porady: Usuwanie rozszerzenia kodu zarządzanego z dokumentów](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime ― Przegląd](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Buforowanie danych](../vsto/caching-data.md)  
  
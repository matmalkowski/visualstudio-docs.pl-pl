---
title: Automatyzacja konfiguracji i obiekty SelectedItem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d4ac269664136aed51542e53900ffc1c87f21fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja konfiguracji i obiekty SelectedItem
Można zautomatyzować kompilacji i procesy wybranego elementu w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automatyzacja dla kompilacji  
 Kompilacji lub konfiguracji ma model automatyzacji, który jest dostępne w przypadku implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Aby uzyskać więcej informacji, zobacz [opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md).  
  
 Utwórz pakiet VSPackage, aby kontrolować opcje konfiguracji należy użyć model automatyzacji.  
  
## <a name="automation-for-selecteditem"></a>Automatyzacja dla SelectedItem  
 Nie masz do implementacji `SelectedItem` obiektu, ponieważ program Visual Studio zawiera standardowej implementacji. Jednak można zaimplementować `SelectedItem` obiektu, jeśli wolisz. Musisz zaimplementować obiekt, który zawiera `SelectedItem` interfejsu i zwracać odpowiedzi na wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> ustawiona metoda z VSITEMID <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Współtworzenie Model automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Ogólne informacje o konfiguracjach kompilacji](../../ide/understanding-build-configurations.md)
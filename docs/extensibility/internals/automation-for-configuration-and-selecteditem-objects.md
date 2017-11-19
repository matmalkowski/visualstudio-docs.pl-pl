---
title: Automatyzacja konfiguracji i obiekty SelectedItem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 42a3b8bdd8930c9006ba49fd0f2e2dd2491b38cb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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
 [Opis konfiguracji kompilacji](../../ide/understanding-build-configurations.md)
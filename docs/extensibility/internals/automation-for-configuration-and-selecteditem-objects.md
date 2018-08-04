---
title: Automatyzacja konfiguracji i obiektów SelectedItem | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 4a1c745ad8f40ac755513f49db7b522f83f075a8
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500735"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automatyzacja obiektów konfiguracji i SelectedItem
Można zautomatyzować kompilacji i procesy wybranego elementu w [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automatyzacja kompilacji  
 Kompilacji lub konfiguracji ma modelu automatyzacji, który znajduje się podczas implementowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Aby uzyskać więcej informacji, zobacz [konfiguracje kompilacji omówienie](../../ide/understanding-build-configurations.md).  
  
 Jeśli utworzysz pakietu VSPackage i chcesz określić opcje konfiguracji, należy użyć modelu automatyzacji.  
  
## <a name="automation-for-selecteditem"></a>Automatyzacja SelectedItem  
 Nie trzeba dostarczyć implementację `SelectedItem` obiektu, ponieważ program Visual Studio zawiera standardowej implementacji. Jednakże, można zaimplementować `SelectedItem` obiektu, jeśli wolisz. Musisz zaimplementować obiekt, który zawiera `SelectedItem` interfejs i zwraca odpowiedź do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody z `VSITEMID` równa <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Współtworzenie modelu automatyzacji](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [O konfiguracjach kompilacji](../../ide/understanding-build-configurations.md)
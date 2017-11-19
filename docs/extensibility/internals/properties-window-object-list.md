---
title: "Lista obiektów okna właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, object list
ms.assetid: 6c159c9d-345d-4b23-8ddd-9839d338b62f
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dad79623bbc721c67c19a37436d2bf5e64b93c59
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-object-list"></a>Lista obiektów okno właściwości
Lista obiektów w **właściwości** okno jest listy rozwijanej, który pozwala na zmianę zaznaczenie do innych obiektów, które są dostępne w ramach jednego lub więcej wybranych systemu windows. Wybranie innego obiektu z na tej liście wyzwala wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> informują środowisko wybrano nowego obiektu. Informacje wyświetlane w **właściwości** okna jest następnie zmieniane, aby wyświetlić właściwości skojarzone z nowo wybranego obiektu.  
  
## <a name="the-object-list"></a>Lista obiektów  
 Lista obiektów składa się z dwóch pól: Nazwa obiektu (wyświetlone czcionką pogrubioną) i typ obiektu.  
  
 Nazwa obiektu wyświetlane na lewo od typu obiektu pogrubione jest pobierana z obiektu przy użyciu `Name` właściwości udostępniane przez <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> interfejsu. <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo.GetClassInfo%2A>, jedyną metodą na <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, zwraca <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> dla danego interfejsu klasy coclass. **Właściwości** używa okna <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo> nazwy klasy coclass, która jest wyświetlana jako nazwa obiektu na liście rozwijanej.  
  
 Jeśli obiekt nie ma `Name` właściwości, nazwa nie jest wyświetlany w obszarze Nazwa listy obiektów. Właściwość Name można dodać do obiektu, jeśli nazwa wyświetlana na liście obiektów.  
  
 Jeśli obiekt COM nie implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IProvideClassInfo>, **właściwości** okno wyświetla nazwę interfejsu zamiast nazwy obiektu po lewej stronie listy.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md)
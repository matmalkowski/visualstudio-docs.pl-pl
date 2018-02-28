---
title: "Szczegóły czasu wykonywania kontroli źródła | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 9b27aa56cdcf48ded56f9a43e40a1e65f3491536
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-runtime-details"></a>Szczegóły czasu wykonywania kontroli źródła
Projekt zostanie dodany do kontroli źródła, gdy użytkownik dodaje plik do projektu do kontroli źródła, albo przez kontroler automatyzacji, takich jak kreatora. Projekt nie określa dla siebie jest pod kontrolą źródła. obsługuje kontroli źródła, ale należy je dodać ręcznie do niego.  
  
## <a name="registering-with-a-source-control-package"></a>Rejestrowanie przy użyciu pakietu kontroli źródła  
 Gdy plik projektu zostanie dodany do kontroli źródła, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> zapewnienie cztery nieprzezroczyste ciągów, które są używane jako plików cookie przez system kontroli źródła. Przechowuj te ciągi w pliku projektu. Te ciągi powinny zostać przekazane do Stub kontroli źródła (składnika programu Visual Studio, która zarządza pakietów kontroli źródła) uruchamianie projektu typu przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. To z kolei ładuje pakiet kontroli odpowiednie źródłowe i przekazuje wywołanie jej implementacja `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
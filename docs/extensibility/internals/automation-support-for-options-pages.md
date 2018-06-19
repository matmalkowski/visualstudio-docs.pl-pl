---
title: Obsługa automatyzacji dla strony opcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d27ad706d4203a3573a734a1cd11b19e3c9df6a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128575"
---
# <a name="automation-support-for-options-pages"></a>Obsługa automatyzacji dla strony opcji
VSPackages zapewniają niestandardowe **opcje** okien dialogowych do **narzędzia** w menu (strony opcji narzędzi) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i udostępnić je do modelu automatyzacji.  
  
## <a name="tools-options-pages"></a>Strony opcji narzędzi  
 Aby utworzyć **opcje narzędzia** strony, pakiet VSPackage należy udostępnić implementację formantu użytkownika zwrócony do środowiska za pośrednictwem implementacja pakiet VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metody (lub dla zarządzanego kodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> Metoda).  
  
 Jest opcjonalna, ale zalecamy, aby zezwolić na dostęp do tej nowej strony za pomocą modelu automatyzacji. Można to zrobić przez następujące kroki:  
  
1.  Rozszerzanie <xref:EnvDTE._DTE.Properties%2A> obiektu za pomocą implementacji obiektu pochodzi od elementu IDispatch.  
  
2.  Zwrócić implementacje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> — metoda (lub dla kodu zarządzanego <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> metody) do obiektu pochodzi od elementu IDispatch.  
  
3.  Gdy wywołuje konsumenta automatyzacji <xref:EnvDTE._DTE.Properties%2A> metoda niestandardowego **opcji** strony właściwości środowiska używa <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodę, aby uzyskać niestandardowego **opcje narzędzia** automatyzacji strony Implementacja.  
  
4.  Obiektu automatyzacji pakiet VSPackage są następnie używane do zapewnienia każdego <xref:EnvDTE.Property> zwrócony przez <xref:EnvDTE._DTE.Properties%2A>.  
  
 Przykładowe wdrożenie niestandardowej strony opcji narzędzi, zobacz [przykłady VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie obiektów projektu](../../extensibility/internals/exposing-project-objects.md)
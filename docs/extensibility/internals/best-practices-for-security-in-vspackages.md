---
title: Najlepsze rozwiązania dotyczące zabezpieczeń w VSPackages | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 689c85e090e44612a87474e8c77dc0e146706e84
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127305"
---
# <a name="best-practices-for-security-in-vspackages"></a>Najlepsze rozwiązania dotyczące zabezpieczeń w VSPackages
Aby zainstalować [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] na komputerze, musi być uruchomione w kontekście przy użyciu poświadczeń administracyjnych. Podstawowa jednostka zabezpieczeń i wdrażania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplikacja jest [VSPackages](../../extensibility/internals/vspackages.md). Pakiet VSPackage musi być zarejestrowana przy użyciu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], które również wymaga poświadczeń administracyjnych.  
  
 Administratorzy mają pełne uprawnienia do zapisu do rejestru i systemu plików, a także do uruchomienia dowolnego kodu. Musi mieć te uprawnienia, wdrażanie, lub zainstaluj pakiet VSPackage.  
  
 Zaraz po jego zainstalowaniu, pakiet VSPackage jest w pełni zaufany. Z powodu wysokiego poziomu uprawnień skojarzonych z pakiet VSPackage jest możliwe zainstalowanie przypadkowo pakiet VSPackage, który ma złośliwymi działaniami.  
  
 Użytkownicy powinien zapewnić ich instalację VSPackages tylko z zaufanych źródeł. Firmom tworzenie VSPackages należy zdecydowanie nazwy i podpisywał je, aby upewnić się, że użytkownik naruszeniu tego nie będzie mógł. Tworzenie VSPackages firm sprawdzić ich zależności zewnętrzne, takie jak usługi sieci web i instalacji zdalnej, aby ocenić i rozwiąż wszelkie problemy z zabezpieczeniami.  
  
 Aby uzyskać więcej informacji, zobacz Secure wskazówki dotyczące pisania kodu platformy .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dodatek zabezpieczeń](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX zabezpieczeń](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)